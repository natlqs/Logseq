# 第6章 索引器、委托、事件和Lambda表达式的应用
	- ## 6.1 索引器
<<<<<<< HEAD
	  collapsed:: true
		- 索引器（Indexer）是C# 引入的一个新型的类成员，它使得类中的对象可以像数组那样方便、直观地被引用。索引器非常类似于属性，不同的是索引器的访问可以有参数列表，且只能作用在实例对象上，而不能在类上直接作用。定义了索引器的类可以像访问数组一样的使用[ ]运算符访问类的成员。
		- ### 6.1.1 索引器的概述及引用
		  collapsed:: true
			- 索引器在语法上方便创建客户端应用程序，可将其作为数组访问的类、结构或接口。索引器通常是在用于封装内部集合或数组的类型中实现的。
			- 索引器表示法不仅简化了客户端应用程序的语法，还使其他开发人员能够更加直观地理解类及其用途。
			- 和方法一样，索引器有5种存取保护级别new、public、protected、internal、private和4种继承行为修饰virtual、sealed、override、abstract，以及索引器可以被重载。唯一不同的是，索引器不能为static的。
			  collapsed:: true
=======
		- 索引器（Indexer）是C# 引入的一个新型的类成员，它使得类中的对象可以像数组那样方便、直观地被引用。索引器非常类似于属性，不同的是索引器的访问可以有参数列表，且只能作用在实例对象上，而不能在类上直接作用。定义了索引器的类可以像访问数组一样的使用[ ]运算符访问类的成员。
		- ### 6.1.1 索引器的概述及引用
			- 索引器在语法上方便创建客户端应用程序，可将其作为数组访问的类、结构或接口。索引器通常是在用于封装内部集合或数组的类型中实现的。
			- 索引器表示法不仅简化了客户端应用程序的语法，还使其他开发人员能够更加直观地理解类及其用途。
			- 和方法一样，索引器有5种存取保护级别new、public、protected、internal、private和4种继承行为修饰virtual、sealed、override、abstract，以及索引器可以被重载。唯一不同的是，索引器不能为static的。
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
			  声明类或结构上的索引器要使用this关键字，声明索引器的语法如下：
				- ```c#
				  访问修饰符 数据类型 this[参数列表]{
				    //get和set访问器
				  }
				  ```
			- *例6-1： 索引器的使用（ConsoleIndexer）*
<<<<<<< HEAD
			  collapsed:: true
=======
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
				- ```c#
				  using System;
				  using System.Collections;
				  using System.Collections.Generic;
				  using System.Diagnostics;
				  using System.Linq;
				  using System.Net.Http.Headers;
				  using System.Security.Cryptography.X509Certificates;
				  using System.Text;
				  using System.Threading.Tasks;
				  
				  namespace Test
				  {
				      internal class Program
				      {
				          static void Main(string[] args)
				          {
				              Cars cars = new Cars();
				              cars[0] = "Aventador";
				              cars[1] = "Italia";
				              cars[2] = "2";
				              Console.WriteLine(cars.Name);
				              Console.WriteLine(cars.PlaceOfOrigin);
				              Console.WriteLine(cars.Seat);
				              Console.ReadLine();
				  
				          }
				      }
				      public class Cars
				      {
				          public string Name
				          {
				              get;
				              set;
				          }
				          public string PlaceOfOrigin
				          {
				              get; set;
				          }
				          public string Seat
				          {
				              get; set;
				          }
				          public string this[int index]
				          {
				              get
				              {
				                  if (index == 0) return Name;
				                  else if (index == 1) return PlaceOfOrigin;
				                  else if (index == 2) return Seat;
				                  else return "";
				              }
				              set
				              {
				                  if (index == 0) Name = value;
				                  else if (index == 1) PlaceOfOrigin = value;
				                  else if (index == 2) Seat = value; 
				              }
				          }
				      }
				  }
				  ```
			- 此例中，声明了一个public的名为Cars的类，Cars类中定义了name、PlaceOfOrigin以及Seat三个自动属性以及一个public的返回值为string参数为int的索引器。在索引器的get、set方法中根据参数的值设置需要返回的属性。在Main方法中实例化Cars类的一个对象c，并使用类似于数组下标的形式为其成员变量赋值，之后直接调用相应的属性输出结果。
			- 看了上面的例子读者可能会感觉索引器与数组或属性有些类似，那么它们之间有什么区别呢？下面就一一介绍下它们的不同点。
			- 索引器与数组的区别如下。
<<<<<<< HEAD
			  collapsed:: true
=======
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
				- （1）索引器的索引值类型不受限制。
				- （2）索引器可以被重载。
				- （3）索引器不是一个变量。
			- 索引器和属性的区别如下。
<<<<<<< HEAD
			  collapsed:: true
=======
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
				- （1）属性以名称来标识，索引器以函数形式标识。
				- （2）索引器可以被重载，属性不可以。
				- （3）索引器不能声明为static，属性可以。
		- ### 6.1.2 索引器的重载
<<<<<<< HEAD
		  collapsed:: true
			- C# 并不将索引类型限制为整数，索引器也可以像方法一样被重载，例6-2演示了索引器的重载。
			- *例6-2：索引器的重载（ConsoleIndexerOverload）*
			  collapsed:: true
=======
			- C# 并不将索引类型限制为整数，索引器也可以像方法一样被重载，例6-2演示了索引器的重载。
			- *例6-2：索引器的重载（ConsoleIndexerOverload）*
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
				- ```c#
				   using System;
				  using System.Collections;
				  using System.Collections.Generic;
				  using System.Diagnostics;
				  using System.Linq;
				  using System.Net.Http.Headers;
				  using System.Security.Cryptography.X509Certificates;
				  using System.Text;
				  using System.Threading.Tasks;
				  
				  namespace Test
				  {
				      internal class Program
				      {
				          static void Main(string[] args)
				          {
				              IndexClass index = new IndexClass();
				              index[1] = "I'm No.1";
				              index["s2"] = "I'm No.2";
				  
				              Console.WriteLine(index["s1"]);
				              Console.WriteLine(index[2]);
				              Console.ReadLine();
				          }
				      }
				      public class IndexClass
				      {
				          private Hashtable SerialNumber = new Hashtable();
				          public string this[string index]
				          {
				              get { return SerialNumber[index].ToString(); }
				              set { SerialNumber.Add(index, value); }
				          }
				          public string this[int index]
				          {
				              get { return SerialNumber["s" + index].ToString(); }
				              set { SerialNumber.Add("s" + index, value); }
				          }
				      }
				  }
				  ```
			- 此例中，分别定义了参数类型为string和int的索引器，在参数类型为int的索引器中，get和set方法分别获取和设置Hashtable对象的key均为以字符串s开头加上参数值组成的key。Main方法中，实例化IndexerClass的一个对象indexer，并给indexer[1]和indexer["s2"]赋值，此两句分别调用了int类型参数的索引器以及string类型参数的索引器执行赋值操作，之后分别输出key为"s1"和"s2"对应的value值。
			- 此外，还可像如下代码片段定义多参数的索引器，多参索引器使用方法同单参索引器。
<<<<<<< HEAD
			  collapsed:: true
=======
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
				- ```c#
				  public book this[string a, int b]{
				    get{
				      ...
				    }
				    set{
				      ...
				    }
				  }
				  ```
	- ## 6.2 委托
<<<<<<< HEAD
	  collapsed:: true
=======
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
		- 委托（delegate）用于将方法作为参数传递给其他方法。
		- 委托是表示对具有特定参数列表和返回类型的方法的引用的类型。
		- 在实例化委托时，用户可以将其实例与任何具有兼容签名和返回类型的方法相关联。可以通过委托实例调用方法。
		- 委托类型的声明与方法签名相似，有一个返回值和任意数目、任意类型的参数，声明委托的语法格式如下：
			- ```c#
			  访问修饰符 delegate 返回值类型 委托名(参数列表);
			  ```
		- 如下代码片段声明了一个公有的、无返回值的、名为TestDelegate的带有一个参数的委托。
			- ```c#
			  public delegate void TestDelegate(string msg);
			  ```
		- ### 6.2.1 委托的基本用法
			- 可将任何可访问类或结构中与委托类型匹配的任何方法分配给委托。该方法可以是静态方法，也可以是实例方法。这样便能通过编程方式来更改方法调用，还可以向现有类中插入新代码。下面的例子演示了委托的声明及其使用。
			- *例6-3：委托的声明及使用（ConsoleDelegate）*
				- id:: 64a4d42f-de5e-455f-b64c-7c156b082959
				  ```c#
				  using System;
				  using System.Collections;
				  using System.Collections.Generic;
				  using System.Diagnostics;
				  using System.Linq;
				  using System.Net.Http.Headers;
				  using System.Security.Cryptography.X509Certificates;
				  using System.Text;
				  using System.Threading.Tasks;
				  
				  namespace Test
				  {
				      public delegate void SayDelegate(string name);
				      internal class Program
				      {
				          static void Main(string[] args)
				          {
				              DelegateClass dc = new DelegateClass();
				              SayDelegate sayDelegate = new SayDelegate(dc.ChineseSay);
				              SayDelegate sayDelegate1 = dc.EnglishSay;
				              dc.Say("李雷", sayDelegate);
				              dc.Say("Lucy", sayDelegate1);
				  
				              SayDelegate sayDelegate2 = delegate (string name)
				              {
				                  Console.WriteLine(name);
				                  Console.WriteLine("こんにちは");
				              };
				              sayDelegate2("おのさん");
				              Console.ReadLine();
				  
				          }
				      }
				      public class DelegateClass
				      {
				          public void ChineseSay(string name)
				          {
				              Console.WriteLine("你好， {0}", name);
				              Console.WriteLine();
				          }
				          public void EnglishSay(string name)
				          {
				              Console.WriteLine("Hello, {0}", name);
				              Console.WriteLine();
				          }
				          public void Say(string name, SayDelegate sayDelegate)
				          {
				              sayDelegate(name);
				          }
				      }
				  }
				  ```
			- 此例演示了对不同国别的人说“你好”的几种不同的表达方式，示例根据传入的name值来调用不同的说“你好”的方法输出消息。示例中声明一个名为SayDelegate的委托。定义了DelegateClass类，并分别声明了三个方法：ChineseSay、EnglishSay和Say，其中，Say方法使用了委托类型作为参数。在Main方法中，分别使用了三种方式来为委托指定方法。第一种方式为使用new关键字来实例化委托对象，并将方法作为参数传递给委托；第二种方式为直接将方法指定给委托对象；第三种方式为使用匿名方法来为委托指定方法。
			- 委托类似于C++中的函数指针，相对于指针来说，委托是类型安全的。在处理它的时候要当作类来看待而不是方法，说白了委托就是对方法或者方法列表的引用，调用一个委托实例就好像是调用C++中的指针一样，它封装了对指定方法的引用，或者说委托起到的是桥梁的作用，实例后的委托对象会将给定的参数传递给它所回调的方法，并去执行方法。
		- ### 6.2.2 方法与委托相关联
			- 我们知道委托是对方法的封装，而且委托可以封装很多方法形成委托链，其实委托就好像是一个容器，它封装了我们想要实现的若干方法，当调用委托对象时，就会顺序地执行它所封装的所有方法，如果有返回值，则返回的是最后一个被执行的方法的返回值，委托链的形成可以用“+=”或“-=”对不同的委托实例进行二元操作，此步骤也被称为方法与委托的绑定与移除。例6-4演示了方法与委托的绑定。
			- *例6-4：方法与委托的绑定（ConsoleFunctionAndDelegate）*
				- ```c#
				  using System;
				  using System.Collections;
				  using System.Collections.Generic;
				  using System.Diagnostics;
				  using System.Linq;
				  using System.Net.Http.Headers;
				  using System.Security.Cryptography.X509Certificates;
				  using System.Text;
				  using System.Threading.Tasks;
				  
				  namespace Test
				  {
				      internal class Program
				      {
				          public delegate void MyDelegate();
				          static void Main(string[] args)
				          {
				              Program p = new Program();
				              MyDelegate myDelegate = new MyDelegate(p.Read);
				  
				              myDelegate += p.Play;
				              myDelegate += p.Watch;
				              myDelegate();
				              myDelegate -= p.Read;
				              myDelegate();
				              Console.ReadLine();
				          }
				          public void Read()
				          {
				              Console.WriteLine("Read a book");
				          }
				          public void Play()
				          {
				              Console.WriteLine("Play games");
				          }
				          public void Watch()
				          {
				              Console.WriteLine("Watch TV");
				          }
				      }
				  }
				  ```
			- 此例中，首先使用Read方法作为初始化参数实例化一个委托对象，之后使用“+=”来绑定Play方法和Watch方法，然后调用委托输出相关信息。之后使用“-=”来移除绑定的方法Read，最后输出移除后的信息。值得注意的是，委托调用方法的顺序始终与方法绑定的顺序相同。
	- ## 6.3 事件
		- 谈到事件，将涉及两个角色：事件发布者（Publisher）和事件订阅者（Scriber），也可以说是事件发送者（Sender）和事件接收者（Receiver）。举个例子来说，使用某视频播放软件来观看电视剧，软件里电视剧很多，电视剧的种类也很多，而我只对其中的某些感兴趣，那么就可以在软件里设置订阅。之后，每当感兴趣的电视剧更新，我就会收到软件的更新提醒。在这个关系中，视频播放软件就相当于事件发送者，而我就是事件订阅者。每天电视剧更新时，就触发了一个事件。
		  用面向对象的语言解释，这两者的意义如下。
		- **1．事件发送者（Publisher）**
			- 它是一个对象，且会维护自身的状态信息。每当状态信息发生变动时，便触发一个事件，并通知所有的事件订阅者。对于视频播放软件来说，每部电视剧都有自己的信息在里面，当电视剧更新时，要通知订阅该类别电视剧的人：电视剧已更新了。
		- **2．事件接收者（Receiver）**
			- 这个对象要注册它感兴趣的对象，也就是订阅它自己喜欢的电视剧类别。另外，这个对象通常要提供一个事件处理方法，在事件发行者触发一个事件后，会自动执行这个方法。对于上面所举的例子来说，也就是我收到电视剧更新后要做什么事情，比如可以立即观看，也可收藏着待有时间再看，具体怎么实现完全取决于自己的喜好。
		- 订阅一个事件的含义是提供代码，在事件发生时执行这些代码，它们被称为事件处理程序。
		- ### 6.3.1 事件处理程序
			- C# 中的事件处理实际上是一种具有特殊签名的委托，单个事件可供多个处理程序订阅，在该事件发生时，这些处理程序都会被调用，其中包括引发该事件的对象所在的类中的事件处理程序，但事件处理程序也可能在其他类中。下面的例子演示了事件的应用，用以阐述事件的思想。
			- *例6-5：事件的应用（ConsoleEvent）*
				- ```c#
				  using System;
				  using System.Collections;
				  using System.Collections.Generic;
				  using System.Diagnostics;
				  using System.Linq;
				  using System.Net.Http.Headers;
				  using System.Security.Cryptography.X509Certificates;
				  using System.Text;
				  using System.Threading.Tasks;
				  
				  namespace Test
				  {
				      public delegate void MyEventHandler();
				      internal class Program
				      {
				          static void Main(string[] args)
				          {
				              MyEventClass myEventClass = new MyEventClass();
				              myEventClass.MyEvent += new MyEventHandler(myEventClass.MyFunction);
				              myEventClass.FireEvent();
				              Console.ReadLine();
				          }
				          
				      }
				      public class MyEventClass
				          {
				              public event MyEventHandler MyEvent;
				              public void FireEvent()
				              {
				                  if(MyEvent != null)
				                  {
				                      MyEvent();
				                  }
				              }
				              public void MyFunction()
				              {
				                  Console.WriteLine("MyFunction");
				              }
				          }
				  }
				  ```
			- 此例中，首先定义一个委托MyEventHandler，在类MyEventClass中声明了一个事件，事件的类型为MyEventHandler，名为MyEvent。然后定义一个FireEvent方法，用于触发MyEvent事件，同时声明了一个名为MyFunction的方法作为事件处理程序。在Main方法中使用“+=”注册事件，最后触发事件，输出消息。值得注意的是，事件必须是委托类型，并且，事件处理函数的方法签名要与委托的方法签名相匹配。
		- ### 6.3.2 事件的应用
			- 在6.3.1节中，简单介绍了事件处理程序，并用一个小例子来说明事件的执行过程，在此对例6-5进行改造，添加事件参数信息，用以完善事件机制。
			- *例6-6：事件机制（ConsoleEvent2）*
				- ```c#
				  using System;
				  using System.Collections;
				  using System.Collections.Generic;
				  using System.Diagnostics;
				  using System.Linq;
				  using System.Net.Http.Headers;
				  using System.Security.Cryptography.X509Certificates;
				  using System.Text;
				  using System.Threading.Tasks;
				  
				  namespace Test
				  {
				      public delegate void MyEventHandler(object sender, EventArgs e);
				      internal class Program
				      {
				          static void Main(string[] args)
				          {
				              MyEventClass myEventClass = new MyEventClass();
				              myEventClass.MyEvent += new MyEventHandler(myEventClass.MyFunction);
				              myEventClass.FireEvent(EventArgs.Empty);
				              Console.ReadLine();
				          }
				          
				      }
				      public class MyEventClass
				          {
				              public event MyEventHandler MyEvent;
				              public void FireEvent(EventArgs e)
				              {
				                  if(MyEvent != null)
				                  {
				                      MyEvent(this, e);
				                  }
				              }
				              public void MyFunction(object sender, EventArgs e)
				              {
				                  Console.WriteLine("MyFunction:{0}", e.ToString());
				              }
				          }
				  }
				  ```
			- 此例中只是简单地把事件处理程序和委托添加了参数，并使得它们的签名相一致，事件处理程序中也只是简单地输出了事件参数类型的字符串，所有的事件参数都继承于System.EventArgs类，可以自定义事件参数类来实现自己的需求。
	- ## 6.4 Lambda表达式
<<<<<<< HEAD
	  collapsed:: true
		- Lambda表达式是一种可用于创建委托或表达式目录树类型的匿名方法。通过使用Lambda表达式，可以写入可作为参数传递或作为函数调用值返回的本地函数。Lambda表达式对于编写LINQ查询表达式特别有用。
		- ### 6.4.1 匿名方法的简介
		  collapsed:: true
			- 匿名方法是一个“内联”语句或表达式，可在需要委托类型的任何地方使用。可以使用匿名方法来初始化命名委托，或传递命名委托（而不是命名委托类型）作为方法参数。
			- 在2.0之前的C# 版本中，声明委托的唯一方法是使用命名方法。C# 2.0引入了匿名方法，而在C# 3.0及更高版本中，Lambda表达式取代了匿名方法，作为编写内联代码的首选方式。可使用匿名方法来忽略参数列表。这意味着匿名方法可转换为具有各种签名的委托，这对于Lambda表达式来说是不可能的。
			- 在例6-3演示的委托的声明及其使用的例子中，用delegate关键字定义内联的匿名方法来初始化命名委托。
			  collapsed:: true
=======
		- Lambda表达式是一种可用于创建委托或表达式目录树类型的匿名方法。通过使用Lambda表达式，可以写入可作为参数传递或作为函数调用值返回的本地函数。Lambda表达式对于编写LINQ查询表达式特别有用。
		- ### 6.4.1 匿名方法的简介
			- 匿名方法是一个“内联”语句或表达式，可在需要委托类型的任何地方使用。可以使用匿名方法来初始化命名委托，或传递命名委托（而不是命名委托类型）作为方法参数。
			- 在2.0之前的C# 版本中，声明委托的唯一方法是使用命名方法。C# 2.0引入了匿名方法，而在C# 3.0及更高版本中，Lambda表达式取代了匿名方法，作为编写内联代码的首选方式。可使用匿名方法来忽略参数列表。这意味着匿名方法可转换为具有各种签名的委托，这对于Lambda表达式来说是不可能的。
			- 在例6-3演示的委托的声明及其使用的例子中，用delegate关键字定义内联的匿名方法来初始化命名委托。
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
				- ```c#
				  SayDelegate sayDelegate3 = delegate(string name)
				             {
				                 Console.WriteLine(name);
				                 Console.WriteLine("こんにちは");
				             };
				  ```
			- 此语法中，delegate关键字总是会带来混淆，因为它既可以用来定义委托类型，又可以作为匿名方法的关键字。
		- ### 6.4.2 Lambda表达式简介
<<<<<<< HEAD
		  collapsed:: true
			- Lambda表达式是一种高效的类似于函数式编程的表达式，Lambda简化了开发中需要编写的代码量。Lambda表达式使用Lambda运算符=>，该运算符读作“goes to”。Lambda运算符的左边是输入参数（如果有），右边是表达式或语句块。
			- 例如，Lambda表达式y => y * y指定名为y的参数并返回y的平方值。
		- ### 6.4.3　表达式Lambda的应用
		  collapsed:: true
=======
			- Lambda表达式是一种高效的类似于函数式编程的表达式，Lambda简化了开发中需要编写的代码量。Lambda表达式使用Lambda运算符=>，该运算符读作“goes to”。Lambda运算符的左边是输入参数（如果有），右边是表达式或语句块。
			- 例如，Lambda表达式y => y * y指定名为y的参数并返回y的平方值。
		- ### 6.4.3　表达式Lambda的应用
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
			- 表达式位于=>运算符右侧的Lambda表达式称为“表达式Lambda”。表达式Lambda广泛用于表达式树的构造。表达式Lambda会返回表达式的结果，并采用以下语法格式：
			- ```c#
			  (input parameters) => expression
			  ```
			- 仅当Lambda只有一个输入参数时，括号才是可选的；否则括号是必需的。括号内的两个或更多输入参数使用逗号加以分隔，例如：
			- ```c#
			  (a, b) => a+=b
			  ```
			- 有时，编译器难以或无法推断输入类型。那么，可以按以下示例中所示方式显式指定参数的类型：
			- ```c#
			  (int a, string b) => b.Length > a
			  ```
			- 但是，值得注意的是，不能在同一个Lambda表达式中同时使用隐式和显式的参数类型。
			- 此外，还可使用空括号指定零个输入参数：
			- ```c#
			  () => SomeMethod()
			  ```
			- 在上一个示例中，请注意表达式Lambda的主体可以包含一个方法调用。但是，如果要创建在.NET Framework之外计算的表达式目录树（如在SQL Server中），则不应在Lambda表达式中使用方法调用。在.NET公共语言运行时上下文之外，方法将没有任何意义。
		- ### 6.4.4 语句Lambda的应用
<<<<<<< HEAD
		  collapsed:: true
=======
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
			- 语句Lambda与表达式Lambda表达式类似，只是语句写在大括号中，其语法格式如下：
			- `(input parameters) => {statement;}`
			- 语句Lambda的主体可以包含任意数量的语句；但是，实际上通常不会多于两个或三个。
			- 如下代码片段演示了使用Lambda表达式来改写示例6-3中以匿名方法来初始化命名委托。
			- ```c#
			  SayDelegate sayDelegate3 = name =>
			    {
			               Console.WriteLine(name);
			               Console.WriteLine("こんにちは");
			    };
			  ```
			- 像匿名方法一样，语句Lambda也不能用于创建表达式目录树。
		- ### 6.4.5　Lambda表达式中的变量范围
<<<<<<< HEAD
		  collapsed:: true
			- 在定义Lambda函数的方法内或包含Lambda表达式的类型内，Lambda可以引用范围内的外部变量。以这种方式捕获的变量将进行存储以备在Lambda表达式中使用，即使在其他情况下，这些变量将超出范围并进行垃圾回收。必须明确地分配外部变量，然后才能在Lambda表达式中使用该变量。
			- Lambda表达式中的变量范围如下所述。
			  collapsed:: true
=======
			- 在定义Lambda函数的方法内或包含Lambda表达式的类型内，Lambda可以引用范围内的外部变量。以这种方式捕获的变量将进行存储以备在Lambda表达式中使用，即使在其他情况下，这些变量将超出范围并进行垃圾回收。必须明确地分配外部变量，然后才能在Lambda表达式中使用该变量。
			- Lambda表达式中的变量范围如下所述。
>>>>>>> 30f479c74294551e969ef96ce35487abcb3ed8f9
				- （1）捕获的变量将不会被作为垃圾回收，直至引用变量的委托符合垃圾回收的条件。
				- （2）在外部方法中看不到Lambda表达式内引入的变量。
				- （3）Lambda表达式无法从封闭方法中直接捕获ref或out参数。
				- （4）Lambda表达式中的返回语句不会导致封闭方法返回。
				- （5）如果跳转语句的目标在块外部，则Lambda表达式不能包含位于Lambda函数内部的goto语句、break语句或continue语句。同样，如果目标在块内部，则在Lambda函数块外部使用跳转语句也是错误的。