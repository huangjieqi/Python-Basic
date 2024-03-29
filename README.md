Python-Basic

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

### 2.1 列表

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

### 2.2 元组

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

### 2.3 字符串

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

### 2.4 字符串格式化问题

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

## Task3

### 3.1 字典

1. 定义

   字典是一种可变容器模型，且可存储任意类型对象。字典的每个键值(key=>value)对用冒号`:`分割，每个对之间用逗号`,`分割，整个字典包括在花括号`{}`中。

2. 创建

   ```python
   dict1 = { 'abc': 456 }
   dict2 = { 'abc': 123, 98.6: 37 }
   ```

   ```
   123
   ```

3. 方法

   ```python
   dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
   print(len(dict))
   print(str(dict))
   print(dict.get('Name')) # 存在的返回键对应的值
   print(dict.get('Nam')) # 不存在的返回None
   print('Age' in dict) # Age存在，返回True
   for k, v in dict.items(): # (键, 值) 元组
       print(k, ':', v)
   for k in dict.keys(): # 键
       print(k)
   for v in dict.values(): # 值
       print(v)
   ```

   ```
   3
   {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
   Runoob
   None
   True
   Name : Runoob
   Age : 7
   Class : First
   Name
   Age
   Class
   Runoob
   7
   First
   ```

### 3.2 集合

1. 特性

   集合（set）是一个**无序**的**不重复元素**序列。

2. 创建

   可以使用大括号 `{}` 或者 `set()` 函数创建集合，**注意：创建一个空集合必须用 `set()` 而不是 `{ }`，因为 `{ }` 是用来创建一个空字典。**

3. 方法

   - 添加元素

     > s.add(x) 和 s.update(x)

     ```python
     thisset = set(("Google", "Tencent", "Taobao"))
     thisset.add("Facebook")
     print(thisset)
     
     thisset.update({1, 3}) # 参数可以是列表，元组，字典等
     print(thisset)
     thisset.update([1, 4], [5, 6]) 
     print(thisset)
     ```

     ```
     {'Facebook', 'Google', 'Tencent', 'Taobao'}
     {'Tencent', 1, 3, 'Google', 'Facebook', 'Taobao'}
     {1, 3, 4, 5, 6, 'Facebook', 'Taobao', 'Google', 'Tencent'}
     ```

   - 删除元素

     > s.remove(x) 和 s.discard(x)

     ```python
     thisset.remove("Taobao") # 不存在会发生错误
     print(thisset)
     
     thisset.discard("Alibaba") # 不存在不会发生错误
     print(thisset)
     ```

     ```
     {1, 3, 4, 5, 6, 'Facebook', 'Google', 'Tencent'}
     {1, 3, 4, 5, 6, 'Facebook', 'Google', 'Tencent'}
     ```

   - 计算集合元素个数

     > len(s)

     ```python
     print(len(thisset))
     ```

     ```
     8
     ```

   - 判断元素是否在集合中存在

     > x in s

     ```python
     print(1 in thisset)
     ```

     ```
     True
     ```

   - 清空集合

     > s.clear()

     ```python
     thisset.clear()
     print(thisset)
     ```

     ```
     set()
     ```

### 3.3 判断语句

Python 中 if 语句的一般形式如下所示：

```python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```

- 如果 "condition_1" 为 True 将执行 "statement_block_1" 块语句
- 如果 "condition_1" 为False，将判断 "condition_2"
- 如果"condition_2" 为 True 将执行 "statement_block_2" 块语句
- 如果 "condition_2" 为False，将执行"statement_block_3"块语句

注意：

- 每个条件后面要使用冒号` :`，表示接下来是满足条件后要执行的语句块。
- 使用缩进来划分语句块，相同缩进数的语句在一起组成一个语句块。
- 在Python中没有`switch – case`语句。

### 3.4 三目表达式

Python没有三目运算符`:`，但有类似的替代方案，如下：

> 为真时的结果 **if** 判定条件 **else** 为假时的结果

```python
x = 4
y = 99 if x > 3 else 999
print(y)
```

```
99
```

### 3.5 循环语句

- while

  一般形式：

  ```python
  while <conditions>：
      <statements>
  ```

  while - else 语句为在条件语句为 false 时执行 else 的语句块：

  ```python
  # while
  n = 100
   
  sum = 0
  counter = 1
  while counter <= n:
      sum = sum + counter
      counter += 1
   
  print("1 到 %d 之和为: %d" % (n, sum))
  
  # while - else 语句
  count = 0
  while count < 5:
     print(count, " 小于 5")
     count = count + 1
  else:
     print(count, " 大于或等于 5")
  ```

  ```
  1 到 100 之和为: 5050
  0  小于 5
  1  小于 5
  2  小于 5
  3  小于 5
  4  小于 5
  5  大于或等于 5
  ```

- for

  for循环可以遍历任何序列的项目，如一个列表或者一个字符串。一般形式如下：

  ```python
  for <variable> in <sequence>:
      <statements>
  else:
      <statements>
  ```

  ```python
  languages = ["C", "C++", "Perl", "Python"] 
  for x in languages:
      print(x)
  ```

  ```
  C
  C++
  Perl
  Python
  ```

  循环语句可以有 else 子句，它在穷尽列表(以for循环)或条件变为 false (以while循环)导致循环终止时被执行，但**循环被break终止时不执行**。

  ```python
  for i in range(0, 10, 2):
      print(i)
  else:
      print(i)
  ```

  ```
  0
  2
  4
  6
  8
  8
  ```

  ```python
  for i in range(0, 10, 2):
      print(i)
      if i >= 8:
          break
  else:
      print(i) # 不执行
  ```

  ```
  0
  2
  4
  6
  8
  ```

## Task4

### 4.1 函数关键字

函数代码块以`def`关键词开头，后接函数标识符名称和圆括号 `()`。

### 4.2 函数的定义

```python
def <name> (<args>):
    <expression>
```

- 匿名函数

  python 使用 **lambda** 来创建匿名函数。

  ```python
  lambda <args>: <expression>
  ```

  ```python
  sum = lambda arg1, arg2: arg1 + arg2
   
  print ("10 + 20 =", sum(10, 20))
  print ("20 + 20 =", sum(20, 20))
  ```

  ```
  10 + 20 = 30
  20 + 20 = 40
  ```

### 4.3 函数参数与作用域

- 参数

  1. 必需参数

     必需参数须以正确的顺序传入函数。调用时的数量必须和声明时的一样。

     ```python
     def printme(str):
        print(str)
        return
      
     # 调用 printme 函数，不加参数会报错
     printme()
     ```

     ```
     TypeError: printme() missing 1 required positional argument: 'str'
     ```

  2. 关键字参数

     函数调用使用关键字参数来确定传入的参数值。使用关键字参数允许函数调用时参数的顺序与声明时不一致。

     ```python
     def printinfo(name, age):
        print("名字:", name)
        print("年龄:", age)
        return
      
     printinfo(age=21, name="Crystal")
     ```

     ```
     名字: Crystal
     年龄: 21
     ```

     声明函数时，参数中星号 \* 可以单独出现。如果单独出现星号 \* 后的参数必须用关键字传入。

     ```python
     def f(a, b, *, c): # 星号*可以单独出现，单独出现星号*后的参数必须用关键字传入
         return a + b + c
     
     f(1, 2, 3)
     ```

     ```
     TypeError: f() takes 2 positional arguments but 3 were given
     ```

     ```python
     f(1, 2, c=3)
     ```

     ```
     6
     ```

  3. 默认参数

     调用函数时，如果没有传递参数，则会使用默认参数。

     ```python
     def printinfo(name, age=20):
        print("名字:", name)
        print("年龄:", age)
        return
      
     printinfo(age=21, name="Crystal")
     printinfo(name="Crystal") # age默认为20
     ```

     ```
     名字: Crystal
     年龄: 21
     名字: Crystal
     年龄: 20
     ```

  4. 不定长参数

     加了星号 \* 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。

     ```python
     def printinfo(arg1, *vartuple):
        print(arg1)
        for var in vartuple:
           print(var)
        return
      
     printinfo(10) # 可传入空的不定长参数
     printinfo(70, 60, 50)
     ```

     ```
     10
     70
     60
     50
     ```

     加了两个星号 \*\* 的参数会以字典(dict)的形式导入。

     ```python
     def printinfo(arg1, **vardict):
        print(arg1)
        print(vardict)
     
     printinfo(1, a=2, b=3, c=4)
     ```

     ```
     1
     {'a': 2, 'b': 3, 'c': 4}
     ```

- 作用域

  变量的作用域决定了在哪一部分程序可以访问哪个特定的变量名称。Python的作用域一共有4种。

  1. L （Local） 局部作用域
  2. E （Enclosing） 闭包函数外的函数中
  3. G （Global） 全局作用域
  4. B （Built-in） 内置作用域（内置函数所在模块的范围）

  以 L –> E –> G –>B 的规则查找，即：在局部找不到，便会去局部外的局部找（例如闭包），再找不到就会去全局找，再者去内置中找。

  ```python
  g_count = 0  # 全局作用域
  def outer():
      o_count = 1  # 闭包函数外的函数中
      def inner():
          i_count = 2  # 局部作用域
  ```

  Python 中只有模块（module），类（class）以及函数（def、lambda）才会引入新的作用域，其它的代码块（如 if/elif/else/、try/except、for/while等）是不会引入新的作用域的，也就是说这些语句内定义的变量，外部也可以访问。

  ```python
  if True:
      msg = 'I am from China'
  print(msg)
  ```

  ```
  I am from China
  ```

  如果将 msg 定义在函数中，则它就是局部变量，外部不能访问。

  ```python
  def test():
      msg_in_func = 'I am from China'
  print(msg_in_func)
  ```

  ```
  NameError: name 'msg_in_func' is not defined
  ```

- 全局变量和局部变量

  定义在函数内部的变量拥有一个局部作用域，定义在函数外的拥有全局作用域。局部变量只能在其被声明的函数内部访问，而全局变量可以在整个程序范围内访问。

  ```python
  total = 0 # 全局变量
  def sum(arg1, arg2):
      total = arg1 + arg2 # 局部变量
      print("函数内是局部变量:", total)
      return total
   
  sum(10, 20)
  print("函数外是全局变量:", total)
  ```

  ```
  函数内是局部变量: 30
  函数外是全局变量: 0
  ```

  使用global关键字可以在内部作用域中修改外部作用域的变量。

  ```python
  num = 1
  def fun1():
      global num
      print(num) 
      num = 123
      print(num) # 函数内
  fun1()
  print(num) # 函数外
  ```

  使用nonlocal关键字可以在嵌套作用域中修改外部变量。

  ```python
  def outer():
      num = 10
      def inner():
          nonlocal num
          num = 100
          print(num)
      inner()
      print(num)
  outer()
  ```

### 4.4 函数返回值

`return [表达式]` 结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回 None。

### 4.5 file

1. open()

   open() 方法用于打开一个文件，并返回文件对象，在对文件进行处理过程都需要使用到这个函数，如果该文件无法被打开，会抛出 OSError。使用 open() 方法一定要保证关闭文件对象，即调用 close() 方法。open() 函数常用形式是接收两个参数：文件名(file)和模式(mode)。

   ```python
   open(file, mode='r')
   ```

   mode参数有：

   | 模式 | 描述                                                         |
   | :--- | :----------------------------------------------------------- |
   | t    | 文本模式 (默认)。                                            |
   | x    | 写模式，新建一个文件，如果该文件已存在则会报错。             |
   | b    | 二进制模式。                                                 |
   | +    | 打开一个文件进行更新(可读可写)。                             |
   | r    | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。 |
   | rb   | 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。一般用于非文本文件如图片等。 |
   | r+   | 打开一个文件用于读写。文件指针将会放在文件的开头。           |
   | rb+  | 以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。一般用于非文本文件如图片等。 |
   | w    | 打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
   | wb   | 以二进制格式打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。 |
   | w+   | 打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
   | wb+  | 以二进制格式打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。 |
   | a    | 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
   | ab   | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
   | a+   | 打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。 |
   | ab+  | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。 |

2. file.close()

   关闭文件。

3. file.readline()

   读取整行，包括 "\n" 字符。

4. file.readlines()

   读取所有行并返回列表。

5. file.seek(offset[, whence])

   设置文件当前位置。

6. file.tell()

   返回文件当前位置。

7. file.write(str)

   将字符串写入文件，返回的是写入的字符长度。

### 4.6 os

1. os.chdir(path)

   改变当前工作目录到指定的路径。

2. os.getcwd()

   返回当前工作目录。

3. os.link(src, dst)

   创建硬链接，src为用于创建硬连接的源地址，dst为用于创建硬连接的目标地址。

4. os.mkdir(path[, mode])

   以数字权限模式创建目录。默认的模式为 0777 (八进制)。

5. os.open(file, flags[, mode])

   打开一个文件，并且设置需要的打开选项，模式参数mode参数是可选的，默认为 0777。

6. os.remove(path)

   删除指定路径的文件。如果指定的路径是一个目录，将抛出OSError。

7. os.rmdir(path)

   删除指定路径的目录。如果文件夹不为空，将抛出OSError。

8. os.path()

   获取文件的属性。

   - os.path.join(path1[, path2[, ...]])

     把目录和文件名合成一个路径

   - os.path.split(path)

     把路径分割成 dirname 和 basename，返回一个元组

   - os.path.abspath(path)

     返回绝对路径

   - os.path.basename(path)

     返回文件名

   - os.path.dirname(path)

     返回文件路径
   

## Task5

### 5.1 面向对象

- 类和实例

  类是抽象的模板，比如Student类，而实例是根据类创建出来的一个个具体的"对象"，每个对象都拥有相同的方法，但各自的数据可能不同。

  在类的内部，使用`def`关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self，且为第一个参数，self 代表的是类的实例。

  ```python
  class Student(object):
  
      def __init__(self, name, score): # 构造函数
          self.name = name # 参数定义
          self.score = score
  
      def print_score(self):
          print('%s: %s' % (self.name, self.score)) # 数据封装
          
  bart = Student('Bart Simpson', 59) # 实例化，传入参数
  lisa = Student('Lisa Simpson', 87)
  bart.print_score()
  lisa.print_score()
  ```

  ```
  Bart Simpson: 59
  Lisa Simpson: 87
  ```

- 访问限制

  在Python中，实例的变量名如果以`__`开头，就变成了一个私有变量（private），只有内部可以访问，外部不能访问。实例的方法名如果以`__`开头，就变成了一个私有方法。

  ```python
  class Student(object):
  
      def __init__(self, name, score):
          self.__name = name # 变量名以"__"开头的为私有变量
          self.__score = score
  
      def print_score(self):
          print('%s: %s' % (self.__name, self.__score))
          
      def get_name(self): # 使用get方法获取私有变量
          return self.__name
  
      def get_score(self):
          return self.__score
      
      def set_score(self, score): # 避免传入无效的参数
          if 0 <= score <= 100:
              self.__score = score
          else:
              raise ValueError('bad score')
              
      def __foo(self): # 私有方法
          print('这是私有方法')
              
  bart = Student('Bart Simpson', 59) # 实例化，传入参数
  bart.print_score()
  bart.set_score(60)
  bart.print_score()
  bart.__foo() # 直接调用私有方法
  ```

  ```
  Bart Simpson: 59
  Bart Simpson: 60
  AttributeError: 'Student' object has no attribute '__foo'
  ```

- 继承和多态

  当我们定义一个class的时候，可以从某个现有的class继承，新的class称为子类（Sub class），而被继承的class称为基类、父类或超类（Base class、Super class）。

  ```python
  class Animal(object): # 父类
      def run(self):
          print('Animal is running...')
          
  class Dog(Animal): # 子类
      def run(self):
          print('Dog is running...')
  
  class Cat(Animal): # 子类
      def run(self):
          print('Cat is running...')
          
  a = Animal()
  d = Dog()
  c = Cat()
  a.run()
  c.run()
  print(isinstance(a, Animal))
  print(isinstance(d, Animal))
  print(isinstance(d, Dog)) # d是Dog，也是Animal
  ```

  ```
  Animal is running...
  Cat is running...
  True
  True
  True
  ```

  任何依赖`Animal`作为参数的函数或者方法都可以不加修改地正常运行，原因就在于**多态**。多态的好处就是，当我们需要传入`Dog`、`Cat`时，我们只需要接收`Animal`类型就可以了，因为`Dog`、`Cat`都是`Animal`类型，然后按照`Animal`类型进行操作即可。由于`Animal`类型有`run()`方法，因此，传入的任意类型，只要是`Animal`类或者子类，就会自动调用实际类型的`run()`方法。

  ```python
  def run_twice(animal):
      animal.run()
      animal.run()
      
  run_twice(Animal())
  run_twice(Dog())
  ```

  ```
  Animal is running...
  Animal is running...
  Dog is running...
  Dog is running...
  ```

- 获取对象信息

  type()、isinstance()、dir()、hasattr()、setattr()、getattr()

  ```python
  class MyObject(object):
      def __init__(self):
          self.x = 9
      
      def __len__(self):
          return 100
      
      def power(self):
          return self.x * self.x
      
  obj = MyObject()
  dir(obj) # 获得一个对象的所有属性和方法
  print(len(obj))
  print(hasattr(obj, 'x')) # 判断是否有属性x
  print(hasattr(obj, 'power')) # 判断是否有方法power
  setattr(obj, 'x', 10) # 设置属性x
  print(getattr(obj, 'x')) # 获取属性x
  print(getattr(obj, 'z', 404)) # 获取属性z，如果不存在，返回默认值404
  ```

  ```
  100
  True
  True
  10
  404
  ```

- 实例属性和类属性

  当我们定义了一个类属性后，这个属性虽然归类所有，但类的所有实例都可以访问到。

  ```python
  class Student(object):
      count = 0
      
      def __init__(self, name):
          self.name = name
          Student.count += 1 # 每实例化一个学生，类属性count加一
          
  s = Student('Crystal')
  print(s.count)
  print(Student.count)
  s = Student('Curry')
  print(s.count)
  print(Student.count)
  ```

  ```
  1
  1
  2
  2
  ```

- 运算符重载

  我们可以对类的专有方法进行重载

  ```python
  class Vector:
     def __init__(self, a, b):
        self.a = a
        self.b = b
   
     def __str__(self):
        return 'Vector (%d, %d)' % (self.a, self.b)
     
     def __add__(self, other): # 类的专有方法
        return Vector(self.a + other.a, self.b + other.b)
   
  v1 = Vector(2, 10)
  v2 = Vector(5, -2)
  print(v1 + v2)
  ```

  ```
  Vector (7, 8)
  ```

### 5.2 正则表达式

正则表达式(Regular Expression)是一种文本模式，包括普通字符（例如，a 到 z 之间的字母）和特殊字符（称为"元字符"）。正则表达式使用单个字符串来描述、匹配一系列匹配某个句法规则的字符串。

- 精确匹配

  `\d`匹配一个数字，`\w`匹配一个字母或数字，`\s`匹配一个空格或Tab等空白符，`.`匹配任意字符

  例：`\w\w\d`可以匹配`py3`，`py.`可以匹配`py3`

- 变长匹配

  `*`表示0个以上字符，`+`表示1个以上字符，`?`表示0个或1个字符，`{n}`表示n个字符，`{n, m}`表示n ~ m个字符

  例：`\d{3, 8}`表示3 ~ 8个数字

- 使用[ ]

  `[0-9a-zA-Z\_]`可以匹配一个数字、字母或者下划线；`[0-9a-zA-Z\_]+`可以匹配至少由一个数字、字母或者下划线组成的字符串，比如`'a100'`，`'0_Z'`，`'Py3000'`等等；`[a-zA-Z\_][0-9a-zA-Z\_]*`可以匹配由字母或下划线开头，后接任意个由一个数字、字母或者下划线组成的字符串，也就是Python合法的变量；`[a-zA-Z\_][0-9a-zA-Z\_]{0, 19}`更精确地限制了变量的长度是1 ~ 20个字符（前面1个字符+后面最多19个字符）。

- 其他

  `A|B`可以匹配A或B，所以`(P|p)ython`可以匹配`'Python'`或者`'python'`。`^`表示行的开头，`^\d`表示必须以数字开头。`$`表示行的结束，`\d$`表示必须以数字结束。

### 5.3 re模块

由于Python的字符串本身也用`\`转义，推荐使用Python的`r`前缀，就不用考虑转义的问题了。

- 匹配

  `match()`方法判断是否匹配，如果匹配成功，返回一个`Match`对象，否则返回`None`。

  ```python
  print(re.match(r'^\d{3}\-\d{3,8}$', '010-12345')) # 匹配成功，返回Match对象
  print(re.match(r'^\d{3}\-\d{3,8}$', '010 12345')) # 匹配失败，返回None
  ```

  ```
  <re.Match object; span=(0, 9), match='010-12345'>
  None
  ```

- 切分字符串

  字符串的split()无法匹配连续的空格，用正则表达式切分字符串比用固定的字符更灵活。

  ```python
  'a b   c'.split(' ')
  ```

  ```
  ['a', 'b', '', '', 'c']
  ```

  ```python
  re.split(r'\s+', 'a b   c') # 以一个或多个空白符分割
  ```

  ```
  ['a', 'b', 'c']
  ```

  ```python
  re.split(r'[\s\,]+', 'a,b, c  d')
  ```

  ```
  ['a', 'b', 'c', 'd']
  ```

- 分组

  除了简单地判断是否匹配之外，正则表达式还有提取子串的强大功能。用`()`表示的就是要提取的分组（Group）。如果正则表达式中定义了组，就可以在`Match`对象上用`group()`方法提取出子串来。

  `group(0)`永远是原始字符串，`group(n)`(n>0)表示第n个子串。

  ```python
  m = re.match(r'^(\d{3})-(\d{3,8})$', '010-12345')
  print(m.group(0)) # 原始字符串
  print(m.group(1)) # 第一个子串
  print(m.group(2)) # 第二个子串
  ```

  ```
  010-12345
  010
  12345
  ```

  例：识别合法的时间

  ```python
  t = '19:05:30'
  m = re.match(r'^(0[0-9]|1[0-9]|2[0-3]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])$', t)
  print(m.groups())
  ```

  ```
  ('19', '05', '30')
  ```

- 贪婪匹配

  正则匹配默认是贪婪匹配，也就是匹配尽可能多的字符。

  ```python
  print(re.match(r'^(\d+)(0*)$', '102300').groups())
  ```

  ```
  ('102300', '')
  ```

  由于`\d+`采用贪婪匹配，直接把后面的`0`全部匹配了，结果`0*`只能匹配空字符串了。

  因此必须让`\d+`采用非贪婪匹配（也就是尽可能少匹配），才能把后面的`0`匹配出来，加个`?`就可以让`\d+`采用非贪婪匹配。

  ```python
  print(re.match(r'^(\d+?)(0*)$', '102300').groups())
  ```

  ```
  ('1023', '00')
  ```

- 编译

  如果一个正则表达式要重复使用几千次，出于效率的考虑，我们可以预编译该正则表达式，接下来重复使用时就不需要编译这个步骤了，直接匹配。

  ```python
  re_telephone = re.compile(r'^(\d{3})-(\d{3,8})$') # 编译
  re_telephone.match('010-12345').groups() # 使用
  ```

  ```
  ('010', '12345')
  ```

### 5.4 datetime

- 获取当前日期和时间

  ```python
  from datetime import datetime
  now = datetime.now()
  print(now)
  ```

  ```
  2019-08-13 16:00:51.950245
  ```

- 获取指定日期和时间

  ```python
  dt = datetime(2020, 9, 1, 0, 0) # 用指定日期时间创建datetime
  print(dt)
  ```

  ```
  2020-09-01 00:00:00
  ```

- datetime转换为timestamp

  ```python
  dt.timestamp()
  ```

  ```
  1598889600.0
  ```

- timestamp转换为datetime

  ```python
  t = 1598889600.0
  print(datetime.fromtimestamp(t)) # 本地时间
  print(datetime.utcfromtimestamp(t)) # UTC时间
  ```

  ```
  2020-09-01 00:00:00
  2020-08-31 16:00:00
  ```

- str转换为datetime

  ```python
  cday = datetime.strptime('2015-6-1 18:19:59', '%Y-%m-%d %H:%M:%S')
  print(cday)
  ```

  ```
  2015-06-01 18:19:59
  ```

- datetime转换为str

  ```python
  now = datetime.now()
  print(now.strftime('%Y-%m-%d %H:%M:%S'))
  ```

  ```
  2019-08-13 16:05:58
  ```

- datetime加减

  ```python
  from datetime import timedelta
  now = datetime.now()
  print(now + timedelta(hours=10)) # 加10个小时
  print(now - timedelta(days=1)) # 减1天
  print(now + timedelta(days=2, hours=12)) # 加2天12小时
  ```

  ```
  2019-08-14 02:07:37.616390
  2019-08-12 16:07:37.616390
  2019-08-16 04:07:37.616390
  ```

- 时区转换

  先通过`utcnow()`拿到当前的UTC时间，再转换为任意时区的时间。

  ```python
  utc_dt = datetime.utcnow().replace(tzinfo=timezone.utc)
  print(utc_dt)
  bj_dt = utc_dt.astimezone(timezone(timedelta(hours=8))) # astimezone()将转换时区为北京时间:
  print(bj_dt)
  ```

  ```
  2019-08-13 08:11:23.673090+00:00
  2019-08-13 16:11:23.673090+08:00
  ```

### 5.5 http请求

使用`urllib`发起http请求。

- 用urllib.request 里的urlopen()方法发送一个请求

  ```python
  import urllib.request
  response = urllib.request.urlopen("https://www.baidu.com")
  html = response.read()
  print(html) 
  ```

  ```
  b'<html>\r\n<head>\r\n\t<script>\r\n\t\tlocation.replace(location.href.replace("https://","http://"));\r\n\t</script>\r\n</head>\r\n<body>\r\n\t<noscript><meta http-equiv="refresh" content="0;url=http://www.baidu.com/"></noscript>\r\n</body>\r\n</html>'  
  ```

- 用urllib.request 里的Request()方法发送一个请求

  urlopen()不支持构造HTTP请求，不能给编写的请求添加head，无法模拟真实的浏览器发送请求。

  ```python
  import urllib.request
  request = urllib.request.Request("https://www.baidu.com")
  response = urllib.request.urlopen(request)
  html = response.read()
  print(html)
  ```

  ```
  b'<html>\r\n<head>\r\n\t<script>\r\n\t\tlocation.replace(location.href.replace("https://","http://"));\r\n\t</script>\r\n</head>\r\n<body>\r\n\t<noscript><meta http-equiv="refresh" content="0;url=http://www.baidu.com/"></noscript>\r\n</body>\r\n</html>'
  ```

## Task6

### 6.1 代码框架

1. 游戏初始化
2. 在shoot.png上按坐标截出飞机、子弹等的图片
3. 游戏主循环
   - 发射子弹
   - 生成敌机
   - 移动子弹、删除子弹
   - 移动敌机、删除敌机
   - 两机碰撞
   - 击中敌机
   - 绘制、显示
   - 处理键盘事件
   - 游戏结束、退出

### 6.2 类和函数

1. 子弹类

   继承自pygame.sprite.Sprite类，构造函数`__init__()`定义了子弹的图片、位置和速度，函数`move()`定义了子弹的移动方式。

   ```python
   class Bullet(pygame.sprite.Sprite):
       def __init__(self, bullet_img, init_pos):
           pygame.sprite.Sprite.__init__(self)
           self.image = bullet_img
           self.rect = self.image.get_rect()
           self.rect.midbottom = init_pos
           self.speed = 10
   
       def move(self):
           self.rect.top -= self.speed
   ```

2. 玩家类

   继承自pygame.sprite.Sprite类，构造函数`__init__()`中调用了父类的构造函数，定义了玩家的飞机的图片、位置、速度和是否被击中等基本属性，函数`shoot()`定义了发射子弹的方法，函数`moveUp()`、`moveDown()`、`moveLeft()`和`moveRight()`分别定义了向上、向下、向左、向右移动的方法。

   ```python
   class Player(pygame.sprite.Sprite):
       def __init__(self, plane_img, player_rect, init_pos):
           pygame.sprite.Sprite.__init__(self)
           self.image = []                                 # 用来存储玩家飞机图片的列表
           for i in range(len(player_rect)):
               self.image.append(plane_img.subsurface(player_rect[i]).convert_alpha())
           self.rect = player_rect[0]                      # 初始化图片所在的矩形
           self.rect.topleft = init_pos                    # 初始化矩形的左上角坐标
           self.speed = 8                                  # 初始化玩家飞机速度，这里是一个确定的值
           self.bullets = pygame.sprite.Group()            # 玩家飞机所发射的子弹的集合
           self.is_hit = False                             # 玩家是否被击中
   
       # 发射子弹
       def shoot(self, bullet_img):
           bullet = Bullet(bullet_img, self.rect.midtop)
           self.bullets.add(bullet)
   
       # 向上移动，需要判断边界
       def moveUp(self):
           if self.rect.top <= 0:
               self.rect.top = 0
           else:
               self.rect.top -= self.speed
   
       # 向下移动，需要判断边界
       def moveDown(self):
           if self.rect.top >= SCREEN_HEIGHT - self.rect.height:
               self.rect.top = SCREEN_HEIGHT - self.rect.height
           else:
               self.rect.top += self.speed
   
       # 向左移动，需要判断边界
       def moveLeft(self):
           if self.rect.left <= 0:
               self.rect.left = 0
           else:
               self.rect.left -= self.speed
   
       # 向右移动，需要判断边界
       def moveRight(self):
           if self.rect.left >= SCREEN_WIDTH - self.rect.width:
               self.rect.left = SCREEN_WIDTH - self.rect.width
           else:
               self.rect.left += self.speed
   ```

3. 敌机类

   继承自pygame.sprite.Sprite类，构造函数`__init__()`定义了敌机的图片、位置和速度等基本属性，函数`move()`定义了敌机移动的方法。

   ```python
   class Enemy(pygame.sprite.Sprite):
       def __init__(self, enemy_img, enemy_down_imgs, init_pos):
           pygame.sprite.Sprite.__init__(self)
           self.image = enemy_img
           self.rect = self.image.get_rect()
           self.rect.topleft = init_pos
           self.down_imgs = enemy_down_imgs
           self.speed = 2
   
       # 敌机移动，边界判断及删除在游戏主循环里处理
       def move(self):
           self.rect.top += self.speed
   ```

### 6.3 实验结果

![](https://github.com/Crysta1ovo/Python-Basic/raw/master/img/plane.png)