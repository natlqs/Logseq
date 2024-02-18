<<<<<<< HEAD
## 4 基本输入与输出
title:: Python：4 基本输入与输出
=======
- ## 4 基本输入与输出
  title:: Python：4 基本输入与输出
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
	- ### python的辅助说明help()
		- help() 函数可以列出某一python的指令或函数的使用说明，如help(print)
	- ### 格式化输出数据使用print()
		- #### print()函数的基本语法
			- ``` python
<<<<<<< HEAD
			  print('aaa')
			  num1=222
			  print('aaa', num1)
			  print('aaa', sep='$$$;)
=======
			  			    print('aaa')
			  			    num1=222
			  			    print('aaa', num1)
			  			    print('aaa', sep='$$$;)
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
			  ```
		- #### 格式化print()输出
			- 基本格式： print('输出格式区' % (变量系列去，...))，默认是sys.stdout，也就是屏幕
			- 输出格式区：
				- %d / %nd: 格式化整数输出, n多少位
				- %f / %m.nf: 格式化浮点数输出, m多少位，n小数部分
				- %x / %nx: 格式化16进制整数输出
				- %o / %no：格式化8进制整数输出
				- %s / %ns: 格式化字符串输出
			- format()函数
				- ``` python
<<<<<<< HEAD
				  score = 90
				  str1 = 'aaa'
				  count = 1
				  print("{}你的第{}次物理考试成绩是{}".format(str1, count, score))
=======
				  				    score = 90
				  				    str1 = 'aaa'
				  				    count = 1
				  				    print("{}你的第{}次物理考试成绩是{}".format(str1, count, score))
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
				  ```
	- ### 输出数据到文件
		- open()函数可以打开一个文件供读取或写入，如果函数执行成功，会传回文件对象。
		- open()函数的基本格式： file_obj = open(file, mode='r')
			- file:欲打开的文件
			- mode：打开文件的模式，默认为'r'
				- r: 读取
				- w: 写入，原先文件内容将被覆盖
				- a: 写入，新写入的数据将附加在后面
				- x: 写入，如果新打开的文件已经存在会产生错误
				- b: 打开二进制文件模式
				- t：打开文本（txt）文件模式，默认
				- +：打开文件供更新用
			- file_obj：文件对象，可以自行给名称，不使用时要关闭"file_obj.close()",才可以返回操作系统的文件管理器观察结果
	- ### 数据输入input()
		- input()函数从屏幕读取用户从键盘输入的数据。
		- 格式：value = input('prompt:'), value是变量，输入数据存入这里，不论输入的是字符串还是数值，返回的一律是字符串数据
	- ### 列出所有内置函数dir()
		- dir(**builtins**)  # 列出python内置函数，可以列出对象有哪些内置的方法