# 一、PYTHON3基础语法

## 1.1 字符串
- 长字符串中的换行、空格、缩进等空白符都会原样输出
- Python 长字符串由三个双引号"""或者三个单引号'''包围


```python
longstr = '''It took me 6 months to write this Python tutorial.
Please give me a to 'thumb' to keep it updated.
The Python tutorial is available at http://c.biancheng.net/python/.'''
print(longstr)
```

    It took me 6 months to write this Python tutorial.
    Please give me a to 'thumb' to keep it updated.
    The Python tutorial is available at http://c.biancheng.net/python/.
    


```python
longstr = '''
It took me 6 months to write this Python tutorial.
Please give me a to 'thumb' to keep it updated.
The Python tutorial is available at http://c.biancheng.net/python/.
'''
print(longstr)
```

    
    It took me 6 months to write this Python tutorial.
    Please give me a to 'thumb' to keep it updated.
    The Python tutorial is available at http://c.biancheng.net/python/.
    
    

**字符串和 bytes 存在着千丝万缕的联系，我们可以通过字符串来创建 bytes 对象，或者说将字符串转换成 bytes 对象。有以下三种方法可以达到这个目的：**
- 如果字符串的内容都是 ASCII 字符，那么直接在字符串前面添加b前缀就可以转换成 bytes。
- bytes 是一个类，调用它的构造方法，也就是 bytes()，可以将字符串按照指定的字符集转换成 bytes；如果不指定字符集，那么默认采用 UTF-8。
- 字符串本身有一个 encode() 方法，该方法专门用来将字符串按照指定的字符集转换成对应的字节串；如果不指定字符集，那么默认采用 UTF-8。
-
***
###  字节串（bytes）和字符串（string）的对比： 
- 字符串由若干个字符组成，以字符为单位进行操作；字节串由若干个字节组成，以字节为单位进行操作。
- 字节串和字符串除了操作的数据单元不同之外，它们支持的所有方法都基本相同。
- 字节串和字符串都是不可变序列，不能随意增加和删除数据。


```python
#通过构造函数创建空 bytes
b1 = bytes()
#通过空字符串创建空 bytes
b2 = b'c'
print(b2)
#通过b前缀将字符串转换成 bytes
b3 = b'http://c.biancheng.net/python/'
print("b3: ", b3)
print(b3[3])
print(b3[7:22])

#为 bytes() 方法指定字符集
b4 = bytes('C语言中文网8岁了', encoding='UTF-8')
print("b4: ", b4)

#通过 encode() 方法将字符串转换成 bytes
b5 = "C语言中文网8岁了".encode('UTF-8')
print("b5: ", b5)

# 通过 decode() 方法将bytes()对象转换成字符串
str1 = b5.decode('UTF-8')
print("str1:",str1)
```

    b'c'
    b3:  b'http://c.biancheng.net/python/'
    112
    b'c.biancheng.net'
    b4:  b'C\xe8\xaf\xad\xe8\xa8\x80\xe4\xb8\xad\xe6\x96\x87\xe7\xbd\x918\xe5\xb2\x81\xe4\xba\x86'
    b5:  b'C\xe8\xaf\xad\xe8\xa8\x80\xe4\xb8\xad\xe6\x96\x87\xe7\xbd\x918\xe5\xb2\x81\xe4\xba\x86'
    str1: C语言中文网8岁了
    

###  <font color="red">与字符串相关函数</font>
- str():数字转字符串，且用[]可以提取字符
- len():求字符串长度
- ord():把string类型转Unicode码
- chr():把十进制数字转对应字符

- **replace():**实现字符串替换


```python
a = ord('A')
b = ord('高')
c = chr(66)
d = round(33.33)
e = str(b)
f = e[3]
g = len(e)
print(a,b,c,d,e,f,g)

# replace()函数实现字符串替换
str1 = 'abdceihhkjghhjgfgyo'
rep1 = 'ppppp'
str1.replace('j',rep1)   # 这里是创建了新的字符串对象，并指向了str1
```

    65 39640 B 33 39640 4 5
    




    'abdceihhkpppppghhpppppgfgyo'



#### split()分割和join()合并


```python
a = "to do or not to do"
b = a.split()
# 这里是split()函数用法
print(b)
print(a.split('do'))

# join()作用和split()相反，用于将一系列字符串连接起来
c = '/'.join(b)   # 用/将他们连接起来
print(c)
```

    ['to', 'do', 'or', 'not', 'to', 'do']
    ['to ', ' or not to ', '']
    to/do/or/not/to/do
    


```python
b = list(map(int,input()))
a = list()
for i in b:
    i = (i+3)%9
    a.append(i)
a[0],a[2] = a[2],a[0]
a[1],a[3] = a[3],a[1]
c = int(''.join(str(s) for s in a))
print(c)
```

    1234
    6745
    

###  字符串常用操作方法
#### 查找方法
- find('value'):返回value第一次出现value的位置
- rfind('value'):返回最后一次出现指定字符串的位置


```python
A = '''大部分编程语言都会提供和 pop() 相对应的方法，就是 push()，该方法用来将元素添加到列表的尾部，类似于数据结构中的“入栈”操作。但是 Python 是个例外，Python 并没有提供 push() 方法，因为完全可以使用 append() 来代替 push() 的功能。'''
len(A)
ret1 = A.startswith('大部分编程')
print(ret1)
ret2 = A.endswith('的功能。')
print(ret2)
ret3 = A.find('的方法')
print(ret3)
ret4 = A.rfind('的')
print(ret4)
```

    True
    True
    22
    136
    

#### 字符串切片sclice操作
- **标准格式：[起始偏移量start:终止偏移量end：步长step]**


```python
strA = 'sikljtgluyrtffghfrttyu'
strB = strA[::-1]       # 实现逆序排列
print(strB)
strC = strA[3:8:2]
print(strC)
```

    uyttrfhgfftryulgtjlkis
    ltl
    

#### <font color="red">**去除首尾信息**</font>
- strip():去除字符串首尾指定信息，默认去空格
- rstrip():去除字符串右边指定信息
- lstrip()：去除字符串左边指定信息


```python
A = '%****%'
ret1 = A.strip('%')
print(ret1)
ret2 = A.lstrip('%')
print(ret2)
ret3 = A.rstrip('%')
print(ret3)
ret4 = '  ***  '.strip()
print(ret4)
```

    ****
    ****%
    %****
    ***
    

#### <font color="red">**大小写转换**</font>
- capitalize()：产生新的字符串，首字母大写
- title()：产生新的字符串，每个单词都首字母大写
- upper()：产生新的字符串，所有字母大写
- lower():产生新的字符串，所有字母小写
- swapcase():产生新的字符串，所有字母大小写转换


```python
A = 'Have a good time!'
ret1 = A.capitalize()
print(ret1)
ret2 = A.title()
print(ret2)
ret3 = A.upper()
print(ret3)
ret4 = A.lower()
print(ret4)
ret5 = A.swapcase()
print(ret5)
```

    Have a good time!
    Have A Good Time!
    HAVE A GOOD TIME!
    have a good time!
    hAVE A GOOD TIME!
    


```python
"""禁止重复注册"""
current_users = ['Niuniu','Niumei','GURR','LOLO']
cus =''
for i in range(len(current_users)):
    cus += current_users[i].lower()
new_users = ['GurR','Niu Ke Le','LoLo','Tuo Rui Chi']
for i in range(len(new_users)):
    if new_users[i].lower() in cus:
        print('The user name {} has already been registered! Please change it and try again!'.format(new_users[i]))
    else:
        print('Congratulations, the user name {} is available!'.format(new_users[i]))
```

    The user name GurR has already been registered! Please change it and try again!
    Congratulations, the user name Niu Ke Le Le is available!
    The user name LoLo has already been registered! Please change it and try again!
    Congratulations, the user name Tuo Rui Chi Le is available!
    

#### <font color="red">**format()格式化函数以及填充和对齐**</font>
- format():python2.6版本后新增了str.format()，增强字符串格式化的功能，基本语法是通过{}和：来代替以前的%，format函数不限参数，位置可以不按顺序
- 填充和对齐：^，>，<分别是居中，右对齐，左对齐，后面带字符串宽度，：号后面带填充的字符，只能是一个字符，默认空格填充


```python
# format()函数
A= "名字是：{}，年龄是{}"
print(A.format('高崎',18))
B = "名字是：{0}，年龄是{1}，{0}是个好伙子"    # 不加序号，默认对齐匹配
print(B.format('高崎',18))

# 填充与对齐
print('{:*^8}'.format('66'))
print('{:*>8}'.format('66'))

# 数字格式化
C = '我是{}，我的存款有{:.2f}'    # 保留2位小数点

print(C.format('高崎',3888.234342))

operators_dict = {'<': 'less than','==': 'equal'}
for i in sorted(operators_dict):
    print(f'Operator {i} means {operators_dict[i]}.')
```

    名字是：高崎，年龄是18
    名字是：高崎，年龄是18，高崎是个好伙子
    ***66***
    ******66
    我是高崎，我的存款有3888.23
    Operator < means less than.
    Operator == means equal.
    

#### 格式排版
- center()：居中
- ljust()：居左
- rjust()：居右


```python
A = 'ppp'
ret1 = A.center(10,'*')
print(ret1)
ret2 = A.center(10)
print(ret2)
ret3 = A.ljust(10,'*')
print(ret3)
ret4 = A.rjust(10,'*')
print(ret4)
```

    ***ppp****
       ppp    
    ppp*******
    *******ppp
    

#### 其他方法
- count('value'):返回value出现次数
- isalnum()：判断所有字符是字母或者数字，输出是False/True
- isalpha():检测字符串是否只由字母组成
- isdigit():检测字符串是否只由数字组成
- isspace():检测是否为空白符
- isupper():是否为大写字母
- islower():是否为小写字母
- startwith():检索字符串是否以指定字符串开头
- endswith():检索字符串是否以指定字符串结尾
- encode():用于将 str 类型转换成 bytes 类型
- deencode():将 bytes 类型的二进制数据转换为 str 类型



```python
A = 'igwhuedgweiugvbshzvg'
ret1 = A.count('g')
print(ret1)
ret2 = A.isalnum()
print(ret2)
ret3 = A.isalpha()
print(ret3)
ret4 = A.isdigit()
print(ret4)
ret5 = A.islower()
print(ret5)
ret6 = A.isupper()
print(ret6)
ret7 = A.isspace()
print(ret7)
```

    4
    True
    True
    False
    True
    False
    False
    

#### 可变字符串
PS：当需要原地修改字符串是，可以使用io.StringIO对象或者array模块


```python
import io
s = "hello string"
sio = io.StringIO(s)
print(sio)
print(sio.getvalue())
print(sio.seek(7))
print(sio.write('g'))
print(sio.getvalue())
```

    <_io.StringIO object at 0x00000271015841F0>
    hello string
    7
    1
    hello sgring
    

## 1.2 列表，元组，字典和集合

### 序列
Python序列类型：有字符串，列表，元组，集合和字典。序列中，每个元素都有自己的索引，Python还支持索引是负数，从-1开始
### 序列切片
<font color="red">语法格式:  sname[start:end:step]</font>


```python
# 序列相乘
str = "python"
print(str*3)
list0 = [1,3]
print(list0*5)

# 检查元素是否包含在序列中
# 格式： value in sequence
str1 = "c.biancheng"
print('c' in str1)
print('c' not in str1)

#找出最大的字符
print(max(str))
#找出最小的字符
print(min(str))
#对字符串中的元素进行排序
print(sorted(str))
```

    pythonpythonpython
    [1, 3, 1, 3, 1, 3, 1, 3, 1, 3]
    True
    False
    y
    h
    ['h', 'n', 'o', 'p', 't', 'y']
    

###  列表
#### 创建列表
- 直接创建：listname = [element1,element2.element3,...,elementn]
- 使用list()函数创建列表
- range()创建整数列表，**格式：range([strat],end,[step])**
- 推导式创建列表，如：list = [i for i in range(4)]
- 还可以用numpy 创建二维列表


```python
# del list      # 在juputer中运行list函数需要加上这一句，避免报错TypeError
#将字符串转换成列表
strTolist = list("12345")
print(strTolist)

#将元组转换成列表
tuple1 = ('Python', 'Java', 'C++', 'JavaScript')
tupleTolist = list(tuple1)
print(tupleTolist)

#将字典转换成列表
dict1 = {'a':100, 'b':42, 'c':9}
dicTolist = list(dict1)
print(dicTolist)

#将区间转换成列表
range1 = range(1, 6)
rangeTolist = list(range1)
print(rangeTolist)

#创建空列表
print(list())

# range()创建整数列表
print(list(range(3,15,2)))

```

    ['1', '2', '3', '4', '5']
    ['Python', 'Java', 'C++', 'JavaScript']
    ['a', 'b', 'c']
    [1, 2, 3, 4, 5]
    []
    [3, 5, 7, 9, 11, 13]
    

####  访问列表


```python
url = list("http://c.biancheng.net/shell/")

#使用索引访问列表中的某个元素
print(url[3])  #使用正数索引
print(url[-4])  #使用负数索引

#使用切片访问列表中的一组元素
print(url[9: 18])  #使用正数切片
print(url[9: 18: 3])  #指定步长
print(url[-6: -1])  #使用负数切片
print(url[::-1])  # 逆序
```

    p
    e
    ['b', 'i', 'a', 'n', 'c', 'h', 'e', 'n', 'g']
    ['b', 'n', 'e']
    ['s', 'h', 'e', 'l', 'l']
    ['/', 'l', 'l', 'e', 'h', 's', '/', 't', 'e', 'n', '.', 'g', 'n', 'e', 'h', 'c', 'n', 'a', 'i', 'b', '.', 'c', '/', '/', ':', 'p', 't', 't', 'h']
    


```python
group_list = [ 'Tom', 'Allen', 'Jane', 'William', 'Tony' ]
print(group_list[0:2])     # group_list[end] 的值不会输出
print(group_list[1:4])
print(group_list[3:5])
```

####  list列表删除列表


```python
intlist = [1, 45, 8, 34]
print(intlist)
del intlist
print(intlist)
```

####  list列表添加元素
- append()方法在列表末尾追加元素
- extend(obj)方法,obj可以是单个元素，也可以是列表，元组等，单不能是单个数字，一次添加多个。把一个列表添加到另一个列表 ，列表合并。
- insert()在列表某个位置插入元素，xxx.insert(index,obj)


```python
# 有问题！！！
l = ['Python', 'C++', 'Java']
#追加元素
l.append('PHP')

print(l)
#追加元组，整个元组被当成一个元素
t = ('JavaScript', 'C#', 'Go')
l.append(t)
print(l)
#追加列表，整个列表也被当成一个元素
l.append(['Ruby', 'SQL'])
print(l)

e = ['Python', 'C++', 'Java']
#追加元素
e.extend('C')
print(e)

#追加元组，元组被拆分成多个元素
e.extend(t)
print(e)

#追加列表，列表也被拆分成多个元素
e.extend(['Ruby', 'SQL'])
print(e)
```

    ['Python', 'C++', 'Java', 'PHP']
    ['Python', 'C++', 'Java', 'PHP', ('JavaScript', 'C#', 'Go')]
    ['Python', 'C++', 'Java', 'PHP', ('JavaScript', 'C#', 'Go'), ['Ruby', 'SQL']]
    ['Python', 'C++', 'Java', 'C']
    ['Python', 'C++', 'Java', 'C', 'JavaScript', 'C#', 'Go']
    ['Python', 'C++', 'Java', 'C', 'JavaScript', 'C#', 'Go', 'Ruby', 'SQL']
    


```python
ls = []
while True:
    str1 = input()
    if str1 != '0':
        ls.append(str1)
    else:
        break
print(" ".join(ls))
```

    qq
    qq
    wed
    0
    0
    

####  list列表删除元素
- del在列表末尾追加元素，可以删除单个列表元素或者一段连续的元素
- pop()方法：根据索引值删除元素
- remove()根据元素值进行删除，只能删除第一个出现的元素值
- clear()：删除列表所有元素


```python
import numpy as np
gamma = 3.136652095
alpha = 9.46232221
theta = 18.43494882
t = 90-gamma
a1 = np.tan(gamma*np.pi/180)
b1 = np.sin(alpha*np.pi/180)*np.tan(theta*np.pi/180)
a2 = np.tan(t*np.pi/180)
b2 = np.sin(theta*np.pi/180)*np.tan(alpha*np.pi/180)
print(a1,b1)
print(a2,b2)
```

    0.054799662438835224 0.054799662437133585
    18.248287589657156 0.05270462767260912
    

####  list列表查找元素
- index()方法：查找某个元素在列表中出现的位置（即查找索引）


```python
nums = [40, 36, 89, 2, 36, 100, 7, -20.5, -999]
#检索列表中的所有元素
print( nums.index(2) )
#检索3~7之间的元素
print( nums.index(100, 3, 7) )
#检索4之后的元素
print( nums.index(7, 4) )
#检索一个不存在的元素
print( nums.index(55) )
```

    3
    5
    6
    


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-1-bbc6c67300e3> in <module>
          7 print( nums.index(7, 4) )
          8 #检索一个不存在的元素
    ----> 9 print( nums.index(55) )
    

    ValueError: 55 is not in list


### tuple元组
#### 创建元组
** 元组和列表的区别：**
- 列表元素可更改，有修改元素值，增删元素，是可变序列
- 元组创建后，元素不可更改，是不可变序列
格式：（element1，element2,……，elementn）
元素的类型可以不同，如整数，字符串，列表，元组等，可以用type()函数验证


```python
# 需要注意的一点是，当创建的元组中只有一个字符串类型的元素时，该元素后面必须要加一个逗号,，否则 Python 解释器会将它视为字符串。
#最后加上逗号
a =("http://c.biancheng.net/cplus/",)
print(type(a))
print(a)

#最后不加逗号
b = ("http://c.biancheng.net/socket/")
print(type(b))
print(b)
```

    <class 'tuple'>
    ('http://c.biancheng.net/cplus/',)
    <class 'str'>
    http://c.biancheng.net/socket/
    

#### 使用tuple函数创建元组
格式：tuple(data)
data表示可以转成元组的数据，包括字符串，元组，range对象


```python
#将字符串转换成元组
tup1 = tuple("hello")
print(tup1)

#将列表转换成元组
list1 = ['Python', 'Java', 'C++', 'JavaScript']
tup2 = tuple(list1)
print(tup2)

#将字典转换成元组
dict1 = {'a':100, 'b':42, 'c':9}
tup3 = tuple(dict1)
print(tup3)

#将区间转换成元组
range1 = range(1, 6)
tup4 = tuple(range1)
print(tup4)

tup4 = tup3
print(tup4)
print(tup4==tup3)
tup4[2] = tup2[1]

#创建空元组
print(tuple())
```

    ('h', 'e', 'l', 'l', 'o')
    ('Python', 'Java', 'C++', 'JavaScript')
    ('a', 'b', 'c')
    (1, 2, 3, 4, 5)
    ('a', 'b', 'c')
    True
    


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-10-09a44b8e6134> in <module>
         21 print(tup4)
         22 print(tup4==tup3)
    ---> 23 tup4[2] = tup2[1]
         24 
         25 #创建空元组
    

    TypeError: 'tuple' object does not support item assignment


#### 访问元组元素
- 使用index：tuple[index],index可以为正数，也可以为负数
- 切片访问元组元素：tuple[start,end,step]


```python
tup = tuple('ghduigdhsag')

print(tup[3],'\n',tup[-1],'\n',tup[2:6],'\n',tup[1:7:2],'\n',tup[::-1])
```

    u 
     g 
     ('d', 'u', 'i', 'g') 
     ('h', 'u', 'g') 
     ('g', 'a', 's', 'h', 'd', 'g', 'i', 'u', 'd', 'h', 'g')
    

#### 修改元组
ps：元组是不可变序列，元组元素不可修改，只能重新创建新的元组去代替旧的


```python
# 重新赋值
tup = (100, 0.5, -36, 73)
print(tup)
#对元组进行重新赋值
tup = ('Shell脚本',"http://c.biancheng.net/shell/")
print(tup)

# 通过连接多个元组（使用+可以拼接元组）的方式向元组中添加新元素
tup1 = (100, 0.5, -36, 73)
tup2 = (3+12j, -54.6, 99)
print(tup1+tup2)
print(tup1)
print(tup2)
```

    (100, 0.5, -36, 73)
    ('Shell脚本', 'http://c.biancheng.net/shell/')
    (100, 0.5, -36, 73, (3+12j), -54.6, 99)
    (100, 0.5, -36, 73)
    ((3+12j), -54.6, 99)
    

#### 删除元组


```python
# 当创建的元组不再时，用del关键字删除
tup = tuple("gvhkguwak")
print(len(tup))
del tup
```

    9
    

#### <font color="red"> ☀ 元组和列表的区别：</font>
- 列表属于可变序列，它的元素可以随时修改或删除，元组是不可变序列，其中元素不可修改，只能整体替换。
- 列表可以使用append()、extend()、insert()、remove()和pop()等方法实现添加和修改，元组则没有这几个方法。
- 列表可以使用切片访问和修改列表中的元素，元组也支持切片，但是它只能通过切片访问。
- 元组比列表的访问和处理速度快，如果只需要访问不需要修改，建议使用元组。
- 列表不能作为字典的键，而元组则可以。


###  dict字典
定义：字典是一种无序的，可变的序列，以键值对（key-value）形式存储，是一种映射关系。
特征：
- 通过键来读取元素；
- 是任意数据类型的无序集合；
- 可变的，可嵌套的；
- 键是唯一的，若有重复，只保留最后一个键值对，且不可变的；


```python
a = {'one':1,'two':2,'three':3}
type(a)
```




    dict



#### 创建字典
- 使用{}创建，如：dictname = {'key':'value1', 'key2':'value2', ..., 'keyn':valuen}
- 通过dict()映射函数创建字典：
    * a = dict(str1=value1, str2=value2, str3=value3),字符串不能带引号
    * demo = [('two',2), ('one',1), ('three',3)] = [['two',2], ['one',1], ['three',3]]= (('two',2), ('one',1), ('three',3))= (['two',2], ['one',1], ['three',3])
     a = dict(demo)
    * keys = ['one', 'two', 'three'] #还可以是字符串或元组,values = [1, 2, 3] #还可以是字符串或元组,a = dict( zip(keys, values) )
- 通过dict.fromkeys()创建字典，如：dictname = dict.fromkeys(list，value=None),通常用来初始化字典，设置value的默认值
- 通过字典推导式创建


```python
""" 重点说明一下dict函数创建字典 """
# 1、用dict将二元组列表(n*2的二维列表，n*2的二维元组，列表元组)创建为字典
list1 = [('aaa',1),('bbb',2),('ccc',3)]
dict1 = dict(list1)
print(dict1)

# 2、用dict和关键字参数创建
dict2 = dict(a=1,b=2,c=3)
print(dict2)

# 3、将dict和zip结合创建字典
dict3 = dict(zip(['a','b','c'],[1,2,3]))
print(dict3)
dict31 = dict(zip('123','xyz'))
print(dict31)
dict32 = dict(zip(('a','b','c'),('x','y','z')))
print(dict32)
```

    {'aaa': 1, 'bbb': 2, 'ccc': 3}
    {'a': 1, 'b': 2, 'c': 3}
    {'a': 1, 'b': 2, 'c': 3}
    {'1': 'x', '2': 'y', '3': 'z'}
    {'a': 'x', 'b': 'y', 'c': 'z'}
    


```python
# 通过字典推导式创建
dict1 = {i:2*i for i in range(4)}
print(dict1)

# 通过dict.fromkeys()创建
dict2 = dict.fromkeys(range(3),'x')
print(dict2)

dict3 = dict()  # 创建空列表
```

    {0: 0, 1: 2, 2: 4, 3: 6}
    {0: 'x', 1: 'x', 2: 'x'}
    

#### 访问字典
- 用键值访问，格式：dictname[key]
- get()方法获取指定键对应的值，格式：dictname.get(key)


```python
# 1、直接访问
tup = (['two',25],['one',24],['three',20],['four',11])
dict1 = dict(tup)     # 映射法创建字典
print(dict1['one'])    # 键存在
# print(dict1['five'])    # 键不存在，会报错

# 2、get()函数访问
print(dict1.get('three'))
```

    24
    20
    


```python
result_dict = {'Allen': ['red', 'blue', 'yellow'],'Tom': ['green', 'white', 'blue'],'Andy': ['black', 'pink']}
result_dict = sorted(result_dict.items())
for k,v in result_dict:
    print("{}'s favorite color are:".format(k))
    for i in v:
        print(i)
```

    Allen's favorite color are:
    red
    blue
    yellow
    Andy's favorite color are:
    black
    pink
    Tom's favorite color are:
    green
    white
    blue
    

#### 字典添加键值对
- 直接添加，格式：dictname[key] = value


```python
a = dict(a=3,b=7,c=9)
print(a)
a['d'] = 10
print(a)
```

    {'a': 3, 'b': 7, 'c': 9}
    {'a': 3, 'b': 7, 'c': 9, 'd': 10}
    

#### 字典修改键值对
- 键值（key）不能被修改，只能修改value


```python
a = dict(a=3,b=7,c=9)
print(a)
a['d'] = 10
print(a)
a['d'] = 99
print(a)

# 用del删除键值对
del a['d']
print(a)

# 判断字典中是否存在指定键值对
print('b' in a)
```

    {'a': 3, 'b': 7, 'c': 9}
    {'a': 3, 'b': 7, 'c': 9, 'd': 10}
    {'a': 3, 'b': 7, 'c': 9, 'd': 99}
    {'a': 3, 'b': 7, 'c': 9}
    True
    

#### 删除字典


```python
a = dict(a=3,b=7,c=9)
print(a)
del a
```

#### 字典的一些方法
- keys(),values()和items()方法
    * keys() 方法用于返回字典中的所有键（key）；
    * values() 方法用于返回字典中所有键对应的值（value）；
    * items() 用于返回字典中所有的键值对（key-value）。
- copy()：返回一个字典的拷贝，也返回一个具有相同键值对的新字典,有深拷贝和浅拷贝
- update():使用一个字典所包含的键值对来更新已有的字典
- pop()：随机删除一个键值对,如：dictname.pop(key)
- popitem():随机删除一个键值对，如：dictname.popitem()
- setdefault():返回某个 key 对应的 value，格式：dictname.setdefault(key, defaultvalue)。
&emsp;也就是说，setdefault() 方法总能返回指定 key 对应的 value：
    * 如果该 key 存在，那么直接返回该 key 对应的 value；
    * 如果该 key 不存在，那么先为该 key 设置默认的 defaultvalue，然后再返回该 key 对应的 defaultvalue。


```python
scores = {'数学': 95, '语文': 89, '英语': 90}

# 1、使用list()把返回的数据转换成列表
b = list(a.keys())
print(b)

# 2、使用for in 循环遍历它们的返回值
for k in scores.keys():
    print(k,end=' ')
print("\n---------------")
for v in a.values():
    print(v,end=' ')
print("\n---------------")
for k,v in a.items():
    print("key:",k," value:",v)

# 3、copy()函数：既有深拷贝，也有浅拷贝。拿拷贝字典 a 为例，copy() 方法只会对最表层的键值对进行深拷贝，也就是说，它会再申请一块内存用来存放 {'one': 1, 'two': 2, 'three': []}；
# 而对于某些列表类型的值来说，此方法对其做的是浅拷贝，也就是说，b 中的 [1,2,3] 的值不是自己独有，而是和 a 共有。
A = {'one': 1, 'two': 2, 'three': [1,2,3]}
B = A.copy()
print(A==B)

# 4、update():使用一个字典所包含的键值对来更新已有的字典
c = {'数学': 85, '语文': 80}
print(scores.update(c))

# 5、pop()和popitem()
scores.pop('语文')
print(scores)
scores.popitem()
print(scores)

# 6、setdefault()

```

    ['a', 'b', 'c']
    数学 语文 英语 
    ---------------
    3 7 9 
    ---------------
    key: a  value: 3
    key: b  value: 7
    key: c  value: 9
    True
    

###  Set集合
- 格式：{element1,element2,...,elementn}
- 同一集合中只能存储不可变的数据类型，包括整形，浮点型，字符串，元组，无法存储列表，字典，集合这些可变的数据，否则会抛出TypeError错误。如{[1,2,3]},{{'a':1}},{{1,2,3}}都会报错。
- Python有两种集合类型，一种是set类型的集合，另一种是frozenset类型的集合

#### 创建set集合
- 1、使用{}直接创建
- 2、set()函数创建集合，如setname = set(iteration),iteration有字符串、列表、元组，range对象等数据


```python
# 直接{}创建
a = {1,'d',2,'c',(1,2,3)}
print(type(a))

# set()函数创建
set1 = set("guikgyukfg.com")
print(set1)
set2 = set([1,2,3])
print(set2)
set3 = set({'a':2,'b':3})
print(set3)
set4 = set((1,'a',(2,)))
print(set4)
print(type((2,)))
```

    <class 'set'>
    {'m', 'y', 'f', '.', 'i', 'k', 'c', 'o', 'g', 'u'}
    {1, 2, 3}
    {'a', 'b'}
    {1, 'a', (2,)}
    <class 'tuple'>
    

#### 访问set集合元素
- 集合是无序的，不能使用下标访问元素，只能用循环访问


```python
a = {1,'c',2,'c',(1,2,3)}
for ele in a:
    print(ele,end=' ')
```

#### set集合中添加元素
- add():添加单个元素，如：stename.add(element),element不能是可变类型（列表，字典，集合）
- update():添加多个元素，批式添加。如set1.update(elem)，就是添加elem中的元素到 set1,比如列表或集合


```python
a = {1,2,3}
a.add((1,2))
print(a)
# a.add([1.2])      # 会报错
# print(a)

a.update([3,4])
print(a)
```

    {(1, 2), 1, 2, 3}
    {1, 2, (1, 2), 3, 4}
    

#### 删除set中的元素
- remove():删除集合中的指定元素，格式：setname.remove(element)
- discard():和remove()不同的是，删除失败时不会报错
- pop():删除一个元素
- clear()：清空集合中所有元素


```python
a = {1,2,3}
a.remove(1)
print(a)
# print(a.remove(1))    # 因为集合中没有这个元素，所以会报KeyError错误
print(a.discard(1))
a.pop()
print(a)
a.clear()
print(a)
```

    {2, 3}
    None
    {3}
    set()
    

#### 删除set集合
- del()


```python
a = {1,'c',1,(1,2,3),'c'}
print(a)
del(a)
print(a)
```

#### set集合的交集，并集，差集运算
- 示意图如下：

![示意图](https://raw.githubusercontent.com/Lyy999110/YanimagesCloud/main/202208072027677.jpg)


```python
set1 = {1,2,3,'a','b','c'}
set2 = {4,2,3,'d','b','c'}
""" 一些集合关系判断函数 """
# isdisjoint()判断 set1 和 set2 是否没有交集，有交集返回 False；没有交集返回 True
print(set1.isdisjoint(set2))
# issubset()判断 set1 是否是 set2 的子集
print(set1.issubset(set2))
# issuperset()判断 set2 是否是 set1 的子集
print(set1.issuperset(set2))

set1 = {1,2,3,'a','b','c'}
set2 = {4,2,3,'d','b','c'}
print('""" 交集操作 """')
set_Cross1 = set1 & set2
# intersection()交集函数
set_Cross2 = set1.intersection(set2)
# intersection_update()直接将交集更新为set1
set1.intersection_update(set2)
print(set_Cross1,'\n',set_Cross2,'\n',set1,'\n')

set1 = {1,2,3,'a','b','c'}
set2 = {4,2,3,'d','b','c'}
print('""" 并集操作 """')
set_And1 = set1 | set2
# union()并集操作，取 set1 和 set2 的并集，赋给 set_And2
set_And2 = set1.union(set2)
# update()更新式添加
set1.update(set2)
print(set_And1,'\n',set_And2,'\n',set1,'\n')

set1 = {1,2,3,'a','b','c'}
set2 = {4,2,3,'d','b','c'}
print('""" 差集操作 """')
set_Sub1 = set1 - set2
# difference()函数实现差
set_Sub2 = set1.difference(set2)
# difference_update()直接将交集更新为set1
set1.difference_update(set2)
print(set_Sub1,'\n',set_Sub2,'\n',set1,'\n')

set1 = {1,2,3,'a','b','c'}
set2 = {4,2,3,'d','b','c'}
print('""" 对称差集操作 ""')
set_Sym1 = set1 ^ set2
# symmetric_difference()实现对称差操作
set_Sym2 = set1.symmetric_difference(set2)
# 对称差直接更新给set1
set1.symmetric_difference_update(set2)
print(set_Sym1,'\n',set_Sym2,'\n',set1,'\n')
```

    False
    False
    False
    """ 交集操作 """
    {2, 3, 'c', 'b'} 
     {2, 3, 'c', 'b'} 
     {2, 3, 'c', 'b'} 
    
    """ 并集操作 """
    {1, 2, 3, 'd', 4, 'c', 'b', 'a'} 
     {1, 2, 3, 'd', 4, 'c', 'b', 'a'} 
     {1, 2, 3, 'd', 4, 'b', 'c', 'a'} 
    
    """ 差集操作 """
    {1, 'a'} 
     {1, 'a'} 
     {1, 'a'} 
    
    """ 对称差集操作 ""
    {1, 'd', 4, 'a'} 
     {1, 'd', 4, 'a'} 
     {1, 'd', 4, 'a'} 
    
    

#### set集合方法
ps：使用dir(set)查看set函数相关的方法，有['add', 'clear', 'copy', 'difference', 'difference_update', 'discard', 'intersection', 'intersection_update', 'isdisjoint', 'issubset', 'issuperset', 'pop', 'remove', 'symmetric_difference', 'symmetric_difference_update', 'union', 'update']
- add():添加元素
- clear():清空集合中所有元素
- copy():拷贝set1给set2，即set2 = set1.copy()

| 方法名 | 语法格式 | 功能 |
| :----: | :----: | :----: |
| add() | set1.add() | 向 set1 集合中添加数字、字符串、元组或者布尔类型 |
|clear()|set1.clear()|清空 set1 集合中所有元素|
|copy()|set2 = set1.copy()|	拷贝 set1 集合给 set2|

#### ✨<font color="red">frozenset集合，set集合的不可变版本</font>
PS：dir(frozenset)可得到frozenset集合的相关函数：['copy', 'difference', 'intersection', 'isdisjoint', 'issubset', 'issuperset', 'symmetric_difference', 'union']
- 使用frozenset集合的两种情况：
    * 当集合的元素不需要改变时，我们可以使用 fronzenset 替代 set，这样更加安全。
    * 有时候程序要求必须是不可变对象，这个时候也要使用 fronzenset 替代 set。比如，字典（dict）的键（key）就要求是不可变对象。


```python
s = {'Python', 'C', 'C++'}
fs = frozenset(['Java', 'Shell'])
s_sub = {'PHP', 'C#'}
#向set集合中添加frozenset
s.add(fs)
print('s =', s)
#向为set集合添加子set集合，
s.add(s_sub)
print('s =', s)
```

    s = {frozenset({'Java', 'Shell'}), 'C', 'C++', 'Python'}
    


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-26-f8f60b8c1da9> in <module>
          6 print('s =', s)
          7 #向为set集合添加子set集合
    ----> 8 s.add(s_sub)
          9 print('s =', s)
    

    TypeError: unhashable type: 'set'


## 1.3 流程控制
- if
- if ... else ...
- if ... elif ... else ...，是多条件判断的
- if (if ... else ...) else ...，是可嵌套的
- while ...
- while ... else ...
- for ... else ...,  for和while都是可嵌套的

###  assert断言函数及其用法
- 语法结构： assert 表达式。
- 意义：与其让程序在晚些时候崩溃，不如在错误条件出现时，就直接让程序崩溃，这有利于我们对程序排错，提高程序的健壮性。



```python
mathmark = int(input())
#断言数学考试分数是否位于正常范围内
assert 0 <= mathmark <= 100
#只有当 mathmark 位于 [0,100]范围内，程序才会继续执行
print("数学考试分数为：",mathmark)
```

    2
    数学考试分数为： 2
    


```python
# for 循环
add = "http://c.biancheng.net/python/"
#for循环，遍历 add 字符串
for ch in add:
print(ch,end="")           # end=""在print()函数中，表示关闭“在输出中自动包含换行”的默认行为
```

### 终止循环体的方法
- break：完全终止当前循环
- continue：可以跳过执行本次循环体的剩余代码，转而执行下一次循环


```python
# for...else ... 用法示例
add = "http://c.biancheng.net/python/,http://c.biancheng.net/shell/"
for i in add:
    if i == ',' :
        #终止循环
        break
    print(i,end="")
else:
    print("执行 else 语句中的代码")
print("\n执行循环体外的代码")

# break只会终止所在循环体的执行，不会作用于所有循环体。
add = "http://c.biancheng.net/python/,http://c.biancheng.net/shell/"
for i in range(3):
    for j in add:
        if j == ',':
            break   
        print(j,end="")
    print("\n跳出内循环")
```


```python
# continue 的用法
add = "http://c.biancheng.net/python/,http://c.biancheng.net/shell/"
# 一个简单的for循环
for i in add:
    if i == ',' :
        # 忽略本次循环的剩下语句
        print('\n')
        continue
    print(i,end="")
```

### <font color = "red"> zip，reversed 和sorted函数</font>


```python
# zip（）
my_list = [11,12,13]
my_tuple = (21,22,23)
print([x for x in zip(my_list,my_tuple)])
my_dic = {31:2,32:4,33:5}
my_set = {41,42,43,44}
print([x for x in zip(my_dic)])
my_pychar = "python"
my_shechar = "shell"
print(list(zip(my_pychar,my_shechar)))
```

    [(11, 21), (12, 22), (13, 23)]
    [(31,), (32,), (33,)]
    [('p', 's'), ('y', 'h'), ('t', 'e'), ('h', 'l'), ('o', 'l')]
    


```python
user_names = list(input().split(" "))
languages = list(input().split(" "))
dict1 = dict(zip(user_names,languages))
print(dict1)
```

    nn ko sdd
    go java c
    {'nn': 'go', 'ko': 'java', 'sdd': 'c'}
    


```python
# reversed（）
#将列表进行逆序
print([x for x in reversed([1,2,3,4,5])])
#将元组进行逆序
print([x for x in reversed((1,2,3,4,5))])
#将字符串进行逆序
print([x for x in reversed("abcdefg")])
#将 range() 生成的区间列表进行逆序
print(list(reversed(range(10))))
```

    [5, 4, 3, 2, 1]
    [5, 4, 3, 2, 1]
    ['g', 'f', 'e', 'd', 'c', 'b', 'a']
    [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
    


```python
# sorted()函数
#对列表进行排序
a = [5,3,4,2,1]
print(sorted(a))
"""sorted和sortde 不同，内置sorted返回一个新的列表，而list.sort是对列表进行操作"""
a.sort(reverse = True)     
#对元组进行排序
a = (5,4,3,1,2)
print(sorted(a))
#字典默认按照key进行排序
a = {4:1,\
     5:2,\
     3:3,\
     2:6,\
     1:8}
print(sorted(a.items()))
#对集合进行排序
a = {1,5,3,2,4}
print(sorted(a))
#对字符串进行排序
a = "51423"
print(sorted(a))

#对列表进行降序排序
a = [5,3,4,2,1]
print(sorted(a,reverse=True))

```

    [1, 2, 3, 4, 5]
    [1, 2, 3, 4, 5]
    [(1, 8), (2, 6), (3, 3), (4, 1), (5, 2)]
    [1, 2, 3, 4, 5]
    ['1', '2', '3', '4', '5']
    [5, 4, 3, 2, 1]
    


```python
"""sorted(iterable, cmp=None, key=None, reverse=False)
iterable：是可迭代类型;
cmp：用于比较的函数，比较什么由key决定;
key：用列表元素的某个属性或函数进行作为关键字，有默认值，迭代集合中的一项;
reverse：排序规则. reverse = True  降序 或者 reverse = False 升序，有默认值。
返回值：是一个经过排序的可迭代类型，与iterable一样
"""
# 下面代码有点问题
myList = ['青海省','内蒙古自治区','西藏自治区','新疆维吾尔自治区','广西壮族自治区']
newlist = sorted(myList,lambda i:len(i),reverse=True)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-4-a26c7dac91b3> in <module>
          7 """
          8 myList = ['青海省','内蒙古自治区','西藏自治区','新疆维吾尔自治区','广西壮族自治区']
    ----> 9 newlist = sorted(myList,lambda i:len(i),reverse=True)
    

    TypeError: sorted expected 1 argument, got 2


### lambda表达式（匿名函数）
- 格式： name = lambda[list]:表达式,list是可选参数
 * 转成普通函数形式，即：
 ```
 def name(list):
     return 表达式
 name(list)
```
 
- 优势：
 * 对于单行函数，使用lambda表达式可以省去定义函数的过程，让代码更加简洁
 * 对于不需要多次复用的函数，使用lambda表达式可以在用完之后立即释放，提高程序执行的性能


```python
def add(x, y):
    return x+ y
print(add(3,4))

add1 = lambda x,y:x+y
add1(3,4)
```

    7
    




    7



### 值传递和引用传递
- 值传递：适用于实参类型为不可变类型（字符串、数字、元组）；
- 引用（地址）传递：适用于实参类型为可变类型（列表，字典）；


```python
def demo(obj) :
    obj += obj
    print("形参值为：",obj)
print("-------值传递-----")
a = "C语言中文网"
print("a的值为：",a)
demo(a)
print("实参值为：",a)
print("-----引用传递-----")
a = [1,2,3]
print("a的值为：",a)
demo(a)
print("实参值为：",a)
b = ('a','b','c')
demo(b)
print("函数运行后b：",b)

```

    -------值传递-----
    a的值为： C语言中文网
    形参值为： C语言中文网C语言中文网
    实参值为： C语言中文网
    -----引用传递-----
    a的值为： [1, 2, 3]
    形参值为： [1, 2, 3, 1, 2, 3]
    实参值为： [1, 2, 3, 1, 2, 3]
    形参值为： ('a', 'b', 'c', 'a', 'b', 'c')
    函数运行后b： ('a', 'b', 'c')
    

### 函数关键字参数用法
- 关键字参数：指使用形式参数的名字来确定输入的参数值。通过此方式指定函数实参时，不再需要与形参的位置完全一致，只要将参数名写正确即可。
- 再次强调，当定义一个有默认值参数的函数时，有默认值的参数必须位于所有没默认值参数的后面。


```python
def dis_str(str1,str2):
    print("str1:",str1)
    print("str2:",str2)
#位置参数
dis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")
#关键字参数
dis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")
dis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")

# 位置参数必须放在关键字参数之前，下面代码错误
# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")

# 当定义一个有默认值参数的函数时，有默认值的参数必须位于所有没默认值参数的后面
# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组
print("================================")
def dis_s(s1,s2,s3="http://c.biancheng.net/python/"):
    pass
print(dis_s.__defaults__)

```

    str1: http://c.biancheng.net/python/
    str2: http://c.biancheng.net/shell/
    str1: http://c.biancheng.net/python/
    str2: http://c.biancheng.net/shell/
    str1: http://c.biancheng.net/shell/
    str2: http://c.biancheng.net/python/
    ================================
    ('http://c.biancheng.net/python/',)
    

#### None(空值)及其用法
- 一个特殊的常量 None（N 必须大写）。和 False 不同，它不表示 0，也不表示空字符串，而表示没有值，也就是空值。
- 在其他语言中，就是Null，nil，或者undefined。


```python
print(None == '')
print(None == 0)
print(type(None))
```

    False
    False
    <class 'NoneType'>
    

### 获取指定作用域范围中的变量
- globals()函数：返回一个包含全局范围内所有变量的字典，该字典中的每个键值对，键为变量名，值为该变量的值。
- locals()函数：返回一个包含当前作用域内所有变量的字典
- vars(object):返回一个指定 object 对象范围内所有变量组成的字典。如果不传入object 参数，vars() 和 locals() 的作用完全相同。


```python
#全局变量
Pyname = "Python教程"
Pyadd = "http://c.biancheng.net/python/"
def text():
    #局部变量
    Shename = "shell教程"
    Sheadd= "http://c.biancheng.net/shell/"
print(globals())
print(globals()['Pyname'])
```

    {'__name__': '__main__', '__doc__': 'Automatically created module for IPython interactive environment', '__package__': None, '__loader__': None, '__spec__': None, '__builtin__': <module 'builtins' (built-in)>, '__builtins__': <module 'builtins' (built-in)>, '_ih': ['', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\nprint(tup)\n66/3.36', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n66/3.36', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n78/1.75/1.75', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n82/1.75/1.75', 'mathmark = int(input())\n#断言数学考试分数是否位于正常范围内\nassert 0 <= mathmark <= 100\n#只有当 mathmark 位于 [0,100]范围内，程序才会继续执行\nprint("数学考试分数为：",mathmark)', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint([x for x in zip(my_pychar,my_shechar)])', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar))', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar)))', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint([x for x in reversed(range(10))])', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10)))', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10))))', '# sorted()函数\n#对列表进行排序\na = [5,3,4,2,1]\nprint(sorted(a))\n#对元组进行排序\na = (5,4,3,1,2)\nprint(sorted(a))\n#字典默认按照key进行排序\na = {4:1,\\\n     5:2,\\\n     3:3,\\\n     2:6,\\\n     1:8}\nprint(sorted(a.items()))\n#对集合进行排序\na = {1,5,3,2,4}\nprint(sorted(a))\n#对字符串进行排序\na = "51423"\nprint(sorted(a))', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\',\'b\',\'c\'}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\':1,\'b\':2,\'c\':3}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_str1(str1="http://c.biancheng.net/python/",str2,str3):\n    pass\nprint(dis_str1.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1="http://c.biancheng.net/python/",s2,s3):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,"http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://b.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 当定义一个有默认值参数的函数时，有默认值的参数必须位于所有没默认值参数的后面\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\nprint("================================")\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', "print(None == '')\nprint(None == 0)\nprint(type(None))", '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\']))', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])'], '_oh': {2: 19.642857142857142, 3: 25.46938775510204, 4: 26.77551020408163}, '_dh': ['F:\\my_jupyter\\python3_basic\\02_BasicA'], 'In': ['', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\nprint(tup)\n66/3.36', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n66/3.36', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n78/1.75/1.75', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n82/1.75/1.75', 'mathmark = int(input())\n#断言数学考试分数是否位于正常范围内\nassert 0 <= mathmark <= 100\n#只有当 mathmark 位于 [0,100]范围内，程序才会继续执行\nprint("数学考试分数为：",mathmark)', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint([x for x in zip(my_pychar,my_shechar)])', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar))', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar)))', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint([x for x in reversed(range(10))])', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10)))', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10))))', '# sorted()函数\n#对列表进行排序\na = [5,3,4,2,1]\nprint(sorted(a))\n#对元组进行排序\na = (5,4,3,1,2)\nprint(sorted(a))\n#字典默认按照key进行排序\na = {4:1,\\\n     5:2,\\\n     3:3,\\\n     2:6,\\\n     1:8}\nprint(sorted(a.items()))\n#对集合进行排序\na = {1,5,3,2,4}\nprint(sorted(a))\n#对字符串进行排序\na = "51423"\nprint(sorted(a))', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\',\'b\',\'c\'}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\':1,\'b\':2,\'c\':3}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_str1(str1="http://c.biancheng.net/python/",str2,str3):\n    pass\nprint(dis_str1.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1="http://c.biancheng.net/python/",s2,s3):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,"http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://b.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 当定义一个有默认值参数的函数时，有默认值的参数必须位于所有没默认值参数的后面\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\nprint("================================")\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', "print(None == '')\nprint(None == 0)\nprint(type(None))", '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\']))', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])'], 'Out': {2: 19.642857142857142, 3: 25.46938775510204, 4: 26.77551020408163}, 'get_ipython': <bound method InteractiveShell.get_ipython of <ipykernel.zmqshell.ZMQInteractiveShell object at 0x000001FAF941E700>>, 'exit': <IPython.core.autocall.ZMQExitAutocall object at 0x000001FAF9499FD0>, 'quit': <IPython.core.autocall.ZMQExitAutocall object at 0x000001FAF9499FD0>, '_': 26.77551020408163, '__': 25.46938775510204, '___': 19.642857142857142, '_i': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '_ii': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\']))', '_iii': "print(None == '')\nprint(None == 0)\nprint(type(None))", '_i1': '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\nprint(tup)\n66/3.36', '_i2': '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n66/3.36', '_2': 19.642857142857142, '_i3': '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n78/1.75/1.75', '_3': 25.46938775510204, '_i4': '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n82/1.75/1.75', '_4': 26.77551020408163, '_i5': 'mathmark = int(input())\n#断言数学考试分数是否位于正常范围内\nassert 0 <= mathmark <= 100\n#只有当 mathmark 位于 [0,100]范围内，程序才会继续执行\nprint("数学考试分数为：",mathmark)', 'mathmark': 2, '_i6': '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint([x for x in zip(my_pychar,my_shechar)])', 'my_list': [11, 12, 13], 'my_tuple': (21, 22, 23), 'my_dic': {31: 2, 32: 4, 33: 5}, 'my_set': {41, 42, 43, 44}, 'my_pychar': 'python', 'my_shechar': 'shell', '_i7': '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar))', '_i8': '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar)))', '_i9': '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint([x for x in reversed(range(10))])', '_i10': '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10)))', '_i11': '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10))))', '_i12': '# sorted()函数\n#对列表进行排序\na = [5,3,4,2,1]\nprint(sorted(a))\n#对元组进行排序\na = (5,4,3,1,2)\nprint(sorted(a))\n#字典默认按照key进行排序\na = {4:1,\\\n     5:2,\\\n     3:3,\\\n     2:6,\\\n     1:8}\nprint(sorted(a.items()))\n#对集合进行排序\na = {1,5,3,2,4}\nprint(sorted(a))\n#对字符串进行排序\na = "51423"\nprint(sorted(a))', 'a': [1, 2, 3, 1, 2, 3], '_i13': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)', 'demo': <function demo at 0x000001FAF95151F0>, '_i14': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\',\'b\',\'c\'}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'b': ('a', 'b', 'c'), '_i15': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\':1,\'b\':2,\'c\':3}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', '_i16': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', '_i17': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)', '_i18': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_str1(str1="http://c.biancheng.net/python/",str2,str3):\n    pass\nprint(dis_str1.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', '_i19': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1="http://c.biancheng.net/python/",s2,s3):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', '_i20': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'dis_str': <function dis_str at 0x000001FAF95DEC10>, 'dis_s': <function dis_s at 0x000001FAF95E7280>, '_i21': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,"http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i22': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i23': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://b.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i24': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i25': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 当定义一个有默认值参数的函数时，有默认值的参数必须位于所有没默认值参数的后面\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\nprint("================================")\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i26': "print(None == '')\nprint(None == 0)\nprint(type(None))", '_i27': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\']))', '_i28': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', 'Pyname': 'Python教程', 'Pyadd': 'http://c.biancheng.net/python/', 'text': <function text at 0x000001FAF95DED30>, '_i29': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])'}
    Python教程
    


```python
#全局变量
Pyname = "Python教程"
Pyadd = "http://c.biancheng.net/python/"
def text():
    #局部变量
    Shename = "shell教程"
    Sheadd= "http://c.biancheng.net/shell/"
    print("函数内部的 locals:")
    print(locals())
    
    # locals()通过指定键访问对应的变量值，但无法对变量值做修改
    print(locals()['Shename'])
    locals()['Shename'] = "shell入门教程"
    print(Shename)
    
text()
print("函数外部的 locals:")
print(locals())
```

    函数内部的 locals:
    {'Shename': 'shell教程', 'Sheadd': 'http://c.biancheng.net/shell/'}
    函数外部的 locals:
    {'__name__': '__main__', '__doc__': 'Automatically created module for IPython interactive environment', '__package__': None, '__loader__': None, '__spec__': None, '__builtin__': <module 'builtins' (built-in)>, '__builtins__': <module 'builtins' (built-in)>, '_ih': ['', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\nprint(tup)\n66/3.36', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n66/3.36', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n78/1.75/1.75', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n82/1.75/1.75', 'mathmark = int(input())\n#断言数学考试分数是否位于正常范围内\nassert 0 <= mathmark <= 100\n#只有当 mathmark 位于 [0,100]范围内，程序才会继续执行\nprint("数学考试分数为：",mathmark)', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint([x for x in zip(my_pychar,my_shechar)])', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar))', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar)))', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint([x for x in reversed(range(10))])', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10)))', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10))))', '# sorted()函数\n#对列表进行排序\na = [5,3,4,2,1]\nprint(sorted(a))\n#对元组进行排序\na = (5,4,3,1,2)\nprint(sorted(a))\n#字典默认按照key进行排序\na = {4:1,\\\n     5:2,\\\n     3:3,\\\n     2:6,\\\n     1:8}\nprint(sorted(a.items()))\n#对集合进行排序\na = {1,5,3,2,4}\nprint(sorted(a))\n#对字符串进行排序\na = "51423"\nprint(sorted(a))', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\',\'b\',\'c\'}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\':1,\'b\':2,\'c\':3}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_str1(str1="http://c.biancheng.net/python/",str2,str3):\n    pass\nprint(dis_str1.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1="http://c.biancheng.net/python/",s2,s3):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,"http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://b.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 当定义一个有默认值参数的函数时，有默认值的参数必须位于所有没默认值参数的后面\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\nprint("================================")\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', "print(None == '')\nprint(None == 0)\nprint(type(None))", '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\']))', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\n    print("函数内部的 locals:")\n    print(locals())\ntext()\nprint("函数外部的 locals:")\nprint(locals())'], '_oh': {2: 19.642857142857142, 3: 25.46938775510204, 4: 26.77551020408163}, '_dh': ['F:\\my_jupyter\\python3_basic\\02_BasicA'], 'In': ['', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\nprint(tup)\n66/3.36', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n66/3.36', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n78/1.75/1.75', '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n82/1.75/1.75', 'mathmark = int(input())\n#断言数学考试分数是否位于正常范围内\nassert 0 <= mathmark <= 100\n#只有当 mathmark 位于 [0,100]范围内，程序才会继续执行\nprint("数学考试分数为：",mathmark)', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint([x for x in zip(my_pychar,my_shechar)])', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar))', '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar)))', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint([x for x in reversed(range(10))])', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10)))', '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10))))', '# sorted()函数\n#对列表进行排序\na = [5,3,4,2,1]\nprint(sorted(a))\n#对元组进行排序\na = (5,4,3,1,2)\nprint(sorted(a))\n#字典默认按照key进行排序\na = {4:1,\\\n     5:2,\\\n     3:3,\\\n     2:6,\\\n     1:8}\nprint(sorted(a.items()))\n#对集合进行排序\na = {1,5,3,2,4}\nprint(sorted(a))\n#对字符串进行排序\na = "51423"\nprint(sorted(a))', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\',\'b\',\'c\'}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\':1,\'b\':2,\'c\':3}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_str1(str1="http://c.biancheng.net/python/",str2,str3):\n    pass\nprint(dis_str1.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1="http://c.biancheng.net/python/",s2,s3):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,"http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://b.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 当定义一个有默认值参数的函数时，有默认值的参数必须位于所有没默认值参数的后面\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\nprint("================================")\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', "print(None == '')\nprint(None == 0)\nprint(type(None))", '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\']))', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\n    print("函数内部的 locals:")\n    print(locals())\ntext()\nprint("函数外部的 locals:")\nprint(locals())'], 'Out': {2: 19.642857142857142, 3: 25.46938775510204, 4: 26.77551020408163}, 'get_ipython': <bound method InteractiveShell.get_ipython of <ipykernel.zmqshell.ZMQInteractiveShell object at 0x000001FAF941E700>>, 'exit': <IPython.core.autocall.ZMQExitAutocall object at 0x000001FAF9499FD0>, 'quit': <IPython.core.autocall.ZMQExitAutocall object at 0x000001FAF9499FD0>, '_': 26.77551020408163, '__': 25.46938775510204, '___': 19.642857142857142, '_i': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '_ii': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '_iii': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\']))', '_i1': '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\nprint(tup)\n66/3.36', '_i2': '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n66/3.36', '_2': 19.642857142857142, '_i3': '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n78/1.75/1.75', '_3': 25.46938775510204, '_i4': '# 当创建的元组不再时，用del关键字删除\ntup = tuple("gvhkguwak")\ndel tup\n# print(tup)\n82/1.75/1.75', '_4': 26.77551020408163, '_i5': 'mathmark = int(input())\n#断言数学考试分数是否位于正常范围内\nassert 0 <= mathmark <= 100\n#只有当 mathmark 位于 [0,100]范围内，程序才会继续执行\nprint("数学考试分数为：",mathmark)', 'mathmark': 2, '_i6': '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint([x for x in zip(my_pychar,my_shechar)])', 'my_list': [11, 12, 13], 'my_tuple': (21, 22, 23), 'my_dic': {31: 2, 32: 4, 33: 5}, 'my_set': {41, 42, 43, 44}, 'my_pychar': 'python', 'my_shechar': 'shell', '_i7': '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar))', '_i8': '# zip（）\nmy_list = [11,12,13]\nmy_tuple = (21,22,23)\nprint([x for x in zip(my_list,my_tuple)])\nmy_dic = {31:2,32:4,33:5}\nmy_set = {41,42,43,44}\nprint([x for x in zip(my_dic)])\nmy_pychar = "python"\nmy_shechar = "shell"\nprint(list(zip(my_pychar,my_shechar)))', '_i9': '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint([x for x in reversed(range(10))])', '_i10': '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10)))', '_i11': '# reversed（）\n#将列表进行逆序\nprint([x for x in reversed([1,2,3,4,5])])\n#将元组进行逆序\nprint([x for x in reversed((1,2,3,4,5))])\n#将字符串进行逆序\nprint([x for x in reversed("abcdefg")])\n#将 range() 生成的区间列表进行逆序\nprint(list(reversed(range(10))))', '_i12': '# sorted()函数\n#对列表进行排序\na = [5,3,4,2,1]\nprint(sorted(a))\n#对元组进行排序\na = (5,4,3,1,2)\nprint(sorted(a))\n#字典默认按照key进行排序\na = {4:1,\\\n     5:2,\\\n     3:3,\\\n     2:6,\\\n     1:8}\nprint(sorted(a.items()))\n#对集合进行排序\na = {1,5,3,2,4}\nprint(sorted(a))\n#对字符串进行排序\na = "51423"\nprint(sorted(a))', 'a': [1, 2, 3, 1, 2, 3], '_i13': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)', 'demo': <function demo at 0x000001FAF95151F0>, '_i14': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\',\'b\',\'c\'}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', 'b': ('a', 'b', 'c'), '_i15': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = {\'a\':1,\'b\':2,\'c\':3}\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', '_i16': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)\nprint("实参值为：",a)', '_i17': 'def demo(obj) :\n    obj += obj\n    print("形参值为：",obj)\nprint("-------值传递-----")\na = "C语言中文网"\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nprint("-----引用传递-----")\na = [1,2,3]\nprint("a的值为：",a)\ndemo(a)\nprint("实参值为：",a)\nb = (\'a\',\'b\',\'c\')\ndemo(b)\nprint("函数运行后b：",b)', '_i18': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_str1(str1="http://c.biancheng.net/python/",str2,str3):\n    pass\nprint(dis_str1.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', '_i19': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1="http://c.biancheng.net/python/",s2,s3):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', '_i20': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")', 'dis_str': <function dis_str at 0x000001FAF95DEC10>, 'dis_s': <function dis_s at 0x000001FAF95E7280>, '_i21': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,"http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i22': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://c.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i23': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s("http://b.biancheng.net/python/",s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i24': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i25': 'def dis_str(str1,str2):\n    print("str1:",str1)\n    print("str2:",str2)\n#位置参数\ndis_str("http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n#关键字参数\ndis_str("http://c.biancheng.net/python/",str2="http://c.biancheng.net/shell/")\ndis_str(str2="http://c.biancheng.net/python/",str1="http://c.biancheng.net/shell/")\n\n# 位置参数必须放在关键字参数之前，下面代码错误\n# dis_str(str1="http://c.biancheng.net/python/","http://c.biancheng.net/shell/")\n\n# 当定义一个有默认值参数的函数时，有默认值的参数必须位于所有没默认值参数的后面\n# 可以使用“函数名.__defaults__”查看函数的默认值参数的当前值，其返回值是一个元组\nprint("================================")\ndef dis_s(s1,s2,s3="http://c.biancheng.net/python/"):\n    pass\nprint(dis_s.__defaults__)', '_i26': "print(None == '')\nprint(None == 0)\nprint(type(None))", '_i27': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\']))', '_i28': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', 'Pyname': 'Python教程', 'Pyadd': 'http://c.biancheng.net/python/', 'text': <function text at 0x000001FAF9591F70>, '_i29': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\nprint(globals())\nprint(globals()[\'Pyname\'])', '_i30': '#全局变量\nPyname = "Python教程"\nPyadd = "http://c.biancheng.net/python/"\ndef text():\n    #局部变量\n    Shename = "shell教程"\n    Sheadd= "http://c.biancheng.net/shell/"\n    print("函数内部的 locals:")\n    print(locals())\ntext()\nprint("函数外部的 locals:")\nprint(locals())'}
    

```
程序输出：
函数内部的 locals:
{'Sheadd': 'http://c.biancheng.net/shell/', 'Shename': 'shell教程'}
shell教程
shell教程
函数外部的 locals:
{...... , 'Pyname': 'Python教程', 'Pyadd': 'http://c.biancheng.net/python/', ...... }
```


```python
# vars(object)
 #全局变量
Pyname = "Python教程"
Pyadd = "http://c.biancheng.net/python/"
class Demo:
    name = "Python 教程"
    add = "http://c.biancheng.net/python/"
print("有 object：")
print(vars(Demo))   # 打印Demo对象中的变量，以字典格式输出
print("无 object：")
print(vars())
```

```
程序输出：
有 object：
{...... , 'name': 'Python 教程', 'add': 'http://c.biancheng.net/python/', ......}
无 object：
{...... , 'Pyname': 'Python教程', 'Pyadd': 'http://c.biancheng.net/python/', ...... }
```

####   局部函数及用法（还有nonlocal关键字）
- 局部函数：Python支持在函数内部定义函数，此类函数又称为局部函数


```python
# 全局变量
def outdef():
    # 局部函数
    def indef():
        print("this is a local function")
    # 调用局部函数
    indef()
# 调用全局函数
outdef()
```


```python
# 就如同全局函数返回其局部变量，就可以扩大该变量的作用域一样，通过将局部函数作为所在函数的返回值，
# 也可以扩大局部函数的使用范围。例如，修改上面程序为
def outdef ():
    #局部函数
    def indef():
        print("调用局部函数")
    #调用局部函数
    return indef
# 调用全局函数
new_indef = outdef()
# 调用全局函数中的局部函数
new_indef()
```

    调用局部函数
    


```python
# 如果局部函数中定义有和所在函数中变量同名的变量，也会发生“遮蔽”的问题
#全局函数
def outdef ():
    name = "所在函数中定义的 name 变量"
    #局部函数
    def indef():
        print(name)
        name = "局部函数中定义的 name 变量"    # 这里会发生错误，1、print函数找不到name；2、遮蔽了局部定义的name
    indef()
#调用全局函数
outdef()
```


    ---------------------------------------------------------------------------

    UnboundLocalError                         Traceback (most recent call last)

    <ipython-input-4-41f8207725dd> in <module>
         10     indef()
         11 #调用全局函数
    ---> 12 outdef()
    

    <ipython-input-4-41f8207725dd> in outdef()
          8         print(name)
          9         name = "局部函数中定义的 name 变量"
    ---> 10     indef()
         11 #调用全局函数
         12 outdef()
    

    <ipython-input-4-41f8207725dd> in indef()
          6     def indef():
          7 #         name = "局部函数中定义的 name 变量"
    ----> 8         print(name)
          9         name = "局部函数中定义的 name 变量"
         10     indef()
    

    UnboundLocalError: local variable 'name' referenced before assignment



```python
""" 使用nonlocal关键字,使得局部变量与外部变量统一化 """
#全局函数
def outdef ():
    name = "所在函数中定义的 name 变量"
    #局部函数
    def indef():
        nonlocal name
        print(name)
        #修改name变量的值
        name = "局部函数中定义的 name 变量"
        print(name)
    indef()
#调用全局函数
outdef()
```

    所在函数中定义的 name 变量
    局部函数中定义的 name 变量
    

### 闭包
- 闭包：又称闭包函数或者闭合函数，其实和前面讲的嵌套函数类似，不同之处在于，闭包中外部函数返回的不是一个具体的值，而是一个函数。一般情况下，返回的函数会赋值给一个变量，这个变量可以在后面被继续执行调用。


```python
# 闭包函数，其中exponent称为自由变量
def nth_power(exponent):
    def exponent_of(base):
        return base**exponent
    return exponent_of      # 返回值是exponent_of函数
square = nth_power(2)    # 计算一个数的平方
cube = nth_power(3)    # 计算一个数的立方

print(square(2))  # 计算 2 的平方
print(cube(2)) # 计算 2 的立方
```

    4
    8
    


```python
# 闭包的优点
def nth_power_rewrite(base, exponent):
    return base ** exponent
# 不使用闭包
res1 = nth_power_rewrite(base1, 2)
res2 = nth_power_rewrite(base2, 2)
res3 = nth_power_rewrite(base3, 2)

# 使用闭包的话
square = nth_power(2)
res1 = square(base1)
res2 = square(base2)
res3 = square(base3)
# 显然，第二种方法更简洁，少传入一个参数
```

#### 闭包的__closure__属性
- 该属性记录着自由变量的地址，当闭包被调用时，系统就会根据该地址找到对应的自由变量，完成整体的函数调用



```python
# 以 nth_power() 为例，当其被调用时，可以通过 __closure__ 属性获取自由变量（也就是程序中的 exponent 参数）存储的地址
def nth_power(exponent):
    def exponent_of(base):
        return base ** exponent
    return exponent_of
square = nth_power(2)
#查看 __closure__ 的值
print(square.__closure__)
```

    (<cell at 0x000002AA04B6AC40: int object at 0x00007FFC1B733740>,)
    

# 二、函数集合篇

##  基础函数

### input()函数：获取用户输入的函数
    * 我们可以使用 Python 内置函数将字符串转换成想要的类型，比如：
    * int(string) 将字符串转换成 int 类型；
    * float(string) 将字符串转换成 float 类型；
    * bool(string) 将字符串转换成 bool 类型。


```python
a = input("Enter a number: ")
b = input("Enter another number: ")
a1 = float(a)
b1 = int(b)
print("aType: ", type(a))
print("b1Type: ", type(b1))

result1 = a + b
result2 = a1 + b1
print("result1Value: ", result1)
print("result1Type: ", type(result1))
print("result2Value: ", result2)
print("result2Type: ", type(result2))
```

    Enter a number: 11
    Enter another number: 110
    aType:  <class 'str'>
    b1Type:  <class 'int'>
    resultValue:  11110
    resultType:  <class 'str'>
    resultValue:  121.0
    resultType:  <class 'float'>
    

###  print()函数：使用%开头的转换说明符对各种类型数据进行格式化输出
    - ps：转换说明符：只是一个占位符，它会被后面表达式（变量、常量、数字、字符串、加减乘除等各种形式）的值代替
    

 
| 转换说明符 | 解释 |
|:----|:----:|
| %d、%i | 转换为带符号的十进制整数  |
| %o| 转换为带符号的八进制整数  |
| %x、%X | 转换为带符号的十六进制整数  |
| %e、%E |  转化为科学计数法表示的浮点数，e表示小写，E即大写  |
| %f、%F | 转化为十进制浮点数  |
| %g | 智能选择使用%f或%e格式  |
| %G | 智能选择使用%F或%E格式  |
| %c | 格式化字符及其ASCII码  |
| %r | 使用repr()函数将表达式转换为字符串  |
| %s | 使用str()函数将表达是转换为字符串 |
|*** | *** |

#### print()方法语法
- print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
    - objects -- 复数，表示可以一次输出多个对象。输出多个对象时，需要用 , 分隔。
    - sep -- 用来间隔多个对象，默认值是一个空格。
    - end -- 用来设定以什么结尾。默认值是换行符 \n，我们可以换成其他字符串。
    - file -- 要写入的文件对象。
    - flush -- 输出是否被缓存通常决定于 file，但如果 flush 关键字参数为 True，流会被强制刷新


```python
print("www","runoob","com",sep=".")  # 设置间隔符

import time

print("---RUNOOB EXAMPLE ： Loading 效果---")

print("Loading",end = "")
for i in range(20):
    print(".",end = '',flush = True)
    time.sleep(0.5)
```

    www.runoob.com
    ---RUNOOB EXAMPLE ： Loading 效果---
    Loading....................

####  **print()函数的指定对齐方式：** 
    * 对于整数，指定左对齐时，在右边补 0 是没有效果的，因为这样会改变整数的值。
    * 对于小数，以上三个标志可以同时存在。
    * 对于字符串，只能使用-标志，因为符号对于字符串没有意义，而补 0 会改变字符串的值。


```python
n = 123456
# %09d 表示最小宽度为9，左边补0
print("n(09):%09d" % n)
# %+9d 表示最小宽度为9，带上符号
print("n(+9):%+9d" % n)

f = 140.5
# %-+010f 表示最小宽度为10，左对齐，带上符号
print("f(-+0):%-+010f" % f)

s = "Hello"
# %-10s 表示最小宽度为10，左对齐
print("s(-10):%-10s." % s)
```

    n(09):000123456
    n(+9):  +123456
    f(-+0):+140.500000
    s(-10):Hello     .
    

#### **print()函数的指定小数精度：**
    - 精度值需要放在最小宽度之后，中间用点号.隔开；也可以不写最小宽度，只写精度
    - 如 %m.nf，%.nfm （m 表示最小宽度，n 表示输出精度，.是必须存在的。）


```python
f = 3.141592653
# 最小宽度为8，小数点后保留3位
print("%8.3f" % f)
# 最小宽度为8，小数点后保留3位，左边补0
print("%08.3f" % f)
# 最小宽度为8，小数点后保留3位，左边补0，带符号
print("%+08.3f" % f)
```

       3.142
    0003.142
    +003.142
    

### map()、filter()、reduce()函数解析

- map():对可迭代对象中的每个元素，都调用指定的函数，并返回一个可以转换list的map对象。


```python
# map功能式对可迭代对象中的每个元素，都调用指定的函数，并返回一个map对象。
def func1(x): # 自定义带一个参数函数，并返回加1结果。
    return x+1

my_list = [1, 2, 3]
new_list = map(func1, my_list)  # map(function, iterable)
print(list(new_list))
```

    [2, 3, 4]
    


```python
# 常规map()函数代码写法，使用lambda表达式创建匿名函数替代func1函数，把传回map对象转换为list使用。
my_list = [1, 2, 3]
new_list = list(map(lambda x: x + 1, my_list))
# 将列表每个元素作为参数传入func1函数,返回每个元素计算结果,我们使用list转换返回map对象
print(new_list)
```

    [2, 3, 4]
    


```python
a = [i for i in range(10,51)]
print("{} {}".format(a[0],a[-1]))
```

    10 50
    

- filter():筛选函数，就是在map加上if判断，返回符合条件可以转换list的filter对象。


```python
def func1(x): # 自定义带一个参数函数，大于1返回真。
	return x>1
	
my_list = [1, 2, 3]
new_list=[]
for i in my_list:
	if func1(i):			# 将列表每个元素作为参数传入func1函数判断。
	 	new_list.append(i)  # 条件为真，将符合元素存放在new_list并返回。
print(new_list)	
```

    [2, 3]
    


```python
# 使用lambda表达式化简
my_list = [1, 2, 3]
new_list = list(filter(lambda x: x > 1, my_list))
print(new_list)
```

    [2, 3]
    

- reduce():累计函数，就是将每个元素进行相加或者相乘计算累计总值


```python
def func1(x, y):# 自定义带两个参数函数，返回相加之和。
    return x + y

my_list = [1, 2, 3]
result = 0
for i in my_list:
    result = func1(i, result)  # 将每个元素相加，返回相加之和。
print(result)
```

    6
    


```python
# 使用lambda表达式化简
from functools import reduce

my_list = [1, 2, 3]
print(reduce(func1, my_list))
```

    6
    

![函数总结](https://raw.githubusercontent.com/Lyy999110/YanimagesCloud/main/202208101751252.jpg)

## <font color="red">python的内置函数</font>
- round():返回四舍五入的值，不改变原有值，产生新值
- sorted()：对所有可迭代的对象进行排序操作
- open():打开一个文件
- sum():对序列进行求和计算
- filter()：用于过滤序列，过滤不符合条件的元素，返回由符合条件元素组成的新列表
- id():用于获取对象的内存地址
- next():返回迭代器的下一个项目
- enumerate():返回一个枚举对象
- getattr():返回对象命名属性的值
- hash():返回对象的哈希值
- pow(base,exp):返回base的exp次方
- property():在新式类中返回属性值
- reversed():返回定向序列的反向迭代器
- zip():将对象中的对应元素打包成元组输出
- max():返回可迭代对象中的最大元素，同理还有min()
- divmod():把除数和余数运算结果结合起来，返回一个包含商和余数的元组(a//b，a%b)
- frozenset():返回一个冻结的集合，冻结后集合不能再添加或者删除任何元素


```python
a = ord('A')
b = ord('高')
c = chr(66)
d = round(33.33)
e = str(b)
f = e[3]
g = len(e)
a,b,c,d,e,f,g
```




    (65, 39640, 'B', 33, '39640', '4', 5)



-👀 eval():计算指定表达式的值，执行完要返回结果
    * 格式：eval(expression,globals=None,locals=None,/)
- exec():执行完，不返回结果
    * 格式：exec(expression,globals=None,locals=None,/) 
- 参数说明：
    * expression：这个参数是一个字符串，代表要执行的语句 。该语句受后面两个字典类型参数 globals 和 locals 的限制，只有在 globals 字典和 locals 字典作用域内的函数和变量才能被执行。
    * globals：这个参数管控的是一个全局的命名空间，即 expression 可以使用全局命名空间中的函数。如果只是提供了 globals 参数，而没有提供自定义的 __builtins__，则系统会将当前环境中的 __builtins__ 复制到自己提供的 globals 中，然后才会进行计算；如果连 globals 这个参数都没有被提供，则使用 Python 的全局命名空间。
    * locals：这个参数管控的是一个局部的命名空间，和 globals 类似，当它和 globals 中有重复或冲突时，以 locals 的为准。如果 locals 没有被提供，则默认为 globals。
    * ps：__builtins__ 是 Python 的内建模块，平时使用的 int、str、abs 都在这个模块中。通过 print(dic["__builtins__"]) 语句可以查看 __builtins__ 所对应的 value。


```python
dic = {}    # 定义一个字典
dic['b'] = 3    # 在dic中加一条元素，key为b
print(dic.keys())    # 先打印dic的key，有一个b元素
exec("a = 4",dic)    #在 exec 执行的语句后面跟一个作用域 dic
print(dic.keys())    #exec 后，dic 的 key 多了一个
```

    dict_keys(['b'])
    dict_keys(['b', '__builtins__', 'a'])
    


```python
a=10
b=20
c=30
g={'a':6, 'b':8} #定义一个字典
t={'b':100, 'c':10} #定义一个字典
print(eval('a+b+c', g, t)) #定义一个字典 116,优先使用local的再考虑globals的

"""exec()和eval()的区别：eval() 执行完会返回结果，而 exec() 执行完不返回结果"""
a = 1
exec("a = 2") #相当于直接执行 a=2
print(a)
a = exec("2+3") #相当于直接执行 2+3，但是并没有返回值，a 应为 None
print(a)
a = eval('2+3') #执行 2+3，并把结果返回给 a
print(a)

# a= eval("a = 2")     # 会报错，exec() 中最适合放置运行后没有结果的语句，而 eval() 中适合放置有结果返回的语句。

"""
需要注意的是:在使用 eval() 或是 exec() 来处理请求代码时，函数 eval() 和 exec() 常常会被黑客利用，成为可以执行系统级命令的入口点，进而来攻击网站。
解决方法是：通过设置其命名空间里的可执行函数，来限制 eval() 和 exec() 的执行范围。
"""
```


```python
x = 10
expr = """
z = 30
sum = x + y + z
print(sum)
"""
 
 
def func():
    y = 20
    exec(expr)
    exec(expr, {'x': 1, 'y': 2})
    exec(expr, {'x': 1, 'y': 2}, {'y': 3, 'z': 4})
 
 
func()

```

    60
    33
    34
    

# 三、python类和对象
## 3.1 类


```python
# 小示例
class tortoise:
    bodyColor = "绿色"
    footNum = 4
    weight = 10
    hasShell = True
    #会爬
    def crawl(self):
        print("乌龟会爬")
    #会吃东西
    def eat(self):
        print("乌龟吃东西")
    #会睡觉
    def sleep(self):
        print("乌龟在睡觉")
    #会缩到壳里
    def protect(self):
        print("乌龟缩进了壳里")
```

- 类：可以理解是一个模板，通过它可以创建出无数个具体实例。比如，前面编写的 tortoise 表示的只是乌龟这个物种，通过它可以创建出无数个实例来代表各种不同特征的乌龟（这一过程又称为类的实例化）。
- 对象：类并不能直接使用，通过类创建出的实例（对象）才能使用
- 属性：类中的所有变量称为属性
- 方法：类中的所有函数称为属性

### __init__()类构造方法
```
def __init__(self,..):
    代码块
```


```python
class TheFirstDemo:
    '''这是一个学习Python定义的第一个类'''
    #构造方法，只有一个self参数的可以忽略不写
    def __init__(self):
        print("调用构造方法")
    # 下面定义了一个类属性
    add = 'http://c.biancheng.net'
    # 下面定义了一个say方法
    def say(self, content):
        print(content)
zhangsan = TheFirstDemo()

```

    调用构造方法
    C语言中文网 的网址为: http://c.biancheng.net
    


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-5-30fe91440d74> in <module>
         21 """类对象的使用"""
         22 # 输出name和add实例变量的值
    ---> 23 print(Clanguage.name,Clanguage.add)
    

    AttributeError: type object 'Clanguage' has no attribute 'name'


### 类对象的创建和调用
- 类对象访问类中实例变量格式：类对象名.变量名
- 类对象调用类中方法的语法格式：对象名。方法名（参数）


```python
# 类的实例化，格式：类名（参数）

# 在 __init__() 构造方法中，除了 self 参数外，还可以自定义一些参数，参数之间使用逗号“,”进行分割。
class CLanguage :
    # 下面定义了2个类变量
    name = "C语言中文网"
    add = "http://c.biancheng.net"
    def __init__(self,name,add):
        #下面定义 2 个实例变量
        self.name = name
        self.add = add
        print(name,"网址为：",add)
    # 下面定义了一个say实例方法
    def say(self, content):
        print(content)
# 将该CLanguage对象赋给clanguage变量
clanguage = CLanguage("C语言中文网","http://c.biancheng.net")

print("- 类对象访问变量或方法")
#输出name和add实例变量的值
print(clanguage.name,clanguage.add)
#修改实例变量的值
clanguage.name="Python教程"
clanguage.add="http://c.biancheng.net/python"
#调用clanguage的say()方法
clanguage.say("人生苦短，我用Python")
#再次输出name和add的值
print(clanguage.name,clanguage.add)

print("- 类动态添加/删除变量")
# 为clanguage对象增加一个money实例变量
clanguage.money= 159.9
print(clanguage.money)
#删除新添加的 money 实例变量
del clanguage.money
#再次尝试输出 money，此时会报错
# print(clanguage.money)

print("- 给类对象动态添加方法")
# 先定义一个函数
def info(self):
    print("---info函数---", self)
# 使用info对clanguage的foo方法赋值（动态绑定方法）
clanguage.foo = info
# Python不会自动将调用者绑定到第一个参数，
# 因此程序需要手动将调用者绑定为第一个参数
clanguage.foo(clanguage)  # ①
# 使用lambda表达式为clanguage对象的bar方法赋值（动态绑定方法）
clanguage.bar = lambda self: print('--lambda表达式--', self)
clanguage.bar(clanguage) # ②
```

    C语言中文网 网址为： http://c.biancheng.net
    - 类对象访问变量或方法
    C语言中文网 http://c.biancheng.net
    人生苦短，我用Python
    Python教程 http://c.biancheng.net/python
    - 类动态添加/删除变量
    159.9
    - 给类对象动态添加方法
    ---info函数--- <__main__.CLanguage object at 0x000002482B55A370>
    --lambda表达式-- <__main__.CLanguage object at 0x000002482B55A370>
    


```python
# 不需要手动给self传值的方法，借助types模块下的MethodType实现，在上块代码块上续写如下：
def info(self,content):
    print("C语言中文网地址为：%s" % content)
    
# 导入MethodType,下面两行代码等同于一句代码：clanguage.info(clanguage)
# from types import MethodType
# clanguage.info = MethodType(info, clanguage)

# 第一个参数已经绑定了，无需传入
clanguage.info("http://c.biancheng.net")
```

    C语言中文网地址为：<__main__.CLanguage object at 0x000002482B55A370>
    C语言中文网地址为：http://c.biancheng.net
    

#### self用法
- 在定义类的过程中，无论是显式创建类的构造方法，还是向类中添加实例方法，都要求将 self 参数作为方法的第一个参数
- 相当于指针，让每个类对象只能调用自己类变量和方法


```python
class Person:
#     game="fun11"
    def __init__(self,game):
        self.game = game    # 对于构造函数中的 self 参数，其代表的是当前正在初始化的类对象
        print("构造方法")
    # 定义一个实例方法
    def funny(self,game):
        print("访问内部定义的game:",self.game)
        print("访问外部输入的game:",game)
zhangsan = Person("bb")
zhangsan.funny("basketball")
zhangsan.funny(zhangsan.game)

"""个人理解，self就是类中的形参变量，在类中声明的变量或者方法"""
```

    构造方法
    访问内部定义的game: bb
    访问外部输入的game: bb
    访问内部定义的game: bb
    访问外部输入的game: bb
    


```python
# 除了类对象可以直接调用类方法，还有一种函数调用的方式
class Person:
    def who(self):
        print(self)
zhangsan = Person()
#第一种方式
zhangsan.who()
#第二种方式
who = zhangsan.who
who()#通过 who 变量调用zhangsan对象中的 who() 方法
""" 无论是类中的构造函数还是普通的类方法，实际调用它们的谁，则第一个参数 self 就代表谁 """
```

    <__main__.Person object at 0x0000023DEB7EB520>
    <__main__.Person object at 0x0000023DEB7EB520>
    




    ' 无论是类中的构造函数还是普通的类方法，实际调用它们的谁，则第一个参数 self 就代表谁 '



### 类变量/属性和实例变量/属性
- 类体中，所有函数之外：此范围定义的变量，称为类属性或者类变量
- 类体中，所有函数内部：以“self.变量名”的方式定义的变量，称为实例属性或实例变量；
- 类体中，所有函数内部：以“变量名=变量值”的方式定义的变量，称为局部变量。

#### 类变量


```python
class Person:
    name = "小明"
    age = 23
    
# 不创建实例对象，通过类名调用类变量并输出
print(Person.name)
print(Person.age)
# 通过类名直接修改类变量，这样会影响所有的实例化对象
Person.name = "花花"
print(Person.name)


```

    小明
    23
    花花
    花花
    23
    小红
    花花
    

#### 实例变量


```python
class Person:
    name = "小明"
    age = 23
    def __init__(self):
        name = "虫虫"
        age = 18
# 创建Person的实例对象，并输出类中定义的类变量值
stu1 = Person()
print(stu1.name)
print(stu1.age)
# 通过类实例化对象修改类变量并输出
stu1.name = "小红"
print(stu1.name)
# 查看类变量的值
print(Person.name)
```

    小明
    23
    小红
    小明
    


```python
class CLanguage :
    name = "xxx"  #类变量
    add = "http://"  #类变量
    def __init__(self):
        self.name = "C语言中文网"   #实例变量
        self.add = "http://c.biancheng.net"   #实例变量
    # 下面定义了一个say实例方法
    def say(self):
        self.catalog = 13  #实例变量
        
clang = CLanguage()
#修改 clang 对象的实例变量
clang.name = "python教程"
clang.add = "http://c.biancheng.net/python"
print(clang.name)
print(clang.add)
# 输出默认实例变量
clang2 = CLanguage()
print(clang2.name)
print(clang2.add)
clang.say()
print(clang.catalog)
#输出类变量的值
print(CLanguage.name)
print(CLanguage.add)
```

    python教程
    http://c.biancheng.net/python
    C语言中文网
    http://c.biancheng.net
    13
    xxx
    http://
    

#### 局部变量


```python
class Clanguage:
    def say(self,money):
        sale = money*0.8    # sale这里是局部变量，只能用于所在函数中，外部不能使用
        print("优惠后的价格是：",sale)
clang = Clanguage()
clang.say(1000)
```

    优惠后的价格是： 800.0
    

### 实例方法，类方法和静态方法
#### 类实例方法


```python
class Plant:
    # 类构造方法，也属于实例方法
    def __init__(self):
        self.name = "rose"
        self.number =  12
        self.color = "red"
    # 再定义一个实例方法
    def bloom(self):
        print(self.name,"盛开了")
flower = Plant()
flower.bloom()

# Python还支持使用类名调用实例方法，但需要手动给self参数赋值
flower2 = Plant()
Plant.bloom(flower2)
```

    rose 盛开了
    rose 盛开了
    

#### 类方法
- 类方法和实例方法相似，最少包含一个参数，只不过类方法中通常将其命名为cls，python会自动将类本身绑定给cls参数，在调用类方法时，<font color="red">无需显式为cls参数传参</font>
- cls参数的命名不是规定的，是一种默认习惯
- 类方法需要用@classmethod修饰符进行修饰


```python
class Furniture:
    def __init__(self):
        name = "chair"
        color = "normal"
    # 定义一个方法
    @classmethod       #如果没有 ＠classmethod，则 Python 解释器会将info() 方法认定为实例方法，而不是类方法
    def info(cls):
        print("正在调用类方法",cls)
        
# 类名直接调用类方法
Furniture.info()
# 使用b对象调用类方法
furni = Furniture()
furni.info()
```

    正在调用类方法 <class '__main__.Furniture'>
    正在调用类方法 <class '__main__.Furniture'>
    

#### 类静态方法
- 静态方法，其实就是我们学过的函数，和函数唯一的区别是，静态方法定义在类这个空间（类命名空间）中，而函数则定义在程序所在的空间（全局命名空间）中。
- 静态方法没有类似 self、cls 这样的特殊参数，因此 Python 解释器不会对它包含的参数做任何类或对象的绑定。也正因为如此，类的静态方法中无法调用任何类属性和类方法。
- 静态方法需要使用＠staticmethod修饰，


```python
class Person:
    @staticmethod
    def info(name,add):
        print(name,add)

# 使用类名调用静态方法
Person.info("小红",10)
# 使用类对象调用静态方法
xiaohong = Person()
xiaohong.info("小红",10)
```

    小红 10
    小红 10
    

### 描述符详解
- 描述符是 Python 中复杂属性访问的基础，它在内部被用于实现 property、方法、类方法、静态方法和 super 类型。本质上看，描述符就是一个类，只不过它定义了另一个类中属性的访问方式。
- 描述符类基于以下 3 个特殊方法，换句话说，这 3 个方法组成了描述符协议：
    - __set__(self, obj, type=None)：在设置属性时将调用这一方法（本节后续用 setter 表示）；
    - __get__(self, obj, value)：在读取属性时将调用这一方法（本节后续用 getter 表示）；
    - __delete__(self, obj)：对属性调用 del 时将调用这一方法。
    - 其中，实现了 setter 和 getter 方法的描述符类被称为数据描述符；反之，如果只实现了 getter 方法，则称为非数据描述符。


```python
"""
实际上，在每次查找属性时，描述符协议中的方法都由类对象的特殊方法 __getattribute__() 调用（注意不要和 __getattr__() 弄混）。
也就是说，每次使用类对象.属性（或者 getattr(类对象，属性值)）的调用方式时，都会隐式地调用 __getattribute__()，
它会按照下列顺序查找该属性：
    1、验证该属性是否为类实例对象的数据描述符；
    2、如果不是，就查看该属性是否能在类实例对象的 __dict__ 中找到；
    3、最后，查看该属性是否为类实例对象的非数据描述符。
"""
# 描述符类
class revealAccess:
    def __init__(self,initval=None,name='var'):
        print(1)
        self.val = initval
        self.name = name
    def __get__(self,obj,objtype):
        print("Retrieving",self.name)
        return self.val        # attention:this is "return"!
    def __set__(self,obj,val):
        print(2)
        print("updating",self.name)
        self.val = val
    def __del__(self):
        class_name = self.__class__.__name__
class myClass:
    x = revealAccess(10,'var"x"')
    y = 5
m = myClass()
print("========")
print(m.x)
print("====2===")
m.x = 20
print(m.x)
print(m.y)
del m
# print(m.x)    # 已销毁，会报错
```

    1
    ========
    Retrieving var"x"
    10
    ====2===
    2
    updating var"x"
    Retrieving var"x"
    20
    5
    


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-19-8e68faa509cd> in <module>
         33 print(m.y)
         34 del m
    ---> 35 print(m.x)
    

    NameError: name 'm' is not defined


### property()函数：定义属性
- “类对象.属性”的方式访问类中属性会破坏类的封装性，类包含的属性应该是隐藏的，只允许通过类提供的方法来间接对类属性访问和操作。


```python
"""
为了不破坏封装性，且有效操作类中的属性，使用“类对象.方法(属性)”方式操作属性
"""
class Person:
    # 构造函数
    def __init__(self,name):
        self.name = name
    # 设置name属性值的函数
    def setname(self,name):
        self.name = name
        
    # 访问name属性值的函数
    def getname(self):
        return self.name
    # 删除name属性值的函数
    def delname(self):
        self.name = "xxx"
        
student = Person("Lucy")
# 获取name属性值
print(student.getname())
# 设置name属性值
student.setname("Linda")
print(student.getname())
# 删除name属性值
student.delname()
print(student.getname())
```

    Lucy
    Linda
    xxx
    

**<font color="red">改进版：使用property()函数</font>**
- 使用格式：属性名 = property(fget=None,fset=None,fdel=None,doc=None)
    - fget 参数用于指定获取该属性值的类方法，
    - fset 参数用于指定设置该属性值的方法，
    - fdel 参数用于指定删除该属性值的方法，
    - 最后的 doc 是一个文档字符串，用于说明此函数的作用。
    - ！！注意，在使用 property() 函数时，以上 4 个参数可以仅指定第 1 个、或者前 2 个、或者前 3 个，当前也可以全部指定。
    也就是说，property() 函数中参数的指定并不是完全随意的。


```python
class Person:
    # 构造函数
    def __init__(self,name):
        self.__name = name
    # 设置name属性值的函数
    def setname(self,name):
        self.__name = name
    # 访问name属性值的函数
    def getname(self):
        return self.__name
    """
    由于 getname() 方法中需要返回 name 属性，如果使用 self.name 的话，其本身又被调用 getname()，
    这将会先入无限死循环。为了避免这种情况的出现，程序中的 name 属性必须设置为私有属性，即使用 __name（前面有 2 个下划线）
    另外，有关类属性和类方法的属性设置（分为共有属性、保护属性、私有属性）
    """
    # 删除name属性值的函数
    def delname(self):
        self.__name = "xxx" 
        
    # 为name属性配置property()函数
#     name = property(getname,setname)
#     name = property(getname)                   # name属性可读，不可写，不可删
#     name = property(getname,setname,delname)       # name属性可读、可写、可删，没有说明文档
    name = property(getname,setname,delname,"指明出处")      # 这里的name不能和上面self.xx的xx重名

# 调取说明文档的两种方式
# print(Person.name.__doc__)
help(Person.name)
stu = Person("Lucy")
# 调用getname()方法
print(stu.name)
# 调用setname()方法
stu.name = "Linda"
print(stu.name)
# 调用delname()方法
del stu.name
print(stu.name)
```

    Help on property:
    
        指明出处
    
    Lucy
    Linda
    xxx
    

### @property装饰器
- property函数字如其名，其在装饰器的主要应用在于，我们要实现
    - 保护类的封装特性
    - 让开发者可以使用“对象.属性”的方式操作操作类属性
- 的功能，除了使用 property() 函数，还可以使用 @property 装饰器。通过 @property 装饰器，可以直接通过方法名来访问方法，不需要在方法名后添加一对“（）”小括号
- @property 的语法格式：
```
@property
def 方法名(self):
    代码块
```


```python
"""
定义一个矩形类，并定义用 @property 修饰的方法操作类中的 area 私有属性
1、@property装饰的方法对应着getter方法，@方法名.setter，@方法名.deleter对应deleter方法
2、方法名注意要统一，相当于托管属性的名称
"""
class Rect:
    def __init__(self,area):
        self.__area = area
    @property
    def area(self):
        return self.__area
    
    # 要实现修改属性值，需要用setter装饰器
    @area.setter
    def area(self,value):
        self.__area = value
    #同理，有了getter和setter方法，在补上deleter方法
    @area.deleter
    def area(self):
        self.__area = 0
rect = Rect(30)
# 直接通过方法名来访问area方法
print("矩形面积是：",rect.area)

"""上面程序中，使用 ＠property 修饰了 area() 方法，
这样就使得该方法变成了 area 属性的 getter 方法。需要注意的是，如果类中只包含该方法，那么 area 属性将是一个只读属性。
下面代码会报错：
"""
# rect.area = 20
# print("矩形面积是：",rect.area)

rect.area = 20
print("修改后的面积是：",rect.area)

del rect.area
print("删除后的area值为：",rect.area)
```

    矩形面积是： 30
    修改后的面积是： 20
    删除后的area值为： 0
    

### 内置类属性
```
- __dict__ : 类的属性（包含一个字典，由类的数据属性组成）
- __doc__ :类的文档字符串
- __name__: 类名
- __module__: 类定义所在的模块（类的全名是'__main__.className'，如果类位于一个导入模块mymod中，那么className.__module__ 等于 mymod）
- __bases__ : 类的所有父类构成元素（包含了一个由所有父类组成的元组
```


```python
class Employee:
   '所有员工的基类'
   empCount = 0
 
   def __init__(self, name, salary):
      self.name = name
      self.salary = salary
      Employee.empCount += 1
   
   def displayCount(self):
     print("Total Employee %d" % Employee.empCount)
 
   def displayEmployee(self):
      print("Name : ", self.name,  ", Salary: ", self.salary)
    
print("Employee.__doc__:", Employee.__doc__)
print("Employee.__name__:", Employee.__name__)
print("Employee.__module__:", Employee.__module__)
print("Employee.__bases__:", Employee.__bases__)
print("Employee.__dict__:", Employee.__dict__)
```

    Employee.__doc__: 所有员工的基类
    Employee.__name__: Employee
    Employee.__module__: __main__
    Employee.__bases__: (<class 'object'>,)
    Employee.__dict__: {'__module__': '__main__', '__doc__': '所有员工的基类', 'empCount': 0, '__init__': <function Employee.__init__ at 0x0000025C11206700>, 'displayCount': <function Employee.displayCount at 0x0000025C11206790>, 'displayEmployee': <function Employee.displayEmployee at 0x0000025C11206820>, '__dict__': <attribute '__dict__' of 'Employee' objects>, '__weakref__': <attribute '__weakref__' of 'Employee' objects>}
    

## <font color="red">类的封装，继承和多态</font>
### 类的封装
- 默认情况下，Python 类中的变量和方法都是公有（public）的，它们的名称前都没有下划线（_）；
- 如果类中的变量和函数，其名称以双下划线“__”开头，则该变量（函数）为私有变量（私有函数），其属性等同于 private。
- 注意，Python 类中还有以双下划线开头和结尾的类方法（例如类的构造函数__init__(self)），这些都是 Python 内部定义的，用于 Python 内部调用。我们自己定义类属性或者类方法时，不要使用这种格式。


```python
class CLanguage :
    def setname(self, name):
        if len(name) < 3:
            '有关 raise 的具体用法，后续章节会做详细的讲解，这里可简单理解成，如果用户输入不规范，程序将会报错'
            raise ValueError('名称长度必须大于3！')
        self.__name = name
    def getname(self):
        return self.__name
    #为 name 配置 setter 和 getter 方法
    name = property(getname, setname)
    def setadd(self, add):
        if add.startswith("http://"):
            self.__add = add
        else:
            raise ValueError('地址必须以 http:// 开头') 
    def getadd(self):
        return self.__add
   
    #为 add 配置 setter 和 getter 方法
    add = property(getadd, setadd)
    #定义个私有方法
    def __display(self):
        print(self.__name,self.__add)
clang = CLanguage()
clang.name = "C语言中文网"
clang.add = "http://c.biancheng.net"
print(clang.name)
print(clang.add)
```

    C语言中文网
    http://c.biancheng.net
    

### 继承机制及使用 


```python
class Shape:
    def draw(self,content):
        print("画",content)
        
'class From(Shape) 就表示 From 继承 Shape。'
class Form(Shape):
    def area(self):
        #....
        print("此图形的面积为...")
```

#### 多继承
- 格式：
```
class 类名(父类1, 父类2, ...)：
    #类定义部分
```
- 注意：如果该类没有显示指定哪个类，则默认继承object类（object类是python中所有类的父类）
- 相对来说，子类继承父类，父类派生子类
- 当使用多继承时，多个父类包含同名的类方法，python的处置方法：根据子类继承多个父类时，这些父类的前后次序决定，即在前面父类中的类方法会覆盖排在后面父类中的同名类方法。


```python
class People:
    def say(self):
        print("我是一个人，名字是：",self.name)
class Animal:
    def display(self):
        print("人也是高级动物")
#同时继承 People 和 Animal 类
#其同时拥有 name 属性、say() 和 display() 方法
class Person(People, Animal):
    pass
zhangsan = Person()
zhangsan.name = "张三"
zhangsan.say()
zhangsan.display()
```


```python
"多继承时，父类包含同名方法，在前面父类中的类方法会覆盖排在后面父类中的同名类方法。"
class People:
    def __init__(self):
        self.name = People
    def say(self):
        print("People类",self.name)
class Animal:
    def __init__(self):
        self.name = Animal
    def say(self):
        print("Animal类",self.name)
#People中的 name 属性和 say() 会遮蔽 Animal 类中的
class Person(People, Animal):
    pass
zhangsan = Person()
zhangsan.name = "张三"
zhangsan.say()
```

    People类 张三
    

### 重写
#### 父类方法重写
- 重写，有时又称覆盖，是一个意思，指的是对类中已有方法的内部实现进行修改。


```python
class Bird:
    #鸟有翅膀
    def isWing(self):
        print("鸟有翅膀")
    #鸟会飞
    def fly(self):
        print("鸟会飞")
        
class Ostrich(Bird):
    # 重写Bird类的fly()方法
    def fly(self):
        print("鸵鸟不会飞")
# 创建Ostrich对象
ostrich = Ostrich()
#调用 Ostrich 类中重写的 fly() 类方法
ostrich.fly()
#调用 Bird 类中的 fly() 方法
Bird.fly(ostrich)
```

    鸵鸟不会飞
    鸟会飞
    

#### super( )函数：调用父类的构造方法
- 类的构造方法就是实例方法，多继承时，构造方法遵循优先选择排在前面父类中的实例方法。



```python
class People:
    def __init__(self,name):
        self.name = name
    def say(self):
        print("我是人，名字为：",self.name)
class Animal:
    def __init__(self,food):
        self.food = food
    def display(self):
        print("我是动物,我吃",self.food)
#People中的 name 属性和 say() 会遮蔽 Animal 类中的
class Person(People, Animal):
    pass
per = Person("zhangsan")
per.say()
# per.display()
```

    我是人，名字为： zhangsan
    

- 在子类中定义构造方法，必须在该方法中调用父类的构造函数，有两种方法：
    - 1、类可以看做一个独立空间，在类的外部调用其中的实例方法，可以向调用普通函数那样，只不过需要额外备注类名（此方式又称为未绑定方法）；
    - 2、使用 super() 函数。但如果涉及多继承，该函数只能调用第一个直接父类的构造方法。
    - 使用格式：super().__init__(self,...)
```
也就是说，涉及到多继承时，在子类构造函数中，调用第一个父类构造方法的方式有以上 2 种，
而调用其它父类构造方法的方式只能使用未绑定方法
```


```python
"针对上述情况，正确做法是：定义Person类自己的构造方法（等于重写第一个直接父类的构造方法）"
# 使用super()函数
class People:
    def __init__(self,name):
        self.name = name
    def say(self):
        print("我是人，名字为：",self.name)
class Animal:
    def __init__(self,food):
        self.food = food
    def display(self):
        print("我是动物,我吃",self.food)
class Person(People,Animal):
    # 自定义构造方法
    def __init__(self,name,food):
        # 调用People类的构造方法
        super().__init__(name)
#         People().__init__(self,name)     # 上行代码等价为这行代码
         #调用其它父类的构造方法，需手动给 self 传值。即非绑定方法
        Animal.__init__(self,food)
per = Person("zhangsan","熟食")
per.say()
per.display()
```

    我是人，名字为： zhangsan
    我是动物,我吃 熟食
    

#### __slots__:限制类实例动态添加属性和方法
- 类动态添加实例方法，静态方法和类方法；但是对于实例对象，只允许动态添加实例方法
- 为单个实例对象添加方法，不会影响该类的其他实例对象，如果为类动态的添加方法，则所有实例对象都可以使用


```python
class CLanguage:
    pass
#下面定义了一个实例方法
def info(self):
    print("正在调用实例方法")
#下面定义了一个类方法
@classmethod
def info2(cls):
    print("正在调用类方法")
#下面定义个静态方法
@staticmethod
def info3():
    print("正在调用静态方法")
#类可以动态添加以上 3 种方法，会影响所有实例对象
CLanguage.info = info
CLanguage.info2 = info2
CLanguage.info3 = info3
clang = CLanguage()
#如今，clang 具有以上 3 种方法
clang.info()
clang.info2()
clang.info3()
#类实例对象只能动态添加实例方法，不会影响其它实例对象
clang1 = CLanguage()
clang1.info = info
#必须手动为 self 传值
clang1.info(clang1)
```

    正在调用实例方法
    正在调用类方法
    正在调用静态方法
    正在调用实例方法
    

- **问题：**如果类中有已经定义好的类，不做限制的话，会被动态修改
- ```__slots__属性：```通过它可以避免用户频繁的给实例对象动态的添加属性或者方法，无法限制动态类添加属性和方法，它显示方法名，不限制参数个数


```python
class CLanguage:
    __slots__ = ('name','add','info')
# 定义的实例方法
def info(self,name):
    print("正在调用实例方法",self.name)
clang = CLanguage()
clang.name = "hello"
# 为clang对象动态添加info实例方法
clang.info = info
clang.info(clang,"hi")

# 下面两行代码会报错，因为__slots__限制了实例对象动态添加方法say
# clang.say = info
# clang.say(clang,"morning")

# __slots__不限制类，所以下面代码ok
CLanguage.say = info
clang2 = CLanguage()
clang2.name = "hi"
clang2.say("Hi")
```

    正在调用实例方法 hello
    正在调用实例方法 hi
    


```python
class CLanguage:
    __slots__ = ('name','add','info')
# CLanguage 的空子类
class CLangs(CLanguage):
    pass
# 定义的实例方法
def info(self,name):
    print("正在调用实例方法",self.name)
```


```python
"__slots__属性对该类派生出的子类也是不起作用的"
class CLanguage:
    __slots__ = ('name','add','info')
#Clanguage 的空子类
class CLangs(CLanguage):
    pass
#定义的实例方法
def info(self):
    print("正在调用实例方法")
clang = CLangs()
# 为子类对象动态添加say()方法
clang.say = info
clang.say(clang)
"""
注意，如果为子类也设置有 __slots__ 属性，那么子类实例对象允许动态添加的属性和方法，
是子类中 __slots__ 属性和父类 __slots__ 属性的和。
"""
```

    正在调用实例方法
    

#### type( )函数：动态创建类
```
语法格式有两种：
    1、type(obj)
    2、type(name,bases,dict)
```
- 第一种语法格式用来查看某个变量（类对象）的具体类型，obj 表示某个变量或者类对象。
- 第二种语法格式用来创建类，其中 name 表示类的名称；bases 表示一个元组，其中存储的是该类的父类；dict 表示一个字典，用于表示类内定义的属性或者方法。


```python
"这里主要介绍一下方法2"
# 定义一个实例方法
def say(self):
    print("我要学python")
# 使用type()函数创建类
#元组语法规定，当 (object,) 元组中只有一个元素时，最后的逗号（,）不能省略。
CLanguage = type("CLanguage",(object,),dict(say=say,name="Hello"))      
# 创建一个实例对象
clangs = CLanguage()
# 调用say()方法和name属性
clangs.say()
print(clangs.name)
```

    我要学python
    Hello
    

### 多态用法详解
- 多态：满足1、继承：多态一定是发生在子类和父类之间；2、重写：子类重写了父类的方法，两个条件


```python
class CLanguage:
    def say(self):
        print("调用的是 Clanguage 类的say方法")
class CPython(CLanguage):
    def say(self):
        print("调用的是CLanguage派生类 CPython 类的say方法")
class CLinux(CLanguage):
    def say(self):
        print("调用的是CLanguage派生类 CLinux 类的say方法")
a = CLanguage()
a.say()
a = CPython()
a.say()
a = CLinux()
a.say()
```

    调用的是 Clanguage 类的say方法
    调用的是CLanguage派生类 CPython 类的say方法
    调用的是CLanguage派生类 CLinux 类的say方法
    

**注意：**同一变量 a 在执行同一个 say() 方法时，由于 a 实际表示不同的类实例对象，因此 a.say() 调用的并不是同一个类中的 say() 方法，这就是多态。


```python
"""这种由多态衍生出的更灵活的编程机制，又称为“鸭子模型”或“鸭子类型”。"""
class WhoSay:
    def say(self,who):
        who.say()
class CLanguage:
    def say(self):
        print("调用的是 Clanguage 类的say方法")
class CPython(CLanguage):
    def say(self):
        print("调用的是 CPython 类的say方法")
class CLinux(CLanguage):
    def say(self):
        print("调用的是 CLinux 类的say方法")
a = WhoSay()
#调用 CLanguage 类的 say() 方法
a.say(CLanguage())
#调用 CPython 类的 say() 方法
a.say(CPython())
#调用 CLinux 类的 say() 方法
a.say(CLinux())
```

- 通过给 WhoSay 类中的 say() 函数添加一个 who 参数，其内部利用传入的 who 调用 say() 方法。这意味着，当调用 WhoSay 类中的 say() 方法时，我们传给 who 参数的是哪个类的实例对象，它就会调用那个类中的 say() 方法。

#### 枚举类
- Enum 枚举类。也就是说，对于这些实例化对象个数固定的类，可以用枚举类来定义。
- 枚举类的每个成员都由 2 部分组成，分别为 name 和 value
- 枚举类不能用来实例化对象，但可以访问枚举类中的成员
- 枚举类成员之间不能比较大小，但可以用 == 或者 is 进行比较是否相等
- 枚举类中各个成员的值，不能在类的外部做任何修改
- 该枚举类还提供了一个 __members__ 属性，该属性是一个包含枚举类中所有成员的字典，通过遍历该属性，也可以访问枚举类中的各个成员。
- 枚举类中各个成员必须保证 name 互不相同，但 value 可以相同
- 除了通过继承 Enum 类的方法创建枚举类，还可以使用 Enum() 函数创建枚举类。


```python
from enum import Enum

class Color(Enum):
    "如果想将一个类定义为枚举类，只需要令其继承自 enum 模块中的 Enum 类即可"
    # 为序列值指定value值
    red = 1
    green = 2
    blue = 3
#调用枚举成员的 3 种方式
print(Color.red)
print(Color['red'])
print(Color(1))
#调取枚举成员中的 value 和 name
print(Color.red.value)
print(Color.red.name)
#遍历枚举类中所有成员的 2 种方式
for color in Color:
    print(color)

# 比较成员
print(Color.red == Color.green)
print(Color.red.name is Color.green.name)

# 下面代码错误，成员不支持在类的外部修改
# Color.red = 4

# __members__属性：访问枚举类中的各个成员
for name,member in Color.__members__.items():
    print(name,"->",member)
```

    Color.red
    Color.red
    Color.red
    1
    red
    Color.red
    Color.green
    Color.blue
    False
    False
    red -> Color.red
    green -> Color.green
    blue -> Color.blue
    


```python
"""成员之间的name不能相同，value可以相同"""
from enum import Enum
class Color(Enum):
    # 为序列值指定value值
    red = 1
    green = 1
    blue = 3
print(Color['green'])

```

```
Color 枚举类中 red 和 green 具有相同的值（都是 1），Python 允许这种情况的发生，它会将 green 当做是 red 的别名，因此当访问 green 成员时，最终输出的是 red。
为避免上述情况，可以使用@unique装饰器，当出现值相同的成员时，报ValueError错误
```


```python
#引入 unique
from enum import Enum,unique
#添加 unique 装饰器
@unique
class Color(Enum):
    # 为序列值指定value值
    red = 1
    green = 1
    blue = 3
# print(Color['green'])    # 会报错
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-47-449eb359e847> in <module>
          3 #添加 unique 装饰器
          4 @unique
    ----> 5 class Color(Enum):
          6     # 为序列值指定value值
          7     red = 1
    

    D:\Anaconda3\lib\enum.py in unique(enumeration)
        858         alias_details = ', '.join(
        859                 ["%s -> %s" % (alias, name) for (alias, name) in duplicates])
    --> 860         raise ValueError('duplicate values found in %r: %s' %
        861                 (enumeration, alias_details))
        862     return enumeration
    

    ValueError: duplicate values found in <enum 'Color'>: green -> red



```python
"""除了通过继承 Enum 类的方法创建枚举类，还可以使用 Enum() 函数创建枚举类。"""
from enum import Enum
#创建一个枚举类
Color = Enum("Color",('red','green','blue'))
#调用枚举成员的 3 种方式
print(Color.red)
print(Color['red'])
print(Color(1))
#调取枚举成员中的 value 和 name
print(Color.red.value)
print(Color.red.name)
#遍历枚举类中所有成员的 2 种方式
for color in Color:
    print(color)
```

    Color.red
    Color.red
    Color.red
    1
    red
    Color.red
    Color.green
    Color.blue
    

## 类特殊成员（属性和方法）
### ``` __new__()方法```
- __new__() 是一种负责创建类实例的静态方法，它无需使用 staticmethod 装饰器修饰，且该方法会优先 __init__() 初始化方法被调用。
- 覆写 __new__() 的实现将会使用合适的参数调用其超类的 super().__new__()，并在返回之前修改实例


```python
class demoClass:
    instances_created = 0
    def __new__(cls,*args,**kwargs):
        print("__new__():",cls,args,kwargs)
        instance = super().__new__(cls)
        instance.number = cls.instances_created
        cls.instances_created += 1
        return instance
    def __init__(self,attribute):
        print("__init__():",self,attribute)
        self.attribute = attribute
test1 = demoClass("abc")
test2 = demoClass("xyz")
print(test1.number,test1.instances_created)
print(test2.number,test2.instances_created)
```


```python
"""__new__() 通常会返回该类的一个实例，但有时也可能会返回其他类的实例，如果发生了这种情况，则会跳过对 __init__() 方法的调用。"""
class nonZero(int):
    def __new__(cls,value):
        return super().__new__(cls,value) if value != 0 else None
    def __init__(self,skipped_value):
        #此例中会跳过此方法
        print("__init__()")
        super().__init__()
print(type(nonZero(-12)))
print(type(nonZero(0)))
```

### ``` __repr__()方法```

### ``` __del__()方法```

### ``` __dir__()方法```

### ``` __dict__方法```

### ``` __call_()方法```

### ```setattr、getattr、hasattr```

### ```issubclass和isinstance```

### 运算符重载

### 迭代器
- 可以用来访问集合元素，可以记住遍历对象的位置的对象
- 迭代器从集合的第一个元素开始访问，一直访问到终点，只能往前访问
- 迭代器的两个基本方法：iter()和 next()


```python
list1 = list(range(8))
it = iter(list1)      # 创建迭代器对象
print(next(it))     # 输出迭代器的下一个元素
print(next(it))

# 用for循环遍历迭代器对象
for x in it:
    print(x,end=" ")

```

    0
    1
    2 3 4 5 6 7 


```python
import sys         # 引入 sys 模块
 
list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
 
while True:
    try:
        print (next(it))
    except StopIteration:
        sys.exit()
```

    ERROR:root:Internal Python error in the inspect module.
    Below is the traceback from this internal error.
    
    

    1
    2
    3
    4
    Traceback (most recent call last):
      File "<ipython-input-19-545929cfd7f5>", line 8, in <module>
        print (next(it))
    StopIteration
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "D:\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 3343, in run_code
        exec(code_obj, self.user_global_ns, self.user_ns)
      File "<ipython-input-19-545929cfd7f5>", line 10, in <module>
        sys.exit()
    SystemExit
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py", line 1169, in get_records
        return _fixed_getinnerframes(etb, number_of_lines_of_context, tb_offset)
      File "D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py", line 316, in wrapped
        return f(*args, **kwargs)
      File "D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py", line 350, in _fixed_getinnerframes
        records = fix_frame_records_filenames(inspect.getinnerframes(etb, context))
      File "D:\Anaconda3\lib\inspect.py", line 1503, in getinnerframes
        frameinfo = (tb.tb_frame,) + getframeinfo(tb, context)
    AttributeError: 'tuple' object has no attribute 'tb_frame'
    


    ---------------------------------------------------------------------------

    StopIteration                             Traceback (most recent call last)

    <ipython-input-19-545929cfd7f5> in <module>
          7     try:
    ----> 8         print (next(it))
          9     except StopIteration:
    

    StopIteration: 

    
    During handling of the above exception, another exception occurred:
    

    SystemExit                                Traceback (most recent call last)

        [... skipping hidden 1 frame]
    

    <ipython-input-19-545929cfd7f5> in <module>
          9     except StopIteration:
    ---> 10         sys.exit()
    

    SystemExit: 

    
    During handling of the above exception, another exception occurred:
    

    TypeError                                 Traceback (most recent call last)

        [... skipping hidden 1 frame]
    

    D:\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py in showtraceback(self, exc_tuple, filename, tb_offset, exception_only, running_compiled_code)
       2035                     stb = ['An exception has occurred, use %tb to see '
       2036                            'the full traceback.\n']
    -> 2037                     stb.extend(self.InteractiveTB.get_exception_only(etype,
       2038                                                                      value))
       2039                 else:
    

    D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py in get_exception_only(self, etype, value)
        821         value : exception value
        822         """
    --> 823         return ListTB.structured_traceback(self, etype, value)
        824 
        825     def show_exception_only(self, etype, evalue):
    

    D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py in structured_traceback(self, etype, evalue, etb, tb_offset, context)
        696             chained_exceptions_tb_offset = 0
        697             out_list = (
    --> 698                 self.structured_traceback(
        699                     etype, evalue, (etb, chained_exc_ids),
        700                     chained_exceptions_tb_offset, context)
    

    D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py in structured_traceback(self, etype, value, tb, tb_offset, number_of_lines_of_context)
       1433         else:
       1434             self.tb = tb
    -> 1435         return FormattedTB.structured_traceback(
       1436             self, etype, value, tb, tb_offset, number_of_lines_of_context)
       1437 
    

    D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py in structured_traceback(self, etype, value, tb, tb_offset, number_of_lines_of_context)
       1333         if mode in self.verbose_modes:
       1334             # Verbose modes need a full traceback
    -> 1335             return VerboseTB.structured_traceback(
       1336                 self, etype, value, tb, tb_offset, number_of_lines_of_context
       1337             )
    

    D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py in structured_traceback(self, etype, evalue, etb, tb_offset, number_of_lines_of_context)
       1190         """Return a nice text document describing the traceback."""
       1191 
    -> 1192         formatted_exception = self.format_exception_as_a_whole(etype, evalue, etb, number_of_lines_of_context,
       1193                                                                tb_offset)
       1194 
    

    D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py in format_exception_as_a_whole(self, etype, evalue, etb, number_of_lines_of_context, tb_offset)
       1148 
       1149 
    -> 1150         last_unique, recursion_repeat = find_recursion(orig_etype, evalue, records)
       1151 
       1152         frames = self.format_records(records, last_unique, recursion_repeat)
    

    D:\Anaconda3\lib\site-packages\IPython\core\ultratb.py in find_recursion(etype, value, records)
        449     # first frame (from in to out) that looks different.
        450     if not is_recursion_error(etype, value, records):
    --> 451         return len(records), 0
        452 
        453     # Select filename, lineno, func_name to track frames with
    

    TypeError: object of type 'NoneType' has no len()



```python
# 创建一个返回数字的迭代器，初始值是1，步长是1，递增
class Mynumbers:
    def __iter__(self):
        self.a = 1
        return self
    def __next__(self):
        x =self.a
        self.a +=1
        return x
myclass = Mynumbers()
myiter = iter(myclass)
print(next(myiter))
print(next(myiter))
print(next(myiter))
```

    1
    2
    3
    

**StopIteration异常**
- 用于标识迭代完成，防止出现无限循环的情况，在next()方法中我们可以设置在完成指定循环次数后触发StopIteration异常来结束迭代


```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    if self.a <= 20:
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration
 
myclass = MyNumbers()
myiter = iter(myclass)
 
for x in myiter:
  print(x)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    

### 生成器
- 使用了 yield 的函数被称为生成器（generator）
- 生成器是一个返回迭代器的函数，只能用于迭代操作
- 调用一个生成器函数，返回的是一个迭代器对象。每次遇到 yield 时函数会暂停并保存当前所有的运行信息，返回 yield 的值, 并在下一次执行 next() 方法时从当前位置继续运行


```python
print([x for x in range(5)])
print((x for x in range(5)))
numbers = (x for x in range(5))
for number in numbers:
    print(number,end=" ")
print(hasattr(numbers,'__iter__'))
print(hasattr(numbers,'next'))
```

    [0, 1, 2, 3, 4]
    <generator object <genexpr> at 0x00000159AE934BA0>
    0 1 2 3 4 True
    False
    

- 生成器表达式使用的是()而不是[]
- 生成器表达式无法像列表推导式那样直接输出，它和可迭代对象一样只能采用for循环调用next()函数，原因在于range返回的是一个可迭代对象，列表推导式之所以能直接print就是因为[]将可迭代对象转为列表


```python
def generator_function():
    print('hello 1')
    yield 1
    print('hello 2')
    yield 2
    print('hell0 3')
    yield 3
g = generator_function()
print(g)
next(g)
next(g)
next(g)

"""
当使用yield时，它自动创建了__iter__()和next()方法，而且在没有数据时，也会抛出StopIteration异常
带有yield函数的执行过程：
1. 调用该函数的时候不会立刻执行代码，而是返回了一个生成器对象
2. 当使用next()在for循环中会自动调用next()作用于返回的生成器对象时，函数开始执行，在遇到yield时会暂停，并且返回当前的迭代值
3. 当再次使用next()的时候，函数会从原来【暂停】的地方继续执行，直到遇到yield语句，如果没有yield语句，就抛出异常
"""
```

    <generator object generator_function at 0x00000159AE93E200>
    hello 1
    hello 2
    hell0 3
    




    3




```python
import sys
 
def fibonacci(n): # 生成器函数 - 斐波那契
    a, b, counter = 0, 1, 0
    while True:
        if (counter > n):
            return
        yield a
        a, b = b, a + b
        counter += 1
f = fibonacci(10) # f 是一个迭代器，由生成器返回生成
 
while True:
    try:
        print (next(f), end=" ")
    except StopIteration:
        sys.exit()
```

### 装饰器


```python

```

# 异常处理机制和文件操作
## 异常处理机制
### try except异常处理
```
try:
    可能产生异常的代码块
except [ (Error1, Error2, ... ) [as e] ]:
    处理异常的代码块1
except [ (Error3, Error4, ... ) [as e] ]:
    处理异常的代码块2
except  [Exception]:
    处理其它异常
```
- Error1, Error2,...) 、(Error3, Error4,...)：其中，Error1、Error2、Error3 和 Error4 都是具体的异常类型。显然，一个 except 块可以同时处理多种异常。
- [as e]：作为可选参数，表示给异常类型起一个别名 e，这样做的好处是方便在 except 块中调用异常类型（后续会用到）。
- [Exception]：作为可选参数，可以代指程序可能发生的所有异常情况，其通常用在最后一个 except 块。


```python
try:
    a = int(input("输入被除数："))
    b = int(input("输入除数："))
    c = a / b
    print("您输入的两个数相除的结果是：", c )
except (ValueError, ArithmeticError):
    print("程序发生了数字格式异常、算术异常之一")
except :
    print("未知异常")
print("程序继续运行")
```

    输入被除数：a
    程序发生了数字格式异常、算术异常之一
    程序继续运行
    

- **获取特定异常的有关信息**
PS：一个except可以同时处理多个异常
- 其实，每种异常类型都提供了如下几个属性和方法，通过调用它们，就可以获取当前处理异常类型的相关信息：
    - args：返回异常的错误编号和描述字符串；
    - str(e)：返回异常信息，但不包括异常信息的类型；
    - repr(e)：返回较全的异常信息，包括异常信息的类型。
    - 还可以使用traceback模块


```python
try:
    1/0
except Exception as e:
    # 访问异常的错误编号和详细信息
    print(e.args)
    print(str(e))
    print(repr(e))
```


```python
a = tuple(input().split(" "))
print(a)
```

    ss dd ff rr
    ('ss', 'dd', 'ff', 'rr')
    

### try except else 
- 在try...except...基础上添加了else


```python
try:
    result = 20/int(input("请输入除数："))
    print(result)
except ValueError:
    print("必须输入整数")
except ArithmeticError:
    print("算术错误，除数不能为0")
else:
    print("没有出现异常")
print("继续执行")
"""程序非法输入时：try捕获异常。except代码块处理异常，else不会执行；
程序合法输入时，except代码块不会执行，但是else代码开会执行
"""
```

### try except finally：资源回收
- finally语句功能：无论try是否发生异常，最终都要进入finally语句，并执行其中代码块，一般用来手动回收变量，类对象等


```python
try:
    a = int(input("请输入a的值"))
    print(20/a)
except:
    print("发生异常")
else:
    print("执行else中代码")
finally:
    print("执行finally块中代码")
"""
1、try中发生异常时，except和finally内代码都执行
2、try不发生异常时，else和finally内代码都执行
3、没有except和else的话，finally也执行
"""
```

### raise用法
- 语法格式：raise[exceptionName[(reason]
    -  [] 括起来的为可选参数，其作用是指定抛出的异常名称，以及异常信息的相关描述。如果可选参数全部省略，则 raise 会把当前错误原样抛出；如果仅省略 (reason)，则在抛出异常时，将不附带任何的异常描述信息。
- raise：单独一个 raise。该语句引发当前上下文中捕获的异常（比如在 except 块中），或默认引发 RuntimeError 异常。
- raise 异常类名称：raise 后带一个异常类名称，表示引发执行类型的异常。
- raise 异常类名称(描述信息)：在引发指定类型的异常的同时，附带异常的描述信息。


```python
try:
    a = input("输入一个数：")
    #判断用户输入的是否为数字
    if(not a.isdigit()):
        raise ValueError("a 必须是数字")
except ValueError as e:
    print("引发异常：",repr(e))
```

**raise不需要参数**



```python
try:
    a = input("输入一个数字：")
    if not a.isdigit():
        raise ValueError("a必须是数字")
except ValueError as e:
    print("引发异常",repr(e))
    raise
```

    输入一个数字：e
    引发异常 ValueError('a必须是数字')
    


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-3-a22128c2a45e> in <module>
          2     a = input("输入一个数字：")
          3     if not a.isdigit():
    ----> 4         raise ValueError("a必须是数字")
          5 except ValueError as e:
          6     print("引发异常",repr(e))
    

    ValueError: a必须是数字



```python
"""当在没有引发过异常的程序使用无参的 raise 语句时，它默认引发的是 RuntimeError 异常"""
try:
    a = input("输入一个数：")
    if(not a.isdigit()):
        raise
except RuntimeError as e:
    print("引发异常：",repr(e))
```

    输入一个数：u
    引发异常： RuntimeError('No active exception to reraise')
    

### sys.exc_info()方法：获取异常信息
- 两种获得异常信息的方法：
1、使用sys模块的exc_info方法
2、使用traceback模块中的相关函数
___
- exc_info() 方法会将当前的异常信息以元组的形式返回，该元组中包含 3 个元素，分别为 type、value 和 traceback，它们的含义分别是：
    - type：异常类型的名称，它是 BaseException 的子类（
    - value：捕获到的异常实例。
    - traceback：是一个 traceback 对象。


```python
# 使用sys模块之前，需要使用import引入
import sys
try:
    x = int(input("请输入一个被除数："))
    print("30除以",x,"=",30/x)
except:
    print(sys.exc_info())
    print("其他异常···")
```

    请输入一个被除数：y
    (<class 'ValueError'>, ValueError("invalid literal for int() with base 10: 'y'"), <traceback object at 0x00000170FA6822C0>)
    其他异常···
    


```python
"""要查看 traceback 对象包含的内容，需要先引进 traceback 模块，
然后调用 traceback 模块中的 print_tb 方法，print_tb 方法也仅是 traceback 模块众多方法中的一个
并将 sys.exc_info() 输出的 traceback 对象作为参数参入
"""
#使用 sys 模块之前，需使用 import 引入
import sys
#引入traceback模块
import traceback
try:
    x = int(input("请输入一个被除数："))
    print("30除以",x,"等于",30/x)
except:
    #print(sys.exc_info())
    traceback.print_tb(sys.exc_info()[2])
    print("其他异常...")
```

### traceback模块：获取异常信息
- 使用 traceback 模块查看异常传播轨迹，首先需要将 traceback 模块引入，该模块提供了如下两个常用方法：
    - traceback.print_exc()：将异常传播轨迹信息输出到控制台或指定文件中。
        - print_exc([limit[, file]]) 的完整形式是 print_exception(etype, value, tb[,limit[, file]])：
            - etype：指定异常类型；
            - value：指定异常值；
            - tb：指定异常的traceback 信息；
            - limit：用于限制显示异常传播的层数，比如函数 A 调用函数 B，函数 B 发生了异常，如果指定 limit=1，则只显示函数 A 里面发生的异常。如果不设置 limit 参数，则默认全部显示。
            - file：指定将异常传播轨迹信息输出到指定文件中。如果不指定该参数，则默认输出到控制台。
    - format_exc()：将异常传播轨迹信息转换成字符串。


```python
class SelfException(Exception):
    pass
def main():
    firstMethod()
def firstMethod():
    secondMethod()
def secondMethod():
    thirdMethod()
def thirdMethod():
    raise SelfException("自定义异常信息")    # 异常源头
main()
"""
main() 函数调用 firstMethod()，firstMethod() 调用 secondMethod()，
secondMethod() 调用 thirdMethod()，thirdMethod() 直接引发一个 SelfException 异常"""
```


    ---------------------------------------------------------------------------

    SelfException                             Traceback (most recent call last)

    <ipython-input-5-a77192356f52> in <module>
          9 def thirdMethod():
         10     raise SelfException("自定义异常信息")
    ---> 11 main()
    

    <ipython-input-5-a77192356f52> in main()
          2     pass
          3 def main():
    ----> 4     firstMethod()
          5 def firstMethod():
          6     secondMethod()
    

    <ipython-input-5-a77192356f52> in firstMethod()
          4     firstMethod()
          5 def firstMethod():
    ----> 6     secondMethod()
          7 def secondMethod():
          8     thirdMethod()
    

    <ipython-input-5-a77192356f52> in secondMethod()
          6     secondMethod()
          7 def secondMethod():
    ----> 8     thirdMethod()
          9 def thirdMethod():
         10     raise SelfException("自定义异常信息")
    

    <ipython-input-5-a77192356f52> in thirdMethod()
          8     thirdMethod()
          9 def thirdMethod():
    ---> 10     raise SelfException("自定义异常信息")
         11 main()
    

    SelfException: 自定义异常信息



```python
import traceback
import sys
class SelfException(Except):
    pass
def main():
    firstMethod()
def firstMethod():
    secondMethod()
def secondMethod():
    thirdMethod()
def thirdMethod():
    raise SelfException("自定义异常信息")

try:
    main()
except:
    traceback.print_exc()
    tarceback.print_exc(file=open('log.txt','a'))
    
```

### 自定义异常
- 创建一个新的异常类来拥有自己的异常，异常类继承自Exception类，可以直接继承、或者间接继承


```python
class MyError(Exception):
    def __init__(self,value):
        self.value = value
    def __str__(self):
        return repr(self.value)
try:
    raise MyError(2*2)
except Error as e:
    print("My exception occurred,value:",e.value)

```


    ---------------------------------------------------------------------------

    MyError                                   Traceback (most recent call last)

    <ipython-input-22-36ca6ac46cad> in <module>
          6 try:
    ----> 7     raise MyError(2*2)
          8 except Error as e:
    

    MyError: 4

    
    During handling of the above exception, another exception occurred:
    

    NameError                                 Traceback (most recent call last)

    <ipython-input-22-36ca6ac46cad> in <module>
          6 try:
          7     raise MyError(2*2)
    ----> 8 except Error as e:
          9     print("My exception occurred,value:",e.value)
    

    NameError: name 'Error' is not defined


## 文件操作
### 绝对路径和相对路径
- 常用文件操作函数：
    - os.getcwd()：获取当前工作路径的字符串
    - os.chdir(path)：改变文件路径,path：文件地址

![绝对路径和相对路径](https://raw.githubusercontent.com/Lyy999110/YanimagesCloud/main/202208281728962.jpeg)


```python
# 文件路径的书写
import os
os.getcwd()

myFiles = ['accounts.txt', 'details.csv', 'invite.docx']
for filename in myFiles:
    print(os.path.join('C:\\demo\\exercise', filename))
```

**python处理绝对路径和相对路径**
- 调用 os.path.abspath(path) 将返回 path 参数的绝对路径的字符串，这是将相对路径转换为绝对路径的简便方法。
- 调用 os.path.isabs(path)，如果参数是一个绝对路径，就返回 True，如果参数是一个相对路径，就返回 False。
- 调用 os.path.relpath(path, start) 将返回从 start 路径到 path 的相对路径的字符串。如果没有提供 start，就使用当前工作目录作为开始路径。
- 调用 os.path.dirname(path) 将返回一个字符串，它包含 path 参数中最后一个斜杠之前的所有内容；调用 os.path.basename(path) 将返回一个字符串，它包含 path 参数中最后一个斜杠之后的所有内容

### 文件基本操作
- 删除、修改权限：作用于文件本身，属于系统级操作。
- 写入、读取：是文件最常用的操作，作用于文件的内容，属于应用级操作。
    - 打开文件：使用 open() 函数，该函数会返回一个文件对象；
    - 对已打开文件做读/写操作：读取文件内容可使用 read()、readline() 以及 readlines() 函数；向文件中写入内容，可以使用 write() 函数。
    - 关闭文件：完成对文件的读/写操作之后，最后需要关闭文件，可以使用 close() 函数。
    
#### open( )函数：打开指定文件
- 语法格式：file = open(file_name [, mode='r' [ , buffering=-1 [ , encoding = None ]]])
    - file：表示要创建的文件对象。
    - file_name：要创建或打开文件的文件名称，该名称要用引号（单引号或双引号都可以）括起来。需要注意的是，如果要打开的文件和当前执行的代码文件位于同一目录，则直接写文件名即可；否则，此参数需要指定打开文件所在的完整路径。
    - mode：可选参数，用于指定文件的打开模式。可选的打开模式如表 1 所示。如果不写，则默认以只读（r）模式打开文件。
    - buffering：可选参数，用于指定对文件做读写操作时，是否使用缓冲区，如果 buffing 参数的值为 0（或者 False），则表示在打开指定文件时不使用缓冲区；如果 buffing 参数值为大于 1 的整数，该整数用于指定缓冲区的大小（单位是字节）；如果 buffing 参数的值为负数，则代表使用默认的缓冲区大小。
    - encoding：手动设定打开文件时所使用的编码格式，不同平台的 ecoding 参数值也不同，以 Windows 为例，其默认为 cp936（实际上就是 GBK 编码）。

![文件打开方式](https://raw.githubusercontent.com/Lyy999110/YanimagesCloud/main/202208291418999.png)


```python
# 以默认方式打开文件
f = open('my_file.txt','w')
# 输出文件是否已经关闭
print(f.closed)
# 输出访问模式
print(f.mode)
#输出编码格式
print(f.encoding)
# 输出文件名
print(f.name)
```

    False
    w
    cp936
    my_file.txt
    

#### read()，readline(),readlines()：读取文件
- read([size]):size指定一次最多可以读取的字节个数，默认一次性读取所有内容
- readline():可读模式下，用于读取文件中的一行，包括最后的换行符'\n'
- readlines()：用于读取文件中的所有行，包括同行的换行符


```python
#以二进制形式打开指定文件
f = open("my_file.txt")
import os
print(os.getcwd(f))
# byt1 = f.readline()
# print(byt1)
# byt2 = f.readlines()
# print(byt2)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-14-5c816ead4bb4> in <module>
          2 f = open("my_file.txt")
          3 import os
    ----> 4 print(os.getcwd(f))
          5 # byt1 = f.readline()
          6 # print(byt1)
    

    TypeError: getcwd() takes no arguments (1 given)


#### write()和writelines()
- 向文件中写入数据


```python
f = open("a.txt", 'w')
f.write("写入一行新数据")
f.close()
```


```python
# 如果向文件写入数据后，不想马上关闭文件，也可以调用文件对象提供的 flush() 函数，它可以实现将缓冲区的数据写入文件中
f = open("a.txt", 'w')
f.write("写入一行新数据")
f.flush()
```


```python
f = open('a.txt', 'r')
n = open('b.txt','w+')
n.writelines(f.readlines())
n.close()
f.close()
```

#### seek()和tell()函数
- 文件指针：用于标明文件读写的起始位置，假如把文件看成一个水流，文件中每个数据（以 b 模式打开，每个数据就是一个字节；以普通模式打开，每个数据就是一个字符）就相当于一个水滴，而文件指针就标明了文件将要从文件的哪个位置开始读起。
- tell() 函数：用于判断文件指针当前所处的位置
-  seek() 函数：用于移动文件指针到文件的指定位置。
    - 格式：file.seek(offset[, whence])
    - file：表示文件对象；
    - whence：作为可选参数，用于指定文件指针要放置的位置，该参数的参数值有 3 个选择：0 代表文件头（默认值）、1 代表当前位置、2 代表文件尾。
    - offset：表示相对于 whence 位置文件指针的偏移量，正数表示向后偏移，负数表示向前偏移。例如，当whence == 0 &&offset == 3（即 seek(3,0) ），表示文件指针移动至距离文件开头处 3 个字符的位置；当whence == 1 &&offset == 5（即 seek(5,1) ），表示文件指针向后移动，移动至距离当前位置 5 个字符处。
    - PS：当 offset 值非 0 时，Python 要求文件必须要以二进制格式打开，否则会抛出 io.UnsupportedOperation 错误


```python
"""当使用 open() 函数打开文件时，文件指针的起始位置为 0，
表示位于文件的开头处，当使用 read() 函数从文件中读取 3 个字符之后，文件指针同时向后移动了 3 个字符的位置"""
f = open("a.txt",'r')
print(f.tell())
print(f.read(3))
print(f.tell())
```


```python
"""格式：file.seek(offset[, whence])
由于程序中使用 seek() 时，使用了非 0 的偏移量，因此文件的打开方式中必须包含 b，
否则就会报  io.UnsupportedOperation 错误，有兴趣的读者可自定尝试。"""
f = open('a.txt', 'rb')
# 判断文件指针的位置
print(f.tell())
# 读取一个字节，文件指针自动后移1个数据
print(f.read(1))
print(f.tell())
# 将文件指针从文件开头，向后移动到 5 个字符的位置
f.seek(5)
print(f.tell())
print(f.read(1))
# 将文件指针从当前位置，向后移动到 5 个字符的位置
f.seek(5, 1)
print(f.tell())
print(f.read(1))
# 将文件指针从文件结尾，向前移动到距离 2 个字符的位置
f.seek(-1, 2)
print(f.tell())
print(f.read(1))
```

#### with...as...
- 表达式：
```
with 表达式 [as target]：
    代码块
```
- ps:用 [] 括起来的部分可以使用，也可以省略。其中，target 参数用于指定一个变量，该语句会将 expression 指定的结果保存到该变量中。with as 语句中的代码块如果不想执行任何语句，可以直接使用 pass 语句代替。

```
with open('a.txt', 'a') as f:
    f.write("\nPython教程")
    
输出：
C语言中文网
http://c.biancheng.net
Python教程
```

#### pickle模块
包括四个函数：
1. dumps()：将 Python 中的对象序列化成二进制对象，并返回；
2. loads()：读取给定的二进制对象数据，并将其转换为 Python 对象；
3. dump()：将 Python 中的对象序列化成二进制对象，并写入文件；
4. load()：读取指定的序列化数据文件，并返回对象
- PS：其中 dumps 和 loads 实现基于内存的 Python 对象与二进制互转；dump 和 load 实现基于文件的 Python 对象与二进制互转。


```python
import pickle
tup1 = tuple(("I am a girl").split(" "))
print(tup1)
#使用 dumps() 函数将 tup1 转成 p1
p1 = pickle.dumps(tup1)
print(p1)
#使用 loads() 函数将 p1 转成 Python 对象
t2 = pickle.loads(p1)
print(t2)

#使用 dumps() 函数将 tup1 转成 p1
with open ("a.txt", 'wb') as f: #打开文件
    pickle.dump(tup1, f) #用 dump 函数将 Python 对象转成二进制对象文件
with open ("a.txt", 'rb') as f: #打开文件
t3 = pickle.load(f) #将二进制文件对象转换成 Python 对象
print(t3)
```

    ('I', 'am', 'a', 'girl')
    b'\x80\x04\x95\x18\x00\x00\x00\x00\x00\x00\x00(\x8c\x01I\x94\x8c\x02am\x94\x8c\x01a\x94\x8c\x04girl\x94t\x94.'
    ('I', 'am', 'a', 'girl')
    

#### fileinput模块：逐行读取多个文件
- 格式：fileinput.input（files="filename1, filename2, ...", inplace=False, backup='', bufsize=0, mode='r', openhook=None）
    - files：多个文件的路径列表；
    - inplace：用于指定是否将标准输出的结果写回到文件，此参数默认值为 False；
    - backup：用于指定备份文件的扩展名；
    - bufsize：指定缓冲区的大小，默认为 0；
    - mode：打开文件的格式，默认为 r（只读格式）；
    - openhook：控制文件的打开方式，例如编码格式等。
___
- fileinput.filename()	返回当前正在读取的文件名称。
- fileinput.fileno()	返回当前正在读取文件的文件描述符。
- fileinput.lineno()	返回当前读取了多少行。
- fileinput.filelineno()	返回当前正在读取的内容位于当前文件中的行号。
- fileinput.isfirstline()	判断当前读取的内容在当前文件中是否位于第 1 行。
- fileinput.nextfile()	关闭当前正在读取的文件，并开始读取下一个文件。
- fileinput.close()	关闭 FileInput 对象。


```python
import fileinput
#使用for循环遍历 fileinput 对象
for line in fileinput.input(files=('my_file.txt', 'file.txt')):
    # 输出读取到的内容
    print(line)
# 关闭文件流
fileinput.close()
```

#### linecache模块：随机读取文件指定行
- linecache.getline(filename, lineno, module_globals=None)：读取指定模块中指定文件的指定行（仅读取指定文件时，无需指定模块）。其中，-filename 参数用来指定文件名，lineno 用来指定行号，module_globals 参数用来指定要读取的具体模块名。注意，当指定文件以相对路径的方式传给 filename 参数时，该函数以按照 sys.path 规定的路径查找该文件。
- linecache.clearcache()：如果程序某处，不再需要之前使用 getline() 函数读取的数据，则可以使用该函数清空缓存。
- linecache.checkcache(filename=None)：检查缓存的有效性，即如果使用 getline() 函数读取的数据，其实在本地已经被修改，而我们需要的是新的数据，此时就可以使用该函数检查缓存的是否为新的数据。注意，如果省略文件名，该函数将检车所有缓存数据的有效性。


```python
import linecache
import string
#读取string模块中第 3 行的数据
print(linecache.getline(string.__file__, 3))
# 读取普通文件的第2行
print(linecache.getline('my_file.txt', 2))
"""
输出结果：
Public module variables:
http://c.biancheng.net/linux_tutorial/
"""
```

#### pathlib模块
- PurePath.parts	返回路径字符串中所包含的各部分。
- PurePath.drive	返回路径字符串中的驱动器盘符。
- PurePath.root	返回路径字符串中的根路径。
- PurePath.anchor	返回路径字符串中的盘符和根路径。
- PurePath.parents	返回当前路径的全部父路径。
- PurPath.parent	返回当前路径的上一级路径，相当于 parents[0] 的返回值。
- PurePath.name	返回当前路径中的文件名。
- PurePath.suffixes	返回当前路径中的文件所有后缀名。
- PurePath.suffix	返回当前路径中的文件后缀名。相当于 suffixes 属性返回的列表的最后一个元素。
- PurePath.stem	返回当前路径中的主文件名。
- PurePath.as_posix()	将当前路径转换成 UNIX 风格的路径。
- PurePath.as_uri()	将当前路径转换成 URL。只有绝对路径才能转换，否则将会引发 ValueError。
- PurePath.is_absolute()	判断当前路径是否为绝对路径。
- PurePath.joinpath(*other)	将多个路径连接在一起，作用类似于前面介绍的斜杠（/）连接符。
- PurePath.match(pattern)	判断当前路径是否匹配指定通配符。
- PurePath.relative_to(*other)	获取当前路径中去除基准路径之后的结果。
- PurePath.with_name(name)	将当前路径中的文件名替换成新文件名。如果当前路径中没有文件名，则会引发 ValueError。
- PurePath.with_suffix(suffix)	将当前路径中的文件后缀名替换成新的后缀名。如果当前路径中没有后缀名，则会添加新的后缀名


```python
from pathlib import *
# 创建PurePath，实际上使用PureWindowsPath
path1 = PurePath('http:','c.biancheng.net','python')
print(path1)
path2 = PurePosixPath('http:','c.biancheng.net','python')
print(path2)
path3 = PurePath()
print(path3)
path4 = PurePath('C://','D://','my_file.txt')
print(path4)
path5 = PurePath('C://./my_file.txt')
print(path5)
# Unix风格的路径区分大小写
print(PurePosixPath('C://my_file.txt') == PurePosixPath('c://my_file.txt'))
# Windows风格的路径不区分大小写
print(PureWindowsPath('C://my_file.txt') == PureWindowsPath('c://my_file.txt'))
path6 = PurePosixPath('C://')
print(path6 / 'my_file.txt')
path7 = PurePosixPath('C://','my_file.txt')
print(str(path7))
"""output:
http:\c.biancheng.net\python
http:/c.biancheng.net/python
.
D:\my_file.txt
C:\my_file.txt
False
True
C:/my_file.txt
C:/my_file.txt
"""
```

#### os.path模块常见函数
1. os.path.abspath(path)	返回 path 的绝对路径。
2. os.path.basename(path)	获取 path 路径的基本名称，即 path 末尾到最后一个斜杠的位置之间的字符串。
3. os.path.commonprefix(list)	返回 list（多个路径）中，所有 path 共有的最长的路径。
4. os.path.dirname(path)	返回 path 路径中的目录部分。
5. os.path.exists(path)	判断 path 对应的文件是否存在，如果存在，返回 True；反之，返回 False。和 lexists() 的区别在于，exists()会自动判断失效的文件链接（类似 Windows 系统中文件的快捷方式），而 lexists() 却不会。
6. os.path.lexists(path)	判断路径是否存在，如果存在，则返回 True；反之，返回 False。
3. os.path.expanduser(path)	把 path 中包含的 "~" 和 "~user" 转换成用户目录。
3. os.path.expandvars(path)	根据环境变量的值替换 path 中包含的 "$name" 和 "${name}"。
3. os.path.getatime(path)	返回 path 所指文件的最近访问时间（浮点型秒数）。
3. os.path.getmtime(path)	返回文件的最近修改时间（单位为秒）。
3. os.path.getctime(path)	返回文件的创建时间（单位为秒，自 1970 年 1 月 1 日起（又称 Unix 时间））。
3. os.path.getsize(path)	返回文件大小，如果文件不存在就返回错误。
3. os.path.isabs(path)	判断是否为绝对路径。
3. os.path.isfile(path)	判断路径是否为文件。
3. os.path.isdir(path)	判断路径是否为目录。
3. os.path.islink(path)	判断路径是否为链接文件（类似 Windows 系统中的快捷方式）。
3. os.path.ismount(path)	判断路径是否为挂载点。
3. os.path.join(path1[, path2[, ...]])	把目录和文件名合成一个路径。
3. os.path.normcase(path)	转换 path 的大小写和斜杠。
3. os.path.normpath(path)	规范 path 字符串形式。
3. os.path.realpath(path)	返回 path 的真实路径。
3. os.path.relpath(path[, start])	从 start 开始计算相对路径。
3. os.path.samefile(path1, path2)	判断目录或文件是否相同。
3. os.path.sameopenfile(fp1, fp2)	判断 fp1 和 fp2 是否指向同一文件。
3. os.path.samestat(stat1, stat2)	判断 stat1 和 stat2 是否指向同一个文件。
3. os.path.split(path)	把路径分割成 dirname 和 basename，返回一个元组。
3. os.path.splitdrive(path)	一般用在 windows 下，返回驱动器名和路径组成的元组。
3. os.path.splitext(path)	分割路径，返回路径名和文件扩展名的元组。
3. os.path.splitunc(path)	把路径分割为加载点与文件。
3. os.path.walk(path, visit, arg)	遍历path，进入每个目录都调用 visit 函数，visit 函数必须有 3 个参数(arg, dirname, names)，dirname 表示当前目录的目录名，names 代表当前目录下的所有文件名，args 则为 walk 的第三个参数。
3. os.path.supports_unicode_filenames	设置是否可以将任意 Unicode 字符串用作文件名。


```python
from os import path
# 获取绝对路径
print(path.abspath("my_file.txt"))
# 获取共同前缀
print(path.commonprefix(['C://my_file.txt', 'C://a.txt']))
# 获取共同路径
print(path.commonpath(['http://c.biancheng.net/python/', 'http://c.biancheng.net/shell/']))
# 获取目录
print(path.dirname('C://my_file.txt'))
# 判断指定目录是否存在
print(path.exists('my_file.txt'))

"""output:
C:\Users\mengma\Desktop\my_file.txt
C://
http:\c.biancheng.net
C://
True
"""
```

#### fnmatch模块：用于文件名的匹配
- fnmatch.filter(names, pattern)	对 names 列表进行过滤，返回 names 列表中匹配 pattern 的文件名组成的子集合。
- fnmatch.fnmatch(filename, pattern)	判断 filename 文件名，是否和指定 pattern 字符串匹配
- fnmatch.fnmatchcase(filename, pattern)	和 fnmatch() 函数功能大致相同，只是该函数区分大小写。
- fnmatch.translate(pattern)	将一个 UNIX shell 风格的 pattern 字符串，转换为正则表达式


```python
import fnmatch
#filter()
print(fnmatch.filter(['dlsf', 'ewro.txt', 'te.py', 'youe.py'], '*.txt'))
#fnmatch()
for file in ['word.doc','index.py','my_file.txt']:
    if fnmatch.fnmatch(file,'*.txt'):
        print(file)
#fnmatchcase()
print([addr for addr in ['word.doc','index.py','my_file.txt','a.TXT'] if fnmatch.fnmatchcase(addr, '*.txt')])
#translate()
print(fnmatch.translate('a*b.txt'))

"""output:
['ewro.txt']
my_file.txt
['my_file.txt']
(?s:a.*b\.txt)\Z
"""
```

#### tempfile模块：生成临时文件 / 目录


```python
import tempfile
# 创建临时文件
fp = tempfile.TemporaryFile()
print(fp.name)
fp.write('两情若是久长时，'.encode('utf-8'))
fp.write('又岂在朝朝暮暮。'.encode('utf-8'))
# 将文件指针移到开始处，准备读取文件
fp.seek(0)
print(fp.read().decode('utf-8')) # 输出刚才写入的内容
# 关闭文件，该文件将会被自动删除
fp.close()
# 通过with语句创建临时文件，with会自动关闭临时文件
with tempfile.TemporaryFile() as fp:
    # 写入内容
    fp.write(b'I Love Python!')
    # 将文件指针移到开始处，准备读取文件
    fp.seek(0)
    # 读取文件内容
    print(fp.read()) # b'I Love Python!'
# 通过with语句创建临时目录
with tempfile.TemporaryDirectory() as tmpdirname:
    print('创建临时目录', tmpdirname)
    
"""output:
C:\Users\admin\AppData\Local\Temp\tmphvehw9z1
两情若是久长时，又岂在朝朝暮暮。
b'I Love Python!'
创建临时目录C:\Users\admin\AppData\Local\Temp\tmp3sjbnwob"""
```

#### 函数大集合
- os.access(path, mode) 检验权限模式
- os.chdir(path) 改变当前工作目录
- os.chflags(path, flags) 设置路径的标记为数字标记。
- os.chmod(path, mode) 更改权限
- os.chown(path, uid, gid) 更改文件所有者
- os.chroot(path) 改变当前进程的根目录
- os.close(fd) 关闭文件描述符 fd
- os.closerange(fd_low, fd_high) 关闭所有文件描述符，从 fd_low (包含) 到 fd_high (不包含), 错误会忽略
- os.dup(fd) 复制文件描述符 fd
- os.dup2(fd, fd2) 将一个文件描述符 fd 复制到另一个 fd2
- os.fchdir(fd) 通过文件描述符改变当前工作目录
- os.fchmod(fd, mode) 改变一个文件的访问权限，该文件由参数fd指定，参数mode是Unix下的文件访问权限。
- os.fchown(fd, uid, gid) 修改一个文件的所有权，这个函数修改一个文件的用户ID和用户组ID，该文件由文件描述符fd指定。
- os.fdatasync(fd) 强制将文件写入磁盘，该文件由文件描述符fd指定，但是不强制更新文件的状态信息。
- os.fdopen(fd[, mode[, bufsize]]) 通过文件描述符 fd 创建一个文件对象，并返回这个文件对象
- os.fpathconf(fd, name) 返回一个打开的文件的系统配置信息。name为检索的系统配置的值，它也许是一个定义系统值的字符串，这些名字在很多标准中指定（POSIX.1, Unix 95, Unix 98, 和其它）。
- os.fstat(fd) 返回文件描述符fd的状态，像stat()。
- os.fstatvfs(fd) 返回包含文件描述符fd的文件的文件系统的信息，Python 3.3 相等于 statvfs()。
- os.fsync(fd) 强制将文件描述符为fd的文件写入硬盘。
- os.ftruncate(fd, length) 裁剪文件描述符fd对应的文件, 所以它最大不能超过文件大小。

- os.getcwdu() 返回一个当前工作目录的Unicode对象
- os.isatty(fd) 如果文件描述符fd是打开的，同时与tty(-like)设备相连，则返回true, 否则False。
- os.lchflags(path, flags) 设置路径的标记为数字标记，类似 chflags()，但是没有软链接
- os.lchmod(path, mode) 修改连接文件权限
- os.lchown(path, uid, gid) 更改文件所有者，类似 chown，但是不追踪链接。
- os.link(src, dst) 创建硬链接，名为参数 dst，指向参数 src
- os.listdir(path) 返回path指定的文件夹包含的文件或文件夹的名字的列表。
- os.lseek(fd, pos, how) 设置文件描述符 fd当前位置为pos, how方式修改: SEEK_SET 或者 0 设置从文件开始的计算的pos; SEEK_CUR或者 1 则从当前位置计算; os.SEEK_END或者2则从文件尾部开始. 在unix，Windows中有效
- os.lstat(path) 像stat(),但是没有软链接
- os.major(device) 从原始的设备号中提取设备major号码 (使用stat中的st_dev或者st_rdev field)。
- os.makedev(major, minor) 以major和minor设备号组成一个原始设备号
- os.makedirs(path[, mode]) 递归文件夹创建函数。像mkdir(), 但创建的所有intermediate-level文件夹需要包含子文件夹。
- os.minor(device) 从原始的设备号中提取设备minor号码 (使用stat中的st_dev或者st_rdev field )。
- os.mkdir(path[, mode]) 以数字mode的mode创建一个名为path的文件夹.默认的 mode 是 0777 (八进制)。
- os.mkfifo(path[, mode]) 创建命名管道，mode 为数字，默认为 0666 (八进制)
- os.mknod(filename[, mode=0600, device]) 创建一个名为filename文件系统节点（文件，设备特别文件或者命名pipe）。
- os.open(file, flags[, mode]) 打开一个文件，并且设置需要的打开选项，mode参数是可选的
- os.openpty() 打开一个新的伪终端对。返回 pty 和 tty的文件描述符。
- os.pathconf(path, name) 返回相关文件的系统配置信息。
- os.pipe() 创建一个管道. 返回一对文件描述符(r, w) 分别为读和写
- os.popen(command[, mode[, bufsize]]) 从一个 command 打开一个管道
- os.read(fd, n) 从文件描述符 fd 中读取最多 n 个字节，返回包含读取字节的字符串，文件描述符 fd对应文件已达到结尾, 返回一个空字符串。
- os.readlink(path) 返回软链接所指向的文件
- os.remove(path) 删除路径为path的文件。如果path 是一个文件夹，将抛出OSError; 查看下面的rmdir()删除一个 directory。
- os.removedirs(path) 递归删除目录。
- os.rename(src, dst) 重命名文件或目录，从 src 到 dst
- os.renames(old, new) 递归地对目录进行更名，也可以对文件进行更名。
- os.rmdir(path) 删除path指定的空目录，如果目录非空，则抛出一个OSError异常。

- os.stat(path) 获取path指定的路径的信息，功能等同于C API中的stat()系统调用。
- os.stat_float_times([newvalue]) 决定stat_result是否以float对象显示时间戳
- os.statvfs(path) 获取指定路径的文件系统统计信息
- os.symlink(src, dst) 创建一个软链接
- os.tcgetpgrp(fd) 返回与终端fd（一个由os.open()返回的打开的文件描述符）关联的进程组
- os.tcsetpgrp(fd, pg) 设置与终端fd（一个由os.open()返回的打开的文件描述符）关联的进程组为pg。
- os.tempnam([dir[, prefix]]) Python3 中已删除。返回唯一的路径名用于创建临时文件。
- os.tmpfile() Python3 中已删除。返回一个打开的模式为(w+b)的文件对象 .这文件对象没有文件夹入口，没有文件描述符，将会自动删除。
- os.tmpnam() Python3 中已删除。为创建一个临时文件返回一个唯一的路径
- os.ttyname(fd) 返回一个字符串，它表示与文件描述符fd 关联的终端设备。如果fd 没有与终端设备关联，则引发一个异常。
- os.unlink(path) 删除文件路径
- os.utime(path, times) 返回指定的path文件的访问和修改的时间。
- os.walk(top[, topdown=True[, onerror=None[, followlinks=False]]]) 输出在文件夹中的文件名通过在树中游走，向上或者向下。
- os.write(fd, str) 写入字符串到文件描述符 fd中. 返回实际写入的字符串长度
- os.path 模块 获取文件的属性信息。

# 运算符
## 运算符

*ps： 主要有算术运算符，赋值运算符，位运算符，比较运算符，逻辑运算符，三目运算符，另外运算符也是有优先级的。*
### python位运算符


```python
a = 4 & 5  # 按位与
b = 4 | 5  # 按位或
c = 4 ^ 5  # 按位异或
d = -a    # 按位取反
e = 4 << 2   # 按位左移
f = 4 >> 2   # 按位右移
print(a,b,c,d,e,f)
```

    4 5 1 -4 16 1
    

### Python关系（比较）运算符

**==和is的区别：**
 用来比较两个变量的值是否相等，而 is 则用来比对两个变量引用的是否是同一个对象


```python
import time  #引入time模块
t1 = time.gmtime() # gmtime()用来获取当前时间
t2 =  time.gmtime()
print(t1 == t2) #输出True
print(t1 is t2) #输出False
```

    True
    False
    

### python位运算符


```python
a = 4 & 5  # 按位与
b = 4 | 5  # 按位或
c = 4 ^ 5  # 按位异或
d = -a    # 按位取反
e = 4 << 2   # 按位左移
f = 4 >> 2   # 按位右移
print(a,b,c,d,e,f)
```

    4 5 1 -4 16 1
    

### Python关系（比较）运算符

**==和is的区别：**
 用来比较两个变量的值是否相等，而 is 则用来比对两个变量引用的是否是同一个对象


```python
import time  #引入time模块
t1 = time.gmtime() # gmtime()用来获取当前时间
t2 =  time.gmtime()
print(t1 == t2) #输出True
print(t1 is t2) #输出False
```

    True
    False
    

### Python逻辑运算符

*ps：Python 逻辑运算符可以用来操作任何类型的表达式，不管表达式是不是 bool 类型；同时，逻辑运算的结果也不一定是 bool 类型，它也可以是任意类型*


```python
print(100 and 200)
print(45 and 0)
print("" or "http://c.biancheng.net/python/")
print(18.5 or "http://c.biancheng.net/python/")
```

    200
    0
    http://c.biancheng.net/python/
    18.5
    

**逻辑运算符的本质：**
- 对于and运算符，如果左边表达式的值为假，那么就不用计算右边表达式的值；
- 对于or运算符，如果左边表达式的值为真，那么就不用计算右边表达式的值；
- not:非运算


```python
url = "http://c.biancheng.net/cplus/"

print("----False and xxx-----")
print( False and print(url) )
print("----True and xxx-----")
print( True and print(url) )
print("----False or xxx-----")
print( False or print(url) )
print("----True or xxx-----")
print( True or print(url) )
```

    ----False and xxx-----
    False
    ----True and xxx-----
    http://c.biancheng.net/cplus/
    None
    ----False or xxx-----
    http://c.biancheng.net/cplus/
    None
    ----True or xxx-----
    True
    

### python三目（三元）运算符

使用 if else 实现三目运算符（条件运算符）的格式如下：  
&emsp;&emsp;<font face=“黑体” color=#FF0000>exp1 if condition else exp2</font>

*ps：condition 是判断条件，exp1 和 exp2 是两个表达式。如果 condition 成立（结果为真），就执行 exp1，并把 exp1 的结果作为整个表达式的结果；如果 condition 不成立（结果为假），就执行 exp2，并把 exp2 的结果作为整个表达式的结果。*


```python
a = int( input("Input a: ") )
b = int( input("Input b: ") )
print("a大于b") if a>b else ( print("a小于b") if a<b else print("a等于b") )
```

    Input a: 1
    Input b: 2
    a小于b
    

- ##### 运算符优先级表格

*// ：用于向下取接近除数的整数*

![运算符优先级](./imgs/运算符优先级.jpg)

## 其他

### 转义字符及其用法

| 转义字符 | 说明 |
|:----|:----:|
|\n	|换行符,将光标位置移到下一行开头。  |
|\r	|回车符,将光标位置移到本行开头。 |
|\t	|水平制表符,也即 Tab 键，一般相当于四个空格。  |
|\a	|蜂鸣器响铃,注意不是喇叭发声，现在的计算机很多都不带蜂鸣器了，所以响铃不一定有效。  |
|\b	|退格（Backspace,将光标位置移到前一列。  |
|\\|	反斜线  |
|\\'|	单引号  |
|\\"|	双引号  |
|\	|在字符串行尾的续行符，即一行未完，转到下一行继续写。  |

### <font color='red'>python数据类型转换函数</font>

| 函数 | 作用 |
|:----|:----:|
| int(x) | 将x转换成整数类型 |
| complex(real,[imag]) | 创建一个复数 |
| repr(x) | 将x转换成表达式字符串 |
| eval(x) | 计算在字符串中的有效python表达式，并返回一个对象 |
| chr(x) | 将整数x转换成一个字符 |
| ord(x) | 将字符x转换成它对应的整数值 |
| hex(x) | 将一个整数x转换成一个十六进制字符串 |
| oct(x) | 将一个整数x转换成一个八进制字符串 |


```python
a = 7>>2
print(a)
```

    1
    

### Python保留字


```python
import keyword
keyword.kwlist
```




    ['False',
     'None',
     'True',
     'and',
     'as',
     'assert',
     'async',
     'await',
     'break',
     'class',
     'continue',
     'def',
     'del',
     'elif',
     'else',
     'except',
     'finally',
     'for',
     'from',
     'global',
     'if',
     'import',
     'in',
     'is',
     'lambda',
     'nonlocal',
     'not',
     'or',
     'pass',
     'raise',
     'return',
     'try',
     'while',
     'with',
     'yield']



### 多行语句
# Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠 \ 来实现多行语句
total = item_one + \
        item_two + \
        item_three
# 在 [], {}, 或 () 中的多行语句，不需要使用反斜杠 \
total2 = ['item_one','item_two','item_three',
        'item_four','item_five']
### python是个弱类型的语言

- 弱类型语言有两个特点：
    - 变量无须声明就可以直接赋值，对一个不存在的变量赋值就相当于定义了一个新变量。
    - 变量的数据类型可以随时改变，比如，同一个变量可以一会儿被赋值为整数，一会儿被赋值为字符串

### python的几种进制
- 十进制
- **八进制：**以0O或者0o或者直接以0开头；
- **二进制：**以0b或者0B开头；
- **十六进制：**以0X或者0x开头
- **指数形式：**aEn 或 aen，2.1E5 = 2.1×10^5

### python的复数运算


```python
c1 = 12 + 0.2j
print("c1Value: ", c1)
print("c1Type", type(c1))

c2 = 6 - 1.2j
print("c2Value: ", c2)

#对复数进行简单计算
print("c1+c2: ", c1+c2)
print("c1*c2: ", c1*c2)
```
