## 学习目标

- 认识数据容器
- 字符串索引和切片
- 字符串常用操作
- 字符串查找和判断
- 认识列表
- 列表增删改查
- 列表排序嵌套



## 一、认识数据容器

### 1. 什么是数据容器

​		数据容器是用于存储和组织数据的数据结构或对象。它们允许我们将一组相关数据元素集合在一起，并提供了访问、操作和管理这些数据的方法和功能。

```python
# 五个变量
name1 = '张三'
name2 = '李四'
name3 = '王五'
name4 = '赵六'
name5 = '孙七'

# 数据容器
name_list = ['张三', '李四', '王五', '赵六', '孙七']
```



### 2. 不同类型的数据容器

- 字符串（str）：字符串是由字符组成的不可变序列。它们用于表示文本和字符数据，并提供了丰富的字符串操作方法，如拼接、切片、格式化等。字符串适用于存储和处理文本信息。

- 列表（list）：列表是由一系列元素组成的有序可变序列。它们允许存储多个不同类型的数据元素，并提供了灵活的操作方法，如添加、删除、修改和访问。列表适用于需要存储和处理一组相关数据的情况。

- 元组（tuple）：元组是由一系列元素组成的有序不可变序列。与列表相比，元组的元素不可被修改，但可以进行访问和解包。元组适用于需要存储不可变数据或作为函数返回值的情况。

- 字典（dict）：字典是由键值对组成的无序可变集合。它们提供了高效的查找和访问方法，通过键来唯一标识和获取对应的值。字典适用于存储和检索具有关联关系的数据。

- 集合（set）：集合是由唯一元素组成的无序可变集合。它们提供了高效的集合运算和元素去重功能。集合适用于存储无序、唯一的元素，并进行集合操作，如并集、交集、差集等。



## 二、字符串索引和切片

### 1. 索引的概念和使用方法

索引是用于访问字符串中特定位置字符的方法。

在Python中，字符串的索引从0开始，即第一个字符的索引为0，第二个字符的索引为1，依此类推。可以使用方括号和索引值来访问字符串中的字符，例如：

```python
my_string = "Hello, World!"
print(my_string[0])  # 输出：H
print(my_string[7])  # 输出：W
```
负数索引表示从字符串末尾开始倒数，例如`-1`表示最后一个字符，`-2`表示倒数第二个字符，以此类推。



### 2. 切片的概念和使用方法

切片用于获取字符串中一部分字符的子串。可以使用冒号`:`来表示切片范围，切片操作会返回一个新的字符串。语法如下：
```python
my_string = "Hello, World!"
substring = my_string[start:end:step]
```
其中，`start`表示切片起始位置的索引（包含），`end`表示切片结束位置的索引（不包含），`step`表示切片步长（默认为1）。

例如，获取从索引1到索引5（不包含）的子串：
```python
my_string = "Hello, World!"
substring = my_string[1:5]
print(substring)  # 输出：ello
```

注意：

1. 步长的正负控制切片方向

   步长正数时切片从左至右，起始为负数也要从左至右，比如：`s[-3:-1]`

   ```python
   my_string = "Hello, World!"
   substring = my_string[-5:-1]
   print(substring)
   ```

   步长负数时切片从右往左，起始必须为负数

   ```python
   my_string = "Hello, World!"
   substring = my_string[::-1]
   print(substring)        # 输出：!dlroW ,olleH
   ```

   

2. 三个参数允许任意省略

   ```python
   my_string = "Hello, World!"
   substring = my_string[:5]
   print(substring)        # 输出：Hello
   
   substring = my_string[7:]
   print(substring)        # 输出：World!
   
   substring = my_string[::2]
   print(substring)        # 输出：Hlo ol!
   ```



## 三、字符串常用操作

字符串的操作一般不会对原字符串产生影响，一般是返回一个新的字符串。

### 1. 字符串的拼接

字符串的拼接是将多个字符串连接在一起形成一个新的字符串。在Python中，可以使用加号运算符（+）来实现字符串的拼接，例如：
```python
str1 = "Hello"
str2 = "World"
result = str1 + " " + str2
print(result)  # 输出：Hello World
```
另外，还可以使用字符串的join()方法来实现字符串的拼接，它接受一个可迭代对象作为参数，将其中的元素连接成一个字符串，例如：
```python
str_list = ["Hello", "World"]
result = " ".join(str_list)
print(result)  # 输出：Hello World
```



### 2. 字符串的重复

使用乘号运算符（*）来实现字符串的重复，例如：
```python
str1 = "Hello"
result = str1 * 3
print(result)  # 输出：HelloHelloHello
```



### 3. 字符串出现次数

统计字符串中某个字符串出现的次数

```python
my_string = "Hello, World!"
count = my_string.count("l")
print(count)  # 输出：3
```



### 4. 字符串的长度

```python
my_string = "Hello, World!"
length = len(my_string)
print(length)  # 输出：13
```



### 5. 字符串分割

```python
a = "python_java_c_c#_javascript"
lst = a.split("_")  # 切割之后的结果会放在列表当中
print(lst)
lst = a.split("_java_")
print(lst)
```



### 6. 字符串的大小写转换

#### 6.1. 首字母大写

- 将字符串第一个字符转为大写

  ```python
  s = "i have a dream!"
  s1 = s.capitalize()
  print(s1)
  ```

- 将字符串每个单词的第一个字符转为大写

  ```python
  s = "i have a dream!"
  s1 = s.title()
  print(s1)
  ```



#### 6.2. 字符串整体转换

```python
my_string = "Hello, World!"
uppercase = my_string.upper()	# 大写转换
lowercase = my_string.lower()	# 小写转换
print(uppercase)  # 输出：HELLO, WORLD!
print(lowercase)  # 输出：hello, world!
```



### 7. 字符串的替换和删除

#### 7.1. 字符串的替换

使用replace()方法：该方法将字符串中的指定子串替换为新的子串，并返回替换后的字符串。例如：

```python
my_string = "Hello, World!"
new_string = my_string.replace("World", "Python")
print(new_string)  # 输出：Hello, Python!

a = "hello i am a good man!"
a1 = a.replace(" ", "")  # 去掉所有的空格
print(a1)	# 输出：helloiamagoodman!
```



#### 7.2. 字符串的删除

使用strip()方法：该方法删除字符串开头和结尾处的指定字符（默认为空格），并返回删除后的字符串。例如：

```python
my_string = "   Hello, World!   "
new_string = my_string.strip()
print(new_string)  # 输出：Hello, World!

my_string = "\"Hello, World!\""
new_string = my_string.strip('\"')
print(new_string)  # 输出：Hello, World!
```



## 四、字符串查找和判断

### 1. 字符串的查找

字符串的查找和定位是指在字符串中查找指定的子串或字符，并确定其在字符串中的位置。在Python中，可以使用以下方法来实现字符串的查找和定位：

- 使用find()方法：该方法返回子串在字符串中第一次出现的索引，如果找不到则返回-1。例如：
  ```python
  my_string = "Hello, World!"
  index = my_string.find("World")
  print(index)  # 输出：7
  ```

- 使用index()方法：该方法返回子串在字符串中第一次出现的索引，如果找不到则抛出ValueError异常。例如：
  ```python
  my_string = "Hello, World!"
  index = my_string.index("World")
  print(index)  # 输出：7
  ```



### 2. 字符串的判断和比较

#### 2.1. 开头或结尾判断

- 使用`startswith()`方法和`endswith()`方法：`startswith()`方法用于判断字符串是否以指定子串开头，`endswith()`方法用于判断字符串是否以指定子串结尾。返回值为布尔类型（True或False）。例如：

  ```python
  my_string = "Hello, World!"
  starts_with_hello = my_string.startswith("Hello")
  ends_with_world = my_string.endswith("World")
  print(starts_with_hello)  # 输出：True
  print(ends_with_world)    # 输出：False
  ```

- 使用==运算符进行相等比较：==运算符用于判断两个字符串是否相等。返回值为布尔类型（True或False）。例如：

  ```python
  str1 = "Hello"
  str2 = "Hello"
  print(str1 == str2)  # 输出：True
  ```



#### 2.2. 包含判断

字符串的包含判断是指判断一个字符串是否包含另一个字符串。在Python中，可以使用in运算符来实现字符串的包含判断，返回值为布尔类型（True或False）。例如：

```python
my_string = "Hello, World!"
contains_hello = "Hello" in my_string
contains_python = "Python" not in my_string
print(contains_hello)   # 输出：True
print(contains_python) # 输出：True
```



#### 2.3. 整数判断

```python
money = input("请输入金额:")
if money.isdigit():  # 判断字符串是否是整数
    money = int(money)
    print("金额输入正确")
else:
    print("对不起,您输入有误....")
```



## 五、认识列表  

### 1. 什么是列表

列表是Python中一种常用的数据容器，用于存储一组**有序**的元素。列表中的元素可以是**不同类型**的数据，如整数、字符串、浮点数等。列表是可变的，可以进行增加、删除和修改等操作。



### 2. 列表的创建和初始化

在Python中，可以使用方括号`[]`来创建一个列表，并在方括号中用逗号分隔各个元素。例如：

```python
my_list = [1, 2, 3, 4, 5]
```



### 3. 列表的特点和用途

- 有序性：列表中的元素按照插入的顺序排列，可以通过索引访问和操作列表中的元素。
- 可变性：列表是可变的，可以通过增加、删除和修改等操作来改变列表中的元素。
- 存储异质数据：列表中的元素可以是不同类型的数据，如整数、字符串、浮点数等。
- 存储多个元素：列表可以存储多个元素，可以根据需要进行动态调整。



## 六、列表增删改查

### 1. 列表元素的访问和修改

可以使用索引来访问列表中的元素，索引从0开始，表示列表中元素的位置。例如：

```python
my_list = ['张三', '李四', '王五', '赵六', '孙七']
print(my_list[0])  # 输出：张三
print(my_list[2])  # 输出：赵六
```

列表中的元素是可变的，可以通过索引来修改列表中的元素。例如：

```python
my_list = [1, 2, 3, 4, 5]
my_list[2] = 10
print(my_list)  # 输出：[1, 2, 10, 4, 5]
```



### 2. 列表元素的添加和删除

可以使用以下方法来添加和删除列表中的元素：

- 使用append()方法添加元素到列表的末尾。例如：

  ```python
  my_list = [1, 2, 3]
  my_list.append(4)
  print(my_list)  # 输出：[1, 2, 3, 4]
  ```

- 使用insert()方法在指定位置插入元素。例如：

  ```python
  my_list = [1, 2, 3]
  my_list.insert(1, 4)
  print(my_list)  # 输出：[1, 4, 2, 3]
  ```

- 使用remove()方法删除指定元素。例如：

  参数为具体值，必须要有参数

  ```python
  my_list = [1, 2, 3, 4]
  my_list.remove(3)
  print(my_list)  # 输出：[1, 2, 4]
  ```

- 使用pop()方法删除指定位置的元素。

  参数为索引，如无参数，则默认删除列表最后一位
  
  例如：
  
  ```python
  my_list = [1, 2, 3, 4]
  my_list.pop(1)
  print(my_list)  # 输出：[1, 3, 4]
  
  my_list.pop()
  print(my_list)  # 输出：[1, 2, 3]
  ```



### 3. 列表的长度和判空

可以使用len()函数来获取列表的长度，即列表中元素的个数。例如：

```python
my_list = [1, 2, 3, 4, 5]
length = len(my_list)
print(length)  # 输出：5
```

可以使用not运算符来判断列表是否为空，如果列表为空则返回True，否则返回False。例如：

```python
my_list = []
is_empty = not my_list
print(is_empty)  # 输出：True
```



### 4. 列表的遍历和查找

可以使用for循环来遍历列表中的元素，并对每个元素进行相应的操作。例如：

```python
my_list = [1, 2, 3, 4, 5]
for item in my_list:
    print(item)
```

可以使用in运算符来查找列表中是否存在指定元素，如果存在则返回True，否则返回False。例如：

```python
my_list = [1, 2, 3, 4, 5]
is_present = 3 in my_list
print(is_present)  # 输出：True
```

以上是关于列表增删改查的操作示例，你可以根据具体的需求使用这些操作来处理列表中的元素，实现相应的功能。



### 5. 循环删除时遇到的问题

循环删除时相邻的两个元素删除应使用临时表删除

```python
lst = ['孙坚', '孙策', '周瑜', '孙权', '吕蒙', '黄盖']

temp = []  # 准备一个临时列表, 负责存储要删除的内容
for item in lst:
    if item.startswith("孙"):
        temp.append(item)  # 把要删除的内容记录下来
        # lst.remove(item)  # 有bug

for item in temp:
    lst.remove(item)  # 去原列表中进行删除操作
print(lst)
```



### 6. 练习列表操作

- 将所有孙姓改成刘姓

  ```python
  lst = ['孙坚', '孙策', '周瑜', '孙权', '吕蒙', '黄盖']
  
  # for item in lst:  # 此时, 我们看不到元素的索引位置
  for i in range(len(lst)):  # len(lst)列表的长度 ->  可以直接拿到列表索引的for循环
      item = lst[i]  # item依然是列表中的每一项
      if item.startswith("孙"):
          new_name = "刘"+item[1:]
          print(new_name)
          lst[i] = new_name  # 修改
  print(lst)
  ```



## 七、列表排序嵌套

### 1. 列表的排序方法

可以使用sort()方法对列表进行排序。sort()方法会直接修改原列表，将列表中的元素按照一定的规则进行排序。例如：

```python
my_list = [5, 2, 8, 1, 3]
my_list.sort()
print(my_list)  # 输出：[1, 2, 3, 5, 8]
```



### 2. 列表的升序和降序排列

sort()方法默认按照升序对列表进行排序，也可以通过传递参数reverse=True来实现降序排序。例如：

```python
my_list = [5, 2, 8, 1, 3]
my_list.sort(reverse=True)
print(my_list)  # 输出：[8, 5, 3, 2, 1]
```



### 3. 列表的嵌套和二维列表

列表可以包含其他列表作为其元素，形成嵌套列表或者二维列表。嵌套列表可以用于存储更复杂的数据结构，如矩阵、表格等。例如：

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(matrix[0])  # 输出：[1, 2, 3]
print(matrix[1][2])  # 输出：6
```



### 4. 列表的常见操作和应用示例

除了排序和嵌套，列表还有许多其他常见的操作和应用场景，例如：

- 列表的复制：

```python
# 使用切片操作复制列表
old_list = [1, 2, 3]
new_list = old_list[:]
print(new_list)  # Output: [1, 2, 3]

# 使用list()函数复制列表
old_list = [1, 2, 3]
new_list = list(old_list)
print(new_list)  # Output: [1, 2, 3]
```



- 列表的连接：

```python
# 使用加号运算符连接列表
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined_list = list1 + list2
print(combined_list)  # Output: [1, 2, 3, 4, 5, 6]

# 使用extend()方法连接列表
list1 = [1, 2, 3]
list2 = [4, 5, 6]
list1.extend(list2)
print(list1)  # Output: [1, 2, 3, 4, 5, 6]
```



- 列表的计数：

```python
my_list = [1, 2, 3, 2, 4, 2, 5]
count = my_list.count(2)
print(count)  # Output: 3
```



- 列表的切片：

```python
my_list = [1, 2, 3, 4, 5]
sub_list = my_list[1:4]
print(sub_list)  # Output: [2, 3, 4]
```



- 列表的去重：

```python
my_list = [1, 2, 3, 2, 4, 2, 5]
unique_list = list(set(my_list))
print(unique_list)  # Output: [1, 2, 3, 4, 5]
```



