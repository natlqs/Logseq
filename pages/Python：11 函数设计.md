- ## 11 函数设计
	- 函数(function)是一系列指令语句所组成，它的目的有两个。
		- 1. 当我们在设计一个大型程序时，若是能将这个程序依功能，将其分割成较小的功能，然后依这些较小功能要求撰写函数程序，如此，不仅使程序简单化，最后程序侦错也变得容易。另外，撰写大型程序时应该是团队合作，每一个人负责一个小功能，可以缩短程序开发的时间。
		- 2. 在一个程序中，也许会发生某些指令被重复书写在许多不同的地方，若是我们能将这些重复的指令撰写成一个函数，需要用时再加以调用，如此，不仅减少编辑程序的时间，更可使程序精简、清晰、明了。
	- ### 函数定义
		- ```
		  		  def 函数名称（参数1，参数2，...）：
		  		  ''' 函数批注'''
		  		  程序代码块
		  		  return [返回值1， 返回值2]
		  ```
		- 函数名称 名称必须是唯一的，程序未来可以调用引用。
		- 参数值  这是可有可无的，完全视函数设计需要，可以接收调用函数传来的变量，各参数值之间是用逗号“,”隔开。
		- 函数批注 这是可有可无的，不过如果是参与大型程序设计计划，当负责一个小程序时，建议所设计的函数需要加上批注，除了自己需要也是方便他人阅读。主要是注明此函数的功能，由于可能有多行批注所以可以用3个双引号（或单引号）包夹。许多英文Python资料称此为docstring(document string的缩写)。
		- return [返回值1,返回值2 , … ]不论是return或接续右边的返回值皆是可有可无，如果有返回多个数据彼此需以逗号“,”隔开。
	- ### 函数参数设计
		- #### 传递一个参数
			- ``` python
			  		  def greeting(name):
			  		    print('hi', name, 'good morning')
			  		  
			  		  greeting('Nelson')  # 将Nelson传入函数name参数
			  ```
		- #### 多个参数传递
			- 当所设计的函数需要传递多个参数，调用此函数时就需要特别**留意传递参数的位置需要正确**，最后才可以获得正确的结果。最常见的传递参数是数值或字符串数据，有时也会需要传递列表、元组或字典。
			- ``` python
			  		  def interest(interest_type, subject):
			  		    print('my interest' + interest_type)
			  		    print('in' + interest_type + ', my favorite is ' + subject))
			  		  
			  		  interest('travel', '敦煌')
			  		  interest('程序设计', 'python')
			  ```
		- #### 关键词参数 参数名称=值
			- 所谓的关键词参数(keyword arguments)是指调用函数时，参数是用参数名称=值配对方式呈现。Python也允许在调用需传递多个参数的函数时，直接将参数名称=值用配对方式传送，这个时候参数的位置就不重要了。
			- ``` python
			  		  def interest(interest_type, subject):
			  		    print('my interest' + interest_type)
			  		    print('in' + interest_type + ', my favorite is ' + subject))
			  		  
			  		  interest('travel', '敦煌')
			  		  interest(subject = '敦煌', interest_type = 'travel')
			  ```
		- #### 参数默认值的处理
			- 在设计函数时也可以给参数默认值，如果调用的这个函数没有给参数值，函数的默认值将派上用场。特别需留意：函数设计时含有默认值的参数，必须放置在参数列的最右边。
			- ``` python
			  		  def interest(interest_type, subject='张家界'):
			  		    print('my interest' + interest_type)
			  		    print('in' + interest_type + ', my favorite is ' + subject))
			  		  
			  		  interest('travel')
			  		  interest('travel', '敦煌')
			  		  interest(subject = '敦煌', interest_type = 'travel')
			  ```
		- #### 函数返回值
			- ##### 返回None
				- 函数没有“return [返回值]”时，Python在直译时会自动返回处理成“return None”，相当于返回None，None在Python中独立成为一个数据类型NoneType。
			- ##### 简单返回数值数据
				- ``` python
				  			  def substract(x1, x2):
				  			    result = x1 - x2
				  			    return result
				  			  
				  			  def addition(x1, x2):
				  			    result = x1 + x2
				  			    return result
				  			  
				  			  a = int(input('a = '))
				  			  b = int(input('b = '))
				  			  print('a - b = ', substract(a, b))
				  			  print('a + b = ', addition(a, b))
				  ```
			- ##### 返回多个数据的应用
				- 使用return返回函数数据时，也允许返回多个数据，各个数据间只要以逗号隔开即可。
				- ``` python
				  			  def mutifunction(x1, x2):
				  			    addresult = x1 + x2
				  			    subresult = x1 - x2
				  			    mulresult = x1 * x2
				  			    divresult = x1 / x2
				  			    return addresult, subresult, mulresult, divresult
				  			  
				  			  x1 = x2 = 10
				  			  add, sub, mul, div = mutifunction(x1, x2)
				  			  print('add = ', add)
				  			  print('sub = ', sub)
				  			  print('mul = ', mul)
				  			  print('div = ', div)
				  ```
			- ##### 简单返回字符串数据
				- 返回字符串的方法与返回数值的方法相同
			- ##### 函数返回字典或列表数据
				- 函数除了可以返回数值或字符串数据外，也可以返回比较复杂的数据，例如，字典或列表等。
		- #### 参数是列表
			- 在调用函数时，也可以将列表（此列表可以是由数值、字符串或字典所组成）当参数传递给函数，然后函数可以遍历列表内容，然后执行更进一步的运作。
			- Python允许在函数内直接修订列表的内容，同时列表经过修正后，主程序的列表也将随之永久性更改结果。
			- ``` python
			  		  def kitchen(unserved, served):
			  		    print('handle all the meal')
			  		    while unserved:
			  		        current_meal = unserved.pop()
			  		        print('menu', current_meal)
			  		        served.append(current_meal)
			  		  def show_unserved_meal(unserved):
			  		    print('below are all the unserved meal')
			  		    if not unserved:
			  		        print('none meal')
			  		    for unserved_meal in unserved:
			  		        print(unserved_meal)
			  		  def show_served_meal(served):
			  		    print('below are all served meal')
			  		    if not served:
			  		        print('none meal')
			  		    for served_meal in served:
			  		        print(served_meal)
			  		  unserved = ['big mike', 'super spicy chicken burg', 'mike chicken piece']
			  		  served = []
			  		  show_unserved_meal(unserved)
			  		  show_served_meal(served)
			  		  kitchen(unserved, served)
			  		  print('kitchen handle finish')
			  		  show_unserved_meal(unserved)
			  		  show_served_meal(served)
			  ```
		- #### 传递任意数量的参数
			- ##### 基本传递处理任意数量的参数
				- ``` python
				  			  def make_icecream(*toppings):
				  			    print('this is the receipe of the ice cream')
				  			    for topping is toppings:
				  			      print('---', topping)
				  			  
				  			  make_icecream('strawberry juice')
				  			  make_icecream('strawberry juice', 'saltana', 'chocolate pieces')
				  ```
			- ##### 设计含有一般参数与任意数量参数的函数
				- 程序设计时有时会遇上需要传递一般参数与任意数量参数，碰上这类状况，任意数量的参数必须放在最右边。下述build_dict()函数内的参数‘**players’，这表示可以接受任意数量关键词参数。
				- ``` python
				  			  def build_dict(name, age, **players):
				  			    info = {}
				  			    info['name'] = name
				  			    info['age'] = age
				  			    for key, value in players.items():
				  			      info[key] = value
				  			    return info
				  			  
				  			  player_dict = build_dict('james', '32',
				  			                           City = 'Cleveland,
				  			                           State = 'Ohio')
				  			  print(palyer_dict)
				  ```
	- ### 递归式函数设计recursive
		- 一个函数可以调用其他函数也可以调用自己，其中调用本身的动作称递归式(recursive)调用，递归式调用有下列特色：
			- 每次调用自己时，都会使范围越来越小。
			- 必须要有一个终止的条件来结束递归函数。
			- 递归函数可以使程序变得很简洁，但是设计这类程序一不小心就很容易掉入无限循环的陷阱，所以使用这类函数时一定要特别小心。递归函数最常见的应用是处理正整数的阶乘(factorial)，一个正整数的阶乘是所有小于以及等于该数的正整数的积，同时如果正整数是0则阶乘为1，依照观念正整数是1时阶乘也是1。此阶乘数字的表示法为n!。
			- ``` python
			  			  def factoria(n):
			  			    '''计算n的阶乘，n必须是正整数'''
			  			    if n == 1:
			  			      return 1
			  			    else:
			  			      return(n * factoria(n -1))
			  			  
			  			  value = 3
			  			  print(value, '的阶乘结果是：', factoria(value))
			  			  value = 5
			  			  print(value, '的阶乘结果是：', factoria(value))
			  ```
	- ### 局部变量与全局变量
		- 某个变量只有在该函数内使用，影响范围限定在这个函数内，这个变量称局部变量(local variable)。
		  如果某个变量的影响范围是在整个程序，则这个变量称全局变量(global variable)。
			- Python程序在调用函数时会建立一个内存工作区间，在这个内存工作区间可以处理属于这个函数的变量，当函数工作结束，返回原先调用程序时，这个内存工作区间就被收回，原先存在的变量也将被销毁，这也是为何局部变量的影响范围只限定在所属的函数内。
			- 对于全局变量而言，一般是在主程序内建立，程序在执行时，不仅主程序可以引用，所有属于这个程序的函数也可以引用，所以它的影响范围是整个程序。
		- 全局变量可以在所有函数使用
		- 程序设计时建议全局变量与函数内部的局部变量不要使用相同的名称。
		- 局部变量内容无法在其他函数引用。
		- 局部变量内容无法在主程序引用。
	- ### lambda匿名函数
		- #### 特点
			- 所谓的匿名函数(anonymous function)是指一个没有名称的函数，Python是使用def定义一般函数，匿名函数则是使用lambda来定义，有的人称之为lambda表达式，也可以将匿名函数称lambda函数。
			- 通常会将匿名函数与Python的内置函数filter( )、map( )等共同使用，此时匿名函数将只是这些函数的参数。
			- 匿名函数一般是用在不需要函数名称的场合，例如，一些高阶函数(higher-order function)的参数可能是函数，这时就很适合使用匿名函数，同时让程序变得更简洁。
		- #### lambda匿名函数定义
			- lambda arg1, agr2...: expression
			- ``` python
			  			  product = lambda x, y: x*y
			  			  print(product)
			  ```
	- #### 匿名函数与filter（）
		- 内置函数filter(),将一次对iterable(可以重复执行），如：字符串，列表，元组的元素放入function中，然后将function()函数执行结果是True的元素组成新的筛选对象返回。
		- ```
		  		  filter(function, iterable)
		  ```
		- ``` python
		  		  mylist = [5, 10, 15, 20, 25, 30]
		  		  oddlist = list(filter(lambda x: (x % 2 == 1), mylist))
		  		  print('奇数列表：'， oddlist)
		  ```
	- #### 匿名函数与map()
		- ```
		  		  map(function, iterable)
		  ```
		- 上述函数将一次对iterable（可以重复执行）例如：字符串，列表，元组的元素放入function内，然后将function()函数执行结果组成新的筛选对象返回。
		- ``` python
		  		  mylist = [5, 10, 15, 20, 25, 30]
		  		  squarelist = list(map(lambda x: x ** 2, mylist))
		  		  
		  		  print('列表的平方值', squarelist)
		  ```
	- #### pass 与函数
		- 不执行任何操作
	- #### type关键字应用在函数
		- 返回函数的类型，如： 内置函数， 函数