## 学习目标

- 元组
- 认识set集合
- set集合常用操作
- 认识字典
- 字典增删改查
- 字典嵌套和常用操作



## 一、元组

### 1. 什么是元组

- 元组是Python中的一种数据容器，用于存储多个元素的有序集合，可以存储不同类型的元素，如整数、浮点数、字符串等。
- 元组是**不可变的**，即一旦创建就不能修改元素的值。
- 元组使用小括号 () 来表示，元素之间使用逗号 , 分隔。



### 2. 元组的创建和初始化

使用小括号 () 创建空元组

```python
my_tuple = ()

my_tuple1 = (1, 2, 3)

my_tuple2 = 1, 2, 3
```

> **注意：**
>
> 当元组中只有一个值时：
>
> ```python
> # 需要如下申明，否则为字符串
> my_tuple = (1,)
> ```



### 3. 元组的访问和修改

- 使用索引访问元组中的元素，索引从0开始

  ```python
  my_tuple1 = (1, 2, 3)
  
  print(my_tuple[0])
  ```

- 元组的元素是**不可修改的**，如果尝试修改元组的元素会导致错误。

> **注意：**
>
> 当元组包含列表时，元组中的列表是可以被修改的，但这并不是因为元组存储的是内存地址。**元组中的每个元素都是直接存储的对象本身，而不是内存地址**。列表的可变性是由于列表本身的特性，与元组无关。



## 二、认识set集合

### 1. 什么是set集合

set集合是Python中的一种**无序**、**不重复**的数据容器。

> **注意：**
>
> 将数字添加到 set 集合中时，它们通常会以升序排列的方式进行输出。这是因为在 Python 中，整数和浮点数等数字类型具有默认的自然顺序，因此在 set 集合中进行迭代时，它们会按照升序排列。
>
> 但是这种顺序输出是在**大多数情况**下观察到的，但并**不是严格保证的**。在特定情况下，可能会出现不同的输出顺序，特别是当使用不同的 Python 解释器或版本时。



### 2. set集合的创建和初始化

```python
# 创建空集合
empty_set = set()

# 初始化一个非空集合
non_empty_set = {1, 2, 3}
```

> **注意：**
>
> set集合中不能加入列表和集合和字典。
>
> 因为集合的内部实现是基于哈希表，它对存储的元素进行哈希处理以提高访问和查找的效率。
>
> 集合中的元素必须是唯一的，集合使用元素的哈希值来确定唯一性。



### 3. set集合的特点和应用场景

- set集合中的元素**不重复**，重复元素会被**自动去除**，保证集合中的元素**唯一性**。
- set集合是**无序的**，元素的存储顺序不确定，**不能通过索引访问**。
- set集合具有高效的成员判断和集合运算操作，适用于需要对元素进行唯一性判断和集合运算的场景。



## 三、set集合常用操作

### 1. set集合的添加和删除元素

- 添加元素到set集合可以使用 `add()` 方法，将指定的元素添加到集合中。
- 删除set集合中的元素可以使用 `remove()` 方法，将指定的元素从集合中移除。

```python
my_set = {'aaa', 'bbb', 'cccc'}

# 添加元素
my_set.add('dd')

# 删除元素
my_set.remove('aaa')
```



### 2. set集合修改

因为set集合无序，无法通过索引访问元素，所以修改集合元素需要使用先删除后添加的办法。

```python
my_set = {'aaa', 'bbb', 'cccc'}

# 修改'bbb'为123
my_set.remove('bbb')
my_set.add(123)
```



### 3. set集合的交集、并集和差集操作

- 交集可以使用 `intersection()` 方法或者 `&` 运算符。

  交集就是指两个集合相同的元素

- 并集可以使用 `union()` 方法或者 `|` 运算符。

  并集就是指两个元素合并到一起的所有元素

- 差集可以使用 `difference()` 方法或者 `-` 运算符。

  差集就是指一个集合去除与另一个集合的公共元素后剩下的元素

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# 交集
intersection_set = set1.intersection(set2)

# 并集
union_set = set1.union(set2)

# 差集
difference_set = set1.difference(set2)
```



### 4. set集合的判断和比较

- 判断两个set集合是否相等可以使用 `==` 运算符。
- 判断一个set集合是否是另一个set集合的子集可以使用 `issubset()` 方法或者 `<=` 运算符。
- 判断一个set集合是否是另一个set集合的超集可以使用 `issuperset()` 方法或者 `>=` 运算符。

```python
set1 = {1, 2, 3}
set2 = {1, 2, 3, 4}

# 判断相等
is_equal = set1 == set2

# 判断子集
is_subset = set1.issubset(set2)

# 判断超集
is_superset = set2.issuperset(set1)
```



### 5. set集合的长度和判空

- 使用 `len()` 函数可以获取set集合的长度。
- 使用 `not` 关键字可以判断set集合是否为空集。

```python
my_set = {1, 2, 3}

# 获取长度
length = len(my_set)

# 判空
is_empty = not my_set
```



### 6. set集合遍历

```python
my_set = {'aaa', 'bbb', 'cccc'}
for item in my_set:
    print(item)
```



## 四、认识字典

### 1. 什么是字典

字典是Python中一种常用的数据结构，用于存储`键-值`对（key-value）。字典中的每个元素由一个**唯一的键**和对应的值组成。字典中的元素是**无序的**，可以根据键来访问和修改对应的值。



### 2. 字典的创建和初始化

字典可以通过花括号 `{}` 或者 `dict()` 函数进行创建。键和值之间使用冒号 `:` 进行分隔，每个键-值对之间使用逗号 `,` 分隔。

```python
# 创建字典
my_dict = {}
my_dict = {"name": "John", "age": 30, "city": "New York"}

# 使用dict()函数创建字典
my_dict = dict()
my_dict = dict(name="John", age=30, city="New York")
```



### 3. 字典的特点和应用场景

- 字典中的键必须是唯一的，不允许重复，但值可以重复。
- 字典中的键是不可变的，可以使用字符串、整数、元组等不可变类型作为键，但列表和字典等可变类型不能作为键。

字典适用于以下场景：

- 存储需要通过唯一键进行查找和访问的数据。
- 表示对象的属性和属性值。
- 统计和存储数据的频率、计数等信息。



## 五、字典增删改查

### 1. 字典元素的访问和修改

通过字典的键可以访问对应的值。使用方括号 `[ ]` 或者 `get()` 方法可以获取字典中的值。

```python
my_dict = {"name": "John", "age": 30, "city": "New York"}
# 访问字典元素①
print(my_dict["name"])  # 输出: John

# 访问字典元素②
print(my_dict.get("name"))

# 修改字典元素
my_dict["age"] = 31
print(my_dict)  # 输出: {"name": "John", "age": 31, "city": "New York"}
```

> **注意：**
>
> 访问字典元素使用key访问和使用get访问区别：
>
> 当访问不存在元素时，key访问直接报错，get访问返回`None`，可以用作判断条件
>
> ```python
> my_dict = {
>     1: "张三",
>     2: "李四",
>     3: "王五",
>     4: "赵六",
> }
> 
> name = input("请输入你要找的人的序号: ")
> val = my_dict.get(name)
> if val is None:
>     print("该序号无对应人员")
> else:
>     print(val)
> ```



### 2. 字典元素的添加和删除

```python
# 添加字典元素
my_dict = {"name": "John", "age": 30}
my_dict["city"] = "New York"
print(my_dict)  # 输出: {"name": "John", "age": 30, "city": "New York"}

# 删除字典元素①
my_dict.pop('age') # 常用
print(my_dict)  # 输出: {"name": "John", "city": "New York"}

# 删除字典元素②
del my_dict["age"]	# 不常用
print(my_dict)  # 输出: {"name": "John", "city": "New York"}
```



### 3. 字典的长度和判空

使用 `len()` 函数可以获取字典中键-值对的数量。通过判断字典是否为空可以确定字典是否包含元素。

```python
# 字典的长度
my_dict = {"name": "John", "age": 30, "city": "New York"}
print(len(my_dict))  # 输出: 3

# 判空
empty_dict = {}
if not empty_dict:
    print("字典为空")
```



### 4. 字典的遍历和查找

#### 4.1. 获取元素指定内容

```python
my_dict = {"name": "John", "age": 30, "city": "New York"}
```

- 获取字典元素所有键

  ```python
  print(list(my_dict.keys()))
  ```

- 获取字典元素所有值

  ```python
  print(list(my_dict.values()))
  ```

- 获取字典所有元素

  ```python
  print(list(my_dict.items()))
  ```



#### 4.2. 遍历字典

> **补充：**
>
> 解构是一种在编程中从复杂数据结构（如列表、元组、字典等）中提取数据并将其赋值给变量的技术。
>
> 解构赋值允许您将复杂的数据结构拆解为更小的部分，并将其赋值给单独的变量。这样可以方便地访问和操作数据，提高代码的可读性和简洁性。
>
> 1. 元组解构：
> ```python
> # 元组解构
> person = ('John', 30, 'New York')
> name, age, city = person
> print(name)  # 输出: John
> print(age)   # 输出: 30
> print(city)  # 输出: New York
> ```
>
> 2. 列表解构：
> ```python
> # 列表解构
> numbers = [1, 2, 3]
> a, b, c = numbers
> print(a)  # 输出: 1
> print(b)  # 输出: 2
> print(c)  # 输出: 3
> ```
>
> 3. 字典解构：
> ```python
> # 字典解构
> person = {'name': 'John', 'age': 30, 'city': 'New York'}
> name, age, city = person.values()
> print(name)  # 输出: John
> print(age)   # 输出: 30
> print(city)  # 输出: New York
> ```
>



- 遍历字典

```python
# 遍历字典的键
my_dict = {"name": "John", "age": 30, "city": "New York"}
for key in my_dict:
    print(key, my_dict[key])  # 输出: name, age, city
    
# 遍历以后解构
for item in my_dict.items():
    key, value = item 
    print(key)

# 遍历字典的键-值对
for key, value in my_dict.items():
    print(key, value)  # 输出: name John, age 30, city New York
```



#### 4.3. 查找字典是否包含指定键

```python
my_dict = {"name": "John", "age": 30, "city": "New York"}
if "age" in my_dict:
    print("找到了 age 键")
```



### 5. 字典循环删除

```python
my_dict = {
    "a1": "eeee",
    "bb": 123,
    "a2": "fff",
    "cc": "ggg"
}
temp = []  # 存放即将要删除的key
for key in my_dict:
    if key.startswith("a"):
        temp.append(key)
        # dic.pop(key)  # 报错：dictionary changed size during iteration

for t in temp:  # 循环列表, 删除字典中的内容
    my_dict.pop(t)

print(my_dict)
```



## 六、字典嵌套和常用操作

### 1. 字典的嵌套

```python
my_dict = {
    'name': '张三',
    'age': 20,
    'tel': 10086,
    'children': [
        {'name': '孩子1', 'age': 8},
        {'name': '孩子2', 'age': 10}
    ],
    'wife': {
        'name': '妻子',
        'age': 22,
        'phone': {
            'name': 'iphone',
            'tel': [10086, 10010]
        }
    }
}

print(my_dict['children'][0]['age'])

print(my_dict['wife']['phone']['tel'])
```



### 2. 字典的常见操作

```python
# 合并字典
dict1 = {"name": "John", "age": 30}
dict2 = {"city": "New York", "country": "USA"}
dict1.update(dict2)
print(dict1)  # 输出: {"name": "John", "age": 30, "city": "New York", "country": "USA"}

# 复制字典
original_dict = {"name": "John", "age": 30}
copied_dict = original_dict.copy()
print(copied_dict)  # 输出: {"name": "John", "age": 30}

# 清空字典
my_dict = {"name": "John", "age": 30}
my_dict.clear()
print(my_dict)  # 输出: {}
```
