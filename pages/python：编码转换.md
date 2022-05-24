- Python3 编码转换
	- 网络传输是以二进制数据进行传输的，在网络传输数据的时候，数据需要先编码转化为二进制（bytes）数据类型。
	- ![image.png](../assets/image_1648820655862_0.png)
	- 数据的编码转化：
		- |函数名|说明|
		  |encode|编码 将字符串转化为字节码|
		  |decode|解码 将字节码转化为字符串|
		- #+BEGIN_QUOTE
		  encode()和decode()函数可以接受参数，encoding是指在编解码过程中使用的编码方案。
		  #+END_QUOTE
			- `bytes.decode(encoding='utf-8')`
			- `str.encode(encoding='utf-8)`