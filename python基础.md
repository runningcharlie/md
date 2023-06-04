#### 准备工作

**Python 交互式页面**

`print`函数：打印

`quit()`函数：退出python交互环境

**编程工具（IDE）**

IDLE：python自带的IDE

Ctrl + N：New file

运行脚本：F5键

#### 基础编程

**Python的特点**

1. 解释性语言：从源代码直接运行
2. 面向对象的编程语言：Python里面所有的东西都是对象

对象可以是任何东西的抽象，它包括三个基本面: 身份、属性和行为。面向对象可扩展，写出的代码容易修改和维护。

**数据类型**

原始数据类型：数字、字符串、布尔值

数字类型：整型、浮点数

整型：从负无穷到正无穷大的整数

浮点数：任何有理数（正或负）

字符串类型

单引号、双引号和三引号标注（多行）

以Unicode规范编码

Unicode规范

旨在列出人类语言中用到的每一个字符，并赋予每一个字符唯一的整数编码

ord函数：获取代表该字符的Unicode编码

char函数：将编码转换成字符串

**变量及其运算**

```python
x = 10
```

None：空值

type函数：检测变量的数据类型

**常用内置函数**

`print()`：输出指定内容

`input()`：获取用户输入

```python
age int(input("你几岁?")) // 将用户输入转换为整数
```

`round()`：保留小数点

```
round(12.45466) // 12 => 保留整数
round(12.45466,2) // 12.45 => 保留两位小数
```

`str()`：将其他数据类型转换为字符串

**运算符**

对数据进行运算的符号

算术运算符: 加(`+`)、减(`-`)、乘(`*`)、除(`/`)、整除(`//`)、取模(`%`)、取幂(`**`)

赋值运算符

优先级

**表达式和语句**

表达式：值、变量、运算符，以及函数调用的组合

语句：解释器可以执行的一个完整的任务

#### 条件语句

**比较运算符和逻辑运算符**

比较运算符：比较两个值，其结果为一个布尔值

```python
x = 1
y = 2
z = 3.2
x == y // 比较两个是否相等
...
```

逻辑运算符：

and：且 -> 用于连接两个布尔值（或返回布尔值的表达式），返回布尔值

or：或 -> 用于连接两个布尔值，返回布尔值

not：非 -> 对布尔值取反

布尔运算的短路效应

**if语句**

根据某种预设条件， 做或者不做某些事， 或者变更路径

如果条件A为真，执行任务B

```python
if 13 > 10:
	print('13大于10')
```

**if/elif/else 语句**

else的用法：

```python
isRain = input('下雨吗？Y/N ')

if isRain == 'Y':
    print('带雨伞出门')
else:
    print('去打球')
```

elif的用法：

```python
temperature = int(input('输入温度： '))
if temperature >= 30:
  print('热')
elif temperature >= 35:
  print('很热')
elif temperature >= 40:
  print('太热了')
else:
  print('不热')
```

**其他形式的条件语句**

- 简短条件语句 

CH3 age_conditional_statement

表达式1 if 条件 else 表达式2

等同于

if条件：

​	表达式1

else:

​	表达式2

- 嵌套if 

CH3  isLeapYear

#### 循环语句

循环：重复执行某个代码块

例子：

```python
1+2+3
1+2+3+4+5+6+7+8+9+10
1+2+...+10000
// 大量有规律的计算可以用循环
```

**while循环**

```python
x = 1
while x <= 5:
	print(x)
	x += 1
```

 while 只在每次循环的开始， 查看条件是否 true， 而不是在循环中

**for循环**

- for in

```python
for x in 1,2,3,4,5
	print(x)
```

- for in range()

```python
for x in range(5)
	print(x)
```

**continue 和 break**

中途改变循环的命令

continue 用于跳过一轮循环

break 用于终止循环

```python
# 使用for循环打印10以内所有的奇数
for x in range(10):
	if x % 2 == 0:
		continue
	print(x)

# 使用while循环打印10以内所有的奇数
  i = 0
while i < 10:
	i += 1
	if i % 2 == 0:
    continue
	print(i)
  
# print the first 5 prime numbers from 1 to 50
count = 0
for i in range(1,50):
    for j in range(2,i):# check for factors
        if i%j == 0:    # if it is divisible by any number from 2 to i, it is NOT a prime
            break       # break out the current range and move to check the next number
    else:               # it is a prime
        if count < 5:
            print(i)
            count += 1
        else:
            break
```

#### 函数

**定义函数**

例1：摄氏温度转换为华氏温度

```python
#定义函数
def CtoF(c):
  return (c * 9 / 5 + 32)
# 调用函数
CtoF(27)
```

例2：打招呼

```python
def sayHi():
  print("hello")  
sayHi()
```

例3：凯撒密码

```python
def CaeCipher(x, y, z):
  a = ord(x) + 2
  b = ord(y) + 2
  c = ord(z) + 2
  return chr(a), chr(b), chr(c)
CaeCipher(a, b, c)
```

例4：求平方数

```python
def power(x, n):
    result = 1
    for i in range(n):
        result = result * x
    return result
print(power(2,2))
```

默认参数

```python
def power(num, n = 2):  # 给参数n指定了一个默认值2
    result = 1
    for i in range(n):
        result = result * num
    print(result)
power(2)
power(2, 3)
power(2, 4)
```

不定参数

```python
def multi_add(*args): # *args表示即将传入不定数量的参数
       result = 0
       for x in args:
           result = result + x
       return result

sum = multi_add(1,2,3,4,5,6,7,8,9,10)
print(sum)
```

函数的本质是模块化

**变量的作用域**

函数内部变量和函数外部变量的区别 => 作用域

作用域：变量的有效范围 => 定义在函数内部的变量无法在函数外部访问

局部变量：函数内部定义的变量

全局变量：函数外部定义的变量 => 任何函数都可以访问全局变量

**匿名函数 lambda**

匿名函数的定义及运行方法

先定义后调用

```python
add = lambda x, y: x + y # 省略了return关键字
add(5,6)

hello = lambda: print('你好')
```

定义的时候直接调用

```python
(lambda x, y: x + y)(7, 8)
```

好处: 简化代码（多行代码用一行代码表达）

lambda只能有一行表达式

#### 文本操作

**I/O**

计算机数据的输入、输出（计算机角度）

input：程序外部的数据迁移到程序内部；output：将程序外部的数据迁移到程序内部（编程角度）

存在计算机内存中的数据会随着程序运作结束而消失，数据必须存储在文件里，才能永久保留

文件处理的三个步骤：打开文件 - 处理文件 - 关闭文件

**文本文件操作**

读写文件：请求操作系统打开一个文件对象（称为文件描述符）=> 通过操作系统提供的接口 => 从文件对象中读写文件

`open()` 打开文件

`file object = open(file, mode, [encoding])` => 打开文件并保存到一个文件对象

| 参数 | 处理模式 | 说明                                                         |
| ---- | -------- | ------------------------------------------------------------ |
| r    | 读出     | 如果file不存在，出错                                         |
| w    | 写入     | 如果file不存在，创建新文件<br />如果file存在，则现有内容被清空 |
| a    | 追加     | 如果file存在，新内容被加到现有内容之后<br />如果file不存在，创建新文件 |

读取非英语文件时需要传入encoding参数以防止显示乱码

read()：一次性读入整个文件，返回字符串

```python
file = open('静夜思.txt', 'r', encoding='utf-8') # 打开文件
contents = file.read() # 读取文件
print(contents) # 打印内容
file.close() # 关闭文件
```

readfile()：读入文件下面一整行，返回字符串

```py
file = open('静夜思.txt', 'r', encoding='utf-8')

while True:
    line = file.readline()
    if not line:
        break
    print(line)
file.close()
```

readfiles()：读入整个文件，返回列表

```py
file1 = open('poem.txt', 'r')
contents = file1.readlines()
for text in contents :
    print(text)
file1.close()
```

write(str)：将str字符串输出到文件中

```py
infile = open('静夜思.txt', 'r', encoding='utf-8')
outfile = open('静夜思_out.txt', 'w', encoding='utf-8')
line_num = 1

for line in infile :
    outfile.write(str(line_num) + ' ' + line)
    line_num += 1

infile.close()
outfile.close()
```

with语句：自动调用close（防止忘记关闭文件）

```py
with open('静夜思.txt', 'r', encoding='utf-8') as infile:
    for line in infile :
        print(line)
```

**处理csv文件**

什么是csv文件

- 逗号分隔值
- 纯文本
- 没有数据类型差别，都是字符串

```py
import csv # 导入csv模块

with open('douban_top20utf8.csv', encoding='utf-8') as inCVSfile:  # 打开文件
    csvreader = csv.reader(inCVSfile, delimiter=',')  # 读取文件
    for row in csvreader:  														# 打印数据
        print('书名: ' + row[0])
        print('作者: ' + row[1])
        print('出版社：' + row[2])
        print('出版日期: ' + row[3])
        print('定价: ' + row[4])
        print('豆瓣评分： ' + row[3])
        print()
```

csv标准库函数

csv.reader() ：读取一整行，返回一个csv对象

csv.writer() ：写入一整行，返回一个csv对象

writerow()

```py
import csv

count = 1
with open('sample.csv', 'w') as output:
    write = csv.writer(output)
    while count < 10:
        write.writerow((lambda x, y, z: x + y + z)('第', str(count), '行'))
        count += 1
```

