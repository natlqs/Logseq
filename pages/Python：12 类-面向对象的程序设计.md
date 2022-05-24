- ## 12 类-面向对象的程序设计
  title:: Python：12 类-面向对象的程序设计
	- Python其实是一种面向对象的编程(Object Oriented Programming)，在Python中其实所有的数据类型皆是对象，Python也允许程序设计师自创数据类型，这种自创的数据类型就是本章的主题类(class)。
	- ### 类的定义与使用
	- #### 定义
		- ```
		  		  class Classname()
		  		    statement1
		  		    ...
		  		    statementn
		  ```
		- ``` python
		  		  class Banks(): # 类名
		  		    title = 'taipei bank' # 属性
		  		    def motto(self):    # 方法
		  		      return '以客为尊'
		  ```
	- #### 类的使用
		- 若是想操作类的属性与方法首先需定义该类的对象(object)变量，可以简称对象，然后使用下列方式操作。
			- object.类的属性
			- object.类的方法( )
		- ``` python
		  		  class Banks(): # 类名
		  		    title = 'taipei bank' # 属性
		  		    def motto(self):    # 方法
		  		      return '以客为尊'
		  		  userbank = Banks()    # 定义类的对象
		  		  print(userbank.title())
		  		  print(userbank.motto())
		  ```
	- #### 类的构造函数
		- 初始化类是在类内建立一个初始化方法(method)，这是一个特殊方法，当在程序内定义这个类的对象时将自动执行这个方法。初始化方法有一个固定名称是“_*init*_()”，写法是init左右皆是2个底线字符，init其实是initialization的缩写，通常又将这类初始化的方法称构造函数(constructor)。在这初始化的方法内可以执行一些属性变量设定
		- ``` python
		  		  class Banks():
		  		    title = 'taipei bank'
		  		    def __init__(self, uname, money):
		  		      self.name = uname
		  		      self.money = money
		  		    def get_balance(self):
		  		      return self.balance
		  		  hungbank = Banks('hung', 100)
		  		  print(hungbank.name.title(), '存款金额', hungbank.get_balance())
		  ```
	- #### 属性初始值的设定
		- 通常Python在设初始值时是将初始值设在`__init__( )`方法内
	- ### 类的访问权限--封装(encapsulation)
		- 类内的属性可以让外部引用的称公有(public)属性，而可以让外部引用的方法称公有方法。
		- Python也提供一个私有属性与方法的观念，这个观念的主要精神是类外无法直接更改类内的私有属性，
		  类外也无法直接调用私有方法，这个观念又称封装(encapsulation)。
	- #### 私有属性
		- 为了确保类内的属性的安全，其实有必要限制外部无法直接获取类内的属性值。
		- Python对于类内的属性增加了私有属性(private attribute)的观念，应用方式是定义时在属性名称前面增加__(2个底线)，类外的程序无法引用私有属性
	- #### 私有方法
		- 私有方法(private method)，类外的程序无法调用。于定义方式与私有属性相同，只要在方法前面加上__(2个底线)符号即可。
	- ### 类的继承
	- #### 类的继承
		- 在面向对象程序设计中类是可以继承的，其中被继承的类称父类(parent class)或基类(base class)，
		  继承的类称子类(child class)或衍生类(derived class)。类继承的最大优点是许多父类的公有方法或属性，在子类中不用重新设计，可以直接引用。
		- ```
		  		  class BaseClassName():
		  		    statement
		  		  class DerivedClassName(BaseClassName):
		  		    statement
		  ```
	- #### 获取基类的私有属性
		- 类外是无法直接取得类内的私有属性，即使是它的衍生类也无法直接读取，如果真要取得可以使用return方式，传回私有属性内容。
	- #### 衍生类与基类有相同名称的属性
		- 程序设计时，衍生类也可以有自己的初始化_*init*_( )方法，同时也有可能衍生类的属性与方法名称和基类重复，碰上这个状况Python会先找寻衍生类是否有这个名称，如果有则先使用，如果没有则使用基类的名称内容。
	- #### 衍生类与基类有相同名称的方法
		- 程序设计时，衍生类也可以有自己的方法，同时也有可能衍生类的方法名称和基类方法名称重复，碰上这个状况Python会先找寻衍生类是否有这个名称，如果有则先使用，如果没有则使用基类的名称内容。
	- #### 衍生类引用基类的方法
		- 衍生类引用基类的方法时需使用super( )
	- #### 三代同堂的类与取得基类的属性super( )
		- super( ).**init**( )  # 将父类的属性复制
	- #### 兄弟类属性的取得
		- 假设有一个父亲(Father)类，这个父亲类有2个儿子，分别是Ivan类和Ira类，如果Ivan类想取得Ira类的属性iramoney，可以使用下列方法。
		- ```
		  		  Ira( ).iramoney  # Ivan取得Ira的属性iramoney
		  ```
	- ### 多态(polymorphism)
	- ### 多重继承
	- ### type和instance
	- ### 特殊属性
	- #### _*doc*_ 文档字符串
		- 文档字符串的英文原意是文档字符串(docstring)，Python鼓励程序设计师在设计函数或类时，尽量为函数或类增加文档的批注，未来可以使用_*doc*_特殊属性列出此文档批注。
	- #### ``__name__``属性
		- ``` python
		  		  if __name__ == '__main__':
		  		    dosomething()
		  ```
		- 如果上述程序是自己执行，那么_*name**就一定是**main*_。
	- ### 类的特殊方法
	- #### _*str*_()方法
		- 该方法可以协助返回易读取的字符串
	- #### _*repr*_()方法
	- #### _*iter*_()方法