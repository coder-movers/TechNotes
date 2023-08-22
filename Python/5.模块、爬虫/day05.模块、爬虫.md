## 学习目标

- 模块
- os模块
- math模块
- random模块
- json模块



## 一、模块

### 1. 介绍模块的概念和作用

#### 1.1. 什么是模块？
- 模块是包含Python代码的文件，用于组织、重用和封装代码。 
- 模块可以包含函数、类、变量和常量等。 
- 模块可以被其他程序导入和使用。



#### 1.2. 模块的作用

- 模块提供了一种组织和管理代码的方式，可以将相关功能封装到独立的模块中。
- 模块的使用可以提高代码的可维护性和可重用性。
- 模块可以促进团队合作和代码的分工。



#### 1.3. 模块的优点和用途

- 代码重用：可以将常用的功能封装到模块中，在多个项目中重复使用。
- 代码组织：可以将相关功能的代码组织到不同的模块中，提高代码的可读性和可维护性。
- 命名空间：模块提供了一个独立的命名空间，避免命名冲突。
- 扩展性：可以通过编写自定义模块扩展Python的功能。



### 2. 导入模块的方式和方法

#### 2.1. import语句的使用方法
使用`import`语句可以导入整个模块。例如：
```python
import math
```



#### 2.2. 使用import导入整个模块

使用`import`语句可以导入整个模块，并使用模块中的功能。例如：
```python
import math

print(math.pi)  # 输出圆周率π的值
```



#### 2.3. 使用from...import导入模块中的部分内容

使用`from...import`语句可以从模块中导入指定的部分内容。例如：
```python
from math import pi

print(pi)  # 输出圆周率π的值
```



#### 2.4. 给导入的模块指定别名

使用`import`语句可以给导入的模块指定别名。例如：
```python
import math as m

print(m.pi)  # 输出圆周率π的值
```



## 二、math模块

### 1. 数学常量

- pi：圆周率π的近似值，约为3.141592653589793。
- e：自然对数的底数e的近似值，约为2.718281828459045。

可以使用以下方式导入math模块并访问数学常量：

```python
import math

print(math.pi)  # 输出圆周率π的值
print(math.e)  # 输出自然对数的底数e的值
```



### 2. 数学运算函数

- 平方根：math.sqrt(x)
- 幂函数：math.pow(x, y)
- 绝对值：math.fabs(x)
- 向上取整：math.ceil(x)
- 向下取整：math.floor(x)
- 四舍五入：math.round(x)

示例代码：

```python
import math

x = 2.5
y = 3

# 计算平方根
sqrt_result = math.sqrt(x)
print(f"平方根: {sqrt_result}")

# 计算幂函数
pow_result = math.pow(x, y)
# pow_result = x ** y
print(f"{x}的{y}次幂: {pow_result}")

# 计算绝对值
fabs_result = math.fabs(-x)
print(f"绝对值: {fabs_result}")

# 向上取整
ceil_result = math.ceil(x)
print(f"向上取整: {ceil_result}")

# 向下取整
floor_result = math.floor(x)
print(f"向下取整: {floor_result}")

# 四舍五入 -- 内置函数
round_result = round(x)
print(f"四舍五入: {round_result}")
```



## 三、os模块

- os模块是Python提供的一个与操作系统交互的模块，可以进行文件和目录操作、执行系统命令等。
- os模块提供了丰富的功能，方便开发者进行操作系统相关的任务。
- 使用os模块可以实现跨平台的编程，因为它可以适应不同操作系统的特性。



### 1. 文件和目录操作函数

- #### 获取当前工作目录：`os.getcwd()`

```python
import os

current_dir = os.getcwd()
print(current_dir)  # 输出当前工作目录的路径
```



- #### 改变当前工作目录：`os.chdir(path)`

```python
import os

os.chdir('/path/to/new/directory')  # 改变当前工作目录
```



- #### 创建目录：`os.mkdir(path)`

```python
import os

os.mkdir('/path/to/new/directory')  # 创建新目录
```



- #### 递归创建目录：`os.makedirs(path)`

```python
import os

os.makedirs('/path/to/new/directory')  # 递归创建新目录
```



- #### 删除目录：`os.rmdir(path)`

```python
import os

os.rmdir('/path/to/directory')  # 删除目录
```



- #### 递归删除目录：`os.removedirs(path)`

```python
import os

os.removedirs('/path/to/directory')  # 递归删除目录
```



- #### 检查文件或目录是否存在：`os.path.exists(path)`

```python
import os

if os.path.exists('/path/to/file'):
    print('文件或目录存在')
else:
    print('文件或目录不存在')
```



- #### 文件和目录重命名：`os.rename(src, dst)`

```python
import os

os.rename('/path/to/old_file', '/path/to/new_file')  # 文件重命名
os.rename('/path/to/old_directory', '/path/to/new_directory')  # 目录重命名
```



### 2. 系统相关函数

- #### 获取操作系统平台：`os.name`

```python
import os

print(os.name)  # 输出操作系统平台的名称
```



- #### 获取环境变量：`os.environ`

```python
import os

env = os.environ
print(env)  # 输出环境变量的字典

```



## 四、random模块

- random模块是Python提供的用于生成随机数的模块。
- random模块提供了丰富的功能和方法，用于在程序中生成随机数、打乱数据顺序、进行随机选择等操作。
- random模块在随机数生成、模拟实验、密码生成、数据处理等领域具有广泛的应用。



### 1. 生成随机数和随机选择

- #### 生成随机整数：`random.randint(a, b)`

```python
import random

random_integer = random.randint(1, 10)
print(random_integer)  # 生成1到10之间的随机整数
```



- #### 生成随机浮点数：`random.random()`

```python
import random

random_float = random.random()
print(random_float)  # 生成0到1之间的随机浮点数
```



- #### 生成指定范围内的随机数：`random.uniform(a, b)`

```python
import random

random_number = random.uniform(0.5, 2.5)
print(random_number)  # 生成0.5到2.5之间的随机浮点数
```



- #### 从序列中随机选择一个元素：`random.choice(sequence)`

```python
import random

colors = ['red', 'green', 'blue']
random_color = random.choice(colors)
print(random_color)  # 从列表中随机选择一个颜色
```



### 2. 打乱和抽样数据

- #### 打乱列表顺序：`random.shuffle(list)`

```python
import random

numbers = [1, 2, 3, 4, 5]
random.shuffle(numbers)
print(numbers)  # 打乱列表中元素的顺序
```



- #### 从列表中随机抽取多个元素：`random.sample(list, k)`

```python
import random

numbers = [1, 2, 3, 4, 5]
random_sample = random.sample(numbers, 3)
print(random_sample) # 从列表中随机抽取3个元素
```



## 五、json模块

- json模块是Python提供的用于处理JSON数据的模块。
- JSON（JavaScript Object Notation）是一种轻量级的数据交换格式，常用于数据的序列化和传输。它采用键值对的形式来组织数据，具有易于阅读和编写的特点。
- json模块提供了一组方法，用于将Python对象转换为JSON格式的字符串，以及将JSON字符串转换为Python对象。
- json模块的优势在于它简单易用，支持广泛的数据类型，并且与其他编程语言的JSON库兼容。

### 1. JSON数据的序列化和反序列化

- #### 将Python对象转换为JSON字符串：`json.dumps(obj)`

| 参数名           | 描述                                                         | 默认值        |
| ---------------- | ------------------------------------------------------------ | ------------- |
| `indent`         | 缩进级别，用于指定每个级别的缩进空格数或字符串               | `None`        |
| `separators`     | 用于指定分隔符的字符，包括键值对之间的分隔符和项之间的分隔符 | `(',', ': ')` |
| `sort_keys`      | 是否按键进行排序输出                                         | `False`       |
| `skipkeys`       | 是否跳过非字符串键的字典项                                   | `False`       |
| `check_circular` | 是否检测循环引用                                             | `True`        |
| `ensure_ascii`   | 是否将非 ASCII 字符转义为 Unicode 转义序列                   | `True`        |

```python
import json

data = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

# 中文需要关闭`ensure_ascii`自动转义
json_str = json.dumps(data, ensure_ascii=False)
print(json_str)  # 将data转换为JSON字符串
```



- #### 将JSON字符串转换为Python对象：`json.loads(json_str)`

```python
import json

json_str = '{"name": "John", "age": 30, "city": "New York"}'

data = json.loads(json_str)
print(data)  # 将JSON字符串转换为Python对象
```



### 2. 读取和写入JSON文件

- #### 从JSON文件中读取数据：`json.load(file)`

```python
import json

with open("data.json") as file:
    data = json.load(file)
    print(data)  # 从JSON文件中读取数据并转换为Python对象
```



- #### 将数据写入JSON文件：`json.dump(obj, file)`

```python
import json

data = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

with open("data.json", "w") as file:
    json.dump(data, file, ensure_ascii=False)
    print("数据已写入JSON文件")  # 将数据写入JSON文件中
```



## 六、爬虫

### 1. 爬虫基础概念

1. 什么是爬虫以及其应用领域
   - 定义爬虫：爬虫是一种自动化程序，用于从互联网上收集和提取数据。
   - 爬虫的应用领域：搜索引擎索引、数据采集与分析、信息监测与抓取、网页内容提取等。

2. 爬虫的工作原理和流程
   - 工作原理：爬虫通过发送HTTP请求，获取网页内容，并解析提取所需数据。
   - 工作流程：发送请求、获取响应、解析网页、提取数据、存储数据。

3. 爬虫的法律和道德问题
   - 法律问题：爬虫应遵守相关法律法规，尊重网站的服务条款和Robots协议。
   - 道德问题：爬虫应遵循道德准则，不进行未经许可的恶意爬取，尊重网站的隐私权和版权。




### 2. HTTP基础

#### 2.1. 了解HTTP协议的基本概念

HTTP（Hypertext Transfer Protocol）是一种用于传输超文本的应用层协议。它定义了客户端和服务器之间进行通信的规则，使得在Web上的信息传输成为可能。以下是关于HTTP协议的基本概念：

- **HTTP的定义和作用**：HTTP是一种无状态的协议，它通过客户端和服务器之间的请求-响应模型来传输和交换数据。它的主要作用是在Web上传输超文本和相关资源，如网页、图像、音频、视频等。

- **HTTP的特点和发展历史**：HTTP具有以下特点：
  
  - 简单、灵活：HTTP的语法和操作相对简单，易于实现和使用。
  - 无状态：HTTP协议本身不会保留客户端和服务器之间的状态信息，每个请求-响应都是相互独立的。
  - 基于请求-响应模型：客户端发送请求，服务器返回响应，形成一次完整的交互过程。
- 可扩展：HTTP协议可以通过扩展头部字段和方法来满足不同的需求。
  
HTTP的发展历史经历了多个版本的演进，包括HTTP/0.9、HTTP/1.0、HTTP/1.1和HTTP/2等。每个版本都在性能、安全性和功能方面进行了改进和增强。
  
- **HTTP的应用场景和协议架构**：HTTP广泛应用于Web浏览器和Web服务器之间的通信，用于获取和传输网页、图像、文件等资源。它是Web应用的基础，也被用于Web服务、API接口等场景。HTTP的协议架构基于客户端-服务器模型，客户端发送请求到服务器，服务器根据请求返回响应。



#### 2.2. HTTP请求和响应的结构

HTTP请求和响应都具有特定的结构，分为请求和响应两部分。以下是它们的基本组成部分：

- **HTTP请求的结构**：
  - **请求行**：包含请求方法、请求的URL和HTTP协议版本。常见的请求方法有GET、POST、PUT、DELETE等。
  - **请求头**：包含关于请求的附加信息，如请求的头部字段（如User-Agent、Content-Type等）和值。
  - **请求体**：可选的，包含请求的数据，通常在POST请求中使用，如表单数据、JSON数据等。

- **HTTP响应的结构**：
  - **状态行**：包含响应的状态码和状态信息，用于表示请求的处理结果。常见的状态码有200（成功）、404（未找到）、500（服务器内部错误）等。
  - **响应头**：包含关于响应的附加信息，如响应的头部字段（如Content-Type、Content-Length等）和值
  - **响应体**：包含响应的数据，如网页内容、文件内容等。

通过请求行、请求头和请求体，客户端向服务器发送请求并传递相关信息。服务器接收到请求后进行处理，并返回相应的响应，包含状态行、响应头和响应体。



#### 2.3. 常见请求和响应码

- 常见的HTTP请求方法包括：
  - **GET**：用于请求获取资源，通过URL传递参数，请求的数据附加在URL上。
  - **POST**：用于提交数据，如表单数据、JSON数据等，数据包含在请求体中。
  - **PUT**：用于创建或更新资源，请求体中包含要创建或更新的数据。
  - **DELETE**：用于删除指定资源。



- 常见的HTTP响应状态码包括：

  - **200**：表示请求成功。

  - **201**：表示成功创建了新资源。
  - **204**：表示成功处理了请求，但没有返回任何内容。
  - **301**：表示请求的资源已永久移动到新的URL。
  - **302**：表示请求的资源暂时移动到新的URL。
  - **400**：表示客户端发送的请求存在语法错误。
  - **401**：表示请求需要身份验证。
  - **403**：表示服务器拒绝请求，权限不足。
  - **404**：表示请求的资源未找到。
  - **500**：表示服务器内部错误。
  - **502**：表示服务器作为网关或代理，从上游服务器接收到无效的响应。
  - **503**：表示服务器暂时不可用，通常是由于过载或维护。



### 3. requests

requests是一个流行的第三方库，用于发送HTTP请求和处理响应数据。它提供了简洁且易于使用的API，使得发送HTTP请求变得简单和方便。

使用requests发送HTTP请求的基本流程如下：

1. 安装requests库：使用pip命令进行安装，例如`pip install requests`。

2. 导入requests模块：在Python脚本中导入requests模块。

3. 发送GET或POST请求

   ```python
   requests.get/post(url,params,data,headers,timeout,verify,allow redirects,cookies)
   ```

   - `url`：要下载的目标网页的URL
   - `params`：字典形式，设置URL后面的参数，比如`?id=l23&name=xiaoming`
   - `data`：字典或者字符串，一般用于`POST`方法时提交数据
   - `headers`：设置`user-agent`、`refer`等请求头
   - `timeout`：超时时间，单位是秒
   - `verify`：`True/False`,是否进行`HTTPS`证书验证，默认是，需要自己设置证书地址
   - `allow_redirects`：`True/False`是否让`requests`做重定向处理，默认是
   - `cookies`：附带本地的`cookies`数据

4. 处理响应

   ```python
   r = requests.get/post(url)
   
   # 查看状态码，如果等于200代表请求成功
   r.status_code
   
   
   # 可以查看当前编码，以及变更编码
   # (重要！requests会根据Headers推测编码，推测不到则设置为IS0-8859-1可能导致乱码)
   r.encoding
   
   
   # 查看返回的网页内容
   r.text
   
   
   # 解析JSON响应
   response.json()
   
   
   # 查看返回的HTTP的headers
   r.headers
   
   
   # 查看实际访问的UR工
   r.url
   
   
   # 以字节的方式返回内容，比如用于下载图片
   r.content
   
   
   # 服务端要写入本地的cookies数据
   r.cookies
   ```
   
   

### 4. 代码示例

- 爬取搜狗搜索结果

  ```python
  import requests
  
  def craw_sougou():
      url = 'https:	//www.sogou.com/web'
  
      headers = {
          'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36'
      }
  
      kw = input('enter a word:')
  
      params = {
          'query': kw
      }
  
      response = requests.post(url, params=params, headers=headers)
  
      if response.status_code == 200:
          page_text = response.text
          print(page_text)
  
          with open(kw + '.html', 'w', encoding='utf-8')as f:
              f.write(page_text)
  
  
  craw_sougou()
  ```

  

- 爬取豆瓣电影评分前10

  ```python
  import requests
  import json
  
  
  def craw_douban():
      url = 'https://movie.douban.com/j/chart/top_list'
  
      headers = {
          'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36'
      }
  
      params = {
          'type': 24,
          'interval_id': '100:90',
          'action': '',
          'start': 0,
          'limit': 20
      }
  
      response = requests.get(url, params=params, headers=headers)
      print(response)
      if response.status_code == 200:
          page_json = response.json()
          print(page_json)
          with open('douban.json', 'w', encoding='utf-8')as f:
              json.dump(page_json, f, ensure_ascii=False)
  
  
  craw_douban()
  ```

  

   



