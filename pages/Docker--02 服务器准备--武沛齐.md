# 学习环境准备

![image-20230528074433855](assets/image-20230528074433855.png)
- 在win电脑安装：**vmware工具** + **创建centos系统（初始化）**
- # 1.VMware
- ## 1.1 下载安装
  
  > 下载后，无脑点击安装即可。
  
  ![image-20230527161048647](assets/image-20230527161048647.png)
- ## 1.2 虚拟化支持
  
  ![image-20230529115828887](assets/image-20230529115828887.png)
  
  
  
  ![image-20230527161335914](assets/image-20230527161335914.png)
  
  注意：开启后重启即可，如果电脑提示无法启动，则需要先进入bios在主板中设置开启支持Hyper-V。
- # 2.CentOS系统
  
  https://mirrors.tuna.tsinghua.edu.cn/centos/7.9.2009/isos/x86_64/
  
  ![image-20230527162958934](assets/image-20230527162958934.png)
  
  
  
  ![image-20230527161048647](assets/image-20230527161048647.png)
  
  
  
  ![image-20230527153846358](assets/image-20230527153846358.png)
  
  ![image-20230527153902312](assets/image-20230527153902312.png)
  
  ![image-20230527153930911](assets/image-20230527153930911.png)
  
  ![image-20230527154018143](assets/image-20230527154018143.png)
  
  ![image-20230527154030142](assets/image-20230527154030142.png)
  
  ![image-20230527165448792](assets/image-20230527165448792.png)
  
  ![image-20230527154105097](assets/image-20230527154105097.png)
  
  ![image-20230527165554552](assets/image-20230527165554552.png)
  
  
  
  ![image-20230527154359448](assets/image-20230527154359448.png)
  
  ![image-20230527154554996](assets/image-20230527154554996.png)
  
  ![image-20230527154538749](assets/image-20230527154538749.png)
  
  
  
  ![image-20230527154706589](assets/image-20230527154706589.png)
  
  
  
  ![image-20230527154754260](assets/image-20230527154754260.png)
  
  
  
  ```
  >>>uname -r
  >>>cat /etc/redhat-release
  ```
  
  
  
  ![image-20230527155315560](assets/image-20230527155315560.png)
- # 3.网络配置
  
  默认登录无法上网，需要配置下网络才行。
- ## 3.1 Win电脑
  
  配置DNS和网关
  
  ![image-20230527233658158](assets/image-20230527233658158.png)
- ## 3.2 CentOS主机
  
  ![image-20230527170655785](assets/image-20230527170655785.png)
  
  
  
  
  
  ![image-20230527165802943](assets/image-20230527165802943.png)
  
  ![image-20230527170150062](assets/image-20230527170150062.png)
  
  ```
  TYPE=Ethernet
  PROXY_METHOD=none
  BROWSER_ONLY=no
  BOOTPROTO=static         # 由原来的dhcp改成static
  DEFROUTE=yes
  IPV4_FAILURE_FATAL=no
  IPV6INIT=yes
  IPV6_AUTOCONF=yes
  IPV6_DEFROUTE=yes
  IPV6_FAILURE_FATAL=no
  IPV6_ADDR_GEN_MODE=stable-privacy
  NAME=ens33
  UUID=cfbd5cd7-fa17-48e6-9d13-715f33e1f08d
  DEVICE=ens33
  ONBOOT=yes              # 由原来的no改成yes
  IPADDR=192.168.115.133  # 新增，当前主机的IP
  GATEWAY=192.168.115.2   # 网关
  NETMASK=255.255.255.0   # 掩码
  DNS1=8.8.8.8            # NDS服务器
  DNS2=8.8.4.4            # NDS服务器
  ```
  
  
  
  ![image-20230527170102150](assets/image-20230527170102150.png)
  
  ```
  service network restart
  ```
  
  ```
  systemctl restart network
  ```
  
  
  
  重启后，可以ping百度测试：
  
  ```
  ping baidu.com
  ```
  
  ![image-20230527170312611](assets/image-20230527170312611.png)
- # 4.系统初始化
- 关闭selinux
	- 查看状态
	  
	  ```
	  getenforce
	  ```
	- 临时关闭
	  
	  ```
	  setenforce 0
	  ```
	- 永久关闭
	  
	  ```
	  vi /etc/selinux/config
	  ```
	  
	  ```
	  # 设置为disabled
	  SELINUX=disabled
	  ```
- 防火墙
	- 查看防火墙状态
	  
	  ```
	  systemctl status firewalld
	  ```
	- 关闭
	  
	  ```
	  systemctl stop firewalld
	  ```
	- 关闭开机启动防火墙
	  
	  ```
	  systemctl disable firewalld
	  ```
- net-tools
  
  ```
  yum install net-tools -y
  ```
- openssh-server
  
  ```
  yum install openssh-server -y
  ```
  
  ```
  systemctl start sshd.service
  ```
  
  ```
  systemctl enable sshd.service
  ```
- 可以在win上用xshell等工具SSH连接centos
- wget
  
  ```
  yum install wget -y
  ```
- centos常用工具包
  
  ```
  yum install -y wget bash-completion vim lrzsz wget expect net-tools nc nmap tree dos2unix htop iftop iotop unzip telnet sl psmisc nethogs glances bc ntpdate openldap-devel
  ```
  
  
  
  
  
  
  
  
  
  ```
  讲师：武沛齐
  微信：wupeiqi666
  B站主页：
  https://space.bilibili.com/336469068
  https://space.bilibili.com/283478842
  ```