- # C# 三层架构详解
- ### 三层架构：
	- 表现层（UI）、业务逻辑层（BLL）、数据访问层（DAL）再加上实体类库（Model）
		- 表现层（UI）：一般都是窗体的设计或者网页的设计，是可以一眼就可以看到的界面。
		- 业务逻辑层（BLL）：对传送数据进行逻辑判断分折，并进行传送正确的值。
		- 数据访问层（DAL）：主要是存放对数据类的访问，即对数据库的添加、删除、修改、更新等基本操作。
		- 实体类库（Model）：主要存放数据库中的表字段。
		- 说到这，大家可能还是有点摸不着头脑！跟着写一个例子就能明白了！
	- 小二，上例子：
		- 整体思路要把控好哈，用户输入账号密码->点击登录->进入BLL层进行输入与数据的逻辑处理->进入DAL层将BLL层的逻辑进行实现（用户输入的账号的密码与数据库匹配），返回结果。
		- collapsed:: true
		  1. 我们先建一个数据库，不用太多字段，一个id，一个账号名，一个密码就行啦！
			- 数据库名：threelayer
			- 表名：Tb_User
			- 字段：id username userpwd
			  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423145732842.png#pic_center)
		- collapsed:: true
		  2. 新建项目吧，设计一个超级简单的窗体，两个lable，两个textbox，一个button。
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423150206854.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
		- collapsed:: true
		  3. 为这个项目加一个应用程序配置文件。
			- 修改配置文件，其实就是连接数据库的一个字符串。
			- ```
			  <?xml version="1.0" encoding="utf-8" ?>
			  <**configuration**>
			  <**connectionStrings**>
			    <**add** name="dbConnection" connectionString="Data Source=.;Initial Catalog=threelayer;Persist Security Info=True;User ID=sa;Password=123"
			          providerName="SQLClient" />
			  </**connectionStrings**>
			  </**configuration**>
			  ```
		- collapsed:: true
		  4. 添加类库：BLL，DAL，Model
			- 右键项目解决方案-添加-新建项目-类库
			  ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020042315083452.png#pic_center)
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423150419820.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
		- collapsed:: true
		  5. 重点来了，重点来了，重点来了。重要的事情说三遍。前面我们说了，Model层是干什么的？==主要存放数据库中的表字段==，那么问题来了，该怎么存放呢？
			- 在这个Model类库下面新建一个类文件名为userInfo.cs
			- ```c#
			  **private** string _username;
			      **private** string _psw;
			  - **public** string username
			      {
			          **set** { _username = **value**; }
			          **get** { **return** _username; }
			      }
			      **public** string psw
			      {
			          **set** { _psw = **value**; }
			          **get** { **return** _psw; }
			      }
			  ```
			- 完整代码：
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423151837561.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
			- ```c#
			  **using** System;
			  **using** System.Collections.Generic;
			  **using** System.Linq;
			  **using** System.Text;
			  
			  **namespace** **Model**
			  {
			    **public** **class** **userInfo**
			    {
			        **private** string _username;
			        **private** string _psw;
			  
			        **public** string username
			        {
			            **set** { _username = **value**; }
			            **get** { **return** _username; }
			        }
			        **public** string psw
			        {
			            **set** { _psw = **value**; }
			            **get** { **return** _psw; }
			        }
			    }
			  }
			  ```
		- collapsed:: true
		  6. 接下来是DAL层：主要是存放对数据类的访问，即对数据库的添加、删除、修改、更新等基本操作。
			- 我们先添加system.configuration引用，使类可以读取配置文件节点，读取配置文件中连接数据库语句；
			- 右键引用-添加引用-选择程序集-勾选-确定
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020042315250549.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
		- collapsed:: true
		  7. 添加 DBbase类，这个类也就是我们常说的SqlHelper这个类，随个人喜好，一个名字而已是吧！
			- using System.Data;
			- using System.Data.SqlClient;
			- 添加这两个引用。
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423152753596.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
			- ```c#
			  **using** System;
			  **using** System.Collections.Generic;
			  **using** System.Data;
			  **using** System.Data.SqlClient;
			  **using** System.Linq;
			  **using** System.Text;
			  
			  **namespace** **DAL**
			  {
			    **public** **class** **DBbase**
			    {
			  
			        //读取配置文件 连接数据库语句
			        **public** **static** string strCon = System.Configuration.ConfigurationManager.ConnectionStrings["dbConnection"].ConnectionString;
			  
			        //实例化连接对象 con
			        SqlConnection con = **new** SqlConnection(strCon);
			  
			        //检测连接是否打开
			        **public** **void** **chkConnection**()
			        {
			            **if** (**this**.con.State == ConnectionState.Closed)
			            {
			                **this**.con.Open();
			            }
			        }
			  
			        //执行语句，返回该语句查询的数据行的总数
			        **public** int **returnRowCount**(string strSQL)
			        {
			            chkConnection();
			            **try**
			            {
			                SqlDataAdapter da = **new** SqlDataAdapter(strSQL, con);
			                DataSet ds = **new** DataSet();
			                da.Fill(ds);
			                **return** ds.Tables[0].Rows.Count;
			            }
			            **catch**
			            {
			                **return** 0;
			            }
			        }
			    }
			  }
			  ```
		- collapsed:: true
		  8. 添加 userAccess类（右键DAL项目-添加-新建项-命名好-确定） 用执行查询语句查找用户输入账号密码在数据库中存在记录条数
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423152954506.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
			- ```c#
			  **using** System;
			  **using** System.Collections.Generic;
			  **using** System.Linq;
			  **using** System.Text;
			  
			  **namespace** **DAL**
			  {
			    **public** **class** **userAccess**
			    {
			        //实例化DBbase 对象
			        DBbase db = **new** DBbase();
			  
			        //用户登录的方法
			        **public** int **userLogin**(string name, string psw)
			        {
			            string strsql = "select * from Tb_User where username = '" + name + "' and userpwd = '" + psw + "'";
			            **return** db.returnRowCount(strsql);
			        }
			    }
			  }
			  ```
			- 查询语句，返回对应的行数。
		- 9. BLL层：对传送数据进行逻辑判断分折，并进行传送正确的值。
		- 在BLL层中添加用户输入数据与数据库匹配的逻辑代码
		  collapsed:: true
			- 实例化DAL.userAccess 类，并新建一个方法调用DAL.userAccess方法，参数为Model实体类中的useInfo类
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020042315351315.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
			- 完整代码：
			- ```c#
			  **using** **System**;
			  **using** **System**.Collections.Generic;
			  **using** **System**.Linq;
			  **using** **System**.Text;
			  - namespace BLL
			  {
			  public **class** userAccess
			  {
			      DAL.userAccess d_userAccess = new DAL.userAccess();
			  - public int userLogin(Model.userInfo m_userInfo)
			      {
			          **return** d_userAccess.userLogin(m_userInfo.username, m_userInfo.psw);
			      }
			  }
			  }
			  ```
		- collapsed:: true
		  10. 接下来就是窗体代码了
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423153737513.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
			- ```c#
			  **using** **System**;
			  **using** **System**.Collections.Generic;
			  **using** **System**.ComponentModel;
			  **using** **System**.Data;
			  **using** **System**.Drawing;
			  **using** **System**.Linq;
			  **using** **System**.Text;
			  **using** **System**.Windows.Forms;
			  
			  namespace ThreeLayer
			  {
			    public partial **class** **Login** : Form
			    {
			  
			        //实例化model层中 userInfo类用于传递数据
			        Model.userInfo m_userInfo = new Model.userInfo();
			  
			        //实例化BLL层中 userAccess方法衔接用户输入与数据库匹配
			        BLL.userAccess b_userAccess = new BLL.userAccess();
			  
			        
			  
			        public **Login**()
			        {
			            InitializeComponent();
			        }
			  
			        private void button1_Click(**object** sender, EventArgs e)
			        {
			            //将用户输入的账号密码 赋值给userInfo类 username、psw属性
			            m_userInfo.username = textBox1.Text.Trim().ToString();
			            m_userInfo.psw = textBox2.Text.Trim().ToString();
			  
			            //如果BLL层中 useLogin调用返回记录条数 大于1 则账号密码正确
			            **if** (b_userAccess.userLogin(m_userInfo) > 0)
			            {
			                MessageBox.**Show**("登录成功");
			            }
			            **else**
			            {
			                MessageBox.**Show**("登录失败");
			            }
			        }
			    }
			  }
			  ```
		- collapsed:: true
		  11. 运行调试，发现报错了，这是为什么呢？一起来看看。
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423154134366.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423154144784.png#pic_center)
			- 这是我们没有在项目中引用，解决如下：
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423154256253.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
			  
			  添加引用就行了。
		- collapsed:: true
		  12. 运行调试。
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020042315441268.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423154424289.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
		- collapsed:: true
		  13. 总结：
			- 三层架构最重要的是中间的引用，这点只要做错了就要重新搭建，所以务必要小心一点。下面是三层的关系。
			- DAL引用Model
			- BLL引用DAL和Model
			- UI层引用BLL和Model
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423154809121.png#pic_center)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423154819370.png#pic_center)
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423154911252.png#pic_center)
			- ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200423155343276.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNzM1OTgy,size_16,color_FFFFFF,t_70#pic_center)
			- 运用三层架知构可以让代码的可读性和功能的扩展性有着很好的提高
			- 个人认为，一般我们说的三层甚至多层架构，是根据一定的分层原则，把一个应用分层处理，每层完成各自的工作，相互之间相对独立。
			- 比如：有一个应用，我们分为界面层道，逻辑内层，数据层，那么这三层分管不同的处理，界面层主要完成与用户的交互；逻辑层完成商业逻辑运算；数据层完成数据存储等。
			- 这样做的好处是方便维护。例如：我们把界面层提供给用户使用，逻辑运算放到远程服务器上，当我们需要调整运算逻辑的时候，只需要调整逻辑层就可以了，在用户那边根本感觉不到改动，也省去了重新部署的麻烦容。
		- 大家如果看的不太明白，在登录按钮那个地方打上一个断点，跟着他一步一步的跳，就会明白怎么运行的了。