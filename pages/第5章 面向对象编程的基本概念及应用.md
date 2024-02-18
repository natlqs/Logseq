- # 第5章 面向对象编程的基本概念及应用
	- ## 5.1 类
	  collapsed:: true
		- 类（class）是对某种类型的对象定义变量和方法的原型。它表示对显示生活中一类具有共同特种的食物的抽象，是面向对象编程的基础。
		- ### 5.1.1 类的概述
		  collapsed:: true
			- 类的是指是一种数据类型，类似于int、char等基本类型，不同的是它是一种复杂的数据类型。因为它的本质是类型，而不是数据，所以不存在与内存中，不能被直接操作，只有被实例化为对象时，才会变得可操作。
			- 类是对现实生活中一类具有共同特征的事务的抽象。如果一个程序里提供的类型应用中的概念有直接的对应，这个程序就会更容易理解，也更容易修改。一组经过很好选择的用户定义的类会使程序更简洁。此外，它还能使各种形式的代码更容易进行。特别地，它还会使编译器有可能检查对象的非法使用。
			- 类的内部封装了方法，用于操作自身的成员。类是对某种对象的定义，具有行为，它描述一个对象能够做什么以及做的方法，他们是可以对这个对象进行操作的程序和过程。它包含有关对象动作方式的信息，包括它的名称、方法、属性和事件。
		- ### 5.1.2 类的面向对象的概述
		  collapsed:: true
			- 面向对象编程（Object Oriented Programming，OOP）是一种计算机编程架构。OOP的一条基本原则是计算机程序是由单个能够起到子程序作用的单元或对象组合而成，OOP达到了软件工程的三个目标：重用性、灵活性和扩展性。为了实现整体运算，每个对象都能够接收信息、处理数据和向其他对象发送信息。面向对象一直是软件开发领域内比较热门的话题，首先，面向对象符合人类看待事物的一般规律。其次，采用面向对象方法可以使系统各部分各司其职、各尽所能，为编程人员敞开了一扇大门，使其编写的代码更简洁，更易于维护，并且具有更强的可重用性。
		- ### 5.1.3 类的声明及其类成员
		  collapsed:: true
			- **类的声明**
			  logseq.order-list-type:: number
			  collapsed:: true
				- 在C# 中，使用class关键字来声明类，其语法如下：
				- ```c#
				  访问修饰符 class 类名{
				    //类成员
				  }
				  ```
				- *例5-1：类的声明及其类成员*
				  collapsed:: true
					- ```c#
					  using System;
					  using System.Collections;
					  using System.Collections.Generic;
					  using System.Linq;
					  using System.Net.Http.Headers;
					  using System.Text;
					  using System.Threading.Tasks;
					  
					  namespace Test
					  {
					      internal class Program
					      {
					          static void Main(string[] args)
					          {
					              Student s = new Student();
					              s.age = 26;
					              s.name = "Test";
					              s.sex = "girls";
					              s.ShowMsg();
					  
					          }
					      }
					      public class Student
					      {
					          public string name;
					          public int age;
					          public string sex;
					          public void ShowMsg()
					          {
					              string str = "学生姓名：" + name + "年龄:" + age + "性别：" + sex;
					              Console.WriteLine(str);
					              Console.ReadLine();
					          }
					      }
					  }
					  ```
				- 此例中，声明了一个public的名为Student的类，Student类中定义了name、age、sex三个成员变量以及ShowMsg方法。在Main方法中实例化Student类的一个对象s，并使用“.”操作符调用类的成员变量为其赋值，之后调用ShowMsg方法输出信息。
			- **方法**
			  logseq.order-list-type:: number
			  collapsed:: true
				- “方法”是包含一系列语句的代码块。程序通过“调用”方法并指定所需的任何方法参数来执行语句。在C# 中，每个执行指令都是在方法的上下文中完成的。方法在类或结构中声明，声明时需要指定访问级别、返回值、方法名称以及任何方法参数。方法参数放在括号中，并用逗号隔开。空括号表示方法不需要参数。其语法如下：
				- ```c#
				  访问修饰符 返回值类型 方法名（参数列表）{
				    //方法体
				  }
				  ```
				- 在例5-1中，public void ShowMsg()声明了一个public(共有)的、void（无返回值）的、名为ShowMsg的无参方法。
				- *例5-2：方法的声明及使用（ConsoleFunction）*
				  collapsed:: true
					- ```c#
					  using System;
					  using System.Collections;
					  using System.Collections.Generic;
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
					  
					              MyClass myClass = new MyClass();
					              myClass.Show();
					              Console.WriteLine(myClass.Show2());
					              Console.WriteLine(myClass.Show3(25));
					  
					              Console.WriteLine(myClass.show4(2, 3));
					              Console.ReadLine();
					          }
					      }
					      public class MyClass
					      {
					          public void Show()
					          {
					              Console.WriteLine("I'm a function without parameter and return value");
					          }
					          public int Show2()
					          {
					              int n = 1;
					              Console.WriteLine("I'm a function has one return value and none parameter");
					              return n;
					          }
					          public string Show3(int age)
					          {
					              Console.WriteLine("I'm a function with parameter and return value");
					              if (age >= 18)
					                  return "you've grow up";
					              else
					                  return "you are still a child";
					          }
					          public int show4(int num1, int num2)
					          {
					              Console.WriteLine("I'm a function with parameter and return value");
					              return num1 + num2;
					          }
					      }
					  }
					  ```
				- 此例中，定义了一个名为MyClass的类，在MyClass类里分别声明了4个不同形式的方法，在Main方法中，初始化MyClass类，并调用其4个方法，输出相关信息。在此要注意的是，有返回值的方法，如Show2，要使用return关键字返回一个与方法返回值类型相匹配的变量或值，且有返回值的方法中有且仅有一个return语句被执行。表5-1中列出了常用的几种访问修饰符。
				- *表5-1 常用的访问修饰符*
				  collapsed:: true
					- |名　称|说　明|
					  |Public|公有的，不限制对该类的访问|
					  |Protected|受保护的，智能从其所在类和所在类的子类进行访问|
					  |Private|私有的，只有.NET中的应用程序或库才能访问|
					  |Internal|内部类，只有其所在类才能访问|
					  |Abstract|抽象类，不允许建立类的实例|
					  |Sealed|密封类，不允许被继承|
		- ### 5.1.4 构造函数和析构函数
		  collapsed:: true
			- 在C# 中，构造函数用来初始化对象，而析构函数则用来清理对象，下面就分别介绍下构造函数和析构函数
			- **构造函数**
			  logseq.order-list-type:: number
			  collapsed:: true
				- 构造函数与类名相同，通常用来初始化对象，任何时候，只要创建类，就会调用它的构造函数。一个类可能有多个接受不同参数的构造函数。构造函数使得程序员可设置默认值、限制实例化以及编写灵活且便于阅读的代码。若不显示地提供构造函数，则默认情况下C# 将创建一个默认的构造函数，该构造函数实例化对象，并将成员变量设置为默认值表中列出的默认值。
				- *例5-3：构造函数的声明及其类成员的初始化（ConsoleClassConstructor）*
				  collapsed:: true
					- ```c#
					  using System;
					  using System.Collections;
					  using System.Collections.Generic;
					  using System.Linq;
					  using System.Net.Http.Headers;
					  using System.Security.Cryptography.X509Certificates;
					  using System.Text;
					  using System.Threading.Tasks;
					  
					  namespace Test
					  {
					      internal class Program
					      {
					          public double longth = 7;
					          public double width = 3;
					          public double area;
					  
					          public Program()
					          {
					              area = longth * width;
					          }
					          public Program(double l, double w)
					          {
					              area = l * w;
					          }
					          static void Main(string[] args)
					          {
					              Program p1 = new Program();
					              Console.WriteLine("the area of this square is :" + p1.area);
					              Program p2 = new Program(9, 4);
					              Console.WriteLine("the area of this square is :" + p2.area);
					              Console.ReadLine();
					          }
					      }
					      
					  }
					      
					  ```
				- 此例中，分别声明了一个不带参数的构造函数以及一个带有两个double类型参数的构造函数，在构造函数中都是执行对变量area的赋值。不同点是默认的构造函数使用成员变量longth和width的乘积来为area的值，而带参数的构造函数则使用两个参数的值乘积为其赋值。在Main方法中，分别使用了两个不同的构造函数初始化了两个Program类的对象p1和p2，之后分别输出其下的area变量的值。
			- **析构函数**
			  logseq.order-list-type:: number
			  collapsed:: true
				- 析构函数用于析构类的实例。析构函数与构造函数想法，当对象脱离其作用域时（例如对象所在的函数已调用完毕），系统自动执行析构函数。析构函数以类加~来命名。
				- *例5-4：析构函数的声明和使用（ConsoleClassDestructor）*
				  collapsed:: true
					- ```c#
					  using System;
					  using System.Collections;
					  using System.Collections.Generic;
					  using System.Linq;
					  using System.Net.Http.Headers;
					  using System.Security.Cryptography.X509Certificates;
					  using System.Text;
					  using System.Threading.Tasks;
					  
					  namespace Test
					  {
					      internal class Program
					      {
					          ~Program()
					          {
					              Console.WriteLine("automative call destructor function success!");
					              Console.ReadLine();
					          }
					  
					          static void Main(string[] args)
					          {
					              Program program = new Program();
					          }
					      }
					      
					  }
					      
					  ```
				- #+BEGIN_NOTE
				  析构函数是自动被调用的，且一个类中只能有一个析构函数存在。
				  #+END_NOTE
		- ### 5.1.5 this关键字
		  collapsed:: true
			- 在面向对象的编程语言中，this关键字用来引用类的当前实例，通过this关键字可以引用当前类的成员变量和方法。
			- *例5-5：this关键字的用法（ConsoleClass  this）*
			  collapsed:: true
				- ```c#
				  using System;
				  using System.Collections;
				  using System.Collections.Generic;
				  using System.Linq;
				  using System.Net.Http.Headers;
				  using System.Security.Cryptography.X509Certificates;
				  using System.Text;
				  using System.Threading.Tasks;
				  
				  namespace Test
				  {
				      internal class Program
				      {
				          private string time;
				          public void SetMessage(string time)
				          {
				              this.time = time;
				          }
				          static void Main(string[] args)
				          {
				              Program program = new Program();
				              program.SetMessage("Four Clock");
				              Console.WriteLine("Metting Notice: there is a meeting this afternoon at {0}", program.time);
				              Console.ReadKey();
				          }
				      }
				      
				  }
				      
				  ```
			- 此例中，定义了一个private的变量time，在SetMessage方法的参数中也定义了一个变量time，这时如果不使用this关键字，那么在方法体中time = time，此时的两个time就会认为是方法参数中的变量，而无法识别成private的成员变量。
		- ### 5.1.6 属性
		  collapsed:: true
			- 属性是这样的成员：它们提供灵活的机制来读取、编写或计算私有字段的值。可以像使用公共数据成员一样使用属性，但实际上它们是称为“访问器”的特殊方法。这使得数据在可被轻松访问的同时，仍能提供方法的安全性和灵活性。
			- **属性的声明及使用**
			  logseq.order-list-type:: number
			  collapsed:: true
				- *例5-6：属性的声明及使用（ConsoleProp）*
				  collapsed:: true
					- ```c#
					  using System;
					  using System.Collections;
					  using System.Collections.Generic;
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
					              Calculate calculate = new Calculate();
					              calculate.Dividend = 10;
					              calculate.Divisor = 3;
					              calculate.Divided();
					  
					              calculate.Dividend = 10;
					              calculate.Divisor = 0;
					              calculate.Divided();
					              Console.ReadLine();
					  
					          }
					      }
					      
					      public class Calculate
					      {
					          private double dividend;
					          private double divisor;
					          public bool flag = false;
					  
					          public double Dividend
					          {
					              get { return dividend; }
					              set { dividend = value; }
					          }
					          public double Divisor
					          {
					              get { return  divisor; }
					              set
					              {
					                  if(value == 0)
					                  {
					                      flag = true;
					                  }
					                  else
					                      divisor = value;
					              }
					          }
					          public void Divided()
					          {
					              if (flag)
					                  Console.WriteLine("divisor can't be 0");
					              else
					                  Console.WriteLine("calculated result is :" + Dividend/Divisor);
					          }
					      }
					  }
					  ```
				- 此例中，声明了一个名为Calculate的类，Calculate类中声明了两个私有的变量dividend和divisor，分别坐位被除数和除数，并为其分别添加了属性，在属性的定义中，使用get/set方法（或访问器），方法中使用value关键字作为要传入或取出的值。在Main方法中，初始化Calculate类，并为其两个属性赋值，为其赋值时会自动调用属性定义中的set方法，取值则调用get方法，之后调用Divided方法显示计算结果。由于除数不能为0，例5-6在Divisor属性定义中使用了一个bool值的变量作为依据。Divided方法中根据bool值输出相应结果。
				- 使用VS2012编程时，在C# 3.0以上版本中提供更简洁的属性的写法，如例5-6中代码：
				  collapsed:: true
					- ```c#
					   private double dividend;
					      public double Dividend
					      {
					          get { return dividend; }
					          set { dividend = value; }
					      }
					  ```
				- 可替换为：
				  collapsed:: true
					- ```c#
					  public double Dividend { get; set; }
					  ```
				- 属性的数据类型必须与它所访问的字段类型一致。属性的类型可以是整型、字符串或者是类等。
			- **属性的访问类型**
			  logseq.order-list-type:: number
			  collapsed:: true
				- 属性的访问类型分为以下三种。
				  collapsed:: true
					- （1）只读属性，只包含get方法。
					- （2）只写属性，只包含set方法。
					- （3）读写属性，包含get和set方法。
					- #+BEGIN_NOTE
					  在此处要注意的是，C# 3.0自动生成的属性的语法必须同时指定get和set，而不能只写其中一个。那么使用自动生成的属性实现只读或只写属性要怎么做呢？方法很简单，如以下代码所示。
					  #+END_NOTE
				- ```c#
				  public string Username { get; private set; }
				  ```
				  。以上为只读属性，只写属性则把private修饰符写在get前面即可。
	- ## 5.2 继承
	  collapsed:: true
		- 继承是面向对象编程最重要的特性之一。任何类都可以从另一个类中继承，这就是说，这个类拥有它继承的类的所有成员。在面向对象编程中，被继承（也称为派生）的类称为父类或者基类。在C# 中，继承只支持单继承，即一个类只能有一个基类。单一继承已经能够满足大多数面向对象应用程序开发上的要求，也有效地降低了复杂性。如果必须使用多继承，可以通过接口来实现。
		- ### 5.2.1 继承简述
		  collapsed:: true
			- 利用类的继承机制，用户可以通过增加、修改或替换类中的方法对这个类进行扩充，以适应不同的应用要求。利用继承，程序员可以在已有类的基础上构造新类。
			- *5-7： 类的继承（ConsoleClassInheritance）*
			  collapsed:: true
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
				              Son son = new Son();
				              son.Calc();
				              son.Show();
				              Console.ReadLine();
				  
				          }
				      }
				  
				      public class Father
				      {
				          public int num1 = 5, num2 = 3;
				          public void Calc()
				          {
				              Console.WriteLine("{0} + {1} = {2}", num1, num2, num1 + num2);
				              Console.WriteLine("I'm the Calc function of the base class");
				          }
				      }
				      public class Son : Father
				      {
				          public  void Show()
				          {
				              Calc();
				              Console.WriteLine("I'm the Show function  of the son class");
				          }
				      }
				      
				  }
				  ```
			- 在此例中，声明了一个名为Father的类，Father类中声明并初始化了两个整型的变量num1和num2，并声明了一个名为Calc的方法，用于计算两数之和并输出相关信息。然后声明一个名为Sun的类，并继承于Father类。在C# 中，声明类时，在类名后放置一个冒号，然后在冒号后指定要继承的类。Sun类中声明一个名为Show的方法，在Show方法内部直接调用了父类的Calc方法。最后在Main方法中初始化了子类Sun的对象，并调用了父类的Calc方法以及自己的Show方法。
		- ### 5.2.2 抽象类及类成员
		  collapsed:: true
			- 抽象类及类成员是不完整且必须在派生类中实现的类和类成员。其语法格式如下：
			  collapsed:: true
				- ```c#
				  访问修饰符 abstruct class 类名
				  {
				    类成员
				  }
				  ```
			- 如下代码片段演示了如何继承抽象类。
			  collapsed:: true
				- ```c#
				  public abstract class Person
				  {
				    
				  }
				  public class Chinese:Person
				  {
				    
				  }
				  ```
			- 抽象类不能实例化。抽象类的用途是提供一个可供多个派生类共享的通用基类定义。抽象类也可以定义抽象方法。方法是将关键字abstract添加到方法的返回类型的前面。如下代码片段演示了在抽象类中添加抽象方法。
			  collapsed:: true
				- ```c#
				  public abstract class Person{
				    public abstract void SayHello();
				  }
				  ```
			- 抽象方法没有实现，所以方法定义后面是分号，而不是常规的方法块。抽象类的派生类必须实现所有抽象方法。
	- ## 5.3 接口
	  collapsed:: true
		- 接口是为了实现多重继承而产生的，由于C# 中的类不支持多重继承但在客观世界中出现多重继承的情况又比较多，因此为了避免传统的多重继承给程序带来复杂性等问题，同时又保证了多重继承带给程序员的诸多好处，因此接口显得尤为重要。本节将对接口进行详细的讲解。
		- ### 5.3.1 接口的介绍及声明
		  collapsed:: true
			- 在C# 中使用interface声明接口，其语法格式如下：
			- ```c#
			  访问修饰符 interface 接口名{
			    // 接口成员
			  }
			  ```
			- 在声明接口时，除interface关键字和接口名外，其他的都是可选的。可以使用public、protected、private、new和internal等修饰符声明接口，但接口成员必须是public的。
			- 接口可包含方法、属性、事件或索引器这4种成员类型，但不能包含字段，也不能设置这些成员的具体值，即只能定义，不能赋值。
			- 所以，接口有以下特性。
			  collapsed:: true
				- 不能直接实例化接口。
				  logseq.order-list-type:: number
				- 接口可以包含方法、属性、事件或索引器。
				  logseq.order-list-type:: number
				- 接口不包含方法的实现。
				  logseq.order-list-type:: number
				- 继承接口的任何非抽象类型都必须实现接口的所有成员。
				  logseq.order-list-type:: number
				- 类和结构以及接口本身都可以从多个接口继承。
				  logseq.order-list-type:: number
			- 接口成员的定义与类成员相似，但是需要注意以下几点区别。
			  collapsed:: true
				- 接口成员不能包含代码体。
				  logseq.order-list-type:: number
				- 接口成员不能用关键字static、abstract、virtual或sealed来定义。
				  logseq.order-list-type:: number
				- 接口不能包含类型定义。
				  logseq.order-list-type:: number
			- 以下代码片段声明了一个public的名为IMyinteface的接口，并定义了一个名为ShouMsg的方法。
			  collapsed:: true
				- ```c#
				  public interface IMyInterface{
				    void ShowMsg();
				  }
				  ```
		- ### 5.3.2 实现接口
		  collapsed:: true
			- 接口通过类的继承来实现，一个类虽然只能有一个基类，但可以继承任意多个接口，实现接口的类必须包含该接口所有成员的实现代码，同时必须匹配指定的签名，并且必须是public的。
			- *例5-8 接口的实现（ConsoleInterface）*
			  collapsed:: true
				- ```c#
				  using System;
				  using System.Collections;
				  using System.Collections.Generic;
				  using System.Linq;
				  using System.Net.Http.Headers;
				  using System.Text;
				  using System.Threading.Tasks;
				  
				  namespace Test
				  {
				      internal class Program
				      {
				          static void Main(string[] args)
				          {
				              IPerson iperson = new Chinese();
				              iperson.Say();
				              iperson = new Western();
				              iperson.Say();
				              Console.ReadKey();
				          }
				      }
				  
				  
				  
				      public interface IPerson
				      {
				          void Say();
				      }
				  
				  
				      public  class Chinese : IPerson
				      {
				          public void Say()
				          {
				              Console.WriteLine("你好！");
				          }
				      }
				      public class Western : IPerson
				      {
				          public void Say()
				          {
				              Console.WriteLine("Hello!");
				          }
				      }
				  }
				  ```
			- 在此例中，声明了一个名为IPerson的接口，IPerson接口中有一个Say方法。接着定义了Chinese和American两个类，并分别实现了IPerson接口，并实现了Say方法。在Main方法中，分别使用两个类的对象实例化IPerson接口，并分别调用其Say方法输出相应信息。
	- ## 5.4 多态
	  collapsed:: true
		- 多态性是指类为名称相同的方法提供不同的实现方式。利用多态性，可以调用类中的某个方法而无需考虑该方法的实现过程。
		- 多态性也是面向对象编程中最重要的特性之一。多态性在运行时，可以通过指向基类的指针，来调用实现派生类中的方法。也可以把一组对象放到一个数组中，然后调用他们的方法，在这种场合下，多态性的作用就体现出来了。本节将具体讲解多态性的有关知识。
		- 当派生类从基类继承时，他会获得基类的所有方法、字段、属性和事件。
		- 在C# 中，类的多态性是通过在子类重写或隐藏基类的方法或函数成员来实现的。下面通过一个小例子来说明方法的重写与隐藏。
		- *例5-9：方法的重写与隐藏（ConsoleOverride)*
		  collapsed:: true
			- ```c#
			  using System;
			  using System.Collections;
			  using System.Collections.Generic;
			  using System.Linq;
			  using System.Net.Http.Headers;
			  using System.Text;
			  using System.Threading.Tasks;
			  
			  namespace Test
			  {
			      internal class Program
			      {
			          static void Main(string[] args)
			          {
			              Animal animal = new Animal();
			              Animal animalDog = new Dog();
			              Animal animalCat = new Cat();
			  
			              animal.HasHairy();
			              animal.Barking();
			  
			              Dog dog = new Dog();
			              Cat cat = new Cat();
			              animalDog.HasHairy();
			              animalCat.HasHairy();
			              animalDog.Barking();
			              animalCat.Barking();
			              dog.Barking();
			              cat.Barking();
			              Console.ReadLine();
			          }
			      }
			  
			      class Animal
			      {
			          public virtual void HasHairy()
			          {
			              Console.WriteLine("I'm an animal with hairy");
			          }
			          public void Barking()
			          {
			              Console.WriteLine("I'm Barking");
			          }
			      }
			      class Dog : Animal
			      {
			          public override void HasHairy()
			          {
			              Console.WriteLine("a dog, has hair");
			          }
			          public new void Barking()
			          {
			              Console.WriteLine("My Barking is wang");
			          } 
			      }
			      class Cat : Animal
			      {
			          public override void HasHairy()
			          {
			              Console.WriteLine("a cat, has hair");
			          }
			          public new void Barking()
			          {
			              Console.WriteLine("My Barking is miao");
			          }
			      }
			  
			  }
			  ```
		- 在此例中，声明了一个名为Animal的类，Animal类中定义了一个名为HasHairy的虚方法（virtual）方法和一个名为Barking的方法。接着定义了Dog和Cat两个类，并分别继承自Animal类，并分别重写（override）与隐藏（new）了基类中的方法。在Main方法中，分别使用两个子类的对象来实例化父类，并各自实例化子类的对象。并分别调用其HasHairy和Barking方法输出相应信息。
		- 在此需要注意的是，父类中的虚方法必须用override来重写，而非虚方法则使用了new关键字来隐藏基类的方法。被隐藏的方法，若实例化的是子类的对象，则调用相应子类中的方法，否则调用父类中的方法。
	- ## 5.5 抽象类与抽象方法的应用
	  collapsed:: true
		- 如果一个类不与具体的事物相联系，而只是表达一种抽象的概念，仅仅是作为其派生类的一个基类，这样的类就是抽象类，在抽象类中声明方法时，如果加上abstract关键字则为抽象方法。
		- ### 5.5.1 抽象类的声明
		  collapsed:: true
			- 抽象类主要用来提供多个派生类可共享的基类的公共定义，抽象类与非抽象类的主要区别如下。
			  collapsed:: true
				- （1）抽象类不能直接被实例化。
				- （2）抽象类中可以包含抽象成员，但非抽象类中不可以。
				- （3）抽象类不能被密封。
			- C# 中，使用abstract关键字来声明抽象类，语法格式如下：
			  collapsed:: true
				- ```c#
				  访问修饰符 abstract class 类名
				      {
				          //类成员
				      }
				  ```
			- 以下代码片段演示了声明一个名为MyAbstractClass的抽象类，其中包含一个string类型的变量msg，以及一个无返回值方法ShowMsg。
			  collapsed:: true
				- ```c#
				  public abstract class MyAbstractClass
				      {
				          public string msg="Hello";
				      
				      public void ShowMsg()
				      {
				          Console.WriteLine(msg);
				      }
				      }
				  ```
		- ### 5.5.2 抽象方法的声明
		  collapsed:: true
			- 抽象方法是在声明方法前加上abstract关键字，抽象方法的特点如下。
			  collapsed:: true
				- （1）抽象方法是隐式的虚方法，抽象方法只能在抽象类中声明。
				- （2）抽象方法不能使用private、static和virtual修饰符。（抽象方法默认是一个virtual方法。）
				- （3）抽象方法声明不提供具体的实现，没有方法体。若要实现抽象方法，需要在派生类（非抽象类）中进行重写该抽象方法，继承类只有实现所有抽象类的抽象方法后才能被实例化。
			- 以下代码片段演示了声明一个名为MyAbstractClass的抽象类，并在其中声明一个无返回值的抽象方法ShowMsg。
			- ```c#
			  public abstract class MyAbstractClass
			    {
			    public abstract void ShowMsg();
			    }
			  ```
		- ### 5.5.3 如何使用抽象类与抽象方法
		  collapsed:: true
			- 本节通过一个简单的示例来讲解下抽象类与抽象方法的使用。
			- *5-10：抽象类与抽象方法的使用*
			  collapsed:: true
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
				              Animal animalDog = new Dog();
				              Animal animalCat=new Cat();
				              Dog dog = new Dog();
				              Cat cat = new Cat();
				  
				              animalDog.Barking();
				              animalCat.Barking();
				              dog.Barking();
				              cat.Barking();
				              Console.ReadLine();
				  
				          }
				      }
				      public abstract class Animal
				      {
				          public abstract void Barking();
				      }
				      public class Dog : Animal
				      {
				          public override void Barking()
				          {
				              Console.WriteLine("wang wang wang");
				          }
				      }
				      public class Cat : Animal
				      {
				          public override void Barking()
				          {
				              Console.WriteLine("miao miao miao");
				          }
				      }
				  
				  }
				  ```
			- 在此例中，声明了一个名为Animal的抽象类，Animal类中定义一个名为Barking的抽象方法。子类Dog、Cat分别继承自抽象类Animal，并分别重写父类中的抽象方法Barking。Main方法中，分别使用子类的对象来实例化父类以及子类本身，并调用其Barking方法输出信息。
			- 抽象类的特点如下。
			  collapsed:: true
				- （1）抽象类使用abstract修饰符，并且它只能用作基类。
				- （2）抽象类不能实例化，当使用new运算符对其实例时会出现编译错误。
				- （3）允许（但不要求）抽象类包含抽象成员，非抽象类不能包含抽象成员。
				- （4）抽象类不能被密封。
				- （5）抽象类可以被抽象类所继承，结果仍是抽象类。
			- 那么，抽象类和接口有什么异同呢？
			  collapsed:: true
				- （1）它们的派生类只能继承一个基类，即只能继承一个抽象类，但是可以继承多个接口。
				- （2）抽象类中可以定义成员的实现，但接口中不可以。
				- （3）抽象类中包含字段、构造函数、析构函数、静态成员或常量等，接口中不可以。
				- （4）抽象类中的成员可以是私有的（只要不是抽象的）、受保护的、内部的或受保护的内部成员，但接口中的成员必须是公共的。
			- 所以，抽象类和接口这两种类型用于完全不同的目的。抽象类主要用作对象系列的基类，共享某些主要特性，例如共同的目的和结构。接口则主要用于类，这些类在基础水平上有所不同，但仍然可以完成某些相同的任务。
	- ## 5.6 密封类与密封方法
	  collapsed:: true
		- 在C# 中，不能被继承的类称为密封类（sealed），密封类可以用来限制扩展性。如果密封了某个方法，则该成员不能被重写。
		- C# 中使用sealed关键字来实现类或方法等成员变量的密封，其语法格式如下：
		  collapsed:: true
			- ```c#
			  访问修饰符 sealed class 类名
			      {
			          //类成员
			      }
			  ```
		- sealed修饰符可以应用于类、实例方法、属性、事件和索引器上，但是不能应用于静态成员。密封类不能被继承。密封成员可以存在于密封或非密封类中。密封方法会重写基类中的方法，但其本身不能在任何派生类中进一步重写。当应用于方法或属性时，sealed修饰符必须始终与override结合使用。将密封类用作基类或将abstract修饰符与密封类一起使用是错误的。
		- 一个密封成员必须对虚成员或隐含虚成员进行重写，如抽象成员。但是，密封成员自己是不能被重写的，因为它是密封的。虽然密封成员不能被重写，但是一个在基类中的密封成员可以用new修饰符在派生类中进行隐藏。更重要的是，由于密封类从不用作基类，所以有些运行时优化可以略微提高密封类成员的调用速度。
		- *例5-11： 密封类与密封成员（ConsoleSealed）*
		  collapsed:: true
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
			              Cars cars = new HatchbackCars();
			              cars.FuelConsumption();
			  
			              cars = new Sedan();
			              cars.FuelConsumption();
			  
			              HatchbackCars hCars = new HatchbackCars();
			              hCars.FuelConsumption();
			  
			              Sedan sedan = new Sedan();
			              sedan.FuelConsumption();
			  
			              Console.ReadLine();
			          }
			      }
			      public abstract class Cars
			      {
			          public virtual void FuelConsumption()
			          {
			              Console.WriteLine("Cars 油耗");
			          }
			      }
			      public sealed class HatchbackCars : Cars
			      {
			          public sealed override void FuelConsumption()
			          {
			              Console.WriteLine("HatchbackCars 油耗");
			          }
			      }
			      public sealed class Sedan : Cars
			      {
			          public sealed override void FuelConsumption()
			          {
			              Console.WriteLine("Sedan 油耗");
			          }
			      }
			  }
			  ```
		- 在此例中，HatchbackCars和Sedan类不能被进一步地细化。此外，HatchbackCars. FuelConsumption与Sedan.FuelConsumption方法均不能被重写。