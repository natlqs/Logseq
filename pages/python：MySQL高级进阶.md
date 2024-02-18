- MySQL实战操作
	- 强化训练
		- ![image.png](../assets/image_1649074932019_0.png)
		- ![image.png](../assets/image_1649074973150_0.png) ![image.png](../assets/image_1649075017132_0.png)
	- 删除异常
		- ![image.png](../assets/image_1649075119265_0.png)
		- ![image.png](../assets/image_1649075196717_0.png)
		- ![image.png](../assets/image_1649075388333_0.png)
		- ![image.png](../assets/image_1649075640293_0.png)
	- 外键的使用
		- ![image.png](../assets/image_1649075955693_0.png)
		- ![image.png](../assets/image_1649076341352_0.png)
		- ![image.png](../assets/image_1649076276876_0.png)
		- ![image.png](../assets/image_1649076356818_0.png)
		- ![image.png](../assets/image_1649076372920_0.png)
	- 视图的概念
		- ![image.png](../assets/image_1649076467893_0.png)
		- ![image.png](../assets/image_1649076542070_0.png)
	- 视图的使用
		- ![image.png](../assets/image_1649076566526_0.png){:height 804, :width 640}
		- ![image.png](../assets/image_1649076789410_0.png)
		- ![image.png](../assets/image_1649076806337_0.png)
	- 事务的概念及特点
		- ![image.png](../assets/image_1649076935359_0.png)
		- ![image.png](../assets/image_1649076946417_0.png)
		- ![image.png](../assets/image_1649076989595_0.png)
		- ![image.png](../assets/image_1649077118790_0.png)
		- ![image.png](../assets/image_1649077139884_0.png)
	- 事务的使用及ACID特性的验证
		- ![image.png](../assets/image_1649077216797_0.png)
	- 索引
		- ![image.png](../assets/image_1649077559068_0.png)
		- ![image.png](../assets/image_1649077576017_0.png)
		- ![image.png](../assets/image_1649077999421_0.png)
- MySQL设计之三范式
	- 设计关系数据库时，遵从不同的规范要求，设计出合理的关系型数据库，这些不同的规范要求被称为不同的范式。各种范式呈递次规范，越高的范式数据库冗余越小。
	- 数据冗余是指数据之间的重复，也可以说是同一数据存储在不同数据文件中的现象。
	- 根据数据库的冗余的大小，目前关系型数据库有六种范式。
	- 六种范式：一般遵循前三种范式即可
	  collapsed:: true
		- 第一范式（1NF）：强调的是字段的原子性，即一个字段不能够再分成其他几个字段。
		- 第二范式（2NF）：满足1NF的基础上，另外包含（1.表必须有一个主键；2.非主键字段必须完全依赖于主键，而不能只依赖于主键的一部分）
		- 第三范式（3NF）非主键字段必须直接依赖于主键，不能存在传递依赖。
		- 巴斯-科德范式（BCNF）
		- 第四范式（4NF）
		- 第五范式（5NF，又称完美范式）
- E-R模型及表间关系
	- E-R模型即实体-关系模型，就是描述数据库存储数据的结构模型。
	- 对于大型公司开发项目，我们需要根据产品经理的设计，先使用建模工具，如：power designer， db desiner等软件来画出实体-关系模型（E-R模型）
	- 然后根据三范式设计数据库表结构
	- E-R模型即表间关系
	  collapsed:: true
		- ![image.png](../assets/image_1649079600839_0.png)
- Python连接MySQL数据库
	- PyMysql模块
		- 如果使用之前学习的mysql客户端来完成这个操作，那么这个工作量无疑是巨大的。
		- 我们可以通过使用程序代码的方式去连接MySQL数据库，然后对MySQL数据库进行增删改查的方式，实现10000条数据的插入，像这样的使用代码的方式操作数据库就成为数据库编程。
		- 安装pymysql
			- Windows：`pip install pymysql`
			- Ubuntu：`sudo pip3 install pymysql`
	- pymysql使用步骤
		- ``` python
		  # python连接mysql数据库_查询操作
		  # 导入pymysql包
		  import pymysql
		  
		  # 创建连接对象
		  conn = pymysql.connect(host='localhost', port=3306, user='root', password='mysql', database='python_test_1', charset='utf8')
		  
		  # 获取游标对象
		  cs = conn.cursor()
		  
		  # pymysql完成数据的查询操作
		  sql = 'select * from students;'
		  # 这里获取的是sql影响的行数
		  # content = cs.execute(sql)
		  cs.execute(sql)
		  # 获取一条数据
		  content = cs.fetchone()
		  print(content)
		  # 获取全部数据
		  content = cs.fetchall()
		  print(content)
		  # 关闭游标和连接
		  cs.close()
		  conn.close()
		  ```
		- 1. 导入pymysql包
			- `import pymysql`
		- 2. 创建连接对象
			- 调用pymysql模块中的connect()函数来创建连接对象，代码如下：
				- conn=connect(参数列表)
					- host: 连接的mysql主机，如果本机是‘localhost'
					- port: 连接的MySQL主机的端口，默认是3306
					- user：连接的用户名
					- password：连接的密码
					- database：数据库的名称
					- charse：通信采用的编码方式，推荐使用utf8
				- 连接对象conn的相关操作
					- conn.close() 关闭连接
					- conn.commit() 提交数据
					- conn.rollback() 撤销数据
		- 3. 获取游标对象
			- 获取游标对象的目标就是要执行sql语句，完成对数据的增删改查操作。代码如下：
				- `cur = conn.cursor()`
			- 游标操作说明：
				- 1 使用游标执行SQL语句：excute(operation [parameters]) 执行SQL语句，返回受影响的行数，主要用于执行insert、 update、 delete、select等语句
				- 2 获取查询结果集中的一条数据：cur.fetchone()返回一个元组，如（1，‘张三’）
				- 3 获取查询结果集中的所有数据： cur.fetchall()返回一个元组，如((1, '张三'),(2, '李四'))
				- 4 关闭游标： cur.close()，表示和数据库操作完成。
		- 4. pymysql完成数据的增删改查操作
			- ```python
			  # python 连接MySQL数据库——增删改操作
			  # 导入pymysql包
			  import pymysql
			  
			  # 创建连接对象
			  conn = pymysql.connect(host='localhost', port=3306, user='root', password='mysql', database='python_test_1', charset='utf8')
			  
			  # 获取游标对象
			  cs = conn.cursor()
			  
			  # 增加数据
			  #sql = 'insert into students(name) values("老王")'
			  #cs.execute(sql)
			  
			  # 删除数据
			  sql = 'delete from students where id=18'
			  cs.execute(sql)
			  
			  # 修改数据
			  sql = 'update students set name="老王" where id = 1'
			  cs.execute(sql)
			  
			  # pymysql完成数据的查询操作
			  sql = 'select * from students;'
			  
			  # for 循环显示数据
			  cs.execute(sql)
			  content = cs.fetchall()
			  for i in content:
			      print(i)
			  
			  # 提交操作
			  conn.commit()
			  
			  # 关闭游标和连接
			  cs.close()
			  conn.close()
			  ```
			- 增删改查的sql语句：
				- `sql = select * from 数据库`
			- 执行sql语句完成相关数据操作
				- `cursor.execute(sql)`
		- 5. 关闭游标和连接
			- 先关闭游标
				- `cur.close()`
			- 后关闭连接
				- `conn.close()`
- SQL语句参数化
	- 什么是SQL注入？
		- 用户提交带有恶意的数据与SQL语句进行字符串方式拼接，从而影响了SQL语句的语义，最终产生数据泄露的现象。
	- 如何防止SQL注入
		- SQL语句参数化
			- SQL语言中的参数使用%s来占位，此处不是python中的字符串格式化操作
			- 将SQL语句中的%s占位所需要的参数存在一个列表中，把参数列表传递给execute方法中的第二个参数
		- 不安全的方式
			- `sql = "select * from goods where name='%s'" % find_name`
			  `cs.excute(sql)`
		- 安全的方式
			- 构造参数列表
				- `params = [find_name]`
			- 执行select语句
				- `sql = "select * from goods where name = %s"` (这里的%s不需要加引号)
				  `cs.execute(sql, params)`
		- ```python
		  # SQL注入
		  # 导入pymysql
		  import pymysql
		  
		  # 创建连接对象
		  conn = pymysql.connect(host='localhost', port=3306, user='root', password='mysql', database='python_test_1', charset='utf8')
		  # 获取游标对象
		  cs=conn.cursor()
		  
		  
		  # # 不安全的方式
		  # # 根据id查询学生信息
		  # find_name=input('请输入您想要查询的学生姓名:') # 如果输入 ‘ or 1 or ' 就会获取到所有数据，导致数据泄漏
		  # sql = 'select * from students where name="%s"' % find_name
		  
		  # 安全的方式
		  find_name = input('请输入想要查询的姓名：')
		  sql = 'select * from students where name=%s'
		  
		  # 显示所有数据
		  cs.execute(sql,find_name)
		  content = cs.fetchall()
		  for i in content:
		      print(i)
		  
		  # 关闭游标和连接
		  cs.close()
		  conn.close()
		  ```