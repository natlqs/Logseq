- ## property属性
	- property属性负责把类中的一个方法当作属性进行使用，这样做可以简化代码使用
	- 定义property属性有两种方式
		- 装饰器方式
			- ![image.png](../assets/image_1649244155777_0.png)
			- ```python
			  class Person(object):
			      def __init__(self):
			          self.__age = 0
			      # 获取属性
			      @property
			      def age(self):
			          return self.__age
			      # 修改属性
			      @age.setter
			      def age(self, new_age):
			          self.__age = new_age
			  # p = Person()
			  # age = p.age()
			  # print(age)
			  
			  p = Person()
			  print(p.age)
			  
			  # 修改属性
			  p.age = 100
			  print(p.age)
			  ```
		- 类属性方式
			- 第一个参数是获取属性时要执行的方法
			- 第二个参数是设置属性时要执行的方法
			- ![image.png](../assets/image_1649245224612_0.png)
			- ```python
			  class Person(object):
			      def __init__(self):
			          self.__age = 0
			      def get_age(self):
			          # 当获取age属性时会使用该方法
			          return self.__age
			  
			      def set_age(self, new_age):
			          # 当设置属性时会使用该方法
			          if new_age >=150:
			              print('年龄错误')
			          else:
			              self.__age = new_age
			      age = property(get_age, set_age)
			  
			  p = Person()
			  print(p.age)
			  # 设置属性
			  p.age = 100
			  print(p.age)
			  ```
- ## with语句和上下文管理器
	- with语句的作用
		- with语句的写法既简单又安全，文件操作的时候使用with语句可以自动调用关闭文件操作，即使出现异常也会自动调用关闭文件操作。
		- ![image.png](../assets/image_1649245446050_0.png)
		- ```python
		  with open('1.txt', 'r') as f:
		      file_data = f.read()
		      print(file_data)
		  ```
	- 上下文管理器
		- with语句之所以这么强大，背后是上下文管理器支撑的。
		- 一个类只要实现了`__enter__()`和`__exit__()`这两个方法，通过该类创建的对象我们就称之为上下文管理器
		- __enter__表示上文方法，需要返回一个操作文件对象
		- _exit__表示下文方法，with语句执行完成会自动执行，即使出现异常也会执行该方法
		- ![image.png](../assets/image_1649245787572_0.png)
		- ```python
		  class File(object):
		      def __init__(self, file_name, file_model):
		          self.file_name = file_name
		          self.file_model = file_model
		  
		      def __enter__(self):
		          print('这是上文')
		          self.file = open(self.file_name, self.file_model)
		          return self.file
		      
		      def __exit__(self, exc_type, exc_val, exc_tb):
		          print('这是下文')
		          self.file.close()
		  
		  with File('1.txt', 'r') as f:
		      file_data = f.read()
		      print(file_data)
		  ```
- ## 生成器的创建方式
	- 生成器的作用
		- 根据程序设计者指定的规则循环生成数据，当条件不成立时则生成数据。生成器的数据不是一次性全部生成出来，而是使用一个，再生成一个，可以节约大量的内存。
	- 生成器的创建方式
		- 生成器推导式
			- 与列表推导式类似，只不过生成器推导式使用小括号
			- **next** 函数可以获取生成器中的下一个值
			- **for 循环**遍历生成器中的每一个值
			- ![image.png](../assets/image_1649247090128_0.png)
			- ![image.png](../assets/image_1649248532758_0.png)
		- yield关键字：
			- yield关键字生成器的特征：在def函数中具有yield关键字
				- ```python
				  def mygenerater(n):
				    for i in range(n):
				      print('开始生成...')
				      yield i
				      print('完成一次...')
				  ```
			- 生成器注意点：
				- 1 代码执行到yield会暂停，然后把结果返回出去，下次启动生成器会在赞同的位置继续往下执行
				- 2 生成器如果把数据生成完成，再次获取生成器中的下一个数据会抛出一个StopIteration异常，表示停止迭代异常
				- 3 while循环内部没有处理异常操作，需要手动添加处理异常操作
				- 4 for循环内部自动处理了停止迭代异常，使用起来更加方便，推荐大家使用。
		- 斐波那契数列
			- ```python
			  # 
			  def fb(num):
			      a = 0
			      b = 1
			      # 记录生成了几个数字
			      index = 0
			      while index < num:
			          result = a
			          a, b = b, a + b
			          yield result
			          index += 1
			  
			  f = fb(5)
			  # print(next(f))
			  print(next(f))
			  for i in f:
			      print(i)
			  ```
- ## 深拷贝浅拷贝
	- 浅拷贝
		- copy函数是浅拷贝，只对可变类型的第一层对象进行拷贝，对拷贝的对象开辟新的内存空间进行存储，不会拷贝对象内部的子对象。
			- ![image.png](../assets/image_1649250910603_0.png)
		- 不可变类型进行浅拷贝不会给拷贝的对象开辟新的内存空间，而只是拷贝了这个对象的引用。
			- ![image.png](../assets/image_1649251177437_0.png)
	- 深拷贝
		- 深拷贝使用deepcopy函数
			- 只要发现拷贝对象又可变类型就会对该对象到最后一个可变类型的每一层对象进行拷贝，对每一层拷贝的对象都会开辟新的内存空间进行存储。
			- ![image.png](../assets/image_1649251423809_0.png)
		- ![image.png](../assets/image_1649251570273_0.png)