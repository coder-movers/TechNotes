## 一、 快速开始

### 1. 导入 Tkinter 模块

在使用 Tkinter 之前，首先要导入 Tkinter 模块。

```python
import tkinter as tk
```

> 导入子模块
>
> 1. 按需导入
>
>    ```python
>    import tkinter as tk
>    from tkinter import Label
>    
>    window = tk.Tk()
>    ```
>
> 2. 全部导入
>
>    ```python
>    from tkinter import *
>                   
>    window = TK()
>    ```



### 2. 创建主窗口

Tkinter 应用程序的窗口是基于 `Tk` 类创建的。创建一个主窗口并命名它。

```python
window = tk.Tk()	# 创建窗口
window.title("My Application")	# 窗口标题
window.geometry("300x100+630+80")  # (宽度x高度)+(x轴+y轴)
window.mainloop() # 进入事件循环，保持连接
```



### 3. 创建按钮

创建按钮并绑定事件

```python
from tkinter import messagebox	# 按需导入

def test_click():
    # 创建弹窗
    messagebox.showinfo("窗口名称", "点击成功")


# 创建按钮，并且将按钮放到窗口里面
btn1 = tk.Button(window, text="点击按钮", command=test_click)
# btn1['text'] = "点击按钮"  # 绑定属性的另一个写法
btn1.pack()  # 按钮布局
```



### 4. 完整demo

```python
import tkinter as tk
from tkinter import messagebox

window = tk.Tk()
window.title("My app")
window.geometry("300x100+630+80")


def test_click():
    # 创建弹窗
    messagebox.showinfo("窗口名称", "点击成功")


# 创建按钮，并且将按钮放到窗口里面
btn1 = tk.Button(window, text="点击按钮", command=test_click)
# btn1['text'] = "点击按钮"  # 绑定属性的另一个写法
btn1.pack()  # 按钮布局

window.mainloop()
```



## 二、Tkinter 的组件

### 1. 核心组件

| 控件           | 名称       | 作用                                           |
| -------------- | ---------- | ---------------------------------------------- |
| `Label`        | 标签       | 显示静态文本或图像                             |
| `Button`       | 按钮       | 触发操作或响应事件                             |
| `Entry`        | 文本框     | 接收用户输入的单行文本                         |
| `Text`         | 文本框     | 接收和显示多行文本                             |
| `Checkbutton`  | 复选框     | 允许用户选择一个或多个选项                     |
| `Radiobutton`  | 单选按钮   | 允许用户从多个选项中选择一个                   |
| `Combobox`     | 下拉框     | 提供一个下拉列表供用户选择                     |
| `Listbox`      | 列表框     | 显示一个列表供用户选择或显示多行文本           |
| `Scrollbar`    | 滚动条     | 允许用户滚动容器中的内容                       |
| `Canvas`       | 画布       | 用于绘制图形和显示图像                         |
| `Frame`        | 框架       | 用于组织和布局其他组件                         |
| `Menu`         | 菜单       | 提供命令和选项供用户选择                       |
| `MessageBox`   | 消息框     | 显示消息或警告信息                             |
| `FileDialog`   | 文件对话框 | 用于选择文件或保存文件                         |
| `ColorChooser` | 颜色选择器 | 允许用户选择颜色                               |
| `Progressbar`  | 进度条     | 显示长时间操作的进度                           |
| `Scale`        | 滑块       | 提供一个可滑动的控件，用于选择值范围           |
| `Spinbox`      | 数字框     | 允许用户通过键盘或按钮选择一个数字             |
| `Treeview`     | 树状视图   | 显示分层次的数据，如目录结构或表格数据         |
| `PanedWindow`  | 分隔窗口   | 创建可调整大小的窗格布局                       |
| `Notebook`     | 选项卡     | 提供多个选项卡，用于切换不同的页面或视图       |
| `Message`      | 信息       | 显示一行或多行文本，自动调整大小以适应内容     |
| `LabelFrame`   | 标签框     | 提供一个带有标题的边框，用于组织和标记相关组件 |
| `Separator`    | 分隔符     | 用于在界面中添加水平或垂直分隔线               |
| `ToolTip`      | 工具提示   | 提供鼠标悬停时显示的提示信息                   |
| `Toplevel`     | 新建窗口   | 在顶层新建窗口                                 |



### 2. 组件的属性和方法

每个组件都有一些特定的属性和方法，用于设置和获取其状态、值和其他属性。

```python
button = tk.Button(window, text="Click me!")
button.config(state="disabled")  # 设置按钮状态为禁用
button["text"] = "New Text"  # 修改按钮文本
button.pack()
```



### 3. 组件共同属性

| 属性        | 说明                                 | 取值                                       |
| ----------- | ------------------------------------ | ------------------------------------------ |
| bg          | 背景颜色                             | 十六进制颜色，比如`#00FF00`                |
| bd          | 加粗                                 | 2                                          |
| borderwidth | 边框宽度                             | 0                                          |
| cursor      | 鼠标悬停时的鼠标样式                 | 默认箭头样式                               |
| font        | 字体                                 | 无                                         |
| fg          | 文本的前景色                         | 无                                         |
| height      | 高度（文本控件的单位为行，不是像素） | 自身内容高度                               |
| width       | 宽度（文本控件的单位为行，不是像素） | 自身内容宽度                               |
| state       | 组件状态                             | normal（默认）、DISABLED                   |
| text        | 文本内容                             | 空字符串                                   |
| wraplength  | 文本允许的换行宽度                   | 0（不换行）                                |
| anchor      | 组件中内容的对齐方式                 | CENTER（默认）、E、S、W、N、NE、SE、SW、NW |
| justify     | 多行文本的对齐方式                   | CENTER、LEFT（默认）、RIGHT、TOP、BOTTOM   |
| padx        | 左右内边距                           | 0                                          |
| pady        | 上下内边距                           | 0                                          |
| relief      | 3D浮雕样式（边框阴影样式）           | flat、raised、sunken、groove、ridge        |

示例：

```python
from tkinter import *

root = Tk()
lb = Label(root, text='我是第一个标签', \
           bg='#d3fbfb', \
           fg='red', \
           font=('华文新魏', 32), \
           width=20, \
           height=2, \
           relief=SUNKEN)
lb.pack()
root.mainloop()
```

如果这个控件实例只需要一次性呈现，也可以不必命名，直接实例化并布局呈现出来，例如:

```python
Label(root,text='我是第一个标签',font='华文新魏').pack()
```



### 4. 组件数据绑定和展示

#### 4.1. 数据绑定

数据绑定是将数据与界面组件进行关联，使数据的变化自动更新到界面上。可以使用 `tkinter.StringVar()` 或 `tkinter.IntVar()` 等变量类型来实现数据绑定。

```python
name_var = tk.StringVar()
name_var.set("John Doe")  # 设置初始值

name_label = tk.Label(window, textvariable=name_var)
```



#### 4.2. 数据展示

可以使用标签（Label）或文本框（Entry）等组件来展示绑定的数据。

```python
name_label = tk.Label(window, textvariable=name_var)
name_entry = tk.Entry(window, textvariable=name_var)
```



### 5. 事件处理机制和用户输入操作

#### 5.1. `bind`绑定事件

使用 `.bind()` 方法来将事件和事件处理函数绑定在一起。可以绑定常见的事件，如按钮点击事件、鼠标事件等。

```python
控件实例.bind(<事件代码>,<函数名>)
```

示例：

```python
def button_click(event):
    print("Button clicked!")

button = tk.Button(window, text="Click me!")
button.bind("<Button-1>", button_click)  # 绑定按钮点击事件
button.pack()
```



#### 5.2. command绑定事件

```python
def button_click():
    print("Button clicked!")

btn1 = tk.Button(window, text="Click me!", command=button_click)
button.bind("<Button-1>", button_click)  # 绑定按钮点击事件
button.pack()
```



#### 5.3. `bind`和`command`区别：

- bind方法可以绑定任何事件，command只能绑定组件自身的command事件，通常是按钮或菜单的点击事件。

- 使用bind时需要传入事件参数，像这样:

  ```python
  btn.bind('<Button-1>', onclick)
  
  def onclick(event):
    pass
  ```

  使用command时不需要事件参数:

  ```python
  btn = Button(command=onclick)
  
  def onclick():
    pass
  ```

- 使用bind可以灵活绑定多个事件处理函数，command只能绑定一个。

- bind可以绑定事件并传参，像这样:

  ```python
  btn.bind('<Button-1>', callback, '+')
  ```

  command不直接支持传参。

- 使用bind绑定的事件处理优先级高于command。

- 使用command更简单直观，bind方式更灵活强大。

所以对于绑定事件，优先使用command参数绑定更方便，其他事件需要用bind方法。



#### 5.4. 事件类型

| 事件代码                                                     | 事件             | 备注                                                         |
| ------------------------------------------------------------ | ---------------- | ------------------------------------------------------------ |
| `<ButtonPress-1>`                                            | 单击鼠标左键     | 可简写为`<Button-1>` 或 `<1>`                                |
| `<ButtonPress-2>`                                            | 单击鼠标中键     | 可简写为`<Button-2>` 或 `<2>`                                |
| `<ButtonPress-3>`                                            | 单击鼠标右键     | 可简写为`<Button-3>` 或 `<3>`                                |
| `<ButtonRelease-1>`                                          | 释放鼠标左键     | ---                                                          |
| `<ButtonRelease-2>`                                          | 释放鼠标中键     | ---                                                          |
| `<ButtonRelease-3>`                                          | 释放鼠标右键     | ---                                                          |
| `<B1-Motion>`                                                | 按住鼠标左键移动 | ---                                                          |
| `<B2-Motion>`                                                | 按住鼠标中键移动 | ---                                                          |
| `<B3-Motion>`                                                | 按住鼠标右键移动 | ---                                                          |
| `<MouseWheel>`                                               | 转动鼠标滚轮     | ---                                                          |
| `<Double-Button-1>`                                          | 双击鼠标左键     | ---                                                          |
| `<Enter>`                                                    | 鼠标进入控件实例 | 注意与回车事件的区别                                         |
| `<Leave>`                                                    | 鼠标离开控件实例 | ---                                                          |
| `<Key>`                                                      | 键盘任意键       | ---                                                          |
| `<Key-字母>`，例如`<key-a>`、`<Key-A>`                       | 字母和数字       | 简写不带小于和大于号，例如：`a`、`A`和`1`等                  |
| `<Return>`                                                   | 回车             | `<Tab>`、`<Shift>`、`<Control>`(注意不能用`<Ctrl>`)、`<Alt>`等类同 |
| `<Space>`                                                    | 空格             | ---                                                          |
| `<Up>` 、`<Down>`、`<Left>`、`<Right>`                       | 方向键           | ---                                                          |
| `<Fn>`例如：`<F1>`等                                         | 功能键           | ---                                                          |
| 键名之间以减号链接，例如`<Control-k>`、`<Shift-6>`、`<Alt-Up>`等 | 组合键           | 注意大小写                                                   |



#### 5.5. 响应参数

所调用的自定义函数若需要利用鼠标或键盘的响应值，可将event作为参数，通过event的属性获取。event的属性见下表：

| event属性                    | 意义                                           |
| ---------------------------- | ---------------------------------------------- |
| x或y（注意是小写）           | 相对于事件绑定控件实例左上角的坐标值(像素)     |
| root_x或root_y（注意是小写） | 相对于显示屏幕左上角的坐标值(像素)             |
| char                         | 可显示的字符，若按键不可显示，则返回为空字符串 |
| keysysm                      | 字符或字符型按键名，如：“a”或“Escape”          |
| keysysm_num                  | 按键的十进制 ASCII 码值                        |

例如：将标签绑定键盘任意键触发事件并获取焦点，并将按键字符显示在标签上

```python
from tkinter import *


def show(event):
    s = event.keysym
    lb.config(text=s)


root = Tk()
root.title('按键实验')
root.geometry('200x200')
lb = Label(root, text='请按键', font=('黑体', 48))
lb.bind('<Key>', show)
lb.focus_set()
lb.pack()
root.mainloop()
```





#### 5.6. 获取用户输入

使用文本框（Entry）组件来获取用户输入。可以使用 `.get()` 方法获取文本框的值。

```python
def get_name():
    name = name_var.get()
    print("Name:", name)

name_var = tk.StringVar()
name_entry = tk.Entry(window, textvariable=name_var)
name_entry.pack()

button = tk.Button(window, text="Get Name", command=get_name)
button.pack()
```



## 三. Tkinter 的布局

Tkinter 提供了几种布局管理器，包括 pack、grid 和 place。布局管理器帮助我们定位和放置组件。

### 1. pack 布局

将组件垂直的排列（默认），或者水平的排列

- 垂直布局

  ```python
  from tkinter import *
  
  root = Tk()
  
  lbred = Label(root, text="Red", fg="Red", relief=GROOVE)
  lbred.pack()
  lbgreen = Label(root, text="绿色", fg="green", relief=GROOVE)
  lbgreen.pack()
  lbblue = Label(root, text="蓝", fg="blue", relief=GROOVE)
  lbblue.pack()
  root.mainloop()
  ```

  

- 水平布局

  | 属性 | 参数                       | 说明                                                       |
  | ---- | -------------------------- | ---------------------------------------------------------- |
  | fill | 不同方向填充               | X（水平方向填充）、Y（垂直方向填充）、BOTH（二维伸展填充） |
  | side | 控件相对于下一个控件的方位 | TOP、LEFT、RIGHT、BOTTOM                                   |

  示例：
  
  ```python
  from tkinter import *
  
  root = Tk()
  
  lbred = Label(root, text="Red", fg="Red", relief=GROOVE)
  lbred.pack()
  lbgreen = Label(root, text="绿色", fg="green", relief=GROOVE)
  lbgreen.pack(side=RIGHT)
  lbblue = Label(root, text="蓝", fg="blue", relief=GROOVE)
  lbblue.pack(fill=X)
  root.mainloop()
  ```
  
  

### 2. grid布局

二维网格布局。pack()方法与grid()方法不能混合使用。

| 选项         | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| column       | 单元格的列号，从0开始的正整数                                |
| columnspan   | 跨列，跨越的列数，正整数                                     |
| row          | 单元格的行号， 从0开始的正整数                               |
| rowspan      | 跨行，跨越的行数，正整数                                     |
| ipadx, ipady | 设置子组件之间的间隔，x方向或y方向，默认单位为像素，非浮点数，默认0.0 |
| padx, pady   | 与之并列的组件之间的间隔，x方向或y方向，默认单位为像素，非浮点数，默认0.0 |
| sticky       | 组件紧贴所在的单元格的某一脚，对应于东南西北中以及4个角。东 = “e”，南=“s”，西=“w”，北=“n”，“ne”，“se”，“sw”， “nw”; |

```python
from tkinter import *

root = Tk()

lbred = Label(root, text="Red", fg="Red", relief=GROOVE)
lbred.grid(column=2, row=0)
lbgreen = Label(root, text="绿色", fg="green", relief=GROOVE)
lbgreen.grid(column=0, row=1)
lbblue = Label(root, text="蓝", fg="blue", relief=GROOVE)
lbblue.grid(column=1, columnspan=2, ipadx=20, row=2)
root.mainloop()
```



### 3. place布局

可以通过坐标精确控制组件的位置，适用于一些布局更加灵活的场景

| 选项                 | 说明                                                 |
| -------------------- | ---------------------------------------------------- |
| x,y                  | 组件左上角的绝对坐标（相当于窗口）                   |
| relx ,rely           | 组件左上角的坐标（相对于父容器）                     |
| width , height       | 组件的宽度和高度                                     |
| relwidth , relheight | 组件的宽度和高度（相对于父容器）                     |
| anchor               | 对齐方式，左对齐“w”，右对齐“e”，顶对齐“n”，底对齐“s” |

```python
import tkinter as tk

root = tk.Tk()

but1 = tk.Button(root, text="按钮1")
but1.place(relx=0.2, x=100, y=20, relwidth=0.2, relheight=0.5)

root.title('演示窗口')
root.geometry("300x150+1000+300")
root.mainloop()
```



### 4. 组件和布局综合案例

组件文字字体、字号、字体粗细、颜色设置

```python
import tkinter.font as font
import tkinter as tk

root = tk.Tk()
'''
family：指定字体名称
size：指定字体大小
weight：指定字体的粗细程度
'''
font_1 = font.Font(family='Helvetica', size=30, weight='normal')
font_2 = font.Font(family='Arial', size=15, weight='bold')

# bg：背景颜色
# foreground: 文字颜色
but1 = tk.Button(root, text="背景色", font=font_1, bg="LightSkyBlue")
but1.grid(row=0, column=0)

Label1 = tk.Label(root, text="文字颜色", font=font_2, foreground="Orange")
Label1.grid(row=0, column=2)

root.title('演示窗口')
root.geometry("300x150+1000+300")
root.mainloop()
```



## 四、组件基本封装

### 1. 基本框架

```python
import tkinter as tk


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x200+1100+150")
        self.interface()

    def interface(self):
        """界面编写位置"""
        pass


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```

### 2. 子组件

#### 2.1. 文本显示_Label

```python
def interface(self):
    """界面编写位置"""
    self.Label0 = tk.Label(self.root, text="文本显示")
    self.Label0.grid(row=0, column=0)
```



#### 2.2. 按钮显示_Button

```python
def interface(self):
    """界面编写位置"""
    self.Button0 = tk.Button(self.root, text="按钮显示")
    self.Button0.grid(row=0, column=0)
```



#### 2.3. 输入框显示_Entry

```python
def interface(self):
    """界面编写位置"""
    self.Entry0 = tk.Entry(self.root)
    self.Entry0.grid(row=0, column=0)
```



#### 2.4. 文本输入框显示_Text

```python
# pack布局
def interface(self):
    """界面编写位置"""
    self.w1 = tk.Text(self.root, width=80, height=10)
    self.w1.pack(pady=0, padx=30)
# grid布局
def interface(self):
    """界面编写位置"""
    self.w1 = tk.Text(self.root, width=80, height=10)
    self.w1.grid(row=1, column=0)
```



#### 2.5. 复选按钮_Checkbutton

```python
def interface(self):
    """界面编写位置"""
    self.Checkbutton01 = tk.Checkbutton(self.root, text="名称")
    self.Checkbutton01.grid(row=0, column=2)
```



#### 2.6. 单选按钮_Radiobutton

```python
def interface(self):
    """界面编写位置"""
    self.Radiobutton01 = tk.Radiobutton(self.root, text="名称")
    self.Radiobutton01.grid(row=0, column=2)
```



#### 2.7. 下拉选择框_Combobox

```python
def interface(self):
    """界面编写位置"""
    values = ['1', '2', '3', '4']
    self.combobox = ttk.Combobox(
        master=self.root,  # 父容器
        height=10,  # 高度,下拉显示的条目数量
        width=20,  # 宽度
        state='',  # 设置状态 normal(可选可输入)、readonly(只可选)、 disabled(禁止输入选择)
        cursor='arrow',  # 鼠标移动时样式 arrow, circle, cross, plus...
        font=('', 15),  # 字体、字号
        textvariable='',  # 通过StringVar设置可改变的值
        values=values,  # 设置下拉框的选项
    )
    self.combobox.grid(padx=150)
```



#### 2.8. 菜单-主菜单、子菜单

```python
import tkinter as tk
from tkinter import Menu


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x200+1100+150")
        # 创建主菜单实例
        self.menubar = Menu(self.root)
        # 显示菜单,将root根窗口的主菜单设置为menu
        self.root.config(menu=self.menubar)
        self.interface()

    def interface(self):
        """"界面编写位置"""
        # 在 menubar 上设置菜单名，并关联一系列子菜单
        self.menubar.add_cascade(label="文件", menu=self.papers())
        self.menubar.add_cascade(label="查看", menu=self.about())

    def papers(self):
        """
        fmenu = Menu(self.menubar): 创建子菜单实例
        tearoff=1: 1的话多了一个虚线,如果点击的话就会发现,这个菜单框可以独立出来显示
        fmenu.add_separator(): 添加分隔符"--------"
        """
        fmenu = Menu(self.menubar, tearoff=0)
        # 创建单选框
        for item in ['新建', '打开', '保存', '另存为']:
            fmenu.add_command(label=item)

        return fmenu

    def about(self):
        amenu = Menu(self.menubar, tearoff=0)
        # 添加复选框
        for item in ['项目复选框', '文件扩展名', '隐藏的项目']:
            amenu.add_checkbutton(label=item)

        return amenu


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```



#### 2.9. 综合案例-电子时钟

- 方法一：利用configure()方法或config()来实现文本变化。

  ```python
  import tkinter
  import time
  
  def gettime():
        timestr = time.strftime("%H:%M:%S") # 获取当前的时间并转化为字符串
        lb.configure(text=timestr)   # 重新设置标签文本
        root.after(1000,gettime) # 每隔1s调用函数 gettime 自身获取时间
  
  root = tkinter.Tk()
  root.title('时钟')
  
  lb = tkinter.Label(root,text='',fg='blue',font=("黑体",80))
  lb.pack()
  gettime()
  root.mainloop()
  ```

  

- 方法二：利用textvariable变量属性来实现文本变化。

  ```python
  import tkinter
  import time
  
  def gettime():
        var.set(time.strftime("%H:%M:%S"))   # 获取当前时间
        root.after(1000,gettime)   # 每隔1s调用函数 gettime 自身获取时间
  
  root = tkinter.Tk()
  root.title('时钟')
  var=tkinter.StringVar()
  
  lb = tkinter.Label(root,textvariable=var,fg='blue',font=("黑体",80))
  lb.pack()
  gettime()
  root.mainloop()
  ```



### 3. 组件使用

#### 3.1. 按钮(Button)绑定事件

```python
    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="运行", command=self.event)
        self.Button0.grid(row=0, column=0, padx=20)

        # 使用lambda表达式创建了一个匿名函数，该函数会调用self.add_page方法并传递参数
        self.Button1 = tk.Button(self.root, text="确定", command=lambda: self.parameter('测试'))
        self.Button1.grid(row=0, column=1, padx=20)

        self.Button2 = tk.Button(self.root, text="退出", command=self.root.destroy, bg="Gray")  # bg=颜色
        self.Button2.grid(row=0, column=2, padx=20)

    def event(self):
        """按钮事件"""
        print("运行成功")

    def parameter(self, data):
        """传入参数"""
        print(f"获取到的参数: {data}")
```



#### 3.2. 输入框(Entry)内容获取

```python
    def interface(self):
        """"界面编写位置"""
        self.entry00 = tk.StringVar()
        self.entry00.set("默认信息")

        self.entry0 = tk.Entry(self.root, textvariable=self.entry00)
        self.entry0.grid(row=1, column=0)

        self.Button0 = tk.Button(self.root, text="运行", command=self.event)
        self.Button0.grid(row=0, column=0)

    def event(self):
        """按钮事件,获取文本信息"""
        a = self.entry00.get()
        print(a)
```



#### 3.3. 文本输入框(Text)，写入文本信息和清除文本信息

```python
    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="清除", command=self.event)
        self.Button0.grid(row=0, column=0)

        self.w1 = tk.Text(self.root, width=80, height=10)
        self.w1.grid(row=1, column=0)
        self.w1.insert("insert", "默认信息")

    def event(self):
        '''清空输入框'''
        self.w1.delete(1.0, "end")
```



#### 3.4. 获取复选按钮(Checkbutton)的状态

```python
  def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="确定", command=self.event)
        self.Button0.grid(row=0, column=0)

        self.v1 = tk.IntVar()
        self.Checkbutton01 = tk.Checkbutton(self.root, text="复选框", command=self.Check_box, variable=self.v1)
        self.Checkbutton01.grid(row=1, column=0)

        self.w1 = tk.Text(self.root, width=80, height=10)
        self.w1.grid(row=2, column=0)

    def event(self):
        '''按钮事件，获取复选框的状态，1表示勾选，0表示未勾选'''
        a = self.v1.get()
        self.w1.insert(1.0, str(a)+'\n')

    def Check_box(self):
        '''复选框事件'''
        if self.v1.get() == 1:
            self.w1.insert(1.0, "勾选"+'\n')
        else:
            self.w1.insert(1.0, "未勾选"+'\n')
```



#### 3.5. 清除控件

```python
    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="确定", command=self.event)
        self.Button0.grid(row=0, column=0)

        self.Label0 = tk.Label(self.root, text="文本显示")
        self.Label0.grid(row=1, column=0)

        self.Entry0 = tk.Entry(self.root)
        self.Entry0.grid(row=2, column=0)

        self.w1 = tk.Text(self.root, width=80, height=10)
        self.w1.grid(row=3, column=0)

    def event(self):
        '''按钮事件，清除Label、Entry、Text组件'''
        a = [self.Label0, self.Entry0, self.w1]
        for i in a:
            i.grid_forget()
```



#### 3.6. 清除复选框勾选状态

```python
    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="确定", command=self.event)
        self.Button0.grid(row=0, column=0)

        self.v1 = tk.IntVar()
        self.Checkbutton01 = tk.Checkbutton(self.root, text="复选框", command=self.Check_box, variable=self.v1)
        self.Checkbutton01.grid(row=1, column=0)

        self.w1 = tk.Text(self.root, width=80, height=10)
        self.w1.grid(row=2, column=0)

    def event(self):
        '''按钮事件，清除复选框勾选状态'''
        self.Checkbutton01.deselect()

    def Check_box(self):
        '''复选框事件'''
        if self.v1.get() == 1:
            self.w1.insert(1.0, "勾选"+'\n')
        else:
            self.w1.insert(1.0, "未勾选"+'\n')
```



#### 3.7. 文本框(Text)内容获取

```python
    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="确定", command=self.event)
        self.Button0.grid(row=0, column=0)

        self.w1 = tk.Text(self.root, width=80, height=10)
        self.w1.grid(row=1, column=0)

    def event(self):
        a = self.w1.get('0.0', 'end')
        print(a)
```



#### 3.8. 下拉选择框绑定事件

```python
    def interface(self):
        """"界面编写位置"""
        self.value = tk.StringVar()
        self.value.set('2')  # 默认值 
        values = ['1', '2', '3', '4']
        self.combobox = ttk.Combobox(
            master=self.root,  # 父容器
            height=10,  # 高度,下拉显示的条目数量
            width=20,  # 宽度
            state='',  # 设置状态 normal(可选可输入)、readonly(只可选)、 disabled(禁止输入选择)
            cursor='arrow',  # 鼠标移动时样式 arrow, circle, cross, plus...
            font=('', 15),  # 字体
            textvariable=self.value,  # 通过StringVar设置可改变的值
            values=values,  # 设置下拉框的选项
            )
        # 绑定事件,下拉列表框被选中时，绑定pick()函数
        self.combobox.bind("<<ComboboxSelected>>", self.pick)
        self.combobox.grid(padx=150)

    def pick(self, *args):  # 处理事件，*args表示可变参数
        print('选中的数据:{}'.format(self.combobox.get()))
        print('value的值:{}'.format(self.value.get()))
```



#### 3.9. 手动选择颜色

```python
import tkinter as tk
from tkinter import colorchooser


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x200+1100+150")
        self.interface()

    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="选择颜色", command=self.get_colors)
        self.Button0.grid(row=0, column=1)

        self.w1 = tk.Text(self.root, width=68, height=10)
        self.w1.grid(row=1, column=0, columnspan=3, padx=10)

    def get_colors(self):
        '''手动选择颜色, 并获取颜色代码'''
        color_code = colorchooser.askcolor()
        # 清除text文本框
        self.w1.grid_forget()
        # 重新添加文本框，并添加颜色
        self.w1 = tk.Text(self.root, width=68, height=10, bg=color_code[1])
        self.w1.grid(row=1, column=0, columnspan=3, padx=10)
        # 打印颜色代码
        self.w1.insert("insert", color_code)


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```



#### 3.10. 选择文件和文件另存

```python
import tkinter as tk
from tkinter import filedialog
import pandas as pd  # pip install pandas


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x200+1100+150")
        self.interface()

    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="选择单个文件", command=self.single_file)
        self.Button0.grid(row=0, column=0)

        self.Button1 = tk.Button(self.root, text="选择多个文件", command=self.multiple_files)
        self.Button1.grid(row=0, column=1)

        self.Button2 = tk.Button(self.root, text="保存文件", command=self.save_file)
        self.Button2.grid(row=0, column=2)

        self.w1 = tk.Text(self.root, width=68, height=10)
        self.w1.grid(row=1, column=0, columnspan=3, padx=10)

    def single_file(self):
        '''获取单个文件'''
        file_path = filedialog.askopenfilename()
        self.w1.insert("insert", file_path)

    def multiple_files(self):
        '''获取多个文件'''
        file_path = filedialog.askopenfilenames()
        self.w1.insert("insert", file_path)

    def save_file(self):
        '''保存文件'''
        # 去掉title='保存为'，标题默认名称“另存为”
        file_name = filedialog.asksaveasfilename(title='保存为', filetypes=[("csv", ".csv")])
        # 文件添加数据并保存
        filename = file_name+'.csv'
        csvfile = open(filename, 'w')
        name = ['姓名', '年龄', '电话']
        list1 = [
            ('王明', '25', '12345678'),
            ('张三', '18', '87654321')
            ]
        save = pd.DataFrame(columns=name, data=list1)
        save.to_csv(filename)


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```



#### 3.11. 日期选择模块

> PyInstaller打包说明：
> 	如果使用了日期选择模块“tkcalendar.DateEntry”，打包是必须加上“--hidden-import babel.numbers”
> 	pyinstaller --hidden-import babel.numbers myscript.py
> 	或通过编辑.spec文件
> 	hiddenimports=["babel.numbers"]

```python
# tkcalendar模块需要安装，命令：pip install tkcalendar
import tkinter as tk
import datetime
from tkcalendar import DateEntry


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x230+1100+150")
        self.interface()

    def interface(self):
        """"界面编写位置"""
        self.Label0 = tk.Label(self.root, text="日期选择")
        self.Label0.grid(row=0, padx=210)
        # 获取当前本地电脑日期
        date = datetime.datetime.now().strftime('%Y-%m-%d')
        date_print = date.split("-")
        # 日期下拉选择框模块
        self.date = DateEntry(self.root,
                              date_pattern='yyyy-mm-dd',  # 指定日期格式
                              width=12,
                              year=int(date_print[0]),
                              month=int(date_print[1]),
                              day=int(date_print[2]),
                              background='skyblue',
                              foreground='white',
                              borderwidth=2)
        self.date.grid(row=1, padx=210)

        self.Button0 = tk.Button(self.root, text="运行", command=self.event)
        self.Button0.grid(row=2, column=0, ipadx=10, padx=10)

        self.w1 = tk.Text(self.root, width=50, height=10)
        self.w1.grid(row=3, column=0)

    def event(self):
        # 获取日期
        self.w1.insert(1.0, f"日期打印：{self.date.get()}\n")


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```



#### 3.12. 子菜单绑定事件

```python
import tkinter as tk
from tkinter import filedialog
from tkinter import Menu


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x200+1100+150")
        # 创建主菜单实例
        self.menubar = Menu(self.root)
        # 显示菜单,将root根窗口的主菜单设置为menu
        self.root.config(menu=self.menubar)
        self.interface()

    def interface(self):
        """界面编写位置"""
        # 在 menubar 上设置菜单名，并关联一系列子菜单
        self.menubar.add_cascade(label="文件", menu=self.papers())
        self.menubar.add_cascade(label="查看", menu=self.about())
        # 文本Text窗口显示
        self.w1 = tk.Text(self.root, width=68, height=10)
        self.w1.grid(row=1, column=0, columnspan=3, padx=10)

    def papers(self):
        fmenu = Menu(self.menubar, tearoff=0)
        # 创建“新建”菜单项，并将其绑定到 open_file() 方法
        fmenu.add_command(label="打开文件", command=self.open_file)

        return fmenu

    def about(self):
        amenu = Menu(self.menubar, tearoff=0)
        # 定义 IntVar 类型的实例变量
        self.V1 = tk.IntVar()
        # 创建“文件扩展名”复选框，并将其绑定到 show_extension() 方法
        amenu.add_checkbutton(label="文件扩展名", variable=self.V1, command=self.show_extension)

        return amenu

    def open_file(self):
        file_path = filedialog.askopenfilename()
        self.w1.insert("insert", file_path)

    def show_extension(self):
        if self.V1.get() == 1:
            self.w1.delete(1.0, "end")
            self.w1.insert("insert", "显示文件扩展名\n")
        else:
            self.w1.delete(1.0, "end")
            self.w1.insert("insert", "隐藏文件扩展名\n")


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```



## 五、高级特性

### 1. 交互对话框

#### 1.1. 消息对话框
引用 tkinter.messagebox 包，可使用消息对话框函数。执行这些函数，可弹出模式消息对话框，并根据用户的响应但会一个布尔值。其通式为：

```python
from tkinter import *
import tkinter.messagebox

def xz():
    answer=tkinter.messagebox.askokcancel('请选择','请选择确定或取消')
    if answer:
        lb.config(text='已确认')
    else:
        lb.config(text='已取消')

root = Tk()

lb = Label(root,text='')
lb.pack()
btn=Button(root,text='弹出对话框',command=xz)
btn.pack()
root.mainloop()
```



#### 1.2. 消息框

消息框用于向用户显示消息或警告信息。

```python
import tkinter.messagebox as mb

mb.showinfo("消息框标题", "这是一条消息")
```



#### 1.3. 输入对话框

引用tkinter.simpledialog包，可弹出输入对话框，用以接收用户的简单输入。输入对话框常用 askstring()、askfloat()和askfloat() 三种函数，分别用于接收字符串、整数和浮点数类型的输入。

示例：

单击按钮，弹出输入对话框，接收文本输入显示在窗体的标签上。

```python
from tkinter.simpledialog import *

def xz():
    s=askstring('请输入','请输入一串文字')
    lb.config(text=s)

root = Tk()

lb = Label(root,text='')
lb.pack()
btn=Button(root,text='弹出输入对话框',command=xz)
btn.pack()
root.mainloop()
```



#### 1.4. 文件选择对话框

引用tkinter.filedialog包，可弹出文件选择对话框，让用户直观地选择一个或一组文件，以供进一步的文件操作。常用的文件选择对话框函数有 askopenfilename()、askopenfilenames()和asksaveasfilename(),分别用于进一步打开一个文件、一组文件和保存文件。其中，askopenfilename()和asksaveasfilenamme()函数的返回值类型为包含文件路径的文件名字符串，而askopenfilenames()函数的返回值类型为元组。

示例：

单击按钮，弹出文件选择对话框（“打开”对话框），并将用户所选择的文件路径和文件名显示在窗体的标签上。

```python
from tkinter import *
import tkinter.filedialog

def xz():
    filename=tkinter.filedialog.askopenfilename()
    if filename != '':
         lb.config(text='您选择的文件是'+filename)
    else:
         lb.config(text='您没有选择任何文件')

root = Tk()

lb = Label(root,text='')
lb.pack()
btn=Button(root,text='弹出文件选择对话框',command=xz)
btn.pack()
root.mainloop()
```



#### 1.5. 颜色选择对话框

引用tkinter.colorchooser包，可使用 askcolor()函数弹出模式颜色选择对话框，让用户可以个性化地设置颜色属性。该函数的返回形式为包含RGB十进制浮点元组和RGB十六进制字符串的元组类型

例如：“((135.527343.52734375,167.65234375,186.7265625)),'#87a7ba'”。通常，可将其转换为字符串类型后，再截取以十六进制数表示的RGB颜色字符串用于为属性赋值。

示例： 

单击按钮，弹出颜色选择对话框，并将用户所选择的颜色设置为窗体上标签的背景颜色

```python
from tkinter import *
import tkinter.colorchooser

def xz():
    color=tkinter.colorchooser.askcolor()
    colorstr=str(color)
    print('打印字符串%s 切掉后=%s' % (colorstr,colorstr[-9:-2]))
    lb.config(text=colorstr[-9:-2],background=colorstr[-9:-2])

root = Tk()

lb = Label(root,text='请关注颜色的变化')
lb.pack()
btn=Button(root,text='弹出颜色选择对话框',command=xz)
btn.pack()
root.mainloop()
```



### 2. 画布和图形绘制

#### 2.1. 画布
画布是 Tkinter 中用于绘制图形的组件。通过创建画布并设置其大小和属性，可以在画布上进行图形绘制。

```python
canvas = tk.Canvas(window, width=500, height=300)
canvas.pack()
```

#### 2.2. 绘制图形
可以使用画布提供的方法来绘制各种图形，如线段、矩形、椭圆等。

```python
canvas.create_line(50, 50, 200, 200)  # 绘制线段
canvas.create_rectangle(100, 100, 300, 200)  # 绘制矩形
canvas.create_oval(150, 150, 250, 250)  # 绘制椭圆
```



### 3. 创建菜单和工具栏

#### 3.1. 菜单
菜单提供了一种组织和显示命令和选项的方式。Tkinter 提供了 `tkinter.Menu` 类来创建菜单。

```python
menu_bar = tk.Menu(window)

file_menu = tk.Menu(menu_bar, tearoff=0)
file_menu.add_command(label="打开")
file_menu.add_command(label="保存")
file_menu.add_separator()
file_menu.add_command(label="退出", command=window.quit)

menu_bar.add_cascade(label="文件", menu=file_menu)
window.config(menu=menu_bar)
```



#### 3.2. 工具栏

工具栏通常位于界面顶部，提供了一组常用操作的快捷方式。可以使用按钮（Button）组件来创建工具栏。

```python
toolbar = tk.Frame(window)

open_button = tk.Button(toolbar, text="打开", command=open_file)
save_button = tk.Button(toolbar, text="保存", command=save_file)

open_button.pack(side=tk.LEFT, padx=2, pady=2)
save_button.pack(side=tk.LEFT, padx=2, pady=2)

toolbar.pack(side=tk.TOP, fill=tk.X)
```



## 六、多线程

### 1. 单线程问题

```python
import tkinter as tk


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x200+1100+150")
        self.interface()

    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="确定", command=self.event)
        self.Button0.grid(row=0, column=0)

        self.w1 = tk.Text(self.root, width=80, height=10)
        self.w1.grid(row=1, column=0)

    def event(self):
        '''按钮事件，一直循环'''
        a = 0
        while True:
            a += 1
            self.w1.insert(1.0, str(a)+'\n')


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```

单线程下，主线程需要运行窗口，如果这个时候点击“确定”按钮，主线程就会去执行event方法，那界面就会出现“无响应”状态，如果要界面正常显示，那我们就需要用到多线程(threading)



### 2. 引入多线程

threading语法：

```python
threading.Thread(group=None, target=None, name=None, args=(), kwargs={}, *, daemon=None)
```

> group：必须为None，与ThreadGroup类相关，一般不使用。
> target：目标函数
> name：线程名，默认Thread-x（x从1开始）
> args：为目标函数传递实参、元组
> kwargs：为目标函数传递关键字参数、字典
> daemon：用来设置线程是否随主线程退出而退出（当daemon设置False时，线程不会随主线程退出而退出，主线程会一直等着子线程执行完。当daemon设置True时，线程会随主线程退出而退出，主线程结束其他的子线程会强制退出）

```python
import tkinter as tk
import threading  # 导入多线程模块


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x200+1100+150")
        self.interface()

    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="确定", command=self.start)
        self.Button0.grid(row=0, column=0)

        self.w1 = tk.Text(self.root, width=80, height=10)
        self.w1.grid(row=1, column=0)

    def event(self):
        '''按钮事件，一直循环'''
        a = 0
        while True:
            a += 1
            self.w1.insert(1.0, str(a)+'\n')
            print(a)

    def start(self):
        T1 = threading.Thread(name='t1', target=self.event, daemon=True)  # 子线程
        T1.start()  # 启动


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```



### 3. 多线程暂停和继续

```python
import tkinter as tk
import threading
from time import sleep

event = threading.Event()


class GUI:

    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x200+1100+150")
        self.interface()

    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="启动", command=self.start)
        self.Button0.grid(row=0, column=0)

        self.Button1 = tk.Button(self.root, text="暂停", command=self.stop)
        self.Button1.grid(row=0, column=1)

        self.Button2 = tk.Button(self.root, text="继续", command=self.conti)
        self.Button2.grid(row=0, column=2)

        self.w1 = tk.Text(self.root, width=70, height=10)
        self.w1.grid(row=1, column=0, columnspan=3)

    def event(self):
        '''按钮事件，一直循环'''
        while True:
            sleep(1)
            event.wait()
            self.w1.insert(1.0, '运行中'+'\n')

    def start(self):
        event.set()
        T1 = threading.Thread(target=self.event, daemon=True)
        T1.start()

    def stop(self):
        event.clear()
        self.w1.insert(1.0, '暂停'+'\n')

    def conti(self):
        event.set()
        self.w1.insert(1.0, '继续'+'\n')


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```



## 七、其他操作

### 1. 创建多窗口应用程序

可以使用 `tkinter.Toplevel()` 类来创建多个顶级窗口，实现多窗口的应用程序。

```python
def open_new_window():
    new_window = tk.Toplevel()
    new_window.title("New Window")

open_button = tk.Button(window, text="Open New Window", command=open_new_window)
open_button.pack()
```



### 2. 不同`.py`文件之间的调用

- a.py - -界面+线程
- one/b.py - -业务逻辑
- 以上.py在不同文件夹下

```python
# a.py 文件
import tkinter as tk
import threading
import sys
sys.path.append(r"./one")
from b import main


class GUI:
    def __init__(self):
        self.root = tk.Tk()
        self.root.title('演示窗口')
        self.root.geometry("500x260+1100+150")
        self.interface()

    def interface(self):
        """"界面编写位置"""
        self.Button0 = tk.Button(self.root, text="确定执行", command=self.start, bg="#7bbfea")
        self.Button0.grid(row=0, column=1, pady=10)

        self.entry00 = tk.StringVar()
        self.entry00.set("")

        self.entry0 = tk.Entry(self.root, textvariable=self.entry00)
        self.entry0.grid(row=1, column=1, pady=15)

        self.w1 = tk.Text(self.root, width=50, height=8)
        self.w1.grid(row=2, column=0, columnspan=3, padx=60)

    def start(self):
        T1 = threading.Thread(name='t1', target=main, args=(self.entry00.get(), self.w1), daemon=True)
        T1.start()


if __name__ == '__main__':
    a = GUI()
    a.root.mainloop()
```

```python
# b.py 文件
import time


def main(a, w1):
    try:
        x = 1
        while True:
            y = int(a)+x
            w1.insert(1.0, str(y)+'\n')
            time.sleep(1)
            x += 1
    except Exception:
        w1.insert(1.0, '请输入数字\n')
```



### 3. 图片

#### 3.1. 图片展示

```python
#插入文件图片
import tkinter as tk

root = tk.Tk()

#创建一个标签类, [justify]:对齐方式
textLabel = tk.Label(root,text="你在右边会看到一个图片，\n我在换个行",
justify = tk.LEFT)#左对齐
textLabel.pack(side=tk.LEFT)#自动对齐,side：方位

 

#创建一个图片管理类
photo = tk.PhotoImage(file="18.png")#file：t图片路径
imgLabel = tk.Label(root,image=photo)#把图片整合到标签类中
imgLabel.pack(side=tk.RIGHT)#自动对齐


tk.mainloop()
```



#### 3.2. 背景图片

```python
#插入文件图片
import tkinter as tk

root = tk.Tk()

frame1 = tk.Frame(root)#这是上面的框架
frame2 = tk.Frame(root)#这是下面的框架


var = tk.StringVar()#储存文字的类
var.set("你在右边会看到一个图片，\n我在换个行")#设置文字

#创建一个标签类, [justify]:对齐方式，[frame]所属框架
textLabel = tk.Label(frame1,textvariable=var,
　　　　　　　　　justify = tk.LEFT)#显示文字内容 
textLabel.pack(side=tk.LEFT)#自动对齐,side：方位

 

#创建一个图片管理类
photo = tk.PhotoImage(file="18.png")#file：t图片路径
imgLabel = tk.Label(frame1,image=photo)#把图片整合到标签类中
imgLabel.pack(side=tk.RIGHT)#自动对齐


def callback():#触发的函数
　　var.set("你还真按了")#设置文字

#[frame]所属框架 ，text 文字内容 command：触发方法
theButton = tk.Button(frame2,text="我是下面的按钮",command=callback)
theButton.pack()#自动对齐

 

frame1.pack(padx=10,pady=10)#上框架对齐
frame2.pack(padx=10,pady=10)#下框架对齐


tk.mainloop()
```



### 4. 打开摄像头并显示

```python
  from tkinter import *
    import cv2
    from PIL import Image,ImageTk
    
    
    def take_snapshot():
        print("有人给你点赞啦！")
    
    def video_loop():
        success, img = camera.read()  # 从摄像头读取照片
        if success:
            cv2.waitKey(100)
            cv2image = cv2.cvtColor(img, cv2.COLOR_BGR2RGBA)#转换颜色从BGR到RGBA
            current_image = Image.fromarray(cv2image)#将图像转换成Image对象
            imgtk = ImageTk.PhotoImage(image=current_image)
            panel.imgtk1 = imgtk
            panel.config(image=imgtk)
            root.after(1, video_loop)
    
    camera = cv2.VideoCapture(0)    #摄像头
    
    root = Tk()
    root.title("opencv + tkinter")
    #root.protocol('WM_DELETE_WINDOW', detector)
    
    
    panel = Label(root)  # initialize image panel
    panel.pack(padx=10, pady=10)
    # root.config(cursor="arrow")
    btn = Button(root, text="点赞!", command=take_snapshot)
    btn.pack(fill="both", expand=True, padx=10, pady=10)
    
    video_loop()
    
    root.mainloop()
    # 当一切都完成后，关闭摄像头并释放所占资源
    camera.release()
    cv2.destroyAllWindows()

```



### 5. Tkinter 主题

Tkinter 允许你修改组件的外观和风格，以满足特定的设计需求。可以使用 `ttk.Style` 类来设置和修改组件的样式。

```python
style = ttk.Style()
style.theme_use("default")  # 设置主题

style.configure("TButton", background="blue", foreground="white")  # 修改按钮的样式
```



### 6. 国际化和本地化

#### 6.1. 多语言支持
Tkinter 提供了一些方法来支持多语言界面的开发。可以使用 `gettext` 模块来实现国际化（Internationalization）和本地化（Localization）。

```python
import gettext

# 创建一个 gettext 实例
_ = gettext.gettext

label_text = _("Hello, World!")  # 使用 _() 函数来获取翻译后的文本
```



#### 6.2. 文本编码

在处理不同语言的文本时，确保正确设置和处理文本的编码，以避免字符显示和处理的问题。

```python
text = "你好世界"
encoded_text = text.encode("utf-8")  # 编码为 UTF-8
decoded_text = encoded_text.decode("utf-8")  # 解码为 Unicode
```



## 八、Themed Tkinter拓展库

### 1. 优势

与标准Tkinter的`tkinter.ttk`模块相比，`ttk`提供了一些额外的功能和改进：

1. **主题化：** `ttk`小部件可以使用系统的窗口装饰和外观样式，使得你的应用程序看起来更具一致性，并且可以在不同平台上获得更好的外观。
2. **更多样式选项：** `ttk`小部件提供了更多样式的选项，可以自定义外观，例如按钮的样式、大小等。
3. **额外的小部件：** `ttk`提供了一些额外的小部件，比标准Tkinter提供的更丰富，例如进度条、树状视图等。
4. **更好的跨平台支持：** `ttk`小部件在不同的操作系统上表现更一致，这意味着你可以更轻松地编写跨平台的GUI应用程序。



### 2. 常用组件

| 组件              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| `ttk.Button`      | 触发特定操作或命令的按钮组件                                 |
| `ttk.Label`       | 显示文本或图像的标签组件                                     |
| `ttk.Entry`       | 允许用户输入文本的输入框组件                                 |
| `ttk.Checkbutton` | 允许用户选择或取消选择一个选项的复选框组件                   |
| `ttk.Radiobutton` | 一组中允许用户选择一个选项的单选按钮组件                     |
| `ttk.Notebook`    | 允许在多个选项卡页面之间切换的带有选项卡的组件               |
| `ttk.Progressbar` | 显示任务进度的进度条组件                                     |
| `ttk.Scale`       | 允许用户在一个范围内选择一个值的滑动条组件                   |
| `ttk.Panedwindow` | 允许用户调整多个子窗口大小的窗口分隔器组件                   |
| `ttk.Combobox`    | 允许用户从预定义选项中选择一个选项的下拉列表组件             |
| `ttk.Spinbox`     | 允许用户通过点击箭头按钮或直接输入来选择一个数值的旋转框组件 |
| `ttk.Treeview`    | 以树状结构显示层次数据的树状视图组件                         |
| `ttk.LabelFrame`  | 带有标题的框架组件，用于将其他小部件分组显示                 |
| `ttk.Separator`   | 在视觉上分隔其他小部件的分隔线组件                           |
| `ttk.Sizegrip`    | 用于调整窗口大小的小部件，通常用于窗口的角落                 |
| `ttk.Calendar`    | 允许用户选择日期的日历组件                                   |





## 附加

- 字体样式标准
  1. 标题字体：Arial Black、Impact、Helvetica Neue Bold 等
  2. 正文字体：Roboto、Helvetica Neue、Arial、Noto Sans、Open Sans 等
  3. 强调字体：Times New Roman、Georgia、Palatino Linotype、Noto Serif 等