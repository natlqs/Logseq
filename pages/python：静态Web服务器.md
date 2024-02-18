- 搭建python自带的静态web服务器
	- 静态web服务器是为发出请求的浏览器提供静态文档的程序。
	- 搭建自带的web服务器使用`python3 -m http.server 端口号`这个命令即可，端口号不指定默认是8000
		- ![image.png](../assets/image_1648895105407_0.png)
		- 打开浏览器输入`本机IP地址:端口号/文件名`即可访问。
			- ![image.png](../assets/image_1648895226630_0.png)
- 静态Web服务器-返回固定页面数据
	- 开发步骤
		- 1. 编写一个TCP服务端程序
		  2. 获取浏览器发送的HTTP请求报文数据
		  3. 读取固定页面数据，把页面数据组装成HTTP响应报文数据发送给浏览器。
		  4. HTTP响应报文数据发送完成以后，关闭服务于客户端的套接字。
		- ```python
		  import socket
		  from urllib import response
		  
		  if __name__ == '__main__':
		      # 1. 编写一个TCP服务端程序
		      tcp_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		      # 设置端口复用
		      tcp_server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, True)
		      # 绑定地址及端口
		      tcp_server_socket.bind(('', 8080))
		      # 设置监听
		      tcp_server_socket.listen(128)
		      while True:
		          # 2. 获取浏览器发送的HTTP请求报文数据
		          # 建立连接
		          client_socket, client_addr = tcp_server_socket.accept()
		          # 获取浏览器的请求信息
		          client_request_data = client_socket.recv(1024).decode()
		          print(client_request_data)
		          # 3. 读取固定页面数据，把页面数据组装成HTTP响应报文数据发送给浏览器
		          with open('.\Python\Web_develop\静态Web服务器\index.html', 'rb') as f:
		              file_data = f.read()
		          # 应答行
		          response_line = "HTTP/1.1 200 OK\r\n"
		          # 应答头
		          response_header = "Server: pwb\r\n"
		          # 应答体
		          response_body = file_data
		          response_data = (response_line + response_header + "\r\n").encode() + response_body
		          client_socket.send(response_data)
		          # 4. HTTP响应报文数据发送完成以后，关闭服务于客户端的套接字
		          client_socket.close()
		  ```
		- #+BEGIN_QUOTE
		  打开浏览器输入`127.0.0.1：8080`即可打开发布的网页
		  #+END_QUOTE
- 静态Web服务器-返回指定页面数据
	- 步骤：
		- 1. 获取用户请求资源的路径
		  2. 根据请求资源的路径，读取指定文件的数据
		  3. 组装指定文件数据的响应报文，发送给浏览器
		  4. 判断请求的文件在服务器端不存在，组装404状态的响应报文，发送给浏览器
		- ```python
		  import socket
		  
		  if __name__ == '__main__':
		      # 1. 编写一个TCP服务端程序
		      tcp_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		      # 设置端口复用
		      tcp_server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, True)
		      # 绑定地址及端口
		      tcp_server_socket.bind(('', 8080))
		      # 设置监听
		      tcp_server_socket.listen(128)
		      while True:
		          # 2. 获取浏览器发送的HTTP请求报文数据
		          # 建立连接
		          client_socket, client_addr = tcp_server_socket.accept()
		          # 获取浏览器的请求信息
		          client_request_data = client_socket.recv(1024).decode()
		          # print(client_request_data)
		          # 获取用户请求资源的路径
		          request_data = client_request_data.split(' ')
		          print(request_data[1])
		          request_path = request_data[1]
		          if request_path == "/":
		              request_path = "/index.html"
		  
		          # 3. 读取固定页面数据，把页面数据组装成HTTP响应报文数据发送给浏览器
		          try:
		              with open('.\Python\Web_develop\静态Web服务器'+ request_path, 'rb') as f:
		                  file_data = f.read()
		          except Exception as e:
		              response_line = "HTTP/1.1 404 Not Found\r\n"
		              response_header = "Server: pwb\r\n"
		              response_body = "404 Not Found Sorry"
		              response_data = (response_line + response_header + "\r\n" + response_body).encode('utf-8')
		              client_socket.send(response_data)
		              pass
		          else:
		              # 应答行
		              response_line = "HTTP/1.1 200 OK\r\n"
		              # 应答头
		              response_header = "Server: pwb\r\n"
		              # 应答体
		              response_body = file_data
		              response_data = (response_line + response_header + "\r\n").encode('utf-8') + response_body
		              client_socket.send(response_data)
		          finally:
		              # 4. HTTP响应报文数据发送完成以后，关闭服务于客户端的套接字
		              client_socket.close()
		  ```
- 静态Web服务器-多任务版
	- 可以使用多线程，节约资源
	- 当客户端和服务端建立连接成功，创建子线程，使用子线程专门处理客户端的请求，防止主线程阻塞。
	- ```python
	  import socket
	  import threading
	  
	  def handle_client_request(client_socket):        # 获取浏览器的请求信息
	      client_request_data = client_socket.recv(1024).decode()
	      # print(client_request_data)
	      # 获取用户请求资源的路径
	      request_data = client_request_data.split(' ')
	      if len(request_data) == 1:
	          client_socket.close()
	          return
	      request_path = request_data[1]
	      if request_path == "/":
	          request_path = "/index.html"
	  
	      # 3. 读取固定页面数据，把页面数据组装成HTTP响应报文数据发送给浏览器
	      try:
	          with open('.\Python\Web_develop\静态Web服务器'+ request_path, 'rb') as f:
	              file_data = f.read()
	      except Exception as e:
	          response_line = "HTTP/1.1 404 Not Found\r\n"
	          response_header = "Server: pwb\r\n"
	          response_body = "404 Not Found Sorry"
	          response_data = (response_line + response_header + "\r\n" + response_body).encode('utf-8')
	          client_socket.send(response_data)
	          pass
	      else:
	          # 应答行
	          response_line = "HTTP/1.1 200 OK\r\n"
	          # 应答头
	          response_header = "Server: pwb\r\n"
	          # 应答体
	          response_body = file_data
	          response_data = (response_line + response_header + "\r\n").encode('utf-8') + response_body
	          client_socket.send(response_data)
	      finally:
	          # 4. HTTP响应报文数据发送完成以后，关闭服务于客户端的套接字
	          client_socket.close()
	  
	  
	  if __name__ == '__main__':
	      # 1. 编写一个TCP服务端程序
	      tcp_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	      # 设置端口复用
	      tcp_server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, True)
	      # 绑定地址及端口
	      tcp_server_socket.bind(('', 8080))
	      # 设置监听
	      tcp_server_socket.listen(128)
	      while True:
	          # 2. 获取浏览器发送的HTTP请求报文数据
	          # 建立连接
	          client_socket, client_addr = tcp_server_socket.accept()
	          # 创建子线程
	          sub_thread = threading.Thread(target=handle_client_request, args=(client_socket,))
	          sub_thread.start()
	  ```
- 静态Web服务器-面向对象开发
	- 1. 把提供服务端Web服务器抽象成一个类（HTTPWebServer)
	  2. 提供Web服务器的初始化方法，在初始化方法里面创建Socket对象
	  3. 提供一个开启Web服务器的方法，让Web服务器处理客户端请求操作
	- ```python
	  import socket
	  import threading
	  
	  class  HttpWebServer():
	      def __init__(self):
	          # 1. 编写一个TCP服务端程序
	          self.tcp_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	          # 设置端口复用
	          self.tcp_server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, True)
	          # 绑定地址及端口
	          self.tcp_server_socket.bind(('', 8080))
	          # 设置监听
	          self.tcp_server_socket.listen(128)
	  
	      def handle_client_request(self, client_socket):        # 获取浏览器的请求信息
	          client_request_data = client_socket.recv(1024).decode()
	          # print(client_request_data)
	          # 获取用户请求资源的路径
	          request_data = client_request_data.split(' ')
	          if len(request_data) == 1:
	              client_socket.close()
	              return
	          request_path = request_data[1]
	          if request_path == "/":
	              request_path = "/index.html"
	  
	          # 3. 读取固定页面数据，把页面数据组装成HTTP响应报文数据发送给浏览器
	          try:
	              with open('.\Python\Web_develop\静态Web服务器'+ request_path, 'rb') as f:
	                  file_data = f.read()
	          except Exception as e:
	              response_line = "HTTP/1.1 404 Not Found\r\n"
	              response_header = "Server: pwb\r\n"
	              response_body = "404 Not Found Sorry"
	              response_data = (response_line + response_header + "\r\n" + response_body).encode('utf-8')
	              client_socket.send(response_data)
	              pass
	          else:
	              # 应答行
	              response_line = "HTTP/1.1 200 OK\r\n"
	              # 应答头
	              response_header = "Server: pwb\r\n"
	              # 应答体
	              response_body = file_data
	              response_data = (response_line + response_header + "\r\n").encode('utf-8') + response_body
	              client_socket.send(response_data)
	          finally:
	              # 4. HTTP响应报文数据发送完成以后，关闭服务于客户端的套接字
	              client_socket.close()
	  
	      def start(self):
	          while True:
	              # 2. 获取浏览器发送的HTTP请求报文数据
	              # 建立连接
	              client_socket, client_addr = self.tcp_server_socket.accept()
	              # 创建子线程
	              sub_thread = threading.Thread(target=self.handle_client_request, args=(client_socket,))
	              sub_thread.start()
	  
	  
	  if __name__ == '__main__':
	      # 创建服务器对象
	      my_web_server = HttpWebServer()
	      # 启动服务器
	      my_web_server.start()
	  ```
- 静态Web服务器-命令行启动动态绑定端口号
	- 步骤
		- 1. 获取执行python程序的终端命令行参数
		  2. 判断参数的类型，设置端口号必须是整形
		  3. 给Web服务器类的初始化方法添加一个端口号参数，用于绑定端口号
	- ```python
	  import socket
	  import threading
	  import sys
	  
	  class  HttpWebServer():
	      def __init__(self, port):
	          # 1. 编写一个TCP服务端程序
	          self.tcp_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	          # 设置端口复用
	          self.tcp_server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, True)
	          # 绑定地址及端口
	          self.tcp_server_socket.bind(('', port))
	          # 设置监听
	          self.tcp_server_socket.listen(128)
	  
	      def handle_client_request(self, client_socket):        # 获取浏览器的请求信息
	          client_request_data = client_socket.recv(1024).decode()
	          # print(client_request_data)
	          # 获取用户请求资源的路径
	          request_data = client_request_data.split(' ')
	          if len(request_data) == 1:
	              client_socket.close()
	              return
	          request_path = request_data[1]
	          if request_path == "/":
	              request_path = "/index.html"
	  
	          # 3. 读取固定页面数据，把页面数据组装成HTTP响应报文数据发送给浏览器
	          try:
	              with open('.\Python\Web_develop\静态Web服务器'+ request_path, 'rb') as f:
	                  file_data = f.read()
	          except Exception as e:
	              response_line = "HTTP/1.1 404 Not Found\r\n"
	              response_header = "Server: pwb\r\n"
	              response_body = "404 Not Found Sorry"
	              response_data = (response_line + response_header + "\r\n" + response_body).encode('utf-8')
	              client_socket.send(response_data)
	              pass
	          else:
	              # 应答行
	              response_line = "HTTP/1.1 200 OK\r\n"
	              # 应答头
	              response_header = "Server: pwb\r\n"
	              # 应答体
	              response_body = file_data
	              response_data = (response_line + response_header + "\r\n").encode('utf-8') + response_body
	              client_socket.send(response_data)
	          finally:
	              # 4. HTTP响应报文数据发送完成以后，关闭服务于客户端的套接字
	              client_socket.close()
	  
	      def start(self):
	          while True:
	              # 2. 获取浏览器发送的HTTP请求报文数据
	              # 建立连接
	              client_socket, client_addr = self.tcp_server_socket.accept()
	              # 创建子线程
	              sub_thread = threading.Thread(target=self.handle_client_request, args=(client_socket,))
	              sub_thread.start()
	  def main():
	      # 获取执行python程序的终端命令行参数
	      print(sys.argv)
	      if len(sys.argv) !=2:
	          print("格式错误 python3 xxx.py 9090")
	          return
	      # 判断参数的类型，设置端口号必须是整形
	      if not sys.argv[1].isdigit():
	          print("格式错误 python3 xxx.py 9090")
	          return
	      port = int(sys.argv[1])
	      # 创建服务器对象
	  
	      my_web_server = HttpWebServer(port)
	      # 启动服务器
	      my_web_server.start()
	  
	  if __name__ == '__main__':
	      main()
	  ```