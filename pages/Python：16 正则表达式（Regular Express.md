- ## 16 正则表达式（Regular Express）
  background-color:: #264c9b
	- ### 正则表达式基础
	  background-color:: #497d46
		- python有关正则表达式的方法是在re模块内，所以使用时需导入re模块
		- ```
		  		  import re    # 导入re模块
		  ```
		- #### 建立搜寻字符串模式
			- 正则表达式是一种文本模式的表达方法，在这个方法中d表示0-9的数字字符。
			- 0518-8722-1534 用正则表达式为： 'dddd-dddd-dddd'
			- 由逸出字符的观念可知，上述表达式当字符串放入函数内需增加'',所以整个正则表达式：
			- ```
			  			  '\\d\\d\\d\\d-\\d\\d\\d\\d-\\d\\d\\d\\d'
			  ```
			- 字符串前加r可以防止字符串内的逸出字符被转译，所以还可以表达为：
			- ```
			  			  r'\d\d\d\d-\d\d\d\d-\d\d\d\d'
			  ```
		- #### 使用re.compile()建立Regex对象
			- re模块内的compile()方法可以将正则表达式当作字符串参数，然后传回一格Reggex(**Reg**ular **ex**pression)对象
			- ```
			  			  phoneRule = re.compile(r'\d\d\d\d-\d\d\d\d-\d\d\d\d')
			  ```
		- #### 搜寻对象 search()
			- 在Regex对象内有search()方法，由Regex对象启用，然后将欲搜寻的字符串放在这个方法
			- ```
			  			  phoneNum = phoneRule.search(msg) # msg是欲搜寻的字符串
			  ```
			- 如果找不到比对相符的字符串会传回None，如果找到比对相符的字符串会将结果传回所设定的phoneNum变量对象。
			- 处理此对象主要是将搜寻结果传回，可以用group()方法将结果传回，不过search()将只传回第一个比对相符的字符串。
			- ``` python
			  			  import re
			  			  msg1='please call my secretary using 0930-919-919 or 0952-001-001'
			  			  msg2='please join dinner with me tommorrow night'
			  			  msg3= 'please join dinner with me tommorrow night, call me 0933-080-080'
			  			  
			  			  def parseString(string):
			  			    # 解析字符串是否含有电话号码
			  			    phoneRule = re.compile(r'\d\d\d\d-\d\d\d-\d\d\d')
			  			    phoneNum = phoneRule.search(string)
			  			    if phoneNum != None:
			  			      print('phone num is : %s' % phoneNum.group())
			  			    else:
			  			      print('%s there is no phone num in this string' % string)
			  			  
			  			  parseString(msg1)
			  			  parseString(msg2)
			  			  parseString(msg3)
			  ```
			- ```
			  			  执行结果
			  			  phone num is : 0930-919-919
			  			  please join dinner with me tommorrow night there is no phone num in this string
			  			  phone num is : 0930-080-080
			  ```
			- #### 搜寻对象 findall()
				- 可以返回所有找到的匹配项，不像search只返回第一个匹配项。
				- 如果没有比对相符的就传回[ ]空列表
				- phoneRule = re.compile(r'dddd-ddd-ddd')
				- phoneNum = phoneRule.findall(string)    # string是欲搜寻的字符串
				- ``` python
				  			  import re
				  			  msg1='please call my secretary using 0930-919-919 or 0952-001-001'
				  			  msg2='please join dinner with me tommorrow night'
				  			  msg3= 'please join dinner with me tommorrow night, call me 0933-080-080'
				  			  
				  			  def parseString(string):
				  			    # 解析字符串是否含有电话号码
				  			    phoneRule = re.compile(r'\d\d\d\d-\d\d\d-\d\d\d')
				  			    phoneNum = phoneRule.findall(string)
				  			    print('phone num is:' % phoneNum)
				  			  
				  			  parseString(msg1)
				  			  parseString(msg2)
				  			  parseString(msg3)
				  ```
				- ```
				  			  执行结果：
				  			  phone num is: ['0930-919-919', '0952-001-001']
				  			  phone num is: []
				  			  phone num is: ['0933-080-080']
				  ```
			- #### re模块
				- python语言的re模块对于search()和findall()有提供更强的功能，可以省略使用re.compile()直接将比对模式放在各自的参数内。语法格式如下：
				- re.search(pattern, string, flags)
				- re.findal(pattern, string, flags)
				- 上述pattern是欲搜寻的正则表达式，string是所搜寻的字符串，flags可以省略。
				- ``` python
				  			  import re
				  			  msg1='please call my secretary using 0930-919-919 or 0952-001-001'
				  			  msg2='please join dinner with me tommorrow night'
				  			  msg3= 'please join dinner with me tommorrow night, call me 0933-080-080'
				  			  
				  			  def parseString(string):
				  			    # 解析字符串是否含有电话号码
				  			    pattern = r'\d\d\d\d-\d\d\d-\d\d\d'   # re参数
				  			    phoneNum = re.search(pattern, string)   # re参数
				  			    if phoneNum != None:
				  			      print('phone num is : %s' % phoneNum.group())
				  			    else:
				  			      print('%s there is no phone num in this string' % string)
				  			  
				  			  parseString(msg1)
				  			  parseString(msg2)
				  			  parseString(msg3)
				  ```
				- ``` python
				  			  import re
				  			  msg1='please call my secretary using 0930-919-919 or 0952-001-001'
				  			  msg2='please join dinner with me tommorrow night'
				  			  msg3= 'please join dinner with me tommorrow night, call me 0933-080-080'
				  			  
				  			  def parseString(string):
				  			    # 解析字符串是否含有电话号码
				  			    pattern = r'\d\d\d\d-\d\d\d-\d\d\d' # re参数
				  			    phoneNum = re.findall(pattern, string)  # re参数
				  			    print('phone num is:' % phoneNum)
				  			  
				  			  parseString(msg1)
				  			  parseString(msg2)
				  			  parseString(msg3)
				  ```
			- ### 正则表达式pattern优化
			  background-color:: #497d46
				- #### 重复出现的字符
					- r'dddd-ddd-ddd'中d重复出现，重复出现的可以用大括号内部加上重复次数表达：
					- r'd{4}-d{3}-d{3}'
				- #### 更多搜寻比对模式
					- ##### 使用小括号分组
						- 025-28350000
						- r'ddd-dddddddd'
						- r'(ddd)-(dddddddd)'
						- r'(d{2})-(d{8})'
					- ##### re.search()--括号分组的group()
						- 当使用re.search()执行比对时，未来可以使用group()传回比对符合的不同分组，
						  如：group()或group(0)传回第一个比对相符的文字，group(1)传回括号的第一组文字，
						  group(2)传回括号的第二组文字。
						- ``` python
						  				  import re
						  				  msg = 'Please call my secretary using 025-26669999'
						  				  pattern = r'(\d{2})-(\d{8})'
						  				  phoneNum = re.search(pattern, msg)    # 传回搜寻结果
						  				  print('full number is : %s' % phoneNum.group())   # 显示完整号码
						  				  print('full number is : %s' % phoneNum.group(0))   # 显示完整号码
						  				  print('area number is : %s' % phoneNum.group(1))   # 显示完整号码
						  				  print('phone number is : %s' % phoneNum.group(2))   # 显示完整号码
						  ```
						- ```
						  				  执行结果
						  				  full number is : 025-26669999
						  				  full number is : 025-26669999
						  				  area number is : 025
						  				  phone number is : 26669999
						  ```
					- ##### re.findall()--括号分组的group()
						- 如果所搜寻比对的正则表达式字符串有用小括号分组，若是使用findall()方法处理，
						  会传回元组(tuple)的列表(list)，元组内的每个元素就是搜寻的分组内容。
						- ``` python
						  				  import re
						  				  msg = 'Please call my secretary using 025-26669999 or 025-24445555'
						  				  pattern = r'(\d{2})-(\d{8})'
						  				  phoneNum = re.search(pattern, msg)    # 传回搜寻结果
						  				  print(phoneNum)
						  ```
						- `执行结果 [('025', '26669999'), ('025', '24445555')]`
					- #### groups()
						- 注意这是groups(), 有在group后面加上s，当我们使用re.search()搜寻字符串时，可以使用这个方法取得分组的内容。
						- 可以使用多重指定的观念
						- areaNum, localNum = phoneNum.groups()   # 多重指定
						- ``` python
						  				  import re
						  				  msg = 'Please call my secretary using 025-26669999'
						  				  pattern = r'(\d{2})-(\d{8})'
						  				  phoneNum = re.search(pattern, msg)    # 传回搜寻结果
						  				  areaNum, localNum = phoneNum.groups()   # 留意是groups()
						  				  print('area number is : %s' % areaNum)   # 显示完整号码
						  				  print('phone number is : %s' % localNum)   # 显示完整号码
						  ```
						- ``` 执行结果： 
						  				  area number is : 025
						  				  phone number is : 26669999
						  ```
					- #### 部分字符在小括号内
						- 常看到部分字符在小括号内，如： (025)-26669999
						- 在处理小括号时，方法是 $和$
					- #### 使用管道 |
						- | 在正在表达式称管道，使用管道可以同时搜寻对比多个字符串。
						- pattern = 'Mary|Tom' # 注意单引号'或|旁不可留空白
					- #### 多个分组的管道搜寻
						- pattern = John(son|nason|nathan)
						- ``` python
						  				  import re
						  				  msg = 'Johnson, Johnnason and Johnnathan will attend my party tonight'
						  				  pattern = 'John(son|nason|nathan)'
						  				  txts = re.findall(pattern, msg)   # 传回搜寻结果
						  				  print(txts)
						  				  for txt in txts:
						  				    print('John' + txt)
						  ```
						- ``` 执行结果
						  				  ['son', 'nason', 'nathan']
						  				  Johnson
						  				  Johnnason
						  				  Johnnathan
						  ```
					- #### 使用 ? 搜寻
						- 在正则表达式中若某些括号内的字符串或正则表达式可有可无，执行搜寻时皆算成功
						- `pattern = r'John((na)?son)'`  # ?前的na字符串可有可无
						- `pattern = r'(\d\d\d-)?(\d{8})` #  ?前括号内的内容可有可无
					- #### 使用 * 搜寻
						- 在正则表达式中某些字符串或正则表达式可从0到多次，执行搜寻时皆算成功。
						- `pattern = 'John((na)*son)'` # 字符串na可以0到n次
					- #### 使用 + 号搜寻
						- 在正则表达式中若是某些字符串或正则表达式壳可从1到多次，执行搜寻时皆算成功。
						- `pattern = 'John((na)+son)'`  # 字符串na可以1到多次
					- #### 搜寻时忽略大小写
						- 搜寻时若是在search()或findall()内增加第三个参数re.I或re.IGNORECASE,
						  搜寻时就会搜寻大小写，至于打印输出时将以原字符串的格式显示。
						- `txt = re.findall(pattern, msg, re.I)` # 传回搜寻忽略大小写的结果
					- #### 贪婪与非贪婪搜寻
						- pattern = `(son){3, 5}` # 代表所搜寻的字符串是'sonsonson', 'sonsonsonson', 'sonsonsonsonson'
						- pattern = `(son){3, }` # 代表重复3此以上皆符合。 pattern = `(son){,10}` # 代表重复10此以下皆符合。
						- ##### 贪婪模式（greedy）
							- ``` python
							  					  import re
							  					  def searchStr(pattern, msg):
							  					    txt = re.search(pattern, msg)
							  					    if txt == None:
							  					      print('search failure', txt)
							  					    else:
							  					      print('search success', txt.group())
							  					  msg = 'sonsonsonsonson'
							  					  pattern = '(son){3, 5}'
							  					  searchStr(pattern, msg)
							  ```
							- 由上述程序可知，搜寻模式中3，4或5个son重复就算找到了，
							  咳嗽python执行结果是列出最多重复的字符串，5次重复，这是python的默认模式，
							  这种模式又称贪婪模式（greedy）。
						- ##### 非贪婪模式
							- 非贪婪模式是列出最少重复的字符串，以这个实例而言是重复3次，方法是在正则表达式的搜寻模式右边增加？符号
							- pattern = '(son){3, 5}?'    # 非贪婪模式
					- #### 正则表达式的特殊字符
						- ##### 特殊字符表
							- `\d`   0~9的整数子元
							- `\D`  除了0~9的整数子元以外的其他字符
							- `\s`  空白、定位、Tab键、换行、换页字符
							- `\S`  除了空白、定位、Tab键、换行、幻夜字符以外的其他字符
							- `\w`  数字、字母和底线_字符， [A-Za-z0-9_]
							- `\W`  除了数字、字符、字母、底线_字符和[A-Za_z0-9_]以外的其他字符
							- `pattern = '\w+'` # 意义是把不限长度的数字、字母和底线字符当作符合搜寻
							- `pattern = 'John\w*'`  # John开头后面接0~多个数字、字母和底线字符
							- `\d+'` 表示不限长度的数字
							- `\s`  表示空格
							- `\w+` 表示不限长度的数字、字母和底线字符连续字符
						- ##### 字符分类
							- 在字符分类中，中括号内可以不用放上正则表示法的反斜杠\执行.、?、*、(、)等字符的转译。
							  例如，[2-5.]会搜寻2-5的数字和句点，这个语法不用写成[2-5.]。
							- `[a-z]`  代表a-z的小写字符
							- `[A-Z]`  代表A-Z的大写字符
							- `[aeiouAEIOU]` 代表英文发音的元音字符
							- `[2-5]`  代表2-5的数字
						- ##### 字符分类的^字符
							- ###### 中括号内的^
								- 如果在中括号内的左方加上^字符，意义是搜寻不在这些字符内的所有字符。
								- `pattern = '[^aeiouAEIOU]'`  返回不会出现[aeiouAEIOU]的字符
							- ###### 正则表达式^字符
								- 在正则表达式起始位置加上^字符，表示正则表达式的字符串必须出现在被搜寻字符串的起始位置，这样搜寻成功才算成功。
						- #### 正则表达式的$字符
							- 正则表示法的末端放置$字符时，表示正则表示法的字符串必须出现在被搜寻字符串的最后位置，这样搜寻成功才算成功。
						- #### 单一字符使用通配符 “.”
							- 正则表示法的末端放置$字符时，表示正则表示法的字符串必须出现在被搜寻字符串的最后位置，这样搜寻成功才算成功。
						- #### 所有字符使用通配符 "."
							- “.”字符与“*”组合，可以搜寻所有字符，意义是搜寻0到多个通配符（换行字符除外）。
						- #### 换行字符
							- “.*”搜寻时碰上换行字符，搜寻就停止。Python的re模块提供参数re.DOTALL，
							  功能是包括搜寻换行字符，可以将此参数放在search( )、findall( )或compile( )。
							- `txt = re.search(pattern, msg, re.DOTALL)` 传回搜寻含换行字符结果