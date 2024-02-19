## 安装vscode
collapsed:: true
	- ### 使用 apt 安装 Visual Studio Code
	  collapsed:: true
		- #### 方法一：
			- sudo apt update
			  sudo apt install com.visualstudio.code
		- #### 方法二：
		- Visual Studio Code 在官方的微软 Apt 源仓库中可用。想要安装它，按照下面的步骤来：
		- 01.以 sudo 用户身份运行下面的命令，更新软件包索引，并且安装依赖软件：
		- ```
		  sudo apt update
		  sudo apt install software-properties-common apt-transport-https wget
		  ```
		  02.使用 wget 命令插入 Microsoft GPG key ：
		  
		  ```
		  wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
		  ```
		  启用 Visual Studio Code 源仓库，输入：
		  ```
		  sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
		  ```
		  03.一旦 apt 软件源被启用，安装 Visual Studio Code 软件包：
		  ```
		  sudo apt install code
		  ```
		  当一个新版本被发布时，你可以通过你的桌面标准软件工具，或者在你的终端运行命令，来升级 Visual Studio Code 软件包：
		  ```
		  sudo apt update
		  sudo apt upgrade
		  ```
- ## 安装 Rust
	- 如果你使用的是 Linux 或 macOS，打开终端并输入下面命令：
	- ```
	  $ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
	  ```
	- 这个命令将下载一个脚本并开始安装 `rustup` 工具，此工具将安装 Rust 的最新稳定版本。可能会提示你输入密码。如果安装成功，将出现下面这行：
	- ```
	  Rust is installed now. Great!
	  ```
- ## 安装Python
-