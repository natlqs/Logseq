- Contents
	- ((62457ca2-d99d-4b0a-b575-c29e5339931e))
	- ((62457da4-93d0-4210-a473-59200f225972))
- Linux内核及发行版
	- Linux内核
	  id:: 62457ca2-d99d-4b0a-b575-c29e5339931e
		- Linux内核是操作系统内部**操作和控制硬件设备的核心程序**，他是芬兰人林纳斯开发的。
	- Linux发行版是Linux内核与各种常用软件的组合产品，通俗来说就是我们常说的Linux操作系统，所以不同的发行版的区别就是各种软件组合的不同，内核都是一样的。
	- 常用的Linux发行版：
		- Ubuntu
		- CentOs
		- Redhat
	-
- Linux命令
  id:: 62457da4-93d0-4210-a473-59200f225972
	- 查看目录命令
		- |命令|说明|
		  |ls|查看当前路径下的目录信息|
		  |tree|以树状方式显示目录|
		  |pwd|查看当前目录路径|
		  |clear|清除终端内容|
		  |ctrl + shift + ”+“|放大窗口字体|
		  |ctrl + ”-“|缩小窗口字体|
	- 切换目录命令
		- ![image.png](../assets/image_1648721615796_0.png){:height 329, :width 586}
	- 绝对路径和相对路径
		- 从根目录算起的路径叫做绝对路径
			- `/home/python/Desktop`
		- 从当前目录算起的路径叫做相对路径
			- `./test/hello`
			- `../static/images`
			-
	- 创建、删除文件和目录命令
		- ![image.png](../assets/image_1648721953805_0.png)
	- 复制、移动文件和目录命令
		- ![image.png](../assets/image_1648722019676_0.png)
		  id:: 62458041-98ae-4eed-8a0f-bea50c6ef0e8
		- `cp a a_cp -r`   -r 表示文件里的所有东西一起复制
		- `cp ./heima ./a`  把当前目录的heima文件拷贝到a文件夹下
		- `mv ./heima_cp ./a`    把heima_cp这个文件移动到a文件夹下
		- `mv ./a ./b`    把文件夹a移动到文件夹b下
		- `mv heima new_name`    把heima重命名为 new_name
	- 远程登陆、远程拷贝命令
		- ![image.png](../assets/image_1648722479307_0.png){:height 154, :width 718}
		- ssh命令的使用
			- ssh是一种协议，协议的目的是使数据的传输更加安全。
			- 使用需要安装相应的服务端和客户端软件。
				- 假如Ubuntu作为服务端，需安装ssh服务端软件，执行命令 `sudo apt-get install opensh-server`
				- macOs不需要安装ssh客户端软件，默认已安装
				- Windows系统则需要安装OpenSSH for Windwos软件
				- 登录命令 ： `ssh python@172.16.62.136`  ssh 远程服务器用户名@远程服务器IP地址
			- scp命令的使用
				- scp是基于ssh进行安全的远程文件拷贝的命令，也就是说需要保证服务端和客户端电脑安装了相应的ssh软件。
				- 远程拷贝文件：
					- scp 本地文件 远程服务器用户名@远程服务器ip地址：指定拷贝到远程服务器的路径
					- scp 远程服务器用户名@远程服务器ip地址：远程服务器文件 指定拷贝到本地的路径
				- 远程拷贝目录：
					- scp -r 本地目录 远程服务器用户名@远程服务器ip地址：指定拷贝到远程服务器的路径
					- scp -r 远程服务器用户名@远程服务器ip地址：远程服务器目录 指定拷贝到本地的路径
					- -r 表示递归拷贝整个目录
		- 软件安装、软件卸载
			- 软件安装
				- 离线安装  deb文件格式安装
					- deb是Ubuntu的安装包格式，可以使用dpkg命令进行软件的安装和卸载。
					- `sudo dpkg -i deb安装包`    离线安装deb安装包
				- 在线安装 apt-get方式安装
					- apt-get是在线安装deb软件包的方式，主要用于在线从互联网的软件仓库中搜索、安装、升级、卸载软件
						- `sudo apt-get install 安装包`  在线安装deb安装包
				- 离线安装
					- 离线安装包的卸载
						- `sudo dpkg -r 安装包名`
					- 在线安装包的卸载
						- `sudo apt-get remove 安装包名`
-
-