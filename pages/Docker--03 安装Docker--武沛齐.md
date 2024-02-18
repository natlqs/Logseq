# 安装Docker

![image-20230528074433855](assets/image-20230528074433855.png){:height 123, :width 964}
- 学习环境：win电脑  ->  centos7虚拟机【docker】   -> docker容器
- 线上环境：云平台    ->  购买云主机【docker】          -> docker容器
- # 1.安装docker-ce社区版
- 配置repo源
  
  ```
  curl -o /etc/yum.repos.d/Centos-7.repo http://mirrors.aliyun.com/repo/Centos-7.repo
  curl -o /etc/yum.repos.d/docker-ce.repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
  
  yum clean all && yum makecache
  ```
- 查看可下载版本
  
  ```
  yum list docker-ce --showduplicates | sort -r
  ```
- 安装
  
  ```perl
  # 最新版
  yum install -y docker-ce
  
  # 指定版本
  yum install -y docker-ce-23.0.6
  ```
- # 2.启动docker-ce社区版
- 设置开机启动
  
  ```
  systemctl enable docker 
  ```
- 启动docker
  
  ```
  systemctl start docker  
  ```
  
  ```
  systemctl restart docker 
  ```
- 停止docker
  
  ```
  systemctl stop docker  
  ```
- 其他
  
  ```powershell
  ## 查看docker信息
  docker version
  
  ## 查看docker信息
  docker info
  
  ## docker-client
  which docker
  
  ## docker daemon
  ps -ef |grep docker
  ```
- # 3.宿主机网卡转发
  
  ```
  cat <<EOF > /etc/sysctl.d/docker.conf
  net.bridge.bridge-nf-call-ip6tables = 1
  net.bridge.bridge-nf-call-iptables = 1
  net.ipv4.conf.default.rp_filter = 0
  net.ipv4.conf.all.rp_filter = 0
  net.ipv4.ip_forward=1
  EOF
  ```
  
  ```
  sysctl -p /etc/sysctl.d/docker.conf
  ```
- # 4.配置镜像加速
  
  类似于pip源，以后在docker中下载镜像时，使用加速器，下载就会比较快。
  
  https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors
  
  ![image-20230527181407037](assets/image-20230527181407037.png)
  
  
  
  https://www.daocloud.io/mirror#accelerator-doc
  
  ![image-20230527233200415](assets/image-20230527233200415.png)
  
  
  
  ```
  sudo mkdir -p /etc/docker
  ```
  
  ```
  sudo tee /etc/docker/daemon.json <<-'EOF'
  {
  "registry-mirrors": [
    "https://t57hdrx1.mirror.aliyuncs.com",
    "http://f1361db2.m.daocloud.io"
  ]
  }
  EOF
  ```
  
  ```
  systemctl daemon-reload
  systemctl restart docker 
  ```
  
  
  
  
  
  
  
  
  
  
  
  ```
  讲师：武沛齐
  微信：wupeiqi666
  B站主页：
  https://space.bilibili.com/336469068
  https://space.bilibili.com/283478842
  ```