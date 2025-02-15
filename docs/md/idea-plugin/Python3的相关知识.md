## Python3的相关知识

### 1.基本数据类型

Python3中常见的基本数据类型有：

* Number(数字)
* String(字符串)
* bool(布尔类型)
* List(列表)
* Tuple(元组)
* Set(集合)
* Dictionary(字典)

其中，Number(数字),String(字符串)和Tuple(元组)属于不可变数据，而List(列表),Set(集合)和Dictionary(字典)则属于可变数据。



### 2.Number(数字)

Python3支持int,float,bool,complex(复数)。

需要注意的是，复数可以用`a+bj`来表示，也可以用`complex(a,b)`来表示，其中，实部a和虚部b都是浮点型。

Number对象的创建是通过指定值来进行的，也就是说，只要指定一个值，Number对象就会被创建：

```
var1 = 1
var2 = 10
```

var1和var2这两个对象就被创建好了。

需要注意的是，可以同时为多个变量赋值：

```
length,money,str,fushu,buer=100.98,60,'abcd',4+3j,True
print(length,money,str,fushu,buer)
```

结果如下所示：

```
100.98 60 abcd (4+3j) True
```

可以看出，Python的赋值是相当方便的。



删除对象可以用del，可以删除单个或多个：

```
del var
del var_a, var_b
```



其中，内置的type()函数可以用来查询变量所指的对象类型，并且isinstance()函数也可以判断

```
length,money,str,fushu,buer=100.98,60,'abcd',4+3j,True
print(length,money,str,fushu,buer)
print(type(length),type(money),type(str),type(fushu),type(buer))
print(isinstance(length,float))
```



效果如下所示：

> 100.98 60 abcd (4+3j) True
> <class 'float'> <class 'int'> <class 'str'> <class 'complex'> <class 'bool'>
> True

可以看到，每个变量所指的对象类型都正确地显示出来了，其中，isinatance()如果类型一致则会输出True。



此外，issubclass(A,B)函数用于判断A是否是B的子类，例如：

```
print(issubclass(bool,int))
```

输出的结果为True，这是因为Python3中bool是int的子类。



数值运算：

在Python中，加减乘以及取余运算都是正常的，但是除法包含两种运算符：

**/** 返回一个浮点数，**//** 返回一个整数。

> 2 / 4 # 除法，得到一个浮点数
>0.5
>\>>> 2 // 4 # 除法，得到一个整数
>0

另外，Python多了一个乘方运算：

> 2**5

就相当于2的5次方，结果是32。

需要注意的一点是，Python在混合运算时，会把整型转化为浮点数。



### 3.String(字符串)

Python中的字符串用单引号`''`或双引号`""`括起来，同时使用反斜杠`\`转义特殊字符

字符串的截取如下：

```
str = 'Runoob'

print (str)          # 输出字符串
print (str[0:-1])    # 输出第一个到倒数第二个的所有字符
print (str[0])       # 输出字符串第一个字符
print (str[2:5])     # 输出从第三个开始到第五个的字符
print (str[2:])      # 输出从第三个开始的后的所有字符
print (str * 2)      # 输出字符串两次，也可以写成 print (2 * str)
print (str + "TEST") # 连接字符串
```

执行以上程序会输出如下结果：

>```
>Runoob
>Runoo
>R
>noo
>noob
>RunoobRunoob
>RunoobTEST
>```

通过上面的案例，可以看到：

* 字符串可以用+运算符连接在一起，用*运算符重复。
* Python中字符串有两种索引方式，从左往右以0开始，从右往左以-1开始。
* 字符串截取时都是左闭右开区间。



Python使用反斜杠`\`转义特殊字符，如果不想转义的话，可在其前面添加一个`r`（raw)，表示原始字符串,实例如下：

```
>>>print('Ru\noob')
Ru
oob
>>> print(r'Ru\noob')
Ru\noob
>>>
```

需要注意的是，Python没有单独的字符类型，一个字符就是长度为1的字符串。

>\>>> word = 'Python'
>\>>> **print**(word[0], word[5])
>P n
>\>>> **print**(word[-1], word[-6])
>n P

并且，Python中的字符串不能被改变。向一个索引位置赋值，比如`word[0]='m'`会导致错误。



### 4.bool(布尔类型)

布尔类型即True或False,有如下特点：

* 布尔类型只有两个值，True或False.
* 布尔类型可以和其他数据类型进行比较，在比较时，Python会将True视为1，将False视为0.
* 布尔类型可以和逻辑运算符一起使用，包括and,or,not,这些运算符可以用来组合多个布尔表达式。
* 布尔类型也可以被转化为其他数据类型，比如整数，浮点数和字符串。在转换时，True会被转换为1，False会被转换为0.

实例如下所示：

>a = True
>b = False
>
>\# 比较运算符
>**print**(2 < 3)  # True
>**print**(2 == 3) # False
>
>\# 逻辑运算符
>**print**(a **and** b) # False
>**print**(a **or** b)  # True
>**print**(**not** a)   # False
>
>\# 类型转换
>**print**(int(a))  # 1
>**print**(float(b)) # 0.0
>**print**(str(a))  # "True"

需要注意的是，在Python中，所有非0的数字和非空的字符串，列表，元组等数据类型都被视为True，只有0、空字符串、空元组、空列表等被视为False。



### 5.List(列表)

List(列表)是Python中使用最频繁的数据类型。

列表可以完成大多数集合类的数据结构实现。列表中元素的类型可以不相同，它支持数字，字符串甚至可以包含列表(嵌套)。

和字符串一样，列表可以被索引和截取，列表被截取后返回一个包含所需元素的新列表。

和字符串一样，索引值以`0`为开始值，`-1`为从末尾的开始位置。

加号`+`是列表连接运算符，星号`*`是重复操作。实例如下：

```
list = [ 'abcd', 786 , 2.23, 'runoob', 70.2 ]
tinylist = [123, 'runoob']

print (list)       # 输出完整列表
print (list[0])     # 输出列表第一个元素
print (list[1:3])    # 从第二个开始输出到第三个元素
print (list[2:])     # 输出从第三个元素开始的所有元素
print (tinylist * 2)   # 输出两次列表
print (list + tinylist) # 连接列表
```



下面是以上实例输出结果：

>```
>['abcd', 786, 2.23, 'runoob', 70.2]
>abcd
>[786, 2.23]
>[2.23, 'runoob', 70.2]
>[123, 'runoob', 123, 'runoob']
>['abcd', 786, 2.23, 'runoob', 70.2, 123, 'runoob']
>```

可以看出，列表的元素可以不一样。

与Python字符串不一样的是，列表元素是可以改变的，执行以下代码：

```
a = [1, 2, 3, 4, 5, 6]
a[0] = 9
a[2:5] = [13, 14, 15]
print(a)
```

得到的结果为：

`[9, 2, 13, 14, 15, 6]`

  需要注意的是，列表截取同样和字符串一样，可以有第三个参数，用来表示步长：

```
letters=['r','u','n','o','o','b']
letters[1:4:2]
```

得到的结果为

`['u','o']`



### 6.Tuple(元组)

Tuple(元组)与列表类似，不同之处在于`元组的元素不能被修改`，且元组写在小括号`()`里，元素之间用逗号隔开。

元组中的元素类型也可以不尽相同：

```
tuple = ( 'abcd', 786 , 2.23, 'runoob', 70.2  )
tinytuple = (123, 'runoob')

print (tuple)             # 输出完整元组
print (tuple[0])          # 输出元组的第一个元素
print (tuple[1:3])        # 输出从第二个元素开始到第三个元素
print (tuple[2:])         # 输出从第三个元素开始的所有元素
print (tinytuple * 2)     # 输出两次元组
print (tuple + tinytuple) # 连接元组
```

运行该实例得到的结果为：

> ```
> ('abcd', 786, 2.23, 'runoob', 70.2)
> abcd
> (786, 2.23)
> (2.23, 'runoob', 70.2)
> (123, 'runoob', 123, 'runoob')
> ('abcd', 786, 2.23, 'runoob', 70.2, 123, 'runoob')
> ```

元组与字符串类似，可以被索引且下标索引从0开始，-1为从末尾开始的位置。也可以进行截取。

其实，可以把字符串看成一种特殊的元组。

``` 
tup=(1,2,3,4,5,6)
print(tup[0])
print(tup[1:5])
```

得到的结果为：

>1
>
>(2,3,4,5)

需要注意的是，虽然Tuple的元素不可变，但它可以包含可变的对象，比如list列表。

构造包含0个或1个元素的元组比较特殊，所以有一些额外的语法规则：

```
tup1=()  #空元组
tup2=(20,)  #一个元素，需要在元素后加逗号
```

String(字符串)、List(列表)和Tuple(元组)都属于sequence(序列)



### 7.Set(集合)

Set(集合)是由一个或数个形态各异的大小整体组成的，构成集合的事物或对象称作元素或是成员。

基本功能是进行成员关系测试和删除重复元素。

可以使用大括号`{ }`或者`set( )`函数创建集合，注意：创建一个空集合必须使用`set( )`而不是`{ }`，因为`{ }`是创建一个空字典。

```
sites = {'Google', 'Taobao', 'Runoob', 'Facebook', 'Zhihu', 'Baidu'}

print(sites)   # 输出集合，重复的元素被自动去掉

# 成员测试
if 'Runoob' in sites :
    print('Runoob 在集合中')
else :
    print('Runoob 不在集合中')


# set可以进行集合运算
a = set('abracadabra')
b = set('alacazam')

print(a)

print(a - b)     # a 和 b 的差集

print(a | b)     # a 和 b 的并集

print(a & b)     # a 和 b 的交集

print(a ^ b)     # a 和 b 中不同时存在的元素
```

该实例运行的结果如下：

> ```
> {'Zhihu', 'Baidu', 'Taobao', 'Runoob', 'Google', 'Facebook'}
> Runoob 在集合中
> {'b', 'c', 'a', 'r', 'd'}
> {'r', 'b', 'd'}
> {'b', 'c', 'a', 'z', 'm', 'r', 'l', 'd'}
> {'c', 'a'}
> {'z', 'b', 'm', 'r', 'l', 'd'}
> ```



### 8.Dictionary(字典)

列表是有序的对象集合，字典是无序的对象集合。两者之间的区别在于：字典当中元素是通过键来存取的，而不是通过偏移存取。

字典是一种映射类型，字典用`{ }`标识，它是一个无序的**键(key)：值(value)**的集合。

键(key)必须使用不可变类型。

在同一个字典中，键(key)必须是唯一的。

```
dict = {}
dict['one'] = "1 - 菜鸟教程"
dict[2]     = "2 - 菜鸟工具"

tinydict = {'name': 'runoob','code':1, 'site': 'www.runoob.com'}


print (dict['one'])       # 输出键为 'one' 的值
print (dict[2])           # 输出键为 2 的值
print (tinydict)          # 输出完整的字典
print (tinydict.keys())   # 输出所有键
print (tinydict.values()) # 输出所有值
```

以上实例输出结果：

> ```
> 1 - 菜鸟教程
> 2 - 菜鸟工具
> {'name': 'runoob', 'code': 1, 'site': 'www.runoob.com'}
> dict_keys(['name', 'code', 'site'])
> dict_values(['runoob', 1, 'www.runoob.com'])
> ```

​	
