### 01.   [VMware](https://so.csdn.net/so/search?q=VMware&spm=1001.2101.3001.7020)   Tools简介
	- VMware Tools 中包含一系列服务和模块，可在 VMware 产品中实现多种功能，从而使用户能够更好地管理客户机操作系统，以及与客户机操作系统进行无缝交互。
	  
	  VMware Tools [生命周期](https://so.csdn.net/so/search?q=%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F&spm=1001.2101.3001.7020)管理为 VMware Tools 的安装和升级提供了一种简单而可扩展的方式。它包含多项功能增强和与驱动程序相关的增强，并支持新的客户机操作系统。
	  
	  Open VM Tools (open-vm-tools) 是适用于 Linux 客户机操作系统的 VMware Tools 的开源实现。如需 Open VM Tools 源代码的最新副本，请参见 [GitHub](https://github.com/vmware/open-vm-tools)。
	  
	  对于 vSphere 部署，VMware 提供了操作系统特定软件包 (OSP) 充当 VMware Tools 的打包和分发机制。有关详细信息，请转到 [VMware 操作系统特定软件包](https://www.vmware.com/download/packages.html)。
- ###   02. VMware Tools功能
	- VMware Tools 中包含一系列服务和模块，可在 VMware 产品中实现多种功能，从而使用户能够更好地管理客户机操作系统，以及与客户机系统进行无缝交互。
	- 例如，VMware Tools 具备如下功能：
		- 将消息从主机操作系统传递到客户机操作系统。
		- 将客户机操作系统作为 vCenter Server 及其他 VMware 产品的组成部分进行自定义。
		- 运行有助于实现客户机操作系统自动化运行的脚本。这些脚本在虚拟机的电源状态改变时运行。
		- 在客户机操作系统与主机操作系统之间同步时间。
		- VMware Tools 生命周期管理为 VMware Tools 的安装和升级提供了一种简单而可扩展的方式。它包含多项功能增强和与驱动程序相关的增强，并支持新的客户机操作系统。请运行最新版本的 VMware Tools，或使用随 Linux 操作系统发行版一同分发的 open-vm-tools。尽管客户机操作系统在不使用 VMware Tools 的情况下也可以运行，但是要使用最新的功能和更新，务必在客户机操作系统中运行最新版本的 VMware Tools。可以将虚拟机配置为在每次打开电源时自动检查和应用 VMware Tools 升级。有关在虚拟机上启用 VMware Tools 自动升级的信息，请参见《vSphere 虚拟机管理指南》
	- **[VMware Tools 服务](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-0BD592B1-A300-4C09-808A-BB447FAE2C2A.html)**
		- 当客户机操作系统启动时，VMware Tools 服务将启动。该服务在主机和客户机操作系统之间传递信息。 [[了解更多内容]](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-0BD592B1-A300-4C09-808A-BB447FAE2C2A.html)**[VMware Tools 生命周期管理](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-14778D23-93A2-42F5-8F23-E19636827762.html)**
		- 从主要版本 10.1.0 开始，VMware Tools 新增了简化且可扩展的 VMware Tools 安装和升级方法，在升级到新版 Linux Tools 时无需重新引导，支持 OSP 升级，增强了使用 UI 的版本报告功能以及使用 API 和 UI 的状态报告功能。此版本实施了多项功能增强和与驱动程序相关的增强，并支持新的客户机操作系统。通过使用脱机包以及与 SCCM 的集成来分发和升级 VMware Tools，VMware Tools 10.2.0 实现了对生命周期管理的多项改进。 [[了解更多内容]](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-14778D23-93A2-42F5-8F23-E19636827762.html)**[VMware Tools 设备驱动程序](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-6994A5F9-B62B-4BF1-99D8-E325874A4C7A.html)**
		- 设备驱动程序可提升声音、图形、网络连接和存储的性能。如果是自定义安装或重新安装 VMware Tools，则可以选择要安装的驱动程序。 [[了解更多内容]](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-6994A5F9-B62B-4BF1-99D8-E325874A4C7A.html)**[VMware 用户进程](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-FB7FA658-7622-4680-BD9F-7A6670C12794.html)**
		- 借助 VMware 用户进程，可以在支持复制和粘贴、拖放等功能的 VMware 产品中使用这些功能。 [[了解更多内容]](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-FB7FA658-7622-4680-BD9F-7A6670C12794.html)**[使用 Open VM Tools](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-8B6EA5B7-453B-48AA-92E5-DB7F061341D1.html)**
		- Open VM Tools (open-vm-tools) 是适用于 Linux 客户机操作系统的 VMware Tools 的开源实现。 [[了解更多内容]](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-8B6EA5B7-453B-48AA-92E5-DB7F061341D1.html)**[适用于 Linux 客户机操作系统的操作系统特定软件包](https://docs.vmware.com/cn/VMware-Tools/11.1.0/com.vmware.vsphere.vmwaretools.doc/GUID-387F1F73-0BFF-40C9-87FC-3B6EB9B78815.html)**
		- 对于 vSphere 部署，VMware 提供了操作系统特定软件包 (OSP) 充当 VMware Tools 的打包和分发机制。这些 VMware Tools OSP 使用本机软件包格式和标准（如 rpm 和 deb）打包。
		- 参考：VMware Tools官方参考手册
	- ###   03. VMware Tools安装方法一
		- 3.1 安装VMware Tools
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528092148303.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RlbmdqaW4yMDEwNDA0MjA1Ng==,size_16,color_FFFFFF,t_70)
		- 3.2 选择设置CD-ROM
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528092157120.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RlbmdqaW4yMDEwNDA0MjA1Ng==,size_16,color_FFFFFF,t_70)
		- 3.3 复制VMware Tools文件
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528092206900.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RlbmdqaW4yMDEwNDA0MjA1Ng==,size_16,color_FFFFFF,t_70)
		- 3.4 解压文件
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528092216467.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RlbmdqaW4yMDEwNDA0MjA1Ng==,size_16,color_FFFFFF,t_70)
		- 3.5 进入对应的目录，执行安装程序
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528092224941.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RlbmdqaW4yMDEwNDA0MjA1Ng==,size_16,color_FFFFFF,t_70)
		- 3.6 执行安装，输入yes，路径默认
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528092232380.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RlbmdqaW4yMDEwNDA0MjA1Ng==,size_16,color_FFFFFF,t_70)
			- 只要出现路径的就按下回车，出现【Yes/No】全部选择Yes。
		- 3.7 安装完成界面
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528092241242.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RlbmdqaW4yMDEwNDA0MjA1Ng==,size_16,color_FFFFFF,t_70)
		- 3.8 重新启动系统
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528092248738.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RlbmdqaW4yMDEwNDA0MjA1Ng==,size_16,color_FFFFFF,t_70)
	- ###   05. VMware Tools安装方法二
		- 进入终端，只需要输入三行命令：（输入之后耐心等待命令执行）
			- ```
			  sudo apt upgrade
			  sudo apt install open-vm-tools-desktop -y
			  sudo **reboot**
			  ```
	- ###   06. 附录
	  
	  6.1 VMware Tools官方文档：[https://docs.vmware.com/cn/VMware-Tools/index.html](https://docs.vmware.com/cn/VMware-Tools/index.html)
	  6.2 VMware Tools下载： [VMwareTools-10.3.21-14772444.tar.gz](https://download.csdn.net/download/dengjin20104042056/12504013)