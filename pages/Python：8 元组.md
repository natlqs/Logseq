- ## 8 元组
  title:: Python：8 元组
	- ### 元组的定义
		- 元组是另一种数据类型，这种数据类型结构和列表完全相同，但是它与列表最大的差异是它的元素值与元素个数不可更改，有时又可称为不可变列表。
		- name_tuple = (item1, ... , itemn)
		- 元组的每一个数据称元素，元素可以是整数、字符串或列表等
	- #### 读取元组元素
		- 和列表一样，用中括号[]索引
	- #### 遍历所有元组元素
		- 在python可以使用for循环遍历所有元组元素
		- ``` python
		  		  keys = ('magic', 'xaab', 000)
		  		  for key in keys:
		  		    print(key)
		  ```
	- #### 修改元组内容产生错误
	- #### 可以使用全新定义方式修改元组元素
	- ### 元组切片（tuple slices）
		- 元组切片与列表切片相同
		- ``` python
		  		  fruits = ('apple', 'orange', 'banana', 'watermelon', 'grape')
		  		  print(fruits[1:3])
		  		  print(fruits[:2])
		  		  print(fruits[1:])
		  		  print(fruits[-2:1])
		  		  print(fruits[0:5:2])
		  ```
	- ### 方法与函数
		- len()         #
		- max(tuple)    # 获得元组最大值
		- min(tuple)    # 获得元组最小值
	- ### 列表与元组数据互换
		- list(tuple): 将元组数据类型改为列表
		- tuple(list): 将列表数据类型改为元组
	- ### 元组的功能
		- 可以更安全的保护数据
		- 增加程序执行速度