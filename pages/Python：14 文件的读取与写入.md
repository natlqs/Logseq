- ## 14 文件的读取与写入
	- ### 文件夹与文件路径
		- 例如： D:Pythonch14ch14_1.py
		- #### 绝对路径与相对路径
			- 绝对路径：路径从根目录开始表达 如：   D:Pythonch14ch14_1.py
			- 相对路径： 相对于当前工作目录的路径
			- 在操作系统处理文件夹的观念中会使用2个图书符号'.'和'..'，
				- '.'指当前文件夹，'..'指上一层文件夹。
				- 当前文件夹可以省略'.'。
		- #### OS模块与OS.path模块
			- 在python内有关文件路径的模块是os，在文件操作时需导入此模块
			- ```
			  			    import os # 导入os模块
			  ```
		- #### 检查路径方法exist/isabs/isdir/isfile
			- exist(path): 如果path的文件或文件夹存在传回True，否则传回Flase
			- isabs(path): 如果path的文件或文件夹是绝对路径传回True，否则传回False
			- isdir(path): 如果path是文件夹传回True，否则传回False
			- isfile(path): 如果path是文件传回True，否则传回False
		- #### 文件与目录的操作mkdir/rmdir/remove/chdir
			- mkdir(path): 建立path目录
			- rmdir(path): 删除path目录，限制只能是空的目录。
			- remove(path): 删除path文件
			- chdir(path): 将当前工作文件夹改至path。
		- #### 结合传回文件路径 os.path.join()
			- os.path.join()参数内的字符串结合为一个文件路径
			- ``` python
			  			  import os
			  			  print(os.path.join('D:\\', 'python', 'ch14', 'ch14_1.py'))
			  ```
		- #### 获得特定文件的大小os.path.getsize()
			- os.path.getsize() 可以获得特定文件的大小
		- #### 获得特定工作目录的内容os.listdir()
			- os.listdir() 以列表的方式列出特定工作目录的内容
			- ``` python
			  			  import os
			  			  print(os.listdir('D:\\python\\ch14'))
			  ```
		- #### 获得特定工作目录内容glob
			- Python内还有一个模块可用于列出特定工作目录内容glob，
			  当导入这个模块后可以使用glob方法获得特定工作目录的内容，
			  这个方法最大特色是可以使用通配符' * '，例如，可用' *.txt '获得所有txt扩展名的文件
			- ``` python
			  			  import glob
			  			  print('方法1：列出\\python\\ch14的所有文件')
			  			  for file in glob.glob('D:\\python\\ch14\*.*'):
			  			      print(file)
			  			  print('方法2: 列出目前工作目录的特定文件')
			  			  for file in glob.glob('ch14_1*.py'):
			  			      print(file)       # ch14_1.py, ch14_10.py, ch14_11.py...
			  			  print('方法3：列出目前工作目录的特定文件')
			  			  for file in glob.glob('ch14_2*.*'):
			  			      print(file)       # ch14_2.py, ch14_21.txt...
			  ```
		- #### 遍历目录树os.walk()
			- os.walk()可以遍历目录树，每次循环时传回3个值：
				- 当前工作目录名称(dirName)
				- 当前工作目录底下的子目录列表(sub_dirNames)
				- 当前工作目录底下的文件列表(fileNames)
			- ```
			  			  for dirName, sub_dirNames, fileNames in os.walk(目录路径):
			  			    程序区块
			  ```
			- 上述dirName, sub_dirNames, fileNames名称可以自行命名，
			  顺序则不可以更改，至于目录路径可以使用绝对地址或相对地址，
			  如果不注明则代表当前工作目录的子目录。
		- #### 取得当前工作目录 os.getcwd()
			- os模块内的getcwd()可以取得当前工作目录
			- ``` python
			  			  import os
			  			  print(os.getcwd())
			  ```
		- #### 取得绝对路径 os.path.abspath
			- os.path.abspath(path)会传回path的绝对路径。
			- ``` python
			  			  import os
			  			  print(os.path.abspath('.'))   # 列出当前目录的绝对路径
			  			  print(os.path.abspath('..'))  # 列出上一层工作目录的绝对路径
			  			  print(os.path.abspath('ch14.py')) # 列出目前文件的绝对路径
			  ```
		- #### 传回特定路段相对路径os.path.relpath()
			- os.path.relpath(path, start) 会传回从start到path的相对路径
			  如果省略start，则传回当前工作目录至path的相对路径
			- ``` python
			  			  import os
			  			  print(os.path.relpath('D:\\'))    # 列出目前目录至D:\的相对路径
			  			  print(os.path.relpath('D:\\python\\ch13'))    # 列出目前目录至特定path的相对路径
			  			  print(os.path.relpath('D:\\', 'ch14.py')) # 列出目前文件至D:\的相对路径
			  ```
	- ### 读取文件
		- Python处理读取或写入文件首先需将文件打开，
		  然后可以一次读取所有文件内容或是一行一行读取文件内容。
		  Python可以使用open( )函数打开文件，文件打开后会传回文件对象，
		  未来可用读取此文件对象方式读取文件内容
		- #### 读取整个文件read()
			- read()读取打开的文件，所有的文件内容将以一个字符串方式被读取然后存入字符串变量内。
			- ``` python
			  			  fn = 'ch14_15.txt'
			  			  file_obj = open(fn)
			  			  data = file_obj.read()
			  			  file_obj.close()      # 文件读取完后要关闭，否则会有不可阈值的 损坏
			  			  print(data)
			  ```
			- 整个文件是以字符串方式被读取与储存，所以打印字符串时最后一行的空白行也将显示出来，
			  不过我们可以使用rstrip( )将data字符串变量（文件）末端的空格符删除。
		- #### with关键词
			- with关键词应用在打开文件与建立文件对象时。
			- ```
			  			  with open(file) as file_obj:
			  			    相关系列指令
			  ```
			- 这种方式打开文件，可以不必在程序中关闭文件，with指令会在结束不需要此文件时自动将它关闭，文件经“with open( ) as文件对象”打开后会有一个文件对象，就可以使用前一节的read( )读取此文件对象的内容
		- #### 逐行读取文件内容
			- ```
			  			  for line in file_obj:     # line 和 file_obj可以自行取名，file_obj是文件对象
			  			      循环相关系列指令
			  ```
			- ``` python
			  			  fn = 'ch14_15.txt'
			  			  with open(fn) as file_obj:    # 用默认mode = r 开启文件
			  			      for line in file_obj:
			  			          print(line)
			  ```
		- #### 逐行读取readlines()
			- 使用with关键词配合open( )时，所打开的文件对象当前只在with区块内使用，
			  特别是想要遍历此文件对象时。Python另外有一个方法readlines( )可以逐行读取，
			  同时以列表方式储存，另一个特色是读取时每行的换行字符皆会储存在列表内。
			  当然更重要的是我们可以在with区块外遍历原先文件对象内容。
			- ``` python
			  			  fn = 'ch14_20.txt'
			  			  with open(fn) as file_obj:
			  			      obj_list = file_obj.readlines()  # 每次读一行
			  			  print(obj_list)   # 打印列表
			  ```
			- ``` python
			  			  fn = 'ch14_20.txt'
			  			  with open(fn) as file_obj:
			  			      obj_list = file_obj.readlines()
			  			  for line in obj_list:
			  			      print(line.rstrip())      # rstrip() 将字符串末端的空格删除
			  ```
		- #### 数据组合
			- Python的多功能用途，可以让我们很轻松地组合数据
			- ``` python
			  			  fn = 'ch14_20.txt'
			  			  with open(fn) as file_obj:
			  			      obj_list = file_obj.readlines()
			  			  str_obj = ' '
			  			  for line in obj_list:
			  			      str_obj += line.rstrip()
			  			  print(str_obj)
			  ```
		- #### 字符串替换
			- 字符串对象.replace(旧字符串， 新字符串)
			- ``` python
			  			  fn = 'ch14_20.txt'
			  			  with open(fn) as file_obj:
			  			      data = file_obj.read()
			  			      new_data = data.replace('工专', '科大')
			  			      print(new_data.rstrip())
			  ```
		- #### 数据搜寻使用find()
			- find()可以执行数据搜寻，还会传回数据的位置索引，如果没有传回-1
			- ```
			  			  index = str.find(sub[,start[,end]]) # sub是欲搜寻字符串
			  ```
			- ``` python
			  			  fn = 'xxx.txt'
			  			  with open(fn) as file_obj:
			  			      obj_list = file_obj.readlines()
			  			  str_obj = ' '
			  			  for line in obj_list:
			  			      str_obj += line.rstrip()
			  			  findstr = input('请输入欲搜寻字符串= ')
			  			  index = str_obj.find(findstr)
			  			  if index >=0: 
			  			      print('搜寻%s字符串在%s文件中' % (findstr, fn))
			  			      print('在索引%s位置出现' % index)
			  			  else:
			  			      print('搜寻%s字符串不在%s文件中' % (findstr, fn))
			  ```
		- #### 普通数据的搜寻
			- ``` python
			  			  fn - 'xxx.txt'
			  			  with open(fn) as file_obj:
			  			      obj_list = file_obj.readlines()
			  			  
			  			  str_obj = ' '
			  			  for line in obj_list:
			  			      str_obj += line.rstrip()
			  			  findstr = input('请输入欲搜寻字符串=')
			  			  if findstr in str_obj:
			  			      print('搜寻%s字符串在%s文件中') % (findstr, fn))
			  			  else:
			  			      print('搜寻%s字符串不在%s文件中') % (findstr, fn))
			  ```
			-