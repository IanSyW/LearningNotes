

> 刚开始的时候，平静地接受自己的笨拙。
>
> 1. 尽快开始这个过程；
> 2. 尽快度过这个过程。
>
> 掌握最少必要知识之后马上开始行动，而后就要把注意力专注在改进之上 。
>
> 要想真正摒弃掉面子这种“刚需”，就要想清楚对于自己来说，更重要的是什么。
>
> 看一个人执行力强不强，就看他在做得不足够好的时候是否持续地做……
>
> 长期。成长。

# Python

> AILearning：https://ailearning.apachecn.org/#/docs/da/007

## 1.演示

### 字符串

- split 字符串分割

``` python
string = "hello world"
string.split()

>>> ['hello', 'world']
```

### 列表

- 用 [ ] 生成列表
  - 可以有各种类型数据
  - 相加是加在后面（和矩阵不同）

``` python
a = [1, 2.0, 'hello'， 1+5.0]
a + a
>>> [1, 2.0, 'hello'， 6.0, 1, 2.0, 'hello'， 6.0]

a.append('world')
```

### 集合

- 用 { } 生成集合
  - 集合可以去重

``` python
s = {2, 2, 3, 4}
s
>>> {2, 3, 4}

s.add(1)
s
>>> {1, 2, 3, 4}

a & b  # 集合的交
a | b  # 集合的并
a - b  # 只在a不在b
a ^ b  # 对称差，在a或在b，但不在a｜b中的
```

### 字典

- 键值对，用 {key : value} 生成

``` python
d = {'dogs':4, 'cats':5}
d
>>> {'cats':5, 'dogs':4}

d["dogs"] = 7  # 修改键值对
d["pigs"] = 7  # 添加键值对
d.items()
>>> [('cats':5), ('dogs':7), ('pigs':7)]

d.items()
d.keys()
d.values()
```

### Numpy

- Array，广播机制
  - arange( )，属于array数组

``` python
from numpy import array
a = array([1,2,3,4])
a + 2, a + a, a
>>> array([3,4,5,6]), array([2,4,6,8]), array([1,2,3,4])
```

### Matplot

- 

``` python
import matplotlib.pyplot as plt
plt.plot()
```

### 循环 Loop

``` python
line = '1 2 3 4 5'
fields = line.split()
fields
>>> ['1', '2', '3', '4', '5']

for field in fields:
  field+=field
```

- 列表推导机制（List Comprehension）

``` python
numbers = [int(firld) for field in fields]
numbers
>>> [1, 2, 3, 4, 5]

sum(numbers)
```

### 文件操作

``` python
cd ~

f = open('1.txt', 'w')
f.write('1 2 3\n')
f.write('1 2 3 4\n')

data = []
for line in f:
  data.append([int(field) for field in line.split()])
f.close()

data
>>> [[1, 2, 3], [1, 2, 3, 4]]

import os
os.remove('1.txt')
```

### 类 Class

``` python
Class Person(object):  # 是object的子类
	# __init__是初始化对象的函数，self等于Java中this
  def __init__(self, first, last, age):
    self.first = first
    self.last = last
    self.age = age
  def full_name(self):
    return self.first + ' ' + self.last

person = Person('A', 'B', 19)
```



## 2.详细

### 2.1 数字

1. 存储过大的数字时，自动变成长整数

``` python
a = 1L
type(a)
>>> 'long'
```

2. 浮点数存储 0.2 时会有误差，用 print 输出会自动校正

3. 复数 complex

``` python
a = 1+2j
a.real
a.imag
a.conjugate()  # 共轭
```

4. 整数除法

``` python
# 返回一个小于结果的最大整数
a // b 
```

5. python支持链式比较

``` python
x = 2
1 < x <= 3
>>> True 
```

### 2.2 字符串

``` python
s = 'echo'
s * 3
>>> 'echoechoecho'
```

#### 2.2.3.替换 replace 返回新字符串，s不变

``` python
1. 分割 split
s = '1,2,3,4,5'
numbers = s.split(',')
numbers
>>> ['1','2','3','4','5']

2. 连接 jion
s = ' '
s.join(numbers)
>>> '1 2 3 4 5'

3. 替换 replace 返回新字符串，s不变
s = 'hello world'
s.replace('world', 'python')

4. 大小写（upper，lower）、去除空格（strip）

5.dir(s)  查看所有字符串函数

6.''' a ''' 多行

7.美观换行，实际不换行（"" ""）（ \ ）

8. 格式化字符串 format
'{} {} {}'.format('a', 'b', 'c')
>>> 'a b c'

'{color} {0} {x} {1}'.format(10, 'foo', x = 1.5, color='blue')
>>> 'blue 10 1.5 foo'
```

### 2.3 索引和分片

1. 分片 [lower : upper : step]，左闭右开

``` python
s = 'hello world'
当step是负数时，从结尾往前分片

s[::-1]
>>> 'dlrow olleh'
s[3::-1]
>>> 'lleh'
s[:4:-1]
>>> 'dlrow '

```

### 2.4 列表

``` python
s = []
s = list()
s = [1, 2, 'num', 2.0]
s * 2
>>> [1, 2, 'num', 2.0, 1, 2, 'num', 2.0]
```

1. 分片 可以修改，也可以整段替换

``` python
a = [1,2,3,4,5]
a[0] = 9
a[1:3] = [11, 12, 13, 14, 15]
a
>>> [9, 11, 12, 13, 14, 15, 4, 5]

修改步长不为1的列表时，修改的元素个数必须相同
```

2. 删除 del

``` python
del a[1:]
>>> [1]
```

3. in / not in 判断是否在列表（或字符串）内
4. 列表中可以包含对象，甚至包含列表

#### 2.4.5. 函数 （pop返回新的，sorted返回新的）

``` python
元素出现了几次
a.count(1)

元素位置，返回第一个该元素的位置，不存在则报错
a.index(1)

添加元素，不展开
a.append([1,2])

添加序列，展开
a.extend([1,2])
>>> [9, 11, 12, 13, 14, 15, 4, 5, 1, 2]

插入元素 (idx, ob) 
a.insert(3, 'a')  # 在3的索引处插入a

移除元素
a.remove('a')  # 移除第一个出现的a 

弹出元素
b = a.pop('a')  # 弹出并返回该元素

排序 sort 排序并返回一个新的数组，原数组不变 sorted
b = sorted(a)

反向
a.reverse()
也可[::-1] 传给一个新的
```

### 2.5 可变和不可变类型

不可变：int、string、long、float、complex、tuple

可变：list、dictionary、set、numpy array

基本数据类型不可变

```python
a = [1,2]
b = a  # 指向同一片内存空间
```

### 2.6 元组 tuple

1. 用 ( ) 生成
2. 可索引和切片，不可变

``` python
a = (10,)  # 元组类型
a = (10)  # int类型

count()
index()
```

3. 元组生成速度比列表快，索引和遍历速度差不多

### 2.7 字典 （hash、map）

1. 用 { } 或 dic( ) 创建
2. 字典没有顺序，不一定按照插入键值的先后顺序显示
3. 不能数字索引
4. 键必须是不可改变的类型，值任意
5. 可以将元组强制转换成 dict( )
6. 方法

``` python
a = {'cat':1, 'dog':2}

get方法，不存在该键值对时，不会报错 (key, default=None)
a['pig']  # 报错
a.get('pig') 
>>> None

pop方法

del方法

update
a.update(new_dict)  # 在原有基础上更新字典（添加或修改）

in查询是否有该键
```

### 2.8 集合

1. 只能放入不可变的元素，去重
2. 用 set( ) 或 {1,2} 创建 **"{ } 是创建空字典**“
3. 一些方法，并"演示”中的

``` python
a = {1,2,3}
b = {1,2}

包含
b <= a		b.issubset(a)
a <= b		a.issuperset(b)

add 添加元素 同列表的append
a.add('l')
a.add((1, 2, 2))

update 逐个添加 同列表的extend

remove pop 删除元素
a.remove(1)  # 没有1就报错

discard 删除元素，没有不报错

difference——update 删除所有元素
a.difference_update(b)  # 从a中删除所有b中的元素

```

### 2.9 不可变集合

1. frozenset 建了就不可变，常用于键值对中的键 

### 2.10 python赋值机制

1. x = y 默认指向同一片内存空间

``` python
x = 100
y = x
x is y
>>> True

y = 'yoo'
x is y
>>> False

# python为每一个变量独立分配空间，但小数值可能相同
x = 100
y = 100
x is y
>>> False

x = 2
y = 2
x is y 
>>> True

x = [100,200,300]
y = x
y[1] = 600  # 新建一个pos存储600，200被回收
y = [800, 900]
x is y
>>> False

```

### 2.11 判断语句

``` python
if < >:
  < >
elif < >:
  < >
  
and or not

被认为是False的：
False
None
0
空字符串、空列表、空字典、空集合
```

### 2.12 循环

``` python
# python3 xrange = range
for i in range(1e60):
for i in xrange(1e60):  # 不会一次性生成所有元素，速度更快
  
# for while 也跟else，必须有break，被break了不执行else，正常结束，执行else
for i in range(10):
  i = i
else:
  print('a')
>>> a
for i in range(10):
  i = i
  break
else:
  print('a')
>>> 

```

### 2.13 列表推导式

1. 列表、集合、字典，元组好像不行

``` python
values = [10,21,4,7,12]
squares = [x**2 for x in values if x <= 10]
print(squares)
square_set = {x**2 for x in values if x <= 10}
square_dict = {x: x**2 for x in values if x <= 10}
```

### 2.14 函数

1. python不指定参数类型

``` python
# 可以指定默认值
def fun(x, y=1):
  return x+y, x-y, x*y
fun(1)
fun(x=1, y=2)

# 不指定参数个数
def fun(x, *args)  # 相当于元组
	return
fun(1,2,3,4)

def fun(x, **kwargs)  # 相当于字典
	for a, b in kwargs.items():
    print(a, b)
	return
fun(x, y=1, z=2)

# 用元组和字典传参
def add(x, y):
  """Add two numbers"""
  a = x + y
  return a

m = (2,3)
w = {'x':2, 'y':3}
add(*m)
add(**w)

# map方法生成列表 map(aFun, aSeq)
def add(x, y): 
    return x + y

a = (2,3,4)
b = [10,5,3]
print map(add,a,b)
>>> [12, 8, 7]
```



# Numpy

## 

``` python
import numpy
from numpy import *
```

## 1. 简介

广播，对应元素相操作，列表就不行

## 2. 数组

### 2.1 介绍

1. 数组中元素类型必须一致，相同
2. 

``` python
a = array ([ ], dtype=float32) 
a.shape  
a.fill( 5 )  # 填充
a.size  # 元素个数
a.ndim  # 维度

# 索引
a[1,3]  equals a[1][3]

# 可以双切片
a[1::,::2]

# !array里的切片指向同一内存地址，列表里的切片不指向同一内存，修改之后原列表不变!
可以用 b=a[:].copy()

# 花式索引，返回复制体而不是引用
indices = [1, 2, -3] 
y = a[[1, 2, -3]]
y

mask = array([0,1,1,0,0,1,0,0], dtype=bool)
y = a[mask]

mask = a > 0.5
a[mask]

# where， 返回元组，多维就返回每一维度的元组
indices = where(a>10)[0]
a > 10

# 多种类型的array
a = array([1,1.2,'hello', [10,20,30]], dtype=object)

# 迭代器
a.flat[:]
for elt in a.flat:
    print elt
```

### 2.2 方法

``` python
b = asarray(a, dtype=float32)  # 元素类型不同则复制，相同则引用
b.astype(uint8)  # 返回新的

求和
sum(a, axis=0)  # 按列求和，将该列的所有加起来变成一个
a.sum(axis=0)

求积 product
prod(a, axis=0)
a.prod(axis=0)

max(), min(), mean(), std()标准差, var()方差

clip(3,5)  # 把小于的变成3，大于的变成5

# 最大最小值的差
ptp()
# 近似
round()

# 对角线
a.diagonal(offset=1)  # 正数表示右偏移，负数左偏

# 比较
if all(a==b): 
if allclose(a,b): 
  
# 降维 reduce
a = np.array([1,2,3,4])
np.add.reduce(a)
a = np.array([[1,2,3],[4,5,6]])
np.add.reduce(a, 1)

# 累加
a = np.array(['ab', 'cd', 'ef'], np.object)
np.add.accumulate(a)

# 间断吃
op.reduceat(a, indices) 
a = np.array([0, 10, 20, 30, 40, 50])
indices = np.array([1,4])
np.add.reduceat(a, indices)
>>> array([60, 90])

# outer
a = np.array([0,1])
b = np.array([1,2,3])
np.add.outer(a, b)
>>> array([[1, 2, 3],
       		 [2, 3, 4]])
```

### 2.3 排序

使用函数不会改变原来的数组

``` python
sort(a)
a.sort(axis=)

argsort(a)  # 返回从小到大的元素位置

searchsorted(sorted_array, values)
# 一个排好序的数组A，将B中元素按顺序插入A中，返回插入的索引值
```

### 2.4 改变形状

``` python
reshape()  # 返回一个新的数组
a.shape = 3,2

a.squeeze()  # 去除长度为1的维度

a.transpose()  equals  a.T
	a = np.arange(60)
	a.shape = 3,4,5
	a.T.shape
  >>> (5, 4, 3)
# 转置只是换一种视角，实际是引用

# 数组连接，两个数组对应维度必须相同
z = concatenate((x,y), axis=0)
vstack(x,y)
hstack(x,y)
dstack(x,y)  equals  z = array((x,y))

# 多维变一维
b = a.flatten()  # 返回复制体
b= a.ravel()  # 返回引用，当a为view状态的时候，返回复制体

atleast_2d(value)	
```

### 2.5 数组转换字符串

a.tostring(order=)

b = np.fromstring(a, dtype=)



### 2.6 生成数组

``` python
np.arange(start, stop, step, dtype)

linspace(start, stop, N)  # 产生N个等间距的元素，包括stop

logspace(start, stop, N)  # 产生 N 个对数等距分布的数组，默认以10为底：

# 生成网格
np.meshgrid(sparse'去冗余')  # 不懂
x_ticks = np.linspace(-1,1,5)
y_ticks = np.linspace(-1, 1,5)
np.meshgrid(x_ticks, y_ticks, sparse=True)
>>>	[array([[-1. , -0.5,  0. ,  0.5,  1. ]]),
 		array([[-1. ],
        	[-0.5],
        	[ 0. ],
        	[ 0.5],
        	[ 1. ]])]

ogrid,  mgrid

# 生成行列向量
np.r_(0:1:.1). np.c_(0:1:.1)
np.r_(0:1:5j)  # 复数5j，表示需要五个元素，这样就包括了1

np.r_[(3,22,11), 4.0, [15, 6]]  # 连接多个序列，产生数组


np.zeros(3, dtype=np.float32)
np.ones([2,3], dtype=np.float32) * 5
np.empty([3,2]) + a.fill(5)  # empty生成的内是乱码

# 产生大小一样、类型一样的数组
empty_like(a)
ones_like(a)
zeros_like(a) 

# 单位矩阵
indentity(n, dtype=float64) 
>>> array([[ 1.,  0.,  0.],
   		     [ 0.,  1.,  0.],
    	     [ 0.,  0.,  1.]])
```

### 2.7 矩阵

``` python
使用 mat 、bmat 方法把二维数组转化为矩阵

a = np.mat(a)
A = np.mat('1,2,4;2,5,3;7,8,9')

a = np.array([[ 1, 2],
              [ 3, 4]])
b = np.array([[10,20], 
              [30,40]])

np.bmat('a,b;b,a')

# 逆矩阵
A.I

# 矩阵指数表示矩阵连乘
A**4
```

### ?

1. `nan` 与任何数进行比较都是 `False`，只有 `0/0` 会得到 `nan`，非0值除以0会得到无穷，`nan` 开头的函数会进行相应的操作，但是忽略 `nan` 值。

### 向量化函数

``` python
# 单纯函数不能处理数组，将其vectorize
vsinc = np.vectorize(sinc)
```



# Matplotlab

## 

``` python
import matplotlib.pyplot as plt
```

### 1.plot函数

``` python
plt.plot(x, y, format_str)
```

![颜色字符参数](/Users/iansy/Documents/Code/python/mkPicAsserts/颜色字符参数.png)

![类型字符参数](/Users/iansy/Documents/Code/python/mkPicAsserts/类型字符参数.png)

``` python
plt.plot([1,2,3,4],[1,4,9,16], 'ro')  # 红色圆点
plt.show()

plt.plot(x, y, linwidth=2.0, color='r')
```

### 2. axis

指定坐标轴显示范围

``` python
plt.axis([xmin, xmax, ymin, ymax])
plt.xlim(a,b)    plt.ylim(a,b)
```

Colormap

### 处理文本

1. r 表示 raw string，$ $ 内存放 Tex 语法

``` python
plt.title(r'$\alpha $')
```

### 标签

``` python
plt.plot([1,2,3],label='max')

plt.legend([x,y],['1','2'])
```

# Pandas

## 十分钟上手Pandas

### ？

1. Series 一维
2. DataFrame 二维

``` python
pd.Series()
pd.DataFrame(a, index=list('ABCDE'),column=list('ABCDE'))

df = pd.DataFrame('A':1,
     			        'B':'list')  # 字典key代表列，列数值类型相同即可

df.head()  df.tail(3)

df.index  # 查看下标 行标
df.columns  # 查看列表 列名
df.values  # 查看数值

# 简单统计数据
df.describe()

# 转置 
df.T

# 排序
df.sort_index(axis=0, ascending=False)
df2.sort_values(by='E', axis=0, ascending=True)  # 按E列的值排序

```

