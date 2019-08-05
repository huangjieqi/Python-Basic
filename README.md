# Python-Basic
Python基础学习

## Task1

### 1.1 环境搭建

- Anaconda环境配置

  Anaconda是Python的包管理器和环境管理器，可在清华镜像（https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/）上下载安装，速度比官方更快。由于之前在机器上已经安装并配置过了Anaconda3，环境配置过程在此省略。

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
  13. 逻辑运算符not` `and` `or`