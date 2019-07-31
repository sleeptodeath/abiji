[TOC]
### 01.计算机的基础知识
* 硬件软件
* 程序设计和编程语言
* 编码
    utf-8
    unicode 
        http://unicode-table.com
        一个码点（code point）
        使用16或32位的十六进制字面量
    gbk

* 进制
    * 正数和负数的二进制表示，符号位
    * 原码补码反码
    *   正数：原码 = 反码 = 补码
    *   负数：反码 = 符号位不变，其他位取反
              补码 = 反码+1
    * 进制转换
* 编译和解释 静态语言和脚本语言
* 互联网

* 模块化设计
* 计算思维： 抽象+自动化
* 自底向上和自顶下下

### 02.Python开发环境配置

#### 2.0 Python解释器

`种类` : CPython, IPython, Jython, PyPy

`退出`: exit()

`帮助`: help(modules)

#### 2.1 windows下python安装

1. https://www.python.org 下载最新版本,注意x64

2. 选择安装目录, 记得勾选 Add to path(添加到环境变量)

3. 如果第二步没选Add to path, 手动将python的目录添加到环境变量

4. 验证是否安装成功, 打开命令行,输入python

   

#### 2.2 Linux下python安装

默认安装了python，默认情况python是python2，可以用python3运行python3

`安装python3-pip`:sudo apt install python3-pip



#### 2.3 编译器推荐

PyCharme

VS Code 

Anaconda(开源免费, 科学计算)



### 03.Python编码规范

`官方规范PEB8` : https://python.org/dev/peps/pep-0008/

`Python之禅`: import this

`常见的格式规范`

* `缩进` ： 4个空格

* `行长`： 不超过80

* `命名规范`
  
```python
module_name, package_name, 
ClassName, ExceptionName, 
function_name, method_name,
GLOBAL_VAR_NAME, 
instance_var_name, function_parameter_name,local_var_name
```



### 04.Python的基本语法元素

#### 4.1 变量  

`特点`: 变量类型不固定

`变量命名` : 字母、数字和下划线, 区分大小写, 不能用关键字, 要见名知意

`注意` : **使用前必须先赋值**

`查看变量类型`: type()



#### 4.2 常量

`常量命名`: 通常用全部大写,下划线连接的变量名

`常见的常量`: PI, E



#### 4.3 关键字
~~~python
import keyword
print(keyword.kwlist)
#['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
~~~

#### 4.4 注释

`注释种类`

```python
# 1. 单行注释: #, 如 
print("hello") # This is a comment

# 2. 多行注释： 3引号,如
'''
author:
time:
version:
'''  

# 3.文档注释：
.__doc__
```

`与java区别`

Java中注释 : 单行注释 //, 多行注释 /* xx */



### 05.基本类型

通过 type(xx)  返回对象类型,用来编写代码检查所处理的类型
if type(L) == type([]) :

isinstance(value, class类型)  判断value 是否是class类型或者是它的子类

#### 5.1 整型  

`特点`: **无限制大小**， 4种进制

`转换函数`: int(x[,base]), int("100"),int(True),int(3.14)

`四种进制`:

|          |      |                                           |
| -------- | ---- | ----------------------------------------- |
| 十进制   |      | int('100', 2) int('77', 8) int('fff', 16) |
| 二进制   | 0b   | bin(231), bin(0xff), bin(0o77)            |
| 八进制   | 0o   | oct(231)                                  |
| 十六进制 | 0x   | hex(231)                                  |

#### 5.2 浮点型 

`原理` : 采用IEEE的浮点数表示, 可参考**CSAPP** 

`转换函数`: float(x), float(True), float(3),float("3.14")

`不精确性`:

```python
print(0.2 + 0.1)  # 0.30000000000000004
print(3 * 0.1)  # 0.30000000000000004

# 由于不精确性,不能用 == 比较相等,可以用四舍五入, 或者选择<1e-4之类判断
print(0.1 + 0.2 == 0.3)  # False
```

#### 5.3 复数

`基本形式`: a+bj 或者　complex(a, b)

* c = a+bj
* 实部：c.real   虚部：c.imag

`复数的数学库`:cmath

#### 5.4 bool类型

`二值`: True, False, **JAVA中true,false**

`False的等价`: Fasel, None, 0, {},[],(), "",

`转换函数`: bool()

`注意`：当参与算术运算时。True当做1，False当做0， JAVA不能

#### 5.4 类型转换

`自动类型转换`: 整数->浮点数->复数

`强制类型转换`:

int(x[,base]) , float(x) , complex()

#### 5.5 数值运算函数

* pow(a, b)

* abs(x) 
* divmod(a,b) ->(商,余数)
* max() ,min(), sum(iterable, start=0), 
* round(x[,d=0]) 取小数点后d为，默认为取整,四舍五入为指定的精度，正好为5时舍入到偶数

* math.sin()  math.cos()  math.tan()  用的是弧度
* math.hypot(), math.sqrt()
* math.ceil(), math.floor(),
* math.exp()  math.log(x[,base])

    

### 06.常用数据结构

`通用序列操作`: 索引,切片,序列相加,乘法,成员资格,长度,最大值和最小值

#### 4.1 字符串 str

`构成 `: 单引号''或者双引号""或者三引号""""""括起来

`特性`: **UTF-8, 不可修改, 不可变,操作后原字符没有变化**

`创建`:

```python
# 空串
s = '', "", ''''''

#单引号
s = 'hello'  
s = 'let\'s go'
s = '"hello"'

# 双引号
s = "hello world"
s = "\"hello"

#三引号 在HTML中较常用, 可保留换行和行首的空格等
s = """ xxx,
'xxx"xx"xx
xxxx"""
```

`转义字符`:

```python
# 包括: \t, \n, \", \', \\, \r, \b, \v
ord('\n') 	# 查看ASCII码值
chr(97) 	# 将ASCII码值转为byte
```

`类型转换`: str() 

```PYTHON
str(98.6)   # '98.6'
str(True)   # 'True'
```
`注意`: 字符串和数字的拼接,要先将数字str()

```PYTHON
print("hello" + 99)  # ERROR
print("hello" + str(99))  # 'hello99'
```

`运算符`:

```python
# len(str) 求字符串长度 
s = "hello"
print(len(s)) 	# 5 

# [x]索引下标为x, 从0开始,也可以从-1负向索引
s = "hello"
print(s[0]) # 'h'
print(s[-1]) # 'o'

# [start:end:step] 切片(不包括end)
s = "hello"
print(s[:])  # 'hello'
print(s[1:])  # 'ello'
print(s[:-1]) # 'hell', 不包括最后一个字符
print(s[::-1]) # 'olleh', 逆序

# + 连接 只能是两个字符串拼接,不能字符串和整型
print("hello" + "world")  # "helloworld"
print("hello" + 12)  # TypeError,可用str转化
print("hello" + str(12))  # "hello12"

# * 重复
s = "hello"
print(s*2)  # "hellohello"
 
# in, not in 判断是否是成员
permission = "rw",
print('w' in permission) # True
print('w' not in permission)  # False

# ==, !=, <, > 比较
print('abc' < 'abd')   # True
print('abc' == 'abc')  # True
print(abc' != 'abc')   # False
```

`常用方法`:(未完待续)

```python
# 大小写, upper(),lower(),title()
"abc".upper() # ABC   大写
"ABC".lower() # abc   小写
"hello world".title() # Hello World  每个单词首字母大写

# 去空格, strip([chars]), lstrip([chars]), rstrip([chars])
"  hello ".strip()   # 'hello' 	 ,去除左右两边的空白符,默认为空白符号
"  hello ".lstrip()  # 'hello '  ,去除左边的空白符,默认为空白符号
"  hello ".rstrip()  # '  hello' ,去除右边的空白符,默认为空白符号

# 合并和拆分 str.join(sequence), s.split([delim])
# str.split([delim]) -> list  将字符串分割成列表
"hello world".split()  # ['hello', 'world'] ,未指定分隔符,默认为空格，分割后为列表

# str.join(sequence)  将若干个字符子串合成大的字符串
print(','.join("1234"))   # '1,2,3,4'
print(','.join(['a','b','c'])) # 'a,b,c'

# 对齐 
ljust(width) 
rjust(width) 
# center(fillchar)
'abc'.center(5)  # ' abc '


# 查找 find(str,start=0, end=len(str)), index(str, start=0)
find(str, start=0)   # 返回offset或-1 
rfind()
index(str, start=0)  # 返回offset 或 ValueError
rindex()

# 计数      
count(sub) 返回子串sub出现的次数
   
# 以..开头和结尾  startswith(str), endswith(str)
# startswith(prefix[, start[, end]])
s = "http://www.baidu.com", 
s.startswith(("http", "https"))
# endswith(suffix[, start[, end]])|
   


# ctype,判断字母和数字
isalpha()
isdigit()
isalunum() 
isspace()
isupper()
islower()

# 替换 replace(old, new[, count=1])
replace(old，new[,count=1]) # 用new替换old的前count个默认全部,没有old什么都不做

# 编码和解码
encode()
"xx".encode(编码格式，xx)
'中国'.encode('utf-8') 
"lå, wørld!".encode("ASCII", "ignore")

decode()
bytes(string, encoding[, errors])|
```

`unicode编码` ;(未完待续)      

```PYTHON
unicode编码，
可变长编码: UTF-8
https://docs.python.org/3/howto/unicode.html 
http://unicode-table.com
unicode 一个码点（code point）
使用16或32位的十六进制字面量（分别加上前缀\u或\U）
"\u00C6"
中文范围：0x4e00-9fff
# -*-coding:utf-8 -*-
```

`字符串格式化`: (未完待续)

```PYTHON
1. %
# 常用: %s, %d, %f, %e等
# 同C的printf
# %[+,0,-]宽度.精度[s,f]

print("hello, %s" % 'world')
print("PI=%.3f" % 3.1415926)
print("%d%%" % 100)  # 100%
print("Hello, %s, My age is %d!" % ("everyone", 21))


2. .format()
 "{}".format()  
#.format格式
print("{name} {name[1]} ".format(name="abcd"))
print("{1} eggs, and {0}".format('span','SPAM'))
#填充-居中方式(^, <, >)-宽度  
print("{:*^20}".format("hello")) 
#精度-类型
print("{:.2f}".format(3.14))
# '#'对于二进制、八进制和十六进制转换，将加上一个前缀。
print("{:#b}".format(10))
#类型  整形 d, b, o, x/X 浮点型: f, e/E 字符型：c
print("{:d} {:b} {:X} {:o} {:.2f}  {:.2E}   {:c}"\
.format(20,  20, 20,  20,  3.14,  3.14,  97))
#      20  10100  14   24  3.140000 3.140000E+00  a
```

8. 原始字符串  r'',  R''  不会将转义字符当做一个字符看    
```PYTHON
# 例如要 打印 c:\nowhere 
print("c:\\nowhere")   # 因为\n是转义，所以要对\转义
print(r"c:\nowhere")   # 但是可以用r""

# 不能以单个反斜杠结尾
# 例如要打印 c:\program file\
print(r'c:\program file\') # SyntaxError: EOL while scanning string literal  
print(r'c:\program file' '\\')  # 可以这样
```

    9. 模式匹配（正则表达式） import re,   re.match()
​    10. 复制  1.[:]


#### 4.2 列表 [] list 
##### `特点`

可修改，可变大小，**可存储任意类型的集合**

##### `列表创建`

```PYTHON
# 1. []创建
list1 = ['username', 'pwd', [2018,9,5]]
# 2. 列表推导式
list2 = [x for x in range(5)] # [0,1,2,3,4]
# 3. list(iterator) 
li = list("cxk")  # ['c','x','k']
l = list(range(1,4)) # [1,2,3]  配合range函数,生成数字序列 
# 4. 先创建空列表[]. 然后再append添加
li = []
li.append(3)  # [3]
```

`运算符` 

```PYTHON
# len(li) 求长度
print(len([1,2,3]))  # 3

# li[x] 索引访问下标为x, 从0开始
li = ['a', 'b', 3, 4]
print(li[2]) # 3
	# 因可修改,比str多的
li[2] = 4	 # 修改

# [s:e:step]切片,可用于增删改
print(li[-3:])
print(li[:3])
print(li[::-1]) 	# 逆序
li1 = li[:]  		# 复制
	# 因可修改,比str多的
li[2:2] = [2,3,4] 	# 添加
li[2:3] = []		# 删除 
li[2:] = ['21',32]  # 修改

# + 连接
print([1,2,3] + [4,5,6]) #  [1,2,3,4,5,6]

# * 重复
print([1,2,3] * 2) # [1,2,3,1,2,3]
li = [None] * 5  # 
li2 = [0] * 10 # 

# in,n ot in 成员资格判断,判断是否在序列中

# ==, !=, <, >比较

# del 删除
li = [1,2,3]
del li[0] # li=[2,3]

# min,max,sum,只能用于数字同类型
li=[1,2,3]
min(li) 	# 1
max(li) 	# 3
sum(li)  	# 6 
```

##### `方法`

```PYTHON
# 1. 删除pop, remove, del, 切片

# 1.1 pop([index=-1]), 按下标删除并返回，默认是最后一个,空或out-of-range会返回IndexError
li1 = ['a', 'b', 'c']
li1.pop() 	# ['a', 'b']
li1.pop(0)	# ['b', 'c']
# 1.2 remove(value)  按值删除第一个出现的,没出现返回ValueEror
li1.remove('d')  # ValueError
li1.remove('a')  # ['b', 'c']
# 1.3 del li[index] del li[i:j] 按下标删除,越界IndexError
del li1[0]  # ['b', 'c']
# 1.4 切片 li[index1:index2] = []
li1[0:1] = []

# 2. 增加 append, insert, 切片, extend

# 2.1 append(value) 在尾部添加
li2 = ['a', 'b', 'c']
li2.append('d')  # ['a', 'b', 'c', 'd']
# 2.2 insert(index, value)  在index位置添加value, 当超过长度，默认在尾部插入
l12.insert(0, 'z') # ['z', 'a', 'b', 'c']
# 2.3 切片 li[index1:index2] = [xx]
li2[0:1] = ['z']  # ['z', 'a', 'b', 'c']
# 2.4 extend, += 
li2.extend(['d', 'e'])  # ['a', 'b', 'c', 'd', 'e']  <==> li2 += ['d', 'e']

# 3. 排序 sort,sorted
# sort(key=None, reverse=False) 会改变列表  同类型才能排序
li3 = [1, 4, 2, 3]
li3.sort()  # [1, 2, 3, 4]
li3.sort(reverse=True)  # [4, 3, 2, 1]
# sorted(iterator,key, reverse=False)->list 内置函数, 不会改变原来的
print(sorted(li3)) # [1,2,3,4]

# 4. 逆序 reverse, reversed
# reverse(), 倒序, 会改变列表
# reversed(sequence)->iterator 内置函数, 不会改变原来的

# 2.拷贝, copy, [:], list
.copy() -> list| 
li1 = [1,2,3]
li2=li.copy()  # 使用copy进行拷贝
li2 = li1[:]   # 使用分片进行拷贝
li2 = list(li1)  #　使用list函数进行拷贝

# 5. 查找
.index()   # 没有找到, ValueError

# 6. 计数 count(x) -> integer
li = [1,2,1,3,1]
li.count(1)	#  3
li.count(4) # 0

# 8.清空 clear()
li = [1,2,3]
li.clear() # li = [],  相当于 li[:] = [] 
```

##### `列表推导式`

形如: [expression `for` item `in` iterable `if` condition] 	

```PYTHON
# + range
li1 = [x for x in range(1, 10)]  # [1,2,3,4,5,6,7,8,9]

# if 判断
li2 = [x for x in range(1, 10) if x % 2 == 0]  # [2,4,6,8]

# 多值元组 (x1,x2..xn)
li3 = [(x, y) for x in range(10) for y in range(5)] 

# 多值列表
li4 = [[x, x + 1, x + 2] for x in range(10)]
```

`多维列表` 

```PYTHON
 li = [[1,2,3],[4,5,6],[7,8,9]] #三行三列
```

`栈` : LIFO , append(x), pop()  

`类型转换 list(sequence) 

```PYTHON
# 将字符串转为列表
list("cat") # ['c', 'a', 't']

# 将元组转为列表
list(('a','b','c'))  # ['a', 'b', 'c']
```

8. 深拷贝和浅拷贝    
    ```PYTHOn
    a=[1,2,3]
    b = a   #b和a指向同一个内存修改b也会修改a
    
    a=[1,2,3]
    b=a[:]  #b和a指向不同的列表，b时a的拷贝
    ```



#### 4.3 元组 () tuple 

##### `特点`: 

不可变的序列,任意类型，任意嵌套

##### `注意`: 

元组不能变，但元组里的可变容器可以变 

##### `创建`

```PYTHON
# 1. 使用()创建
t = ()  # 空元组
t= (1,)  # 只含一个元素的元组需要,

# 2.使用tuple()创建
t = tuple()  # 空元组
t = tuple('abc')  # ('a','b','c')

# 元组没有推导式
a = (num for num in range(1,6))  # 生成器推导式  type(a) == generotor
```

##### `元组解包`:

```PYTHON
t = ('a','b','c')
a,b,c = t  # 解包
```

##### `类型转换`: tuple()

```
t = tuple([1,2,3])  # (1,2,3)
t = tuple("abc")  # ('a','b','c')
```

##### `元组的用处`: 

- 用来做函数参数, 函数返回值
- 作为字典的键

##### `运算符`:  

```PYTHON
- len()求长度, 
- [x] 索引访问下标为x, 
- [s:e:step]切片, 
- + 连接 ,
- * 重复
- in ,not in 成员资格检查
- ==, !=
- min, max, sum
```

##### `方法`: 

```PYTHON
count(value) # value出现的次数 

index(value[,start[,stop]]) # value第一次出现的offset, 没有ValueError
```



#### 4.4 字典 {} dict   
##### `特点`: 

**可变类型**; key/value 的映射; **键唯一**,而值可不唯一; keyvalue称为项,存储是无顺序的

##### `键的类型`: 

任何**不可变**的类型，如整数，浮点数（实数）、字符串或元组。

##### `字典的优缺点`: 

空间换时间

查找和插入快,不会随key的增加而变慢(Hash),   占用大量内存,浪费空间

##### `创建`

```PYTHON
# 1. 通过{key1: value1,key2: value2}创建
D = {'food':'apple', 'price':10, 'color':'red'}

# 2. 先空字典{},在添加
D = {}
D['food'] = 'apple'

# 3. dict() 方法创建 将包含双值子序列的序列转换成字典
d = dict()  # 空字典
# 关键字参数
d = dict(name='Gumby', age=42)  # d = {'name':'Gumby', 'age': 42}

# 4. dict.fromkeys(seq, value=None]) 创建

# 5. 字典推导式
word = 'letter'
d = {letter: word.count(letter) for letter in word}
```

##### `类型转换`: dict()

```PYTHON
# 将包含双值子序列的序列转换成字典
dict(
 ([a,b])/  [(a,b)]/  ((a,b))/  [[a,b],[c,d]]/  ('ab')/  ['ab'])
 
items = [('name', 'xqy'), ('no', 123), ('age', 21)]
D = dict(items)  # D = {'name':'xqy', 'no':123, 'age': 21} 
```

##### `运算符`: 

```PYTHON
# 长度, len(d)->integer
d = {'A':65, 'B': 66}
print(len(d))  # 2

# 索引,添加和修改
d = {'name': 'xqy', 'age': 21}
d['name']  # 索引 'xqy'
d['sex'] = 'male'  # 不存在则添加
d['name'] = 'ypz'  # 存在则修改

# del d[key] 删除
del d['name']

# int, not in 成员资格判断
d = {'name': 'xqy', 'age': 21}
print('name' in d)   # True  == d.get('name')
print('name' not in d)  # False
```

##### `方法`:

```PYTHON
# 1.清除 clear
d = {'key': 'value'}
d.clear()  # d = {}

# 2. fromkeys(iterable, value=None)->dict
#　创建一个新字典，其中包含指定的键，且每个键对应的值都是None
d = dict.fromkeys(['name','age'])
print(d)  # {'name':None,'age':None}

# 3. get(key[,default=None]) -> D[key] if key in D, else default. 
d={'name': 'xqy', 'age': 21}
result = d.get('name', 'unknow')  # xqy
result = d.get('name@sss')  # None

# 4. keys()  -> dict_keys 迭代
for key in d.keys():
    print(key, d[key])

# 5. items() -> dict_items 迭代形式
for key,value in d.itmes():
    print(key, value)

# 6. values() -> dict_values 迭代形式
for value in d.values():
    print(value)

# 7.copy() 注意深拷贝,浅拷贝
x = {'username': 'admin', 'account': ['foo', 'bar', 'baz']}
y = x.copy()
y['username'] = 'mlh'
y['account'].remove('bar')

print(y) # {'username': 'mlh', 'machines': ['foo', 'baz']}
print(x) # {'username': 'admin', 'machines': ['foo', 'baz']}

# 删除 pop(k[,d])->v 
d = {'name':'xqy'}
d.pop('name')  # 'xqy'
d.pop('name1', 'none')  # none

# .popitem() -> (k, v) 
# remove and return some (key, value) pair as a 2-tuple; but raise KeyError if D is empty.

d = {'name':'xqy'}
k,v = d.popitem() # k='name', v='xyq'

# setdefault(k[,d]) 类似与get()返回默认值避免异常,但当键不存在时会在字典中添加
d = {'a': 1, 'b': 2}
print(d.get('c', 'none')) # 'none'
print(d.setdefault('c', '3')) # d={'a':1,'b':2,'c':3}

# update(dict１)->None   将dict1中的项添加到旧字典中，如果有相同的键会覆盖
first = {'a':1,'b':2}
second = {'b':3}
first.update(second)  # {'a':1,'b':3}
```



#### 4.5 集合 {} set  

##### `特点`: 

可变类型, 唯一的，无序，**只能包含不可变的元素(类似字典的键)**

##### `创建`:

```PYTHON
# {}创建
s = {}   # type(s) == dict  无法以这中方式创建空集合
s = {1,2,3,4}

# 2. set(iterator/dict/tuple.list/str)创建,用来去重
s = set()  # 空集合
s = set("abc") # s = {'a','b','c'}

# 3.集合推导式
s = {number for number in range(1,6) if number % 3 ==1} # {1,4}
```

##### `类型转换`: set(),用来去重

```
# 将字符串转换为集合
s = set("letter") # s = {'l','e','t','r'}

# 将列表转换为集合, 去重
# 将元组转换为集合, 去重
# 将字典转换为集合, 只有键被使用
```

##### `运算符`  

```PYTHON
# 1. len()求长度
len ({1,2,3})  # 3
# 2. < 子集 , > 父集, <=, >= 
{1} < {1,2}  # True
{1,2} > {1}  # True

# 3. & 取交集, | 取并集， - 取差集，^ 对称差, 
a = {1,2}
b = {2,3}
a & b # {2}
a | b  # {1,2,3}
a - b # {1}
a ^ b # {1,3}

#  in , not  成员资格测试
```

##### `方法`

```PYTHON
1. 删除 
remove(item) # 不存在keyError; 
discard() # 不报错, 
pop()
2. 添加 add(item)  
3. 交 x.intersection(y) &
   并 x.union()         |
   差 x.difference()    - 
   子集 issubset 		  <  
   父集 issuperset 	  >
4. 拷贝 copy()
5. 更新 x.update(set())
```



### 06.运算符

#### 6.1 算术运算符 

`包括`: +, -, *, /, //, %, **

`特有`: **(幂运算), 可用pow()代替

`优先级`: ** `>` *, /, //, % `>` +,-

`与Java中的区别`

|      | Python              | Java                |
| ---- | ------------------- | ------------------- |
| /    | 结果浮点数,3/2=1.5  | 整除,3/2=1          |
| %    | **向下圆整**,-5%2=1 | **向0取整**,-5%2=-1 |
| //   | 整除, 3 // 2 = 1    |                     |

#### 6.2 关系运算符  

< > <= >= == !=

#### 6.3 逻辑运算符 

and, or, not

`注意`: and,or的**短路逻辑**

#### 6.4 位运算符  

& , |, ^,  ~, <<, >>

#### 6.5 赋值运算符 

= += -= *= /=

#### 6.6 isinstance(value, class类型)  

判断value 是否是class类型或者是它的子类

#### 6.7 成员运算符

in, not in

#### 6.8 身份运算符: 

is, is not

`同==区别`: ==判断等,is判断id(x)==id(y)

#### 6.9 if运算符 

a if condition else b

#### 6.10 优先级：

|||
| --- | --- |
|**|指数|
|+, -,  ~|一元加减号,位取反|
|*, /, //, % |乘除法|
|+, -|加减法 |
|<<, >>|移位运算|
|&, ^,\| | |
|<,>,>=,<=,==,!=|关系运算符 |
|=,+=,/=|赋值运算符|
|is, is not| 身份运算|
|in, not in| 成员运算|
|and or | 逻辑运算|
|lambda |lambda表达式 |

`注意`:

1. is和==的区别
    * a is b <=> id(a) == id(b) 判断内存相等
    * a == b   判断值相等

### 07.输入输出
#### 输入 input,命令行参数 
##### input
* input(promt)，返回`字符串类型`
* 等价于python2中的raw_input
* 可以用类型转化，转为其他类型（如:int(input())) 
```PYTHON
    x = input("Input a int:")  
    x = int(input("Input a int"))
```
##### 命令行参数
* import sys;
    sys.argv  ['test.py', xxx, xxx]
* import 

#### 输出 print
`函数原型`: print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)

1. f''字符串形式

   ```PYTHON
   class A:
   	i = 4
   
   a = A()
   print(f"{a.i}")  # 4
   li = [1,2,3,4]
   print(f"{li[2]}") # 3
   ```

   

2. format 字符串格式输出

`形式`: "{}".format()

```PYTHON
# 位置填充
print("{}, {} and {}".format("first", "second", "third"))
print("{3} {0} {2} {1} {3} {0}".format("be", "not", "or", "to"))

# key来填充
print("{name} is approximately {value:.2f}.".format(value=pi, name="π"))

# 通过列表来填充
fullname = ["Alfred", "Smoketoomuch"]
print("Mr {name[1]}".format(name=fullname)) # 'Mr Smoketoomuch'

# 可使用索引，还可使用句点表示法来访问导入的模块中的方法、属性、变量和函数

# 格式转化
print("{:.2f}".format(3.1415926))
```
2. "%s" %()
| | |
| -- | -- |
|%c | 字符 |
|%s	|通过str() 字符串转换来格式化|
|%i	|有符号十进制整数|
|%d	|有符号十进制整数|
|%u	|无符号十进制整数|
|%o	|八进制整数|
|%x	|十六进制整数（小写字母）|
|%X	|十六进制整数（大写字母）|
|%e	|索引符号（小写'e'）|
|%E	|索引符号（大写“E”）|
|%f	|浮点实数|
|%g	|％f和％e 的简写|
|%G	|％f和％E的简写|


### 08.控制语句
#### 赋值语句
```PYTHON
# 多个变量同时赋值:   序列解包
x1,x2,x3 = y1,y2,y3
x,y = 3,4,5 # ERROR 左右两边数量要相等

    # 交换两个变量:
    x,y=3,4
    x, y = y, x
    print(x,y)  # 4, 3

# 链式赋值
x = y = 2

# *号：
a, b, *rest = [1, 2, 3, 4] # a:1,b:2,rest:[3,4]

# 增量赋值； +=，/=, //=
```

#### 分支语句 

`分支语句的基本格式`:

```PYTHON
if condition_1:
    #语句
	if condition_11:
		#语句
	else:
		#语句
elif condition_2:
	#语句
else:
	#语句
```

`等价于False`: False,None, 0, "", (),[],{},其余都为真

`判断条件`:

```PYTHON
# >, <, ==, !=, <=, >=
if a > 10:
    print("ok")
    
# and, or
if (number > 0) and (number < 10):
    print("ok")
 
if (number < 0) or (number > 10):
    print("ok")
   
# in, not in
if user in admit:  #检查是否再列表内 
	print("ok")

if user not int admit:
	print('error')
```
#### 循环语句 
* for-in,  else,
  
    `可迭代对象`: 元组,字符串,列表,字典,文件,
    
    ```PYTHON
    # 返回迭代对象, 遍历数字,range(start,end[,step]), 包括[start,end)
    for i in range(10): # 0-9
        print(i)
        
    for i in range(2, 10, 2):  # 2, 4, 6, 8
        print(i)
        
    # 字符串遍历
    for c in "fdas":   
        print(c)
        
    # 列表遍历
    for l in ['b', 'a', 'c']:
        print(l)
        
    # 文件遍历    
    for line in f:  
        print(line)
    
    # 内置函数
    for i, v in enumerate(iterator[,start=0]):  # 给每个元素+数字下表
        print(i, v)
    
    # zip() 返回迭代对象, 对多个序列进行并行迭代,迭代次数等于最短长度
    for x, y,z in zip(li1,li2,li3): 
        print(x, y, z)
        
    for i in sorted():
        print(i)
    for i in reversed():
        print(i)
    ```
    
* while 
    ```PYTHON
    while condition:
       # statement
    else:  # 正常结束(没有break跳出)
       # statement 
    ```

* break， continue

* pass  空语句,相当于占位

### 09.函数 
##### `函数定义`

```PYTHON
def 函数名(参数列表): 
	'''函数文档 调用help(函数名) 显示'''  
	函数体 
	[return 返回值]
```

`变量作用域`

    L(ocal) - > E(nclosing) -> G(lobal) -> B(uilt-in)
    locals()   局部变量
    globals()  全局变量

`局部变量和全局变量`: global

    * 在函数外边定义的变量叫做全局变量
    * 全局变量能够在所有的函数中进行访问
    * 如果在函数中修改全局变量，那么就需要使用global进行声明，否则出错
    * 如果全局变量的名字和局部变量的名字相同，那么使用的是局部变量的，小技巧强龙不压地头蛇

#### 参数传递 

* 传引用
* 可传递任意参数, 甚至是函数
  * def fun(func, a, b): func(a,b)
  * def add(a,b): print(a+b)
  * def sub(a,b): print(a-b)
  * fun(add, 4, 5)
* 不可变类型   不会改变 
* 可变类型    可能会被改变,如果不想改变传递副本（copy) 

##### `关键字参数`: 

作用: 将名称和值关联起来，而**无需考虑参数顺序**

`同相比JAVA`: JAVA不支持

```PYTHON
def describe_pet(animal_type, pet_name):
    """print pet's information"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
    
# 将名称和值关联起来，而无需考虑参数顺序
describe_pet(pet_name='willie', animal_type='dog')

```

##### `默认参数`: 

`同相比JAVA`: JAVA不支持

`注意`: 默认参数只能放再最右边

```PYTHON
def describe_pet(pet_name, animal_type='dog'):
    """print pet's information"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet('willie')  #aninmal_type用默认参数
describe_pet('willie', 'hamster')   #为aninmal_type显示提供参数
```

##### `不定长参数`:
* *arg  元组, **kwargs 字典
```PYTHON
def test(a,b,c=33,*args,**kwargs):#在定义的时候 *,**用来表示后面的变量有特殊功能
	print(a)
	print(b)
	print(c)
	print(args)
	print(kwargs)
    
#test(11,22,33,44,55,66,77,task=99,done=89)
A = (44,55,66)
B = {"name":"laowang","age":18}
    
test(11,22,33,*A,**B) #在实参中*,**表示对元祖/字典进行拆包
```

#### 返回值 

可返回各种类型

* return \[a,[b]]
    * 无返回值 None
    * 一个
    * 多个（返回元组）
* 可返回任意类型
    * 例如列表，字典,函数等
    

#### 匿名函数(lambda函数)
`基本格式`: lambda 参数 ： 表达式

`特点`: 

1.一行表达式,有返回值 2.不能有return 3.可以没有参数,也可以有多个参数

`应用:`

1. 与filter结合使用,作为函数参数

   ```PYTHON
   # 返回列表中大于3的元素
   # 一般实现
   li1 = [1,2,3,4,5,6,7]
   li2 = []
   for i in li1:
   	if i > 3:
   	li2.append(i)
   	
   # filter+lambda实现
   li2 = [item for item in filter(lambda x:x>3, li1)]
   ```

2. 自定义函数

```PYTHON
    def fun(a, b, opt):
        return opt(a, b)
    print(fun(1,2, lambda x, y :x + y))
    print(fun(1,2, lambda x, y :x - y))
    print(fun(1,2, lambda x, y :x * y))
```

3. 作为sort等内置函数参数

```PYTHON
    stus = [
        {"name":"zhangsan", "age":18}, 
        {"name":"lisi", "age":19}, 
        {"name":"wangwu", "age":17}
    ]
    stu.sort(key = lambda x:x
    ['name']))
    stu.sort(key = lambda x: x['age'])
```

#### 递归函数

`注意`: 递归过深,会导致**栈溢出** (RecursionError)

`包括`: 1.基例  2.链条

```PYTHON
#汉诺塔
cnt = 1
def hanoi(n, src, dest, vi):
	global cnt  #引用全局函数
	if n == 1:  #基例
		print("{}:{} -> {}".format(cnt, src, dest))
		cnt += 1
	else: # 链条
		hanoi(n-1, src, vi, dest) 
         print("{}:{} -> {}".format(cnt, src, dest))
         cnt += 1
         hanoi(n-1, vi, dest, src)
#调用
hanoi(3, 'a', 'b', 'c')
print("共用了{}次".format(cnt))
```

#### 内置函数
```PYTHON
# 
sorted(iterable, key=None, reverse=False)->list 
key:比较函数
reversed：是否逆序

sorted('Python')->['P', 'h', 'n', 'o', 't', 'y']

# reversed(sequence)->iterator  # 逆置
# min()
# max()
# sum()
# pow()
# round()|
# abs()
# divmod()
# zip() 

map() 返回迭代器， map函数会根据提供的函数对指定序列做映射，
map(function, sequence[, sequence, ...]) 
map(lambda x:x**2, [1,2,3])

id() 获得地址,判断是否为同一个引用

filter() 指定序列执行过滤操作, 返回迭代器
filter(function or None, sequence) -> filter
filter(lambda x:x % 2, range(10))

reduce
在Python3里,reduce函数已经被从全局名字空间里移除了, 它现在被放置在fucntools模块里用的话要先引入： from functools import reduce 
reduce(function, iterable[, initializer])
reduce(lambda x, y:x +y, [1,2,3,4], 5)
```

#### 闭包

`概念`: 在一个外函数中定义了一个内函数，内函数里运用了外函数的临时变量，并且外函数的返回值是内函数的引用。这样就构成了一个闭包。

`特点`:

内部函数直接使用外部函数的参数

返回值是内部函数

```PYTHON
def outer(saying):
    def inner():
        return "hello," + saying   # 内部函数直接使用外部函数的参数
    return inner   # 返回内部函数

# 
f = outer("world")
f()  # "hello,world"

```

#### functools 工具函数 
    * import functools
    
    * partial() 把一个函数的某些参数设置默认值
    ```PYTHON
        import functools
        def add(a, b, c):
            print(a,b,c)
        add_two = functools.partial(add, 1)  #相当于add(1, b, c)
    ```
    
    * wrap
    ```PYTHON
    import functools
    def decorate(func):
        "decorate function"
        @functools.wraps(func)  
        def wrapper():
            "wrapper function"
            print('note something')
            return func()
        return wrapper
    
    @note
    def test():
        "test function"
        print('I am test')
    
    test()
    print(test.__doc__)  
    #打印"test function"， 如果没有 @functools.wraps(func)  ，则将打印 "wrapper function"
    ```

* 注意 
    * python不支持函数重载

### 10. 异常

`基本格式`:

```PYTHON
try:
	# 
except exceptiontype as name:   # 捕捉特定异常并取别名
except (IndexError, ValueError):  # 使用元组捕捉指定集合的异常
except:  # 捕捉所有异常 等价于 except Exception:
finally: # 不管是否有异常一定会调用
```

`例子`:

```PYTHON

li = [1,2,3,4,5]

while True:
    value = input("Position [q to quit]?")
    if value == 'q':
        break
    try:
        position = int(value)
        print(li[position])
    except IndexError:
        print("Bad position", position)
    
    except Exception as err:
        print("Something error", err)
    

```

#### 自定义异常 
Exception类的子类
```PYTHON
class MyException(Exception):
    '''自定义异常'''
    def __init__(self, length, at_least):
        super().__init__()
        self.lenth = length
        self.at_least = at_least
    def __str__(self):
        return "MyException:输入的长度是{},长度至少应是{}'.format(self.length, self.at_least))"
def main():
    try:
        s = input()
        if len(s) < 5:
            raise MyException(len(s), 5)
    except MyException as error:
        print(error)
    except:
        print("小于3")
    else:
        print("没有异常发生")
main()
```

#### with
```PYTHON
    with open('in.txt', 'r') as f:
        for line in f:
            print(line)
```

#### 常见异常
`NameError`: name 'mesage' is not defined
`SyntaxError`: invalid syntax
`TypeError`: cannot concatenate 'str' and 'int' objects
`IndexError`: list assignment index out of range
`ValueError`: list.remove(x): x not in list
`ZiroDivisionError`: division by zero

### 11.文件 utf-8  

* 文件的类型：文本文件t，二进制文件b
* 文件的操作
    1. 打开，f = open('文件路径/绝对路径和相对路径', '读取方式 r/w/a/b/t/+', encoding='utf-8')
    2. 关闭  f.close()
    3. 读写  f.write('fdsafs')  向文件写入字符串
             f.writelines()    将一个元素全为字符串的列表写入文件
             f.read(size=-1)  读给定size长度的文件内容，默认为全部文件内容
             f.readline(szie=-1)  读入改行前size个单词,默认一整行
             f.readlines(size=-1) 读入size行，保存在列表中

    4. 读文件的最佳方式，用迭代器  for line in f: 
    5. 返回当前位置  f.tell()  返回当前的流位置
    6. 跳转  f.seek(offset, whence=0)   whence:  0:starte ; 1 :current ;  2:end
* 乱码 ： encoding='utf-8'
```PYTHON
    #文件操作

    # f = open("in.txt", "r", encoding="utf-8")

    #文件读法一： 全读
    # text = f.read()
    #处理
    # print(text)
    #f.close()

    #文件读法二： 按数量读
    # text = f.read(2)
    # while text != "":
        #处理
    #     print(text, end="")
    #     text = f.read(2)
    #f.close()

    #文件读法三： 逐行读
    # for line in f:
        #处理
    #     print(line)   #处理
    #     print(line)
    # f.close()

    # f = open("out.txt", "w", encoding = "utf-8")

    #文件写法一：
    # text = " 滚滚长江东逝水，浪花淘尽英雄。是非成败转"
    # f.write(text)
    # f.close()

    #文件写法二：
    # ls = ["what", "hello", "world", "!!!"]
    # f.writelines(ls) #文件内容为： whathelloworld!!!  连在一起了
    # f.close()
```

### 13 面向对象

* 类的创建,销毁
    * 创建过程：1.创建类对象， 2.调用__init__方法， 3.返回实例对象
    * 声明:  变量名 =  类名() 例如： s = Student()
    * 调用类方法:   x.method(...)  例如：s.study()
    * 销毁： del a

* 类属性的修改 1.set 2.动态添加属性 3.__init__初始化

* 动态添加属性和方法
    ```PYTHON
    import types
    class Test(object):
        pass

    T = Test()
    T.name = None  #添加对象属性

    def test0(self):
        pass
    T.test0 = types.MethodType(test0, T)     #为对象添加实例方法
    ```


    def test(self)
        pass
    Test.test = test  #为类添加实例方法
    
    @classmethod
    def test1(cls):
        pass
    Test.test1 = test1  #为类添加类方法
    
    @staticmethod
    def test2():
        pass
    Test.test2 = test2  #为类添加静态方法
    ```

* __slots__限制对象添加的属性, 但不限制类添加属性
    ```PYTHON
    class Person(object):
        __slots__ = ("name", "age")  #不能随便添加，只能添加name，age
    ```
* self  相当于 this

* 魔法方法 __xx__  dir(__builtin__)
    * \__new__()     # 负责创建对象 
    * \__init__()    # 负责初始化  两者加起来等于构造函数
    * \__del__()     # import sys;   sys.getrefcount(t)  获得对象引用的个数
    * \__str__()     # 打印时显示的
    * \__call__()    # 对象可像函数一样调用 t()
    * \__doc__()     # 文档注释 
    * \__add__()     # + addition
    * \__sub__()     # - subtraction
    * \__mul__()     # *
    * \__truediv__() # /
    * \__floordiv__()# //
    * \__mod__()     # %
    * \__eq__()      # ==
    * \__ne__()      # !=
    * \__lt__()      # <
    * \__gt__()      # >
    * \__le__()      # <=
    * \__ge__()      # >=
    
      
    ```PYTHON
        class Test(object):
            def __new__(cls, *args, **kwargs) 
                return object.__new__(cls)
            def __init__(self, *args, **kwargs)
                #初始化
                pass
            def __str__(self):
                return "对象的描述"
            def __del__(self):
                print("对象被销毁")
    ```
```
    
* 操作符重载：
    ```PYTHON
    class Rational(object):
        """Rational class"""
        def __init__(self, num, den):
            #判断类型是否为int
            if not isinstance(num, int) or not isinstance(den, int):
                raise TypeError("不是整型")
            if den == 0:  #检查分母是否为0
                raise ZeroDivisionError("分母不能为0")
            sign = 1
            if num < 0:
                num, sign = -num, -sign
            if den < 0:
                den, sign = -den, -sign
            g = Rational.__gcd(num, den)
            self.__num = num // g * sign
            self.__den = den // g
            
        def den(self):
            return self.__den
        def num(self):
            return self.__num
            
        def __add__(self, r):  #重载加法
            num = self.__num*r.den() + self.__den*r.num()
            den = self.__den * r.den()
            return Rational(num, den)
        
        def __sub__(self, r):   #重载减法
            num = self.__num*r.den() - self.__den*r.num()
            den = self.__den * r.den()
            return Rational(num, den)
        
        def __mul__(self, r):   #重载乘法
            num = self.__num * r.num()
            den = self.__den * r.den()
            return Rational(num, den)
        
        def __floordiv__(self, r):  #重载 //
            if r.num() == 0:
                raise ZeroDivisionError
            num = self.__num * r.den()
            den = self.__den * r.num()
            return Rational(num, den) 
        # %：__mod__, /: __truediv__

        def __str__(self):
            if self.__num == 0:
                return "0"
            return "{}/{}".format(self.__num, self.__den)

        @staticmethod
        def __gcd(m, n):
            while m != 0:
                r = n % m
                n = m
                m = r
            return n
```

* set/get
* 私有属性和私有方法   "__"   相当于private
* property 写出简短的代码，同时保证对参数进行必要的检查，
    ```PYTHON
    
    ```



* 类属性  
   * 类似于 c++中的static的变量
    * 只能通过 类名.属性名 修改 例如：Test.counter+=1， 不能通过  类的实例对象.属性 来修改

    ```PYTHON
        class Test(object):
            counter = 0  #类属性
            def __init__(self):
                Test.counter+=1
            @classmethod
            def get_counter(cls):
                return cls.counter
        Test.counter = 3
        t = Test()
        t.counter = 4 #会为对象t添加掉counter属性,不能修改类属性counter
    ```


##### `方法的类型`
`包括`: 实例方法, 类方法, 静态方法
* `实例方法`: 方法的第一个参数为 `self`
* `类方法`: 用`@classmethod`修饰,方法的第一个参数为 `cls`
    * 通常用来实现与类的所有对象都有关的操作,例如计数器
* `静态方法`: 用`@staticmethod`修饰, 不需要self或者cls参数
    * 实际上就是普通函数
```PYTHON
class Test(object):
	num = 0  #类属性

	#实例方法  self
	def fun1(self):  # 第一个参数是self
    	Test.num += 1

 	#类方法 cls
	@classmethod   # 用@classmethod修饰
	def fun2(cls):  # 第一个参数是cls
		print(cls.num)

	#静态方法 不需要参数
	@staticmethod    # 用@staticmethod修饰
	def fun3():		# 不需要cls或者self
		pass 

 t = Test()
 t.fun1()   	# 通过 对象名.方法名 调用实例方法
 Test.fun2()	# 通过 类名.方法名 调用类方法
 Test.fun3() 	# 通过 类型.方法名 调用静态方法
```

##### `构造函数`

def \__init__(self)

一个类可以定义多个构造函数,但只有最后一个构造函数有用,建议只定义一个构造函数

```PYTHON
class MyClass(object):
	def __init__(self,name):
        '''构造函数'''
		self.name = name
```

`对象创建过程:`

1. 在内存中实例化一个对象
2. 调用对象的\__init__方法, 进行初始化
3. 返回对象

##### `权限控制`

Python中变量名如果以__开头,就会变成私有变量,这样外界不能修改,同理私有方法

```PYTHON
class MyClass(object):
    def __init__(self, name, age)
    	self.__name = name
        self.age = age
    def f(self):    # 公有方法
        pass
   	def __f(self):  # 私有方法
        pass

```
##### `魔法方法 `
__xx__  dir(__builtin__)
|||
| -- | -- |
| \__new__()     | 负责创建对象|
| \__init__()    | 负责初始化  new+init等于构造函数 |
| \__del__()     | import sys;   sys.getrefcount(t)  获得对象引用的个数|
| \__str__(self) | 定义如何打印对象信息, str(self) |
| \__len__(self) | len(self) |
| \__call__() | 对象可像函数一样调用 t() |
| \__doc__() | 文档注释 |
| \__add__(self, other) | + addition |
| \__sub__(self, other) | - subtraction |
| \__mul__(self, other) | *    |
| \__truediv__(self, other) | /    |
| \__floordiv__(self, other) | //   |
| \__mod__(self, other) | %    |
| \__pow__(self, other) | ** |
| \__eq__(self, other) | ==   |
| \__ne__(self, other) | !=   |
| \__lt__(self, other) | <    |
| \__gt__(self, other) | >    |
| \__le__(self, other) | <=   |
| \__ge__(self, other) | >=   |
#### 封装

PYTHON中类的所有属性都是公开的, 可直接访问和修改, 不需要setter和getter,但可以通过property定义setter和getter方法

`私有属性`

通过在属性前面 +  __  ,例如 self.__name

`property`

设置属性的setter和getter方法,有两种方式

```PYTHON
#第一种 property(getter,setter)函数
class Money(object):
    def __init__(self, money):
        self.__money = money
    def getMoney(self):
        return self.__money
    def setMoney(self, value):
        self.__money = value
        
    money = property(getMoney, setMoney)  #property(getter,setter)s
    
#第二种 @property, @属性.setter 修饰符
class Money(object):
    def __init__(self, money):
        self.__money = money

    @property    #只读 相当于getMoney()
    def money(self):    
        return self.__money
    
    @money.setter       #可写 相当于 setMoney()
    def money(self, value):
        self.__money = value
    
```



#### 继承

```PYTHON
class DeriveClass(BaseClass1[,BaseClass2..]):  # 在()中写继承的父类,可以有多个
	pass
```

`同JAVA区别`: JAVA单继承,Python多继承

`继承原则`: 父类私有属性和私有方法不会被继承

`方法重写`:

当父类的方法不满足时,可以对父类的方法进行重写

`isinstance`:

`super的用法`:

调用父类的方法

```PYTHON
1. super().方法名(argv)
def __init__(self, name):
	super().__init__(name)  # 调用父类构造函数

2. 父类名.方法名(self, argv)
def __init__(self, name):
	Fu.__init__(self, name)  # 调用父类构造函数
```

`多继承`: 

#### 多态  

体现不明显

只要求有相同的方法,不一定要继承

#### 深拷贝和浅拷贝和引用
    * import copy
        a = copy.copy(b)    #浅拷贝 对象拷贝值，子对象是引用。
        a = copy.deepcopy(b)    #深拷贝 对象和子对象都是拷贝值
    
    * 引用， 对象赋值实际上是引用，两个指向完全一样的空间s
    ```PYTHON
    a =[1, 2, 3, 4, ['a', 'b', 'c']]
    b = a
    print(id(a), id(b))  #两个id相等，指向同一个空间
    a.append(14)
    print(a, b) #改变a也会改变b
    ```
    
    * 浅拷贝  copy.copy() 子对象拷贝的是引用。
        * 当时不可变类型时(如元组)， 对象拷贝时是引用
        * 可变类型时，对象拷贝的值，子对象是引用
    
    ```PYTHON
    import copy
    a =[1, 2, 3, 4, ['a', 'b', 'c']]
    b = copy.copy(a)
    print(id(a), id(b))   #两个id不相同
    a.append(14)
    print(a, b)     #改变a不会改变b
    print(id(a[4]), id(b[4]))  #两个id相同，子对象拷贝的是引用
    a[4].append(3)  #改变a的子对象也会改变b的子对象
    print(a, b)
    
    a = (1,2,3,['a'])
    b = copy.copy(a)
    print(id(a), id(b))  #两个id相同
    ```
    
    * 深拷贝 copy.deepcopy() 对象和子对象都是拷贝值
    ```PYTHON
    import copy
    a =[1, 2, 3, 4, ['a', 'b', 'c']]
    b = copy.deepcopy(a)
    print(id(a), id(b))   #两个id不相同
    a.append(14)
    print(a, b)         #改变a不会改变b
    print(id(a[4]), id(b[4]))  #两个id不相同，子对象拷贝也是值
    a[4].append(3)  #改变a的子对象不会改变b的子对象
    print(a[4], b[4])  #不相同 
    ```

### 14.迭代器和生成器
#### 迭代器  

* iter() ,next()
  
    * 迭代器的遍历
        ```PYTHON
        l = [1,2,3,4]
        it = iter(l)    #创建迭代器
        #第一种 for-in 遍历
        for i in it：
        print(i)
    
        it = iter(l)
        #第二种 
        try:
            while True:
                print(next(it)) #next返回一个
        except StopInteration:
            pass
        ```
    ```
    
    ```
    
* 抛出 StopInteration 异常
  
    * 判断是不是可以迭代
        from collectios import Iterable
    isinstance(xx, Iterable)
    
    * 判断是否是迭代器
        from collections import Iterator
        isinstance(xx, Iterator)
    
#### 生成器

`优点`:

当函数返回一个列表，并且列表很大时会浪费内存，这时可以用生成器保存中间结果

`产生生成器的方法:`

`方式一:` 生成器函数, yield

`特点`: 与普通函数类型,但是返回值语句使用yield而不是return

```PYTHON
# 实现和range功能的生成器函数
def my_range(first=0, last=0, step=1):
    num = first
    while num < last:
        yield num
        num += step

for i in my_range(1,5):
	print(i)
# 1,2,3,4
```

`方式二`: 生产器推导式, 

`特点`: 将一个列表表达式放到元组中去

```PYTHON
l = (x for x in range(10))
print(type(l)) # generotor
for i in l:
	print(i)
```

`方式三`: 生成器类

`特点`: 用类的iter和next方法

```PYTHON

class MyRange(object):

    def __init__(self, first=0, last=0, step=1):
        self.first = first
        self.last = last
        self.step = step
    
    def __iter__(self):
        self.first -= 1
        return self
    
    def __next__(self):
        if self.first == self.last:
            raise StopIteration
        self.first += 1
        return self.first

for i in MyRange(1,10):
    print(i)
```



### 15.装饰器
* 无参数的装饰器
* 不定长参数的装饰器
* 带返回值的装饰器
* 多个装饰器的执行顺序
```PYTHON
#装饰器的通用模板
def deco(fun):
    def wrapper(*args, **kwargs):
        ret = fun(*args, **kwargs)
        return ret
    return wrapper

@deco
def test():
    pass
```
* 类装饰器
    ```PYTHON
    class Test(object):
        def __init__(self, fun):
            self.__fun = fun
        
        def __call__(self, *args, **kwargs):
            ret = self.__fun(*args, **kwargs)
            return ret

    @Test
    def test(*args, **kwargs):
        pass
    ```

* 装饰器的功能
    * 引入日志
    * 函数执行时间统计
    * 执行函数前预备处理
    * 执行函数后清理功能
    * 权限校验等场景
    * 缓存

### 16.多线程和多进程
* 时间片轮转
* 优先级调度
* 并行和并发
* 调度算法

* 进程和线程的区别

* fork 创建进程 linux/unix下才有,windows不可以用
    * os.fork()  产生子进程
        * > 0 父进程，返回的是子进程的pid
        * == 0 子进程
    * os.getpid() 获取当前进程的pid  
    * os.getppid() 获取当前进程的父进程的pid
    * 父进程不会等子进程结束才结束
    * 进程不共享全局变量, 想要完成进程间的数据共享,需要一些方法:命名管道/无名管道/共享内存/消息队列/网络等
    * 多次fork的分析
    * fork炸弹 while True:
                    os.fork()
    
* multiprocess 创建进程 跨平台，以后不要用fork了 
    * Process
        * 常用属性
            * name 当前进程实例别名
            * pid 当前进程的PID值；
        * Process(group=None, target=None, name=None, args=(), kwargs={}, *, daemon=None)
            * target：表示这个进程实例所调用对* 象；
            * name：为当前进程实例的别名；
            * args：表示调用对象的位置参数元组；
            * kwargs：表示调用对象的关键字参数字* 典；
            * group：大多数情况下用不到；
        * .is_alive() 判断进程实例是否还在执行；
        * .join([timeout]) 是否等待进程实例执行结束，或等待多少秒；
        * .start()  启动进程实例（创建子进程）
        * .terminate()不管任务是否完成，立即终止；
        * .run() 如果没有给定target参数，对这个对象调用start()方法时，就将执行对象中的run()方法；

        * 主进程会等子进程结束后才结束

        * 写个target的函数创建子进程
        ```PYTHON
        from multiprocessing import Process
        import os
        import time

        def test(name):
            while True:
                print("{} ,pid={},ppid={}".format(name, os.getpid(), os.getppid()))

        p = Process(target=test, args=('test',))
        p.start() #调用test方法
        time.sleep(1)
        p.terminate()
        #p.join() #阻塞
        while True:
            print("main")

        ```

        * 继承Process的子类，并重写run方法,来创建子进程
        ```PYTHON
        import os
        import time
        from multiprocessing import Process

        class MyProcess(Process): #继承Process
            def __init__(self, interval):
                super().__init__()
                self.interval = interval

            def run(self): #重写run方法
                print("子进程{} 开始执行 父进程：{}".format(os.getpid(), os.getppid()))
                start = time.perf_counter()
                time.sleep(self.interval)
                end = time.perf_counter()
                print("子进程{} 执行结束， 耗时{:.2f}s".format(os.getpid(), end-start))

        if __name__=='__main__':
            start = time.perf_counter()
            print("当前进程为：{}".format(os.getpid()))
            p = MyProcess(2)
            p.start()
             #对一个不包含target属性的Process类执行start()方法，就会运行这个类中的run()方法，所以这里会执行p.run()
            p.join()
            end = time.perf_counter()
            print("执行结束，耗时{:.2f}s".format(end-start))
        ```

    * Pool  进程池，用来创建多个进程
        * apply_async(func[, args[, kwds]]) ：使用非阻塞方式调用func（并行执行，堵塞方式必须等待上一个进程退出才能执行下一个进程），args为传递给* func的参数列表，kwds为传递给func的关键字参数列表；
        * apply(func[, args[, kwds]])：使用阻塞方式调用func
        * close()：关闭Pool，使其不再接受新的任务；
        * terminate()：不管任务是否完成，立即终止；
        * join()：主进程阻塞，等待子进程的退出， 必须在close或terminate之后使用；

        * 主进程不会等子进程结束后才结束

        * Pool创建进程
        ```PYTHON
        from multiprocessing import Pool
        import time
        import os
        import random

        def test(num):
            print("{} 开始执行, pid={}, ppid={}".format(num, os.getpid(), os.getppid()))
            start = time.perf_counter()
            time.sleep(random.random() * 2)
            end = time.perf_counter()
            print("{} 执行结束，pid={}, 用时：{:.2f}".format(num, os.getpid(), end-start))

        if __name__ == '__main__':
            p = Pool(3)

            for i in range(10):
                # p.apply_async(test, args=(i,))
                p.apply(test, args=(i,))
            print("start".center(20, '='))
            p.close()
            p.join()
            print("over".center(20, '='))
        ```

    * Queue  队列
        * 初始化Queue(maxsize = 0)对象时（例如：q=Queue()），若括号中没有指定最大可接收的消息数量，或数量为负值，那么就代表可接受的消息数量没有上限（直到内存的尽头）；
        * Queue.qsize()：返回当前队列包含的消息数量；
        * Queue.empty()：如果队列为空，返回True，反之False ；
        * Queue.full()：如果队列满了，返回True,反之False；

        * Queue.get([block[, timeout]])：获取队列中的一条消息，然后将其从列队中移除，block默认值为True；
            * 如果block使用默认值，且没有设置timeout（单位秒），消息列队如果为空，此时程序将被阻塞（停在读取状态），直到从消息列队读到消息为止，如果设置了timeout，则会等待timeout秒，若还没读取到任何消息，则抛出"Queue.Empty"异常；
            * 如果block值为False，消息列队如果为空，则会立刻抛出"Queue.Empty"异常；
        * Queue.get_nowait()：相当Queue.get(False)；

        * Queue.put(item,[block[, timeout]])：将item消息写入队列，block默认值为True；
            * 如果block使用默认值，且没有设置timeout（单位秒），消息列队如果已经没有空间可写入，此时程序将被阻塞（停在写入状态），直到从消息列队腾出空间为止，如果设置了timeout，则会等待timeout秒，若还没空间，则抛出"Queue.Full"异常；
            * 如果block值为False，消息列队如果没有空间可写入，则会立刻抛出"Queue.Full"异常；
        * Queue.put_nowait(item)：相当Queue.put(item, False)；


* 线程
    * Thread
        * from threading import Thread
        * Thread(group=None, target=None, name=None, args=(), kwargs=None)

        *  主线程会等待所有的子线程结束后才结束
        * 多进程共享变量
        * target创建线程
        ```PYTHON
        from threading import Thread
        import time

        #1. 如果多个线程执行的都是同一个函数的话，各自之间不会有影响，各是个的
        def test(name,):
            print("{}----昨晚喝多了，下次少喝点---".format(name))
            time.sleep(1)
        ```


        if __name__ == '__main__':
            t = Thread(target=test, args=('test',))
            t.start()
            t.join()
            print("over")
        ```
    
        * 继承Thread类创建进程
        ```PYTHON
        from threading import Thread
        import time
        import os
    
        class MyThread(Thread):
            def __init__(self, name,interval):
                # Thread.__init__(self)
                super().__init__()
                self.name = name
                self.interval = interval
            
            def run(self):
                print("线程{}, pid{},开始执行".format(self.name, os.getpid()))
                start = time.perf_counter()
                time.sleep(self.interval)
                end = time.perf_counter()
                print("线程{}, pid{},执行结束，耗时:{:.2f}s".format(self.name, os.getpid(), 
                                                            end-start))
        if __name__ == '__main__':
            print(os.getpid())
            t = MyThread('test',2)
            t.start()
            t.join()
            print("over")
        ```

### 模块和包
#### 模块导入

##### `模块导入方式`

`import导入`

用来导入整个模块

```python
import math    # 导入 import module
print(math.pi)  # 访问 module.对象

# as 取别名 适用于库名太长，取个简单的别名
import pygame as pg  # 将pygame取别名为 pg
```

`from import导入`

导入指定模块的某些对象

```PYTHON
from math import sin, pi # 从math中导入sin和pi

# 可直接使用对象名称,而不用加上模块名
print(sin(pi))			


# as 取别名 适用于名太长，取个简单的别名
from math import sqrt as sq

# 导入模块的所有对象, 不建议
from math import *
```

##### `模块导入的搜索路径`

```PYTHON
import sys
print(sys.path)   # 搜索路径
```



* 模块重新导入
    import importlib
    importlib.reload(_module_)
* 在 Python 2.x 中，reload() 是内置函数。
    * 在 Python 3.0 - 3.3 中，可以使用 imp.reload(module)。
    * 在 Python 3.4 中，imp 已经被废弃，取而代之的是 importlib。
    
* 避免循环导入

3. 自定义模块
    * .py
    * 测试
        if __name__ == 'main':
            main()
    *  当模块中有__all__ = ["xx", "yy"] ,则 "from 包名 import *" 时只导入 xx和yy

#### 包

> * 将有联系的模块组织在一起，即放到同一个文件夹下，并且在这个文件夹创建一个名字为__init__.py 文件，那么这个文件夹就称之为包。有效避免模块名称冲突问题，让应用组织结构更加清晰
>
> * __init__.py控制着包的导入行为
> * _init__.py为空,仅仅是把这个包导入，不会导入包中的模块
> * 在__init__.py文件中，定义一个__all__变量，它控制着 “from 包名 import *”时导入的模块

5. 模块的发布和使用
    1. 目录结构
        ├── setup.py
        ├── suba
        │   ├── aa.py
        │   ├── bb.py
        │   └── __init__.py
        └── subb
            ├── cc.py
            ├── dd.py
            └── __init__.py
    2. 编辑 setup.py文件，py_modules需指明所需包含的py文件
    ```PYTHON
    from distutils.core import setup
    setup(name="XQY", version="1.0", description="xqy's module", author="xqy", py_modules=['suba.aa', 'suba.bb', 'subb.cc', 'subb.dd'])
    ```

    * 
6. 安装第三方模块或包
    * https://pypi.org
    * pip -h
            install   
        uninstall  
        download  
        search 
        list
    * anaconda

### 标准库

`官方网站`: <https://docs.python.org/3/library/>

#### math库
improt math
|A|B|
|:---:|:---: |
|math.sin()| math.sin(math.pi / 2) = 1 用的是弧度|
|math.cos()| math.cos(0), math.cos(math.pi/2) 用的是弧度|
|math.tan()|  math.tan(math.pi/4) 用的是弧度|
|math.hypot()|math.hypot(3,4) = 5 |
|math.sqrt() | math.sqrt(2)=1.44 不能是负数|
|math.ceil()|向下取整：math.ceil(2.1) = 3|
|math.floor()|向上取整：math.floor(2.9) = 2|
|math.exp() |e的多少次方，math.exp(2) = 7.389|
|math.log(x[,base])|以base为底, math.log(4, 2) = 2|

#### cmath库
import cmath  
from cmath import sqrt

| A    | B    |
| ---- | ---- |
| sqrt() | sqrt(-1)=1j |
|  |             |
|        |             |

#### sys库

```PYTHON
sys.path  # 返回搜索路径

# sys.argv 返回命令行参数,列表
python test1.py a b  
print(sys.arv)  # ['test1.py','a','b']
```



#### turtle库

* 官方文档：https://docs.python.org/3/library/turtle.html
* 使用 
    * title('xxx')
    * 布局:setup(width, height, start-x, start-y)  
    * goto(x, y) 绝对坐标
    * fd() 正数前进
    * rt(angle) lt(angle) 
    * seth()  绝对角度[0,360]
    * color()  
        1. rgb:(255,255,255) 或 (0.5,0.5,0.5)默认Wie小数
    * 填充:begin_fill()  end_fill()  
    * 画笔:
        * pensize()
        * pencolor()
        * penup() ,pendown()
    * circle(半径, 角度)
    * .hideturtle()  隐藏箭头s
    * .done() 程序不会自动退出，

* 实例
    ```PYTHON
        #五角星
        import turtle

        turtle.color("red", "black") #设置边框和填充颜色
        turtle.begin_fill() #填充

        for i in range(5):
            turtle.fd(100) #前进
            turtle.rt(144) #右转

        turtle.end_fill() #结束填充
        turtle.done()
        turtle.hideturtle()
    ```

#### time库
* 获取时间
    * time() 返回1970.1.1 到现在的秒数,浮点数
    * ctime([secs]) 返回当前时间的字符串,传入时间戳
    * gmtime([secs])  返回时间的结构体,0时区的, 传入时间戳
    * localtime([secs]) 返回时间的结构体，当地时区的, 传入时间戳
    * mktime(t)     传入时间结构体，返回sec

* 时间格式化
    * strftime(格式, 时间结构) time.strftime("%Y-%m-%d %H:%M:%S %A %a %p %B %b", t) 返回指定格式的字符串
    * strptime(str, 格式)  time.strptime("2018-7-12 16:03", "%Y-%m-%d %H:%M") 返回时间的结构体

* 计时
    * perf_counter() 用来计时       
    * sleep(sec) 休眠sec秒

* 实例
    ```PYTHON
        import time

         # time() 返回1970.1.1 到现在的秒数,浮点数 :
        print(time.time())  #1531876806.8038387
        #ctime(),返回当前时间的字符串 :
        print(time.ctime()) #'Wed Jul 18 09:19:55 2018'
        #gmtime(),返回0时区的的结构体:
        print(time.gmtime()) #time.struct_time(tm_year=2018, tm_mon=7, tm_mday=18, tm_hour=1, tm_min=20, tm_sec=39, tm_wday=2, tm_yday=199, tm_isdst=0)
        # localtime返回当前时区的结构体
    print(time.localtime()) #time.struct_time(tm_year=2018, tm_mon=7, tm_mday=18, tm_hour=9, tm_min=20, tm_sec=39, tm_wday=2, tm_yday=199, tm_isdst=0)
    
        #strftime(格式, 时间结构)  返回指定格式的字符串
        t = time.gmtime()
        print(time.strftime("%Y-%m-%d %H:%M:%S %A %a %p %B %b", t)) #2018-07-18 01:23:22 Wednesday Wed AM July Jul
        #strptime()  返回时间的结构体
        print(time.strptime("2018-7-12 16:03", "%Y-%m-%d %H:%M")) #time.struct_time(tm_year=2018, tm_mon=7, tm_mday=12, tm_hour=16, tm_min=3, tm_sec=0, tm_wday=3, tm_yday=193, tm_isdst=-1)
        
        #perf_counter()
        start = perf_counter()  #开始计时
        end = perf_counter()    #结束计时
        dur = end-start 
    ```



#### calendar库
* 打印年，月份，和星期
    * .month(year, month, wid=2, l=1)   # 返回这个月的日历字符串, w宽度, l没行占多少行
    * .prmonth(year, month, wid=2, l=1) # 打印这个月的日历
    * .calendar(year,w=2,l=1,c=6)       # 返回这年的日历字符串
    * .prcal(year,w=2,l=1,c=6)          # 打印这年的日历

* 
    * .isleap(year)      # 判断闰年
    * .monthrange(2015,9)#(1, 30)   # 返回某个月的weekday的第一天和这个月的所有天数
    * .weekday(year, month, day)    # 返回星期几 0-6 对应星期一-日

* 实例
    ```PYTHON
    import calendar
    #返回某月日历
    m = calendar.month(2018, 8, 4, 2)
    print(m)
    #打印出一个月日历
    calendar.prmonth(2018, 8, 4, 2)

    #返回一年的日历
    m = calendar.calendar(2018, 2, 2, 3)
    print(m)
    #打印一年的日历
    calendar.prcal(2018, 2, 2, 3)

    #判断某年是否为闰年？
    print(calendar.isleap(2015))#False

    #返回某个月的weekday的第一天和这个月的所有天数
    print(calendar.monthrange(2015,9))#(1, 30)
    ```
    
#### timeit库 测试执行时间
* .Timer(stmt='pass', setup='pass', timer=<built-in function perf_counter>, globals=None)
    * stmt参数是要测试的代码语句（statment）；
    * setup参数是运行代码时需要的设置；
    * timer参数是一个定时器函数，与平台有关。

* .timeit(stmt='pass', setup='pass', timer=<built-in function perf_counter>, number=1000000, globals=None) 返回执行时间
  
* number次数
  
* .repeate(stmt='pass', setup='pass', timer=<built-in function perf_counter>,repeate=3, number=1000000,globals=None)
  
* repeate 重复的次数，返回为列表
  
* 实例
    ```PYTHON
    import timeit

    def fun():
        l = []
        for i in range(100):
            l.append(i)
    #Timer
    t = timeit.Timer('[i for for i in range(100)]')
    print(t.timeit())
    print(t.timeit(number=100))
    print(t.repeat(number=100, repeat=5))

    # timeit
    print(timeit.timeit('[i for i in range(100)]')) #默认为1000000
    print(timeit.timeit('[i for i in range(100)]', number=100))
    ```


    # timeit(函数名_字符串，运行环境_字符串，number=运行次数)
    t = timeit.timeit('fun()', 'from __main__ import fun', number = 100)
    
    #repeate
    t = timeit.timeit('fun()', 'from __main__ import fun', number = 100, repeat = 5)
    print(min(t))
    
    ```

#### random库
* 伪随机数， 梅森旋转算法
* 最基本的两个
    * seed() 种子相同，则随机序列相同, 默认是当前时间
    * random() 产生[0,1),默认用当前时间作为种子
* 拓展的
    * randint(a, b) 产生[a,b]之间的整数，包括a，b
    * randrange(a, b, step)  [a,b)之间的整数
    * uniform(a, b) 产生[a,b]之间的随机小数
    * choice(seq) 从序列中随机选取一个元素
    * shuffle(seq) 对可变序列进行随机排列,会修改序列
    * getrandbits(k) k bit的值
    
    

#### os库
* os.path   
    * .exists(path) 文件是否存在
    * .abspath() 返回绝对路径
    * .normpath() 路径归一化
    * .relpath() 相对路径
    * .dirname() 目录部分
    * .basename() 文件部分
    * .isfile()
    * .isdir()
    * .getatime(path) 访问,getmtime() 修改 ,.getctime(path) 创建
    * .getsize()  以字节为单位

* 进程管理
    import os
    os.system("")  传命令行参数

* 环境参数
    * os.sep  分隔符
    * os.getcwd() 返回当前路径
    * os.listdir()  列出目录包含的内容
    * os.chdir()    切换目录
    * os.mkdir()    创建文件
    * os.remove()   删除文件
    * os.rmdir()    删除文件夹
    * os.rename(old, new)  重命名文件
    * os.renames(old, new) 重命名文件夹
    * os.getlogin() 
    * os.cpu_count()

#### collections

##### `deque`

双端队列

- 比list多 appendleft  popleft  extendleft ；
- 构成栈和队列,可以在任意一段添加和删除

```PYTHON
from collections import deque:

popleft()
pop()

append()
appendleft()
```



##### `Counter`

```PYTHON
# 字典,用来计数 
from collections import Counter  # 导入

breakfast = ['spam', 'spam', 'eggs', 'spam']
breakfast_counter = Counter(breakfast)  # 

print(breakfast_counter) # Counter({'spam': 3, 'eggs': 1})

# most_common()
breakfast_couter.most_common()  # 返回列表  
# [('spam', 3), ('eggs', 1)]

```

##### `namedtuple`

##### 命名元组，使用 .对特性进行访问，`不可变`，效率高

```PYTHON
from collections import namedtuple
Duck = namedtuple('Duck', 'bill tail')
duck = Duck('wide orange', 'long')
print(duck.bill)  # wide orange
print(duck.tail)  # long

# 用字典构造命名元组
parts = {'bill': 'wide orange', 'tail': 'long'}
duck2 = Duck(**parts)
print(duck2.bill) # wide orange

```






defaultdict from collections import defaultdict:
  字典，  会默认设置值
  defaultdict(int/list/dict) defaultdict(function)

OrderedDict  from collections import OrderedDict:
  有序字典，按照进入字典的先后顺序打印

itertools   import itertools
  返回迭代器
  itertools.cycle([1,2,3,4])无线循环  itertools.chain([1,2,3])链式访问
  itertools.accumulate([12,3,4,5],lambda x,y:x * y)  累加，累乘

#### pickle
* 使用
    * pickle.dump(obj, file) 
    * pickle.load(file)
* 实例：
    ```PYTHON
        import pickle

        # 使用pickle模块将数据对象保存到文件
        data1 = {'a': [1, 2.0, 3, 4+6j],
                'b': ('string', u'Unicode string'),
                'c': None}
        data2 = [1, 2, 3]

        output = open('data.pkl', 'wb')

        pickle.dump(data1, output)
        pickle.dump(data2, output)

        output.close()

        f = open('data.pkl', 'rb')
        get1 = pickle.load(f)
        get2 = pickle.load(f)
        print(get1)
        print(get2)
        f.close()
    ```

### 第三方库  
#### pyinstaller库 转为exe文件
+ 安装 : 
    1.管理员运行cmd,* 
    2.pip install pyinstaller   
+ 使用
    1. pyinstaller -i cur.ico -F <文件名.py>  
        * -i icon图标  -F 要py的文件 -w 不要控制台
    
#### jieba库 中文分词
* github: https://github.com/fxsjy/jieba
* 安装 : 
    1.管理员运行cmd, 
    2.pip install jieba
* 使用
    * 精确模式  
    ```PYTHON
        seg_list = jieba.cut("我来到北京清华大学",cut_all=False) 
        seg_list = jieba.lcut("我来到北京清华大学",cut_all=False)  //lcut 直接返回列表
        seg_list = jieba.cut("我来到北京清华大学")     #默认 为False
        print('/'.join(seg_list))
    ```

    * 全模式    
    ```PYTHON
        jieba.cut("我来到北京清华大学",cut_all=True)
        print('/'.join(seg_list))
    ```

    * 搜索引擎模式
    ```PYTHON
        jieba.cut_for_search("小明硕士毕业于中国科学院计算所，后在日本京都大学深造")
        print('/'.join(seg_list))
    ```

    * 添加分词
        jieba.add_word("路明非")

#### wordcloud库
1. 安装 : 
    1.管理员运行cmd, 
    2.pip install wordcloud
2. 使用
    * wordcloud.WordCloud(param)
        参数:
            width默认为400， height默认为200，
            min_font_size默认为4号， max_font_size根据高度自动调节
            font_step, 字号步进间隔，默认为1
            font_path 指定字体文件的路径
            max_words 最大单词数量，默认为200，
            stop_words={'python'}, 排除词列表
            mask 指定词云形状 import scipy.misc ； mk = scipy.misc.imread("pic.png"); 
                            w = wordcloud.WordCloud(mask = mk)
            background_color 指定背景颜色，默认黑色
    * w.generate(txt) 向wordcloud中加载txt文本
    * w.to_file(filename) 将词云输出为图像， .png，.jpg格式

3. 实例
    ```PYTHON 
        import wordcloud
        import jieba
        import scipy.misc

        mask = scipy.misc.imread("china_map.jpg")

        #打开文件文件
        f = open("十九大报告.txt", "r", encoding="utf-8")
        content = f.read()
        #中文分词 jieba.cut
        text = " ".join(jieba.cut(content))  
        f.close()   #关闭文件

        font = "STXINWEI.TTF"  #设置支持中文的字体，解决默认不支持中文的问题
        w = wordcloud.WordCloud(width = 1000, font_path = font, mask=mask,
                                height = 700, background_color='white')    #01.配置词云 
        w.generate(text)   #02.加载词云文件
        w.to_file("pywordcloud.png")    #03.输出为图片

    ```
4. 注意：
    * wordcloud的默认字体不支持中文： 解决：font_path设置一种支持中文的字体即可
    * 指定形状mask时   需要先安装1.numpy+mkl 2.scipy  

### 设计模式
* 单例模式 懒汉模式
    ```PYTHON
        #单例模式
        # 确保某一个类只有一个实例，而且自行实例化并向整个系统提供这个实例，这个类称为单例类，单例模式是一种对象创建型模式。
        class Singleton(object):

            __instance = None    #单例对象,只创建一个对象
            __first_init = False   #创建单例时，只执行一次__init__

            def __new__(cls, *args, **kwargs):
                #如果类属性__instance 没有 或 等于 None
                #那么就通过调用父类的__new__创建一个对象，并且赋值给__instance下
                #如果已经创建过对象了即__instance不是None，直接返回__instance，不创建对象
                if not cls.__instance :
                    cls.__instance = super(Singleton, cls).__new__(cls)
                return cls.__instance

            def __init__(self, number):
                #如果__fisrt_init 等于 False， 那么执行赋值， 并将__fisrt_init 改为 True
                # 如果已经有过赋值了，那么啥也不干
                if not Singleton.__first_init:  
                    self.number = number
                    Singleton.__first_init = True

        s1 = Singleton(2)
        s2 = Singleton(5)

        print(s1)
        print(s2)
        print(s1.number)
        print(s2.number)
    ```

* 工厂模式
    ```PYTHON
        #简单工厂模式
        #原先
        car1 = BWM()
        car2 = Benz()

        class SimpleFactory(object):
            def produce_car(self, name):
                if name == 'BMW':
                    return BMW()
                elif name == 'Benz':
                    return Benz()
                # .....将其他车添加进去

        car1 = SimpleFactory().produce_car('BMW')
        car2 = SimpleFactory().produce_car('Benz')

        #工厂方法    
        class SimpleFactory(object):
            def produce_car(self, name):
                pass

        class BMWFactory(SimpleFactory):
            def produce_car(self, name):
                
                if name = "BMW1"
                    return BMW1()
                elif #BMW的车型
                
        class BenzFactory(SimpleFactory):
            def produce_car(self, name):
                
                if name = "Benz1"
                    return Benz1()
                elif #Benz的车型

        car1 = BMWFactory().produce_car('BMW1')
        car2 = BenzFactory().produce_car('Benz1')

        #抽象工厂方法
        class SimpleFactory(object):
            def produce_car_A(self, name):
                pass
            def produce_car_B(self, name):
                pass
        #......
    ```

### 数据处理
1. 一维数据处理
    * 数据表示
        * 有序  列表
        * 无序  集合
    * 数据存储
        *  使用空格, 缺点不能出现空格  中国 美国 德国 英国 日本
        *  使用',',  缺点不能出现','  中国,美国,德国,英国,日本
    * 数据处理
        * 读 ls = text.split()
        * 写 text = ' '.join(ls)
        * 遍历 for item in ls:
        ```PYTHON
            #读  
            f = open(fname, "r")
            text = f.read()
            text = text.replace('\n', '')
            ls = text.split() # 按空格分隔的
            #ls = text.split(',') #按 ，分隔的
            f.close()

            #写
            ls = ["中国", "美国", "德国", "英国", "日本"]
            f = open(fname, "w")
            text = ' '.join(ls)  # 按空格分隔的
            #text = ','.join(ls)  #按 ，分隔的
            f.write(text)
            f.close()

            #遍历处理
            for item in ls:
                print(item, end = '')
        ```

2. 二维数据 
    * 数据表示
      
        * 二维列表 [[], [], []]
    * 数据存储
        * csv（comma-separated values)  .csv文件  
            * 每行一个一维数据， 采用逗号分隔，无空行
            ```
                省份,省会,序号
                福建,福州,01 
                四川,成都,0 
                浙江,杭州,03
            ```
    * 数据处理
    ```PYTHON
        #二维数据读入
    # f = open("in.txt", "r", encoding='utf-8')
    
        # ls = []
        # for line in f:
        #     line = line.replace("\n", "")
    #     ls.append(line.split(","))
    
        # f.close()
    ```


        #二维数据写入
    
        ls = [['省份', '省会', '序号'], 
            ['福建', '福州', '01'], 
            ['四川', '成都', '02'], 
            ['浙江', '杭州', '03']
        ]
        
        f = open("out.csv", "w", encoding = "utf-8")
    
        for i in ls:
            text = ','.join(i) + '\n'
            f.write(text)
    
        # 二维数据的遍历处理
        for row in ls:
            for column in row:
                print(column, end= ',')
            print()
    
    ```
* json数据处理
    * import json
    * json.dumps() 将 Python 对象编码成 JSON 字符串
    * json.loads() 将已编码的 JSON 字符串解码为 Python 对象
    * python和json的类型转换
        Python	JSON
        dict	object
        list, tuple	array
        str, unicode	string
        int, long, float	number
        True	true
        False	false
        None	null
### 正则表达式

`正则表达式符号`:

|      |                      |
| ---- | -------------------- |
| ^    | 匹配 开头            |
| $    | 匹配 结尾            |
| .    | 匹配 单一字符(除\n以外) |
| ?    | 匹配 0 个 或 1 个字符 |
| *    | 匹配 0 个 或 多个字符  |
| +    | 匹配 1 个 或 多个字符  |
| {m,n} | 匹配 m~n 次         |
| \s | 匹配 空白符, \s+ 一个或多个空白符 |
| \S | 匹配 非空白符 |
| \d | 匹配 一个数字字符 |
| \D | 匹配 一个非数字字符 |
| \w | 匹配 一个字母(包括_)或数字字符 |
| \W | 匹配 一个非字符非数字字符 |
| \    | 用来转义: ? * + () [] ^ $ {} '\\'|
| expr1\|expr2 | 匹配 expr1或expr2 |
| [abc] | 匹配 a,b,c |
| [^abc] | 匹配 非(a,b,c) |
| prev (?=next) | 匹配 后面为next的prev |
| (?<=prev) next | 匹配 前面为prev的next |

`re库的方法`:

`导入`: import re

* re.match(pattern, str[,flag])   # 只匹配以pattern作为开头的str

```PYTHON
# 第一种方式
source = "Young Frankenstein"
m = re.match(r"You", source) # r'',可以避免\b\n等情况
if m:
	print(m.group())  # You
      
# 第二种方式,对于复杂的匹配,可以先编译compile,再匹配
apattern = re.compile(r"You")
m = apattern.match(source)
if m:
	print(m.group())  # You
    
# flag取值：
re.I	使匹配对大小写不敏感
re.L	做本地化识别（locale-aware）匹配
re.M	多行匹配，影响 ^ 和 $
re.S	使 . 匹配包括换行在内的所有字符
re.U	根据Unicode字符集解析字符。这个标志影响 \w, \W, \b, \B.
re.X	该标志通过给予你更灵活的格式以便你将正则表达式写得更易于理解。
```

* re.search(pattern, str[, flag])   # 匹配存在str的字符串,只匹配第一个
```PYTHON
source = "Young Frankenstein"
m = re.match(r"Frank", source) # 匹配不到,因为不以Frank开头,可以改为m = re.match(".*Frank", source)

# 使用search进行匹配:
m = re.search(r"Frank", source)
if m:
    print(m.group()) # Frank
```

* re.findall(pattern, str)  # 寻找所有匹配,返回列表

```PYTHON
source = "Young Frankenstein"
m = re.findall(r'n', source)
print(m)  # ['n', 'n', 'n', 'n']
m = re.findall('n.', source)
print(m)  # ['ng', 'nk', 'ns']
m = re.findall('n.?', source)  # ? 0或1次
print(m)  # ['ng', 'nk', 'ns', 'n']
```

* re.split(pattern, str)   # 按照pattern对str进行切分,返回列表

```PYTHON
m = re.split(r'\s+', 'a b  c')  # 按空白符进行切割
print(m) # ['a', 'b', 'c']

source = "Young Frankenstein"
m = re.split(r'n', source)
print(m)  # ['You', 'g Fra', 'ke', 'stei', '']
```

* re.sub(patter, repl, str, count = 0)  # 替换匹配,返回替换后的字符串

```PYTHON
source = "Young Frankenstein"
m = re.sub(r'n', '?', source)
print(m)  # 'You?g Fra?ke?stei?'
```

`规则`:

* 贪婪匹配(尽可能多的匹配), 可以在后面加?,尽可能少匹配

`例子`:

* 非负整数：^\d+$
* 正整数：^[0-9]*[1-9][0-9]*$
* 非正整数：^((-\d+)|(0+))$
* 负整数：^-[0-9]*[1-9][0-9]*$
* 整数：^-?\d+$
* 非负浮点数：^\d+(\.\d+)?$
* 正浮点数 : ^((0-9)+\.[0-9]*[1-9][0-9]*)|([0-9]*[1-9][0-9]*\.[0-9]+)|([0-9]*[1-9][0-9]*)$
* 非正浮点数：^((-\d+\.\d+)?)|(0+(\.0+)?))$
* 负浮点数：^(-((正浮点数正则式)))$
* 英文字符串：^[A-Za-z]+$
* 英文大写串：^[A-Z]+$
* 英文小写串：^[a-z]+$
* 英文字符数字串：^[A-Za-z0-9]+$
* 英数字加下划线串：^\w+$
* E-mail地址：^[\w-]+(\.[\w-]+)*@[\w-]+(\.[\w-]+)+$
* URL：^[a-zA-Z]+://(\w+(-\w+)*)(\.(\w+(-\w+)*))*(\?\s*)?$ 
*  或：^http:\/\/[A-Za-z0-9]+\.[A-Za-z0-9]+[\/=\?%\-&_~`@[\]\':+!]*([^<>\"\"])*$
* 邮政编码：^[1-9]\d{5}$
* 中文：^[\u0391-\uFFE5]+$
* 电话号码：^((\(\d{2,3}\))|(\d{3}\-))?(\(0\d{2,3}\)|0\d{2,3}-)?[1-9]\d{6,7}(\-\d{1,4})?$
* 手机号码：^((\(\d{2,3}\))|(\d{3}\-))?13\d{9}$
* 双字节字符(包括汉字在内)：^\x00-\xff
* 匹配首尾空格：(^\s*)|(\s*$)（像vbscript那样的trim函数）
* 匹配HTML标记：<(.*)>.*<\/\1>|<(.*) \/>
* 匹配空行：\n[\s| ]*\r
* 提取信息中的网络链接：(h|H)(r|R)(e|E)(f|F)  *=  *('|")?(\w|\\|\/|\.)+('|"|  *|>)?
* 提取信息中的邮件地址：\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*
* 提取信息中的图片链接：(s|S)(r|R)(c|C)  *=  *('|")?(\w|\\|\/|\.)+('|"|  *|>)?
* 提取信息中的IP地址：(\d+)\.(\d+)\.(\d+)\.(\d+)
* 提取信息中的中国手机号码：(86)*0*13\d{9}
* 提取信息中的中国固定电话号码：(\(\d{3,4}\)|\d{3,4}-|\s)?\d{8}
* 提取信息中的中国电话号码（包括移动和固定电话）：(\(\d{3,4}\)|\d{3,4}-|\s)?\d{7,14}
* 提取信息中的中国邮政编码：[1-9]{1}(\d+){5}
* 提取信息中的浮点数（即小数）：(-?\d*)\.?\d+
* 提取信息中的任何数字 ：(-?\d*)(\.\d+)? 
* IP：(\d+)\.(\d+)\.(\d+)\.(\d+)
* 电话区号：/^0\d{2,3}$/
* 腾讯QQ号：^[1-9]*[1-9][0-9]*$ 
* 帐号(字母开头，允许5-16字节，允许字母数字下划线)：^[a-zA-Z][a-zA-Z0-9_]{4,15}$
* 中文、英文、数字及下划线：^[\u4e00-\u9fa5_a-zA-Z0-9]+$
* 匹配中文字符的正则表达式： [\u4e00-\u9fa5] 
* 匹配双字节字符(包括汉字在内)：[^\x00-\xff] 
* 匹配空行的正则表达式：\n[\s| ]*\r
* 匹配HTML标记的正则表达式：/<(.*)>.*<\/\1>|<(.*) \/>/
* sql语句：^(select|drop|delete|create|update|insert).*$
* 匹配首尾空格的正则表达式：(^\s*)|(\s*$)
* 匹配Email地址的正则表达式：\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*

****

### py2 和 py3区别   


from __future__ import xx

||python2  | python3|
|---|---|---|
|| #-*- coding:utf-8 -*-   	|    默认为utf-8                     |
||   raw_input			    |    input                          |
||ascii(u'dfsa')          	|    unicode                        |
||print				        |    print()                        |
||long(L)                 	|    无long                         |
||3/2 = 1			        |    3/2  = 1.5                     |
||dict.keys()返回列表		 |    返回dict_keys需要list(a.keys()) |
||type(L) <type 'lsit'>		|    type(L)  <class 'list'>        |
||type(type(L)) <type 'type>	|    type(type(L)) <class 'type'>   |
||八进制  017			     |     八进制 0o12                   |

## python例子
