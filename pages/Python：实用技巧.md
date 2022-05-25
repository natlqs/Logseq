- ### 网页源码乱码原因及解决办法
	- #### 网页源代码乱码的原因
		- 网页源代码乱码的原因主要是Python获取的网页源代码的编码格式和网页实际的编码格式不一致。网页中常用的编码格式有UTF-8、GBK、ISO-8859-1。
		  用开发者工具查看网页源代码，然后展开<head>标签，查看<meta>标签里的charset属性，如下图所示，该属性的值就是网页的编码格式，这里为UTF-8。
		- 用Requests库的encoding属性可以查看Python获取的网页源代码的编码格式，代码如下：
		  id:: 62673e94-dbb8-4604-84a0-d15f38ce8c3a
			- ```python
			  code = requests.get(url, headers=headers).encoding
			  ```
	- #### 网页源代码乱码的解决方法
		- ##### 方法1：对获取的网页源代码文本进行处理
			- ```python
			  res = requests.get(url).text
			  res = res.encode('ISO-8859-1').decode('utf-8')
			  ```
		- ##### 方法2：对获取的网页相应进行编码处理，再提取文本
			- ```python
			  res = requetst.get(url, headers=headers)
			  res.encoding = 'utf-8'
			  res = rex.text
			  ```
	- #### 网页源代码乱码的通用解决方法
		- #### 方法1：对于大部分网页，可以先尝试直接获取
			- ```python
			  res = requests.get(url).text
			  ```
		- #### 方法2：如果方法1直接获取的内容有乱码，尝试如下代码
			- ```python
			  res = requests.get(url).text
			  res = res.decode('ISO-8859-1').decode('gbk')
			  ```
		- #### 方法3：如果方法2爬取的内容还是乱码或报错，尝试如下代码
			- ```python
			  res = requests.get(url).text
			  res = res.encode('ISO-8859-1').decode('utf-8')
			  ```
		- #### 方法4：如果不想逐个尝试，可以通过try/except将3种方法整合到一起
			- ```python
			  res = requests.get(url).text
			  try:
			    res = res.encode('ISO-8859-1').decode('utf-8')
			  except:
			    try:
			      res = res.encode('ISO-8859-1').decode('gbk')
			    except:
			      res = res
			    
			  ```
	- #### 补充知识点：encode()函数和decode()函数
		- ##### encode()函数和decode()函数的功能
			- encode()函数的功能是把字符串转换成院士的二进制字符。
			  		```python
			  		res = '华小智能'
			  		res = res.encode('utf-8')# 将中文字符串转换为二进制字符
			  		print(res)
			  		```
				- 输出结果：
				  	`b'\xe5\x8d\x8e\xe5\xb0\x8f\xe6\x99\xba`
			- decode()函数的功能是把二进制字符转化成字符串。
				- ```python
				  res = b'\xe5\x8d\x8e\xe5\xb0\x8f\xe6\x99\xba'
				  res = res.decode('utf-8')#将二进制字符转换为字符串
				  print(res)
				  ```
				- 输出结果：
					- `华小智`