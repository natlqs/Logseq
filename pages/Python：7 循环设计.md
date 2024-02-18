<<<<<<< HEAD
## 7 循环设计
title:: Python：7 循环设计
=======
- ## 7 循环设计
  title:: Python：7 循环设计
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
	- ### for循环
		- for循环可以让程序将整个**对象**内的元素遍历（也可以迭代），在遍历期间，同时可以记录或输出每次遍历的状态或称轨迹。
		- #### 基本使用方法
			- ```
<<<<<<< HEAD
			  for var in **可迭代对象** ： # 可迭代对象 iterable object
			  	程序代码块
			  ```
			- 可迭代对象可以是列表、元组、字典、集合或range(),在信息科学中迭代可以解释为重复执行。上述语法可以解释为将可迭代对象的元素当作var，重复执行，直到每个元素都被执行一次，整个循环才会停止。
			- ```
			  for var in **可迭代对象**： 
			    程序代码块
			    程序代码块
			  ```
			- #### 举例
			- ``` python
			  files = ['da1.c','da2.py','da3.py','da4.java']
			  py = []
			  for file in files:
			    if file.endswith('.py'):
			      py.append(file)
			  print(py)
=======
			  			  for var in **可迭代对象** ： # 可迭代对象 iterable object
			  			    程序代码块
			  ```
			  可迭代对象可以是列表、元组、字典、集合或range(),在信息科学中迭代可以解释为重复执行。上述语法可以解释为将可迭代对象的元素当作var，重复执行，直到每个元素都被执行一次，整个循环才会停止。
			- ```
			  			  for var in **可迭代对象**： 
			  			    程序代码块
			  			    程序代码块
			  ```
			- #### 举例
			- ``` python
			  			  files = ['da1.c','da2.py','da3.py','da4.java']
			  			  py = []
			  			  for file in files:
			  			  	if file.endswith('.py'):
			  			          py.append(file)
			  			  print(py)
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
			  ```
			- ``` python
			  			  names = ['hong', 'hind', 'dong', 'dceing']
			  			  lastname=[]
			  			  for name in names:
			  			      if name.startswith('h'):
			  			          lastname.append(name)
			  			  print(lastname)
			  ```
	- ### range()函数
		- python可以使用range()函数产生一个等差序列，我们又称这个等差序列为可迭代对象，也可以称为range对象。
		- range(start, stop, step)  # stop是唯一必须的值，等差序列是产生stop的前一个值。step默认为1， start默认为0
		- #### 举例
			- ``` python
			  			  n=5
			  			  for i in range(n):
			  			      print(i)
			  ```
			- ``` python
			  			  n= 5
			  			  sum = 0
			  			  for i in range(1, n):
			  			      sum += i
			  ```
			- ``` python
			  			  for x in range(2, 11,2):
			  			      print(x)
			  ```
	- ### 列表生成式
		- 新列表= [ 表达式 for item in 可迭代对象], ： square = [num ** 2 for num in range(1, n+1)]
	- ### 进阶的for循环应用
		- #### 嵌套循环，一个循环内有另一个循环。
		- ```
		  		  for item in a:
		  		  	...
		  		  	for item2 in b:
		  		  		...
		  ```
		- ``` python
		  		  for i in range(1, 10):
		  		      for j in range(1, 10):
		  		          result = i*j
		  		          print(i, j, i*j)
		  ```
	- #### -break指令，强制离开for循环
		- 如果期待某些条件发生时可以离开循环，可以在循环内执行break指令。
		- ```
		  		  for item in a:
		  		  	程序代码块1
		  		  	if 条件：
		  		  		程序代码块2
		  		  		break
		  		  程序代码3
		  ```
	- #### -continue指令，for循环暂时停止不往下执行
		- ```
		  		  for item in a:
		  		  	程序代码1
		  		  	if 条件：		#如果条件表达是True，则不执行程序代码3
		  		  		程序代码2
		  		  		continue
		  		  	程序代码3
		  ```
	- #### for...else循环
		- 在设计for循环时，如果期待所有的if条件是False，最后一次循环后，可以执行特定程序区块指令。
		- ```
		  		  for item in a:
		  		  	程序代码1
		  		  	if 条件：	# 如果条件是True,则离开for循环
		  		  		程序代码2
		  		  		break
		  		  	程序代码3
		  		  else:
		  		  	程序代码4	# 最后一次循环条件表达式是False则执行
		  ```
	- ### While循环
		- #### 基本while循环
			- ```
			  			  while 条件：
			  			  	程序区块
			  ```
			- ``` python
			  			  answer = 30
			  			  guess = 0
			  			  while guess != answer:
			  			      guess = int(input('请猜1-100间的数字'))
			  			      if guess > answer:
			  			          print('请猜小一点')
			  			      elif guess < answer:
			  			          print('请猜大一点')
			  			      else:
			  			          print('恭喜答对了')
			  ```
		- #### 嵌套while循环
			- ```
			  			  while 条件：
			  			  	...
			  			  	while 条件1：
			  			  		...
			  ```
			- ``` python
			  			  i = 1				# 设定i初始值
			  			  while i <= 9:		# 当i大于9跳出外层循环
			  			      j = 1			# 设定j初始值
			  			      while j <= 9:	# 当j大于9跳出内层循环
			  			          result = i * j
			  			          j += 1
			  			      print()	#换行输出
			  			      i += 1
			  ```
		- #### -break 指令，强制离开while循环
			- ```
			  			  while 条件1：
			  			  	程序代码1
			  			  	if 条件2：		# 判断条件2
			  			  		程序代码2
			  			  		break	# 如果条件2是True，离开while循环
			  			  	程序代码3
			  ```
		- #### -continue指令，while循环暂时停止不往下执行
			- ```
			  			  while 条件1：
			  			  	程序代码1
			  			  	if 条件2	# 如果条件是True，则不执行程序代码3
			  			  		程序代码2
			  			  		continue
			  			  	程序代码3
			  ```
		- #### pass
			- pass指令是什么事也不做
		- ### enumerate对象使用for循环