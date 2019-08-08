# Python-Basic
Python基础学习

## Task1

### 1.1 环境搭建

- Anaconda环境配置

  Anaconda是Python的包管理器和环境管理器，可在清华镜像 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/ 上下载安装，速度比官方更快。由于之前在机器上已经安装并配置过了Anaconda3，环境配置过程在此省略。

- 解释器

  Python存在着多种解释器

  1. CPython

     官方版本，使用C语言开发，使用最广

  2. IPython

     基于CPython之上，**交互式**

  3. PyPy

     动态编译，执行速度快，相同的Python代码分别在CPython和PyPy下执行可能会有不同的结果

  4. Jython

     运行在Java平台上，把Python代码编译成Java字节码执行

  5. IronPython

     运行在微软.Net平台上，把Python代码编译成.Net字节码执行

### 1.2 Python初体验

- print()

  ```python
  print('hello, world!')
  print('The quick brown fox', 'jumps over', 'the lazy dog') # 将多个字符串拼接起来输出
  print(100 + 200) # 打印计算结果
  print('100 + 200 =', 100 + 200)
  ```

  ```
  hello, world!
  The quick brown fox jumps over the lazy dog
  300
  100 + 200 = 300
  ```

- input()

  ```python
  name = input('please enter your name: ') # 自定义输入提示
  print('hello,', name)
  ```

  ```
  please enter your name: Crystal
  hello, Crystal
  ```

### 1.3 Python基础讲解

- 变量特性和命名规则

  ```python
  a = 123
  a = 'ABC' # 变量本身类型不固定
  print(a)
  ```

  ```
  ABC
  ```

  ```python
  a = 'ABC'
  b = a # 把变量b指向变量a所指向的数据
  a = 'XYZ' # 变量a的指向改为'XYZ'，但变量b并没有更改
  print(b)
  ```

  ```
  ABC
  ```

  变量名必须是大小写英文、数字和`_`的组合，且不能用数字开头

  Google 开源项目风格指南 https://zh-google-styleguide.readthedocs.io/en/latest/google-python-styleguide/contents/

- 注释方法

  ```python
  # 单行注释
  '''
  多行注释
  '''
  """
  多行注释
  """
  print("hello, world")
  ```

  ```
  hello, world
  ```

  ```python
  def a():
      '''这是文档字符串'''
      pass
  print(a.__doc__) # 输出函数的注释
  ```

  ```
  这是文档字符串
  ```

- ":"的作用

  Python采用代码缩进和冒号来区分代码之间的层次

  ```python
  def f(x):
      if x > 0:
          return True
      else:
          return False
  ```

- dir()

  `dir()`函数不带参数时，返回当前范围内的变量、方法和定义的类型列表；带参数时，返回参数的属性、方法列表

  ```python
  dir([ ]) # 查看列表的方法
  ```

  ```python
  ['__add__', '__class__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__iadd__', '__imul__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
  ```

- help()

  `help()`函数用于查看函数或模块用途的详细说明

  ```python
  a = [1, 2, 3]
  help(a)
  ```

  ```
  Help on list object:
  
  class list(object)
   |  list(iterable=(), /)
   ...
  ```

- import

  ```python
  import os # 导入包
  from math import pow # 从包中导入函数
  import numpy as np # 导入包并赋予别名
  from math import * # 导入包中所有内容
  ```

- pep8

  pep8是Python代码样式指南，旨在提高代码的可读性。在编辑器中可通过配置相应的插件从而实现对代码的自动化规范。但使用时也需要根据实际情况判断是否需要完全遵循该规范。

### 1.4 Python数值基本知识

- 数值类型

  1. 整数

     十进制：1，100， -8080， 0

     十六进制：0xff00

  2. 浮点数

     3.14，-9.01，1.23e9，1.2e-5

  3. 字符串

     ```python
     print('abc') # 单引号
     print("abc") # 双引号
     print("I'm OK") # 字符串内部包含单引号，可以用双引号括起来
     print('I\'m \"OK\"!') # 转义字符
     ```

     ```
     abc
     abc
     I'm OK
     I'm "OK"!
     ```

     ```python
     print('abc\ndef') # \n表示换行符
     print('abc\tdef') # \t表示制表符
     print('abc\\def') # \\表示\
     print('\\\t\\') 
     print(r'\\\t\\') # r''表示''内部的字符不转义
     print('''line1
     line2
     line3''') # 如果字符串内部有很多换行，可用'''...'''的格式表示多行内容
     ```

     ```
     abc
     def
     abc	def
     abc\def
     \	\
     \\\t\\
     line1
     line2
     line3
     ```

  4. 布尔值

     ```python
     print(3 > 2)
     print(3 > 5)
     print(5 > 3 and 3 > 1) # True and True
     print(5 > 3 or 1 > 3) # True or False
     print(not 1 > 2) # not False
     ```

     ```
     True
     False
     True
     True
     True
     ```

  5. 空值

     None

- 算术运算符

  ```python
  a = 2
  b = 3
  
  c = a + b
  print(c) # 2 + 3 = 5
   
  c = a - b
  print(c) # 2 - 3 = -1
   
  c = a * b
  print(c) # 2 * 3 = 6
   
  c = a / b
  print(c) # 2 / 3 = 0.666...
   
  c = a % b
  print(c) # 2 % 3 = 2
   
  c = a**b
  print(c) # 2^3 = 8
   
  c = a // b # 整除
  print(c) # 2 // 3 = 0 
  ```

  ```
  5
  -1
  6
  0.6666666666666666
  2
  8
  0
  ```

- 逻辑运算符

  ```python
  print(5 > 3 and 3 > 1) # True and True
  print(5 > 3 or 1 > 3) # True or False
  print(not 1 > 2) # not False
  ```

  ```
  True
  True
  True
  ```

- 成员运算符

  ```python
  a = 10
  b = 5
  list = [1, 2, 3, 4, 5]
  print(a in list)
  print(b in list)
  print(a not in list)
  ```

  ```
  False
  True
  True
  ```

- 身份运算符

  ```python
  '''身份运算符用于比较两个对象的存储单元'''
  
  a = 20
  b = 20
  
  print(id(a)) # a对象内存地址
  print(id(b)) # b对象内存地址
  print(a is b)
  print(a is not b)
   
  b = 30
  
  print(id(a)) # a对象内存地址
  print(id(b)) # b对象内存地址
  print(a is b)
  print(a is not b)
  ```

  ```
  140735794484640
  140735794484640
  True
  False
  140735794484640
  140735794484960
  False
  True
  ```

- 运算符优先级

  1. 指数`**`
  2. 按位反转`~`
  3. 乘`*`，除`/`，取模`%`，取整除`//`
  4. 加号`+`，减号`-`
  5. 右移`>>`，左移`<<`
  6. 按位与`&`
  7. 按位或`|`，按位非`^`
  8. 比较运算符`<=` `<` `>` `>=`
  9. 等于运算符`<>` `==` `!=`
  10. 赋值运算符`=` `%=` `+=` `-=` ...
  11. 身份运算符`is` `is not`
  12. 成员运算符`in` `not in`
  13. 逻辑运算符`not` `and` `or`
  

## Task2

### 1.1 列表

- 标志

  列表是一种有序的集合，可以随时添加和删除其中的元素。列表的标志为`[ ]`，列表中的元素用`,`分隔开。列表的数据项不需要具有相同的类型。

- 基本操作

  1. 创建

     创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。

     ```python
     list1 = ['physics', 'chemistry', 1997, 2000]
     list2 = [1, 2, 3, 4, 5]
     ```

  2. append()

     > list.append(obj)

     append() 方法用于在列表末尾添加新的对象。

     ```python
     list = [123, 'xyz', 'zara', 'abc']
     list.append(2009)
     print(list)
     ```

     ```
     [123, 'xyz', 'zara', 'abc', 2009]
     ```

  3. pop()

     > list.pop([index=-1])

     pop() 函数用于移除列表中的一个元素（默认最后一个元素），并且返回该元素的值。

     ```python
     list = ['Google', 'Runoob', 'Taobao']
     element = list.pop(1)
     print(list)
     print(element)
     list.pop()
     print(list)
     ```

     ```
     ['Google', 'Taobao']
     Runoob
     ['Google']
     ```

  4. del()

     可以使用 del 语句来删除列表的元素。

     > del list[index]

     ```python
     list = ['physics', 'chemistry', 1997, 2000]
     del list[2]
     print(list)
     ```

     ```
     ['physics', 'chemistry', 2000]
     ```

  5. 拷贝

     list1 = list0 表示 list1和 list0 指向同一个内存地址，只是名称不同。

     list2 ~ list6 则是指向不同的列表，原列表 list0 发生改变时，拷贝列表不变，但是里面元素本身的地址并没有改变，所以如果子元素为列表时，子元素列表在拷贝时地址并不会发生变化，所以**当原列表中子列表发生改变时，拷贝列表同样会发生改变**。

     list7 是深度拷贝，所以无论列表中嵌套了几层列表，拷贝列表都不会随着原列表的改变而改变。
     
     ```python
     import copy
     
     list0 = [[1, 2], 10, 20]
     list1 = list0  # 第1种
     list2 = list0[:]  # 第2种
     list3 = list(list0)  # 第3种
     list4 = list0*1  # 第4种
     list5 = copy.copy(list0)  # 第5种
     list6 = [x for x in list0]  # 第6种
     list7 = copy.deepcopy(list0)  # 第7种
      
     list0.append(30)
     list0[0].append(3)
      
     print('list0:', list0)
     print('list1:', list1)
     print('list2:', list2)
     print('list3:', list3)
     print('list4:', list4)
     print('list5:', list5)
     print('list6:', list6)
     print('list7:', list7)
     ```
     
     ```
     list0: [[1, 2, 3], 10, 20, 30]
     list1: [[1, 2, 3], 10, 20, 30]
     list2: [[1, 2, 3], 10, 20]
     list3: [[1, 2, 3], 10, 20]
     list4: [[1, 2, 3], 10, 20]
     list5: [[1, 2, 3], 10, 20]
     list6: [[1, 2, 3], 10, 20]
     list7: [[1, 2], 10, 20]
     ```

- 列表相关方法

  | 表达式                                | 结果                         | 描述                 |
  | ------------------------------------- | ---------------------------- | :------------------- |
  | len([1, 2, 3])                        | 3                            | 长度                 |
  | [1, 2, 3] + [4, 5, 6]                 | [1, 2, 3, 4, 5, 6]           | 组合                 |
  | ['Hi!'] * 4                           | ['Hi!', 'Hi!', 'Hi!', 'Hi!'] | 重复                 |
  | 3 in [1, 2, 3]                        | True                         | 元素是否存在于列表中 |
  | for x in [1, 2, 3]: print(x, end=" ") | 1 2 3                        | 迭代                 |

### 1.2 元组

- 标志

  Python 的元组与列表类似，不同之处在于元组的元素不能修改。元组使用小括号，列表使用方括号。

- 基本操作
  
  1. 创建
  
     元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。
  
     ```python
     tup1 = ('Google', 'Runoob', 1997, 2000)
     tup2 = "a", "b", "c", "d" # 可以不加括号
     tup3 = () # 空元组
     ```
  
  2. 不可变性
  
     元组中的元素值是不允许修改的。

### 1.3 字符串

- 定义
  
  字符串是 Python 中最常用的数据类型。我们可以使用引号( **'** 或 **"** )来创建字符串。
  
- 基本操作

  1. +

     字符串连接

     ```python
     var1 = 'Hello World!' 
     print(var1[:6] + 'Python!')
     ```

     ```
     Hello Python!
     ```
     
  2. *

     重复输出字符串

     ```python
     print(var1*2)
     ```

     ```
     Hello World!Hello World!
     ```

  3. 读取方式

     Python 访问子字符串，可以使用方括号来截取字符串。遵循**左闭右开**原则。

     ```python
     var2 = "Python"
     print ("var1[0]: ", var1[0])
     print ("var2[1:5]: ", var2[1:5])
     ```

     ```
     var1[0]:  H
     var2[1:5]:  ytho
     ```

- 字符串相关方法

  1. `len(string) `返回字符串长度
  2. `split(str="", num=string.count(str))`以 str 为分隔符截取字符串，如果 num 有指定值，则仅截取 num+1 个子字符串
  3. `startswith(substr, beg=0,end=len(string))`检查字符串是否是以指定子字符串 substr 开头，是则返回 True，否则返回 False。如果beg 和 end 指定值，则在指定范围内检查

### 1.4 字符串格式化问题

在 Python 中，字符串格式化使用与 C 中 sprintf 函数一样的语法。

```python
print ("我叫 %s 今年 %d 岁!" % ('小明', 10))
```

```
我叫 小明 今年 10 岁!
```

| 符号 | 描述                                 |
| ---- | ------------------------------------ |
| %c   | 格式化字符及其ASCII码                |
| %s   | 格式化字符串                         |
| %d   | 格式化整数                           |
| %f   | 格式化浮点数字，可指定小数点后的精度 |

