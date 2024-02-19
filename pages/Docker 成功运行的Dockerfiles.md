## Debian+Django+Sqlite3
	- ```
	  # Base images 基础镜像
	  FROM centos:7.9.2009
	  
	  #MAINTAINER 维护者信息
	  LABEL maintainer natlqs@outlook.com
	  
	  
	  # GCC编译器
	  RUN yum install gcc -y
	  
	  # Python依赖
	  RUN yum install -y zlib zlib-devel bzip2 bzip2-devel ncurses ncurses-devel readline readline-devel openssl openssl-devel  xz lzma xz-devel sqlite sqlite-devel gdbm gdbm-devel tk tk-devel  mysql-devel python-devel libffi-devel
	  
	  # wget
	  RUN yum install wget -y
	  
	  # 目录
	  RUN mkdir -p /data/
	  WORKDIR /data/
	  
	  # SQLite升级
	  RUN wget https://www.sqlite.org/2024/sqlite-autoconf-3450100.tar.gz  --no-check-certificate
	  RUN tar -zxvf sqlite-autoconf-3450100.tar.gz
	  WORKDIR /data/sqlite-autoconf-3450100
	  RUN ./configure
	  RUN make && make install
	  ENV LD_LIBRARY_PATH="/usr/local/lib"
	  
	  # Python3.12环境
	  WORKDIR /data/
	  RUN wget https://www.python.org/ftp/python/3.12.1/Python-3.12.1.tgz
	  RUN tar -xvf Python-3.12.1.tgz
	  WORKDIR /data/Python-3.12.1/
	  RUN ./configure --with-ssl
	  RUN ./configure --prefix=/usr/local/python3
	  RUN make && make install
	  RUN ln -s /usr/local/bin/pip3 /usr/bin/pip3
	  RUN yum install -y python3-pip
	  RUN pip3 install -U pip
	  RUN pip3 config set global.index-url https://pypi.douban.com/simple/
	  
	  # git
	  RUN yum install git -y
	  RUN git config --global user.name "natlqs"
	  RUN git config --global user.email "natlqs@outlook.com"
	  
	  # git拉代码
	  WORKDIR /data/
	  RUN git clone https://gitee.com/natlqs/resturant.git
	  
	  
	  # 虚拟环境
	  RUN pip3 install virtualenv -i https://pypi.douban.com/simple/ --trusted-host pypi.douban.com
	  RUN virtualenv  /envs/resturant --python=python3
	  RUN /envs/resturant/bin/pip3 install django pillow
	  
	  # 运行项目
	  WORKDIR /data/resturant
	  
	  CMD ["/envs/resturant/bin/python","manage.py","runserver","0.0.0.0:9000"]
	  ```
-