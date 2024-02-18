- ## 15 程序除错与异常处理
	- 将程序错误(error)称作程序异常(exception)
	- ### 程序异常
		- #### 撰写异常处理程序 try - except
			- ```
			  			  try - except    # 发生异常被捕捉时程序会执行异常处理程序，然后跳开异常位置，再继续往下执行。
			  ```
			- ``` python
			  			  try:
			  			    指令   # 预先设想可能引发错误异常的指令
			  			  except 异常对象： # error名称如： ZeroDivisionError
			  			    异常处理程序    # 通常是指出异常原因，方便修正
			  ```
			- ``` python
			  			  def division(x, y):
			  			    try:    # try - except
			  			      retrun x/y
			  			    except ZeroDivisionError:   # 除数为0时执行
			  			      print('除数不可为0')
			  			  
			  			  print(division(10, 2))
			  			  print(division(5, 0))
			  			  print(division(6, 3))
			  ```
		- #### try-except-else、
		- ```
		   try-except-else # try内的指令正确时，可以执行else的指令区块。
		  ```
		- #### FileNotFoundError 找不到文件错误
			- 程序设计时另一个常常发生的异常是打开文件时找不到文件，这时会产生FileNotFoundError异常。
		- #### 分析单一文件的字数
		  ```python
		  			 def wordsNum(fn):
		  			    try:
		  			      with open(fn) as file_obj:
		  			      data = file_obj.rad()
		  			    except FileNotFoundError:
		  			      print('找不到%s文件'% fn)
		  			    else:
		  			      wordlist = data.split()
		  			      print(fn, '文章的字数是', len(wordlist))
		  			  
		  			  file = 'ch15_6.txt'
		  			  wordsNum(file)
		  ```
		- #### 分析多个文件的字数
			- ``` python
			  			  def wordsNum(fn):
			  			    try:
			  			      with open(fn) as file_obj:
			  			        data = file_obj.rad()
			  			    except FileNotFoundError:
			  			      print('找不到%s文件'% fn)
			  			    else:
			  			      wordlist = data.split()
			  			      print(fn, '文章的字数是', len(wordlist))
			  			  
			  			  files = ['data1.txt', 'data2.txt', 'data3.txt']
			  			  for file in files:
			  			    wordsNum(file)
			  ```
	- ### 设计多组异常处理程序
		- #### 常见的异常处理对象
			- AttributeError    # 通常指对象没有这个属性
			- Exception   # 一般错误皆可用
			- FileNotFoundError   # 找不到open()打开的文件
			- IOError     # 在输入或输出时发生错误
			- IndexError    # 索引超出范围区间
			- KeyError    # 在映射中没有这个键
			- MemoryError   # 需求内存空间超出范围
			- NameError     # 对象名称未申明
			- SyntaxError   # 语法错误
			- SystemError   # 直译器的系统错误
			- TypeError     # 数据类型错误
			- ValueError    # 传入无效参数
			- ZeroDivisionError   # 除数为0
		- #### 设计捕捉多个异常
			- ```
			  			  try:	
			  			    指令
			  			  except 异常对象1：
			  			    异常处理程序1
			  			  except 异常对象2：
			  			    异常处理程序2
			  ```
			- ``` python
			  			  def division(x, y):
			  			    try:    # try - except
			  			      retrun x/y
			  			    except ZeroDivisionError:   # 除数为0时执行
			  			      print('除数不可为0')
			  			    except TypeError:
			  			      print('使用字符做除法运算异常')
			  			  
			  			  print(division(10, 2))
			  			  print(division(5, 0))
			  			  print(division(6, 3))
			  ```
		- #### 使用except捕捉多个异常
			- ```
			  			  try:
			  			    指令
			  			  except (异常对象1， 异常对象2， ......):
			  			    异常处理程序
			  ```
			- ``` python
			  			  def division(x, y):
			  			    try:    # try - except
			  			      retrun x/y
			  			    except (ZeroDivisionError, TypeError):   # 除数为0时执行
			  			      print('除数为0发生 或 使用字符做除法运算异常')
			  			  
			  			  print(division(10, 2))
			  			  print(division(5, 0))
			  			  print(division(6, 3))
			  ```
		- #### 处理异常但是使用python内置的错误信息
			- python也支持发生异常时使用系统内置的异常处理信息。
			- ```
			  			  try:
			  			    指令
			  			  except 异常对象 as e:
			  			    print(e)
			  ```
			- ``` python
			  			  def division(x, y):
			  			    try:    # try - except
			  			      retrun x/y
			  			    except (ZeroDivisionError, TypeError) as e:   # 除数为0时执行
			  			      print('e')
			  			  
			  			  print(division(10, 2))
			  			  print(division(5, 0))
			  			  print(division(6, 3))
			  ```
		- #### 捕捉所有异常
			- ```
			  			  try:
			  			    指令
			  			  except:
			  			    异常处理程序
			  ```
			- ``` python
			  			  def division(x, y):
			  			    try:
			  			      return x/y
			  			    except:
			  			      print('异常发生')
			  			  print(division(10, 2))
			  			  print(division(5, 0))
			  			  print(division('a', 'b'))
			  			  print(division(6, 3))
			  ```
	- ### 丢出异常
		- 设计程序时如果发生某些状况，我们自己将它定义为异常然后丢出异常信息，
		  程序停止正常往下执行，同时让程序跳到自己设计的except去执行。
			- ```
			  			  raise Exception('msg')
			  			  ...
			  			  ...
			  			  try:
			  			    指令
			  			  except Exception as err:
			  			    print('messge1', + str(err))
			  			  - ```python
			  			  def passWord(pwd):
			  			    pwdlen = len(pwd)
			  			    if pwdlen < 5:
			  			      raise Exception('密码长度不足')
			  			    if pwdlen > 8:
			  			      raise Exception('密码长度太长')
			  			    print('密码长度正确')
			  			  for pwd in ('aaabbbccc', 'aaa', 'aaabbb'):
			  			    try:
			  			      passWord(pwd)
			  			    except Exception as err:
			  			      print('密码长度检查异常发生：', str(err))
			  ```
	- ### 记录Traceback字符串
		- 每次错误屏幕皆出现Traceback字符串，在这个字符串中指出程序错误的原因。
		  如果我们导入traceback模块，就可以使用traceback.format_exc( )记录这个Traceback字符串。
		- ``` python
		  		  def passWord(pwd):
		  		    pwdlen = len(pwd)
		  		    if pwdlen < 5:
		  		      raise Exception('密码长度不足')
		  		    if pwdlen > 8:
		  		      raise Exception('密码长度太长')
		  		    print('密码长度正确')
		  		  for pwd in ('aaabbbccc', 'aaa', 'aaabbb'):
		  		    try:
		  		      passWord(pwd)
		  		    except Exception as err:
		  		      errlog = open('errch15_16.txt', 'a')
		  		      errlog.write(traceback.format_exc())
		  		      errlog.close()
		  		      print('将traceback写入错误文件err15_16.txt完成')
		  		      print('密码长度检查异常发生：', str(err))
		  ```
		- ### finally
			- finally和try配合使用，在try之后可以有except或else，
			  这个finally关键词必须放在except和else之后，
			  同时不论是否有异常发生一定会执行这个finally内的程序代码。
			  这个功能主要是用在Python程序与数据库连接时，输出连接相关信息。
			- ``` python
			  			  def division(x, y):
			  			    try:
			  			      return x/y
			  			    except:
			  			      print('异常发生')
			  			    finally:
			  			      print('阶段任务完成')
			  			  print(division(10, 2), '\n')
			  			  print(division(5, 0), '\n')
			  			  print(division('a', 'b'), '\n')
			  			  print(division(6, 3), '\n')
			  ```
	- ### 程序断言assert
		- #### 设计断言
			- assert关键词主要功能是协助程序设计师在程序设计阶段，
			  对整个程序的执行状态做一个全面性的安全检查，
			  以确保程序不会发生语意上的错误。
			- ``` python
			  			  class Banks():
			  			    title = 'Taipei Bank'
			  			    def __init__(self, uname, money):
			  			      self.name = uname
			  			      self.balance = money
			  			    def save_money(self, money):
			  			      assert money > 0, '存款money必须大于0'  # 如果出现该错误，报错
			  			      self.balance += money
			  			      print('存款'， money, '完成')
			  			    def withdraw_money(self, money):
			  			      assert money > 0, '提款金额必须大于0 '  # 如果小于0 ，报错
			  			      assert money <= self.balance, '存款金额不足'
			  			      self.balance -= money
			  			      print('提款', money, '完成')
			  			    def get_balance(self):
			  			      print(self.name.title(), '目前余额：', self.balance)
			  			  hungbank = Banks('hung', 100)
			  			  hungbank.get_balance()
			  			  hungbank.save_money(300)
			  			  hungbank.get_balance()
			  			  hungbank.save_money(-300)
			  			  hungbank.get_balance()
			  ```
		- #### 停用断言
			- 断言assert一般是用在程序开发阶段，如果整个程序设计好了以后，
			  想要停用断言assert，可以在Windows的命令提示环境（可参考附录B-2-1），
			  执行程序时使用“-O”选项停用断言。
	- ### 程序日志模块logging
		- 程序日志logging功能，这个功能可以协助我们执行程序的除错,
		  有了这个功能我们可以自行设定关键变量在每一个程序阶段的变化，
		  由这个关键变量的变化可方便我们执行程序的除错，
		  同时未来不想要显示这些关键变量数据时，可以不用删除，
		  只要适度加上指令就可隐藏它们
		- #### logging模块
			- logging模块有提供方法可以让我们使用程序日志logging功能，
			  在使用前须先使用import导入此模块。
			- ```
			  			  import logging
			  ```
	- #### logging的等级
		- DEBUG等级使用logging.debug( )显示程序日志内容，所显示的内容是程序的小细节，最低层级的内容，感觉程序有问题时可使用它追踪关键变量的变化过程。
		- INFO等级使用logging.info( )显示程序日志内容，所显示的内容是记录程序一般发生的事件。
		- WARNING等级使用logging.warning( )显示程序日志内容，所显示的内容虽然不会影响程序的执行，但是未来可能导致问题的发生。ERROR等级使用logging.error( )显示程序日志内容，通常显示程序在某些状态将引发错误的缘由。
		- CRITICAL等级使用logging.critical( )显示程序日志内容，这是最重要的等级，通常是显示将让整个系统当掉或中断的错误。
	- ### BUG典故