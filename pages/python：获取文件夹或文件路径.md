- GUI程序与用户交互，一个重要的方面就是让用户选择文件或文件夹，比如选择要执行某个动作的文件或文件夹，或者要选择一个文件来保存某些内容的时候。Python标准的tkinter.filedialog模块，提供了这类对话框实现的简单接口。
- **不想显示黑窗口**
	- ```python
	  root = Tkinter.Tk()
	  root.withdraw()
	  ```
- **获取文件路径** **askopenfilename**
	- ```python
	  >>> import tkinter as tk
	  >>> root = tk.Tk()
	  >>> from tkinter.filedialog import (askopenfilename, 
	                                      askopenfilenames, 
	                                      askdirectory, 
	                                      asksaveasfilename)
	  >>> 
	  >>> askopenfilename()
	  '/home/xinlin/repos/sendslip/config.ini'
	  >>> askopenfilename()
	  >>> ''
	  ```
	- ![image.png](../assets/image_1648737595122_0.png)
	- 上面示例代码，调用askopenfilename没有使用任何参数，选择一个文件，返回此文件路径的字符串，如果不选择，Cancel或直接关闭，返回一个空的字符串（测试时出现过Cancel或直接关闭，返回空tuple）。
	- askopenfilename函数（本文介绍的其它几个函数一样）还有几个参数可以考虑使用，要采用key=value的方式：**title，窗口名称；initialdir初始路径；filetypes，文件类型。**
	- ```python
	  askopenfilename(title='Please choose a file', 
	                    initialdir='/', filetypes=[('Python source file','*.py')])
	  ```
	- ![image.png](../assets/image_1648737335590_0.png){:height 293, :width 426}
- **askopenfilenames**  打开多个文件
	- 这个对话框，可以让用户同时选择多个文件。打开的对话框样子是一样的，就不再贴图了。
	- askopenfilenames可以同时选择多个文件（按住Ctrl键多选），返回一个tuple，tuple的每个元素都是一个pathname，如果只选择一个文件，也是返回tuple，里面包含一个元素。如果Cancel或者直接关闭，返回空字符串。
	- ```python
	  >>> askopenfilenames()
	  ('/home/xinlin/repos/sendslip/config.ini', '/home/xinlin/repos/sendslip/README.md', '/home/xinlin/repos/sendslip/sendslip.py', '/home/xinlin/repos/sendslip/sendslip2.py')
	  >>> askopenfilenames()
	  ('/home/xinlin/repos/sendslip/sendslip2.py',)
	  >>> askopenfilenames()
	  ''
	  ```
- **获取多个路径**  **askdirectory**
	- 这个对话框，要求用户选择一个文件夹。返回选择的文件夹路径，Cancel或直接关闭，返回空串（再次出现了返回空tuple）。
	- ![image.png](../assets/image_1648737651171_0.png)
	- ```python
	  >>> askdirectory()
	  '/home/xinlin/repos/auto10g'
	  >>> askdirectory()
	  ''
	  >>> askdirectory()
	  ()
	  ```
- **另存为文件名称**  **asksaveasfilename**
	- 让用户指定一个文件保存数据。此函数返回一个pathname字符串，如果Cancel或者直接关闭窗口，返回空字符串。返回的文件名如何操作，是其它代码的事情，这个对话框只是返回选择的文件名。
	- ![image.png](../assets/image_1648737666475_0.png)
	- ```python
	  >>> asksaveasfilename()
	  '/home/xinlin/repos/sendslip/dasdfasd.kkk'
	  >>> asksaveasfilename()
	  ''
	  ```
- filedialog子模块内还有几个ask...函数，它们会返回已经打开的文件句柄，而不是返回文件的pathname，本人是不建议使用这几个函数的，它们是：askopenfile，askopenfiles，asksaveasfile。这几个函数所在的源文件，有写着 FIXME 这样的注释，也在质疑它们是不是“太方便”了......
- ```python
  import tkinter as tk
  from tkinter import Button, Widget, font, filedialog, scrolledtext
  
  def Select_Source_Folder():
      global filepath_source
      filepath_source0=filedialog.askdirectory()
      filepath_source=filepath_source0.replace('/', '\\')
  ```