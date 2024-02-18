<<<<<<< HEAD
## 6 列表（list）
title:: Python：6 列表
=======
- ## 6 列表（list）
  title:: Python：6 列表
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
	- 列表(list)是Python的一种可以**更改**内容的数据类型，它是由一系列元素所组成的序列。如果现在我们要设计班上同学的成绩表，班上有50位同学，可能需要设计50个变量，这是一件麻烦的事。如果学校单位要设计所有学生的数据库，学生人数有1000人，需要1000个变量，这似乎是不可能的事。Python的列表数据类型，可以只用一个变量，解决这方面的问题，要存取时用列表名称加上索引值即可，这也是本章的主题。
	  列表类似于其他编程语言的数组（array），不过，Python的列表功能除了可以存储相同数据类型，例如，整数、浮点数、字符串，也可以存储不同数据类型，例如，**列表内同时含有整数、浮点数和字符串**。甚至一个列表也可以内含其他列表或是字典(dict)
	- ### 列表基础
		- #### 定义
			- 定义： name_list = [元素1， 元素2， ...，元素n]
			- 元素可以是整数、浮点数、字符串、列表、字典
	- #### 读取元素列表
		- 用列表名称与索引读取列表元素的内容，在Python中元素是从索引值0开始配置。所以如果是列表的第一个元素，索引值是0，第二个元素索引值是1，其他依此类推。
		- name_list[i] # 读取索引i的列表元素
	- #### 列表切片（list slices）
		- 在设计程序时，常会需要取得列表前几个元素、后几个元素、某区间元素或是依照一定规则排序的元素，所取得的系列元素也可称子列表，这个观念称列表切片(list slices)
		- name_list[start:end]    # 读取从索引start到(end-1)索引的列表元素
		- name_list[:n]           # 取得列表前n名
		- name_list[n:]           # 取得列表索引n到最后
		- name_list[-n:]          # 取得列表后n名
		- name[:]                 # 取得所有元素
		- name_list[start🔚step]   # 每隔step，读取从索引start到(end-1）索引的列表元素
		- name_list[-1]           # 取得最后一个元素
	- #### 列表统计资料、最大值max()、最小值min()、总和sum()
		- Python有内置一些执行统计运算的函数，如果列表内容全部是数值则可以使用
		- max( )函数获得列表的最大值，
		- min( )函数可以获得列表的最小值，
		- sum( )函数可以获得列表的总和。
		- 如果列表内容全部是字符或字符串则可以使用max( )函数获得列表的unicode码值的最大值，min( )函数可以获得列表的unicode码值最小值。sum( )则不可使用在列表元素为非数值情况。
	- #### 列表个数len()
	- #### 更改列表元素的内容
		- 使用列表名称和索引值更改列表元素的内容
			- ``` python
<<<<<<< HEAD
			  james = [23, 19, 22, 31, 18]
			  print(james)
			  james[4] = 28
			  print(james)
=======
			  			  james = [23, 19, 22, 31, 18]
			  			  print(james)
			  			  james[4] = 28
			  			  print(james)
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
			  ```
	- #### 列表的相加
		- 列表的相加相当于列表的结合
	- #### 列表乘以一个数字
		- 如果将列表乘以一个数字，相当于列表元素重复次数
	- #### 删除列表元素
		- del name_list[i]		# 删除索引i的列表元素
		- del name_list[start:end]		# 删除从索引start到end-1索引的列表元素
		- del name_list[start🔚step] # 每隔step,删除从索引start到（end-1）索引的列表元素
	- #### 列表为空列表的判断
		- name_list = [ ]		# 这是空列表
	- #### 删除列表
		- del name_list 	# 删除列表 name_list
	- ### 列表内置方法
	- #### 列表的元素更改方法
		- append():		在列表末端增加元素, name_list.append('new item')
		- insert():  	可以在任意位置插入元素， name_list.insert(i, 'new item')
		- pop():		删除将弹出所删除的值，
			- value = name_list.pop()       # 默认删除最后一个
			- value = name_list.pop(i)      # 删除指定索引值的列表元素
		- remove():    name_list.remove(想删除的元素内容)
	- #### 列表的排序方法
		- reverse():		# 颠倒排序name_list列表元素    name_list.reverse()
		- sort():	         # 对元素由小到大排序 ，排序后原列表的元素顺序永久更改  name_list.sort()
		- sorted():	    # 用新列表存储排序，原列表序列不更改      new_list.sorted(name_list)
	- ### 进阶列表操作
		- index():	# 返回特定元素内容第一次出现的索引值   name_list.index(value)
		- count():     # 返回特定元素内容出现的次数 name_list.count(value)
		- join():        # 将列表的元素组成一个字符串