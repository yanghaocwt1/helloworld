# 1.一些概念

0.计算机不能直接理解任何除机器语言以外的语言，所以必须要把程序员所写的程序语言翻译成机器语言，计算机才能执行程序。将其他语言翻译成机器语言的工具，被称为编译器。编译器翻译的方式有两种：一个是编译，一个是解释。
1.python 是非常高级语言，Python 是一门解释性的语言，Python是可扩展的

2.Python源文件默认以UTF-8编码。

# 2.小用法

1.可以在 #!行之后再增加一个特殊注释行来定义文件的编码
例如： # -*- coding: utf-8 -*-(必须在第一行指定，除非第一行使用了#!/usr/bin/env python3）

2.要做 floor 除法 并且得到一个整数结果(返回商的整数部分) 可以使用 // 运算符;要计算余数可以使用 %：同时获取两者可以使用divmod(x,y

```python
    x = 17
    y = 3
    print(x//y) #结果是5
    print(x%3) #结果是2
    print(divmod(x,y)) #结果是(5, 2)
```

3.通过Python,可以使用`**`做n次方运算:5 ** 2 # 结果是25`

4.同时混合的数型的运算将使结果由整数转换为浮点数︰7.0 / 2 # 结果是3.5`

5.在交互模式下，最后输出的表达式会被赋值给变量

```python
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06
```

6.当遍历一个序列时，使用`enumerate()`函数可以同时得到位置索引和对应的值。

7.同时遍历两个或更多的序列，使用`zip()`函数可以成对读取元素。

##2.1 迭代器：

（1）迭代器的用法在 Python 中普遍而且统一。在后台，for语句调用容器对象的iter()方法。该函数返回一个定义了__next__()方法的迭代器对象，它一次访问容器中的一个元素。没有后续的元素时，__next__()会引发StopIteration 异常，告诉 for循环停止迭代。你可以使用内建的 next() 来调用__next__()，例子如下：

```python
>>> s = 'abc'
>>> it = iter(s)
>>> it
<iterator object at 0x00A1DB50>
>>> next(it)
'a'
>>> next(it)
'b'
>>> next(it)
'c'
>>> next(it)
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
    next(it)
StopIteration
```

（2）看过迭代器协议背后的机制后，将很容易将迭代器的行为添加到你的类中。定义一个__iter__()方法，它返回一个带有__next__()的对象。如果类已经定义__next__()，那么__iter__()可以直接返回self：



```python
def fun20_iter():
	class Reverse:
    	"""Iterator for looping over a sequence backwards."""

    	def __init__(self, data):
        	self.data = data
        	self.index = len(data)

   	 	def __iter__(self):
        	return self

    	def __next__(self):
        	if self.index == 0:
            	raise StopIteration
        	self.index = self.index - 1
        	return self.data[self.index]

	rev = Reverse('spam')
	for c in rev:
    	print(c,end='')
if name == "main":
    fun20_iter()
#输出结果
maps
```
##2.2 生成器

生成器是一种可以简单有效的创建迭代器的工具。它们像常规函数一样撰写，但是在需要返回数据时使用yield语句。每当对它调用next()，生成器从它上次停止的地方重新开始（它会记住所有的数据值和上次执行的语句）。以下示例演示了生成器可以非常简单地创建出来：

```python
def fun21_yeild():
    def reverse(data):
        for index in range(len(data) - 1, -1, -1):
            yield data[index]
    for c in reverse('sabcdefg'):
    print(c,end='')
if name == "main":
    fun21_yeild()
    
```

#3.数据结构

##3.1 字符串

（1）如果你不想让 \ 被解释为特殊字符开头的字符，您可以通过添加 r 使用 原始字符串

```python
>>> print('C:\some\name')  # here \n means newline!
C:\some
ame
>>> print(r'C:\some\name')  # note the r before the quote
C:\some\name
```

（2）字符串可以用+操作符连接，也可以用*操作符重复多次：

（3）相邻的两个或多个字符串字面量（用引号引起来的）会自动连接。
这个功能在你想切分很长的字符串的时候特别有用：

（4）除了索引，还支持切片。索引用于获得单个字符，切片让你获得子字符串（顾左不顾右）：

（5）切片索引具有非常有用的默认值;省略的第一个索引默认为零，省略第二个索引默认为切片字符串的长度。

（6）Python 字符串不能更改。因此，赋值给字符串索引的位置会导致错误

##3.2 列表

Python 有几个 复合数据类型，用来组合其他的值。其中之一是列表
1.各种切片操作会返回一个包含所请求元素的新列表。这意味着下面这个切片操作将会返回一个此列表的（浅）拷贝：

```python
>>> squares + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

###3.2.1 列表方法

引用自：列表操作

list.append(x)
添加一个元素到列表的末尾。相当于 a[len(a):] = [x].

list.extend(L)
将给定列表L中的所有元素附加到原列表a的末尾。相当于 a[len(a):] = L.

list.insert(i, x)
在给定位置插入一个元素。第一个参数为被插入元素的位置索引，因此 a.insert(0, x) 在列表头插入值， a.insert(len(a), x)相当于 a.append(x).

list.remove(x)
删除列表中第一个值为 x 的元素。如果没有这样的项目则会有一个错误。

list.pop([i])
删除列表中给定位置的元素并返回它。如果没有给定位置，a.pop()将会删除并返回列表中的最后一个元素。（i 两边的方括号表示这个参数是可选的，而不是要你输入方括号。你会在 Python 参考库中经常看到这种表示法)。

list.clear()
删除列表中所有的元素。相当于 del a[:].

list.index(x)
返回列表中第一个值为 x 的元素的索引。如果没有这样的元素将会报错。

list.count(x)
返回列表中 x 出现的次数。

list.sort(key=None, reverse=False)
排序列表中的项 (参数可被自定义, 参看 sorted() ).

list.reverse()
列表中的元素按位置反转。

list.copy()
返回列表的一个浅拷贝。相当于 a[:].

###3.2.2 用途

####3.2.2.1 栈

列表方法使得将列表用作堆栈非常容易，使用 append()添加项到栈顶。使用无参的 pop() 从栈顶检出项。

```python
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack.append(7)
>>> stack
[3, 4, 5, 6, 7]
>>> stack.pop()
7
>>> stack
[3, 4, 5, 6]
```

####3.2.2.2 队列

列表也有可能被用来作队列，效率很低。若要实现一个队列， collections.deque 被设计用于快速地从两端操作。例如：

```python
def fun15_queue():
    from collections import deque
    q = deque(['1',2,3,4,5,6])
    q.popleft()
    print(q)
if name == "main":
    fun15_queue()
```

####3.2.2.3 推导式

3.2.2.3.1 普通推导式
列表推导式提供一个生成列表的简洁方法。
例如：squares = [x**2 for x in range(10)]
上面的例子用于生成一个具有10个元素的列表，元素的值分别是是0,1,…9的平方。
列表推导式由一对方括号组成，方括号包含一个表达式，其后跟随一个for子句，然后是零个或多个for或if子句。结果将是一个新的列表，其值来自将表达式在其后的for和if子句的上下文中求值得到的结果。

如果表达式是一个元组（例如，前面示例中的(x, y)），它必须位于圆括号中，否则会报错

3.2.2.3.2 嵌套推导式
列表推导式的第一个表达式可以是任何表达式，包括另外一个列表推导式。

##3.3 元组

有两种序列数据类型，因为 Python 是一个正在不断进化的语言，其他的序列类型也可能被添加进来。还有另一种标准序列数据类型：元组（不可改变）。

一个特殊的问题是构造包含0个或1个元素的元组：为了实现这种情况，语法上有一些奇怪。空的元组通过一对空的圆括号构造；只有一个元素的元组通过一个元素跟随一个逗号构造（仅用圆括号把一个值括起来是不够的）。丑陋，但是有效。

##3.4 集合

集合中的元素不会重复且没有顺序。集合的基本用途包括成员测试和消除重复条目。集合对象也支持数学运算，如并，交，差和对称差。
类似于列表推导式，集合也支持推导式

##3.5 字典

与由数字索引的序列不同，字典是依据键索引的，键可以是任意不可变的类型；字符串和数字始终能作为键。元组可以用作键，如果它们只包含字符串、 数字或元组；如果一个元组直接或间接地包含任何可变对象，它不能用作键。不能使用列表作为键。

##3.6 总结

序列对象可以与具有相同序列类型的其他对象相比较。比较按照 字典序 进行： 首先比较两个序列的首元素，如果不同，就决定了比较的结果；如果相同，就比较后面两个元素，依此类推，直到其中一个序列穷举完。如果要比较的两个元素本身就是同一类型的序列，就按字典序递归比较。如果两个序列的所有元素都相等，就认为序列相等。如果一个序列是另一个序列的初始子序列，较短的序列就小于另一个。字符串的词典序使用Unicode码点数字来排序单个字符。

#4.控制流程

1.我们可以写一个生成斐波那契 初始子序列的程序，如下所示

```python
>>> # Fibonacci series:
... # the sum of two elements defines the next
... a, b = 0, 1
>>> while b < 10:
...     print(b)
...     a, b = b, a+b
...
# 输出结果
1 1 2 3 5 8
```

2.关键字参数 end 可以避免在输出后面的空行，或者可以指定输出后面带有一个不同的字符串：

```python
>>> a, b = 0, 1
>>> while b < 1000:
...     print(b, end=',')
...     a, b = b, a+b
...
1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
```

3.for 语句是种 迭代器。list() 函数是另一个;它从可迭代量创建列表︰
4.循环语句可以有一个 else 子句;当（for）循环迭代完整个列表或（while）循环条件变为假，而非由break语句终止时，就会执行这个else语句。

5.与在if语句中的用法相比，循环中的else子句与try语句的else子句有更多的共同点：try语句的else子句在未出现异常时运行，循环的else子句在未出现break时运行。

##4.1 输入和输出

1.f/F化输出
要使用格式化的字符串文字，请在一个字符串之前（单引号或三引号之前）放一个f或F。在这个字符串中，你可以在{}字符之间放一个Python表达式，它可以引用变量或文字值，（很类似于format格式字符串的变体）。

```python
def fun18_fF():
    year = 2016
    event = 'Referendum'
    print(f'Results of the {year} {event}')

if __name__ == "__main__":
    fun18_fF()
# 输出结果
'Results of the 2016 Referendum'
```

2.如何将值转换为字符串？幸运的是，python已经有方法把任何值转换成字符串：使用repr() 或 str() 方法。

```python
def fun19_str_repr():
    str1 = 'hello\nworld!'
    repr1= 'hello\nworld!'
    print(str(str1))
    print(repr(repr1))

if __name__ == "__main__":
    fun19_str_repr()
# 输出结果
hello
world!
'hello\nworld!'
```

3.!a（运用ascii()）、!s（运用str()）和!r（运用repr()）可以用来在格式化之前转换相应的值：

```python
>>> contents = 'eels'
>>> print('My hovercraft is full of {}.'.format(contents))
My hovercraft is full of eels.
>>> print('My hovercraft is full of {!r}.'.format(contents))
My hovercraft is full of 'eels'.
```

#5.函数

1.执行 一个函数会引入一个用于函数的局部变量的新符号表。更确切地说，函数中的所有的赋值都是将值存储在局部符号表；而变量引用首先查找局部符号表，然后是上层函数的局部符号表，然后是全局符号表，最后是内置名字表。因此，在函数内部无法给一个全局变量直接赋值（除非在一个 global 语句中命名），虽然可以引用它们。

```python
a = 3
def fun07():
    print(a) # 输出3 （可以引用）
    a = 7
    print(a) # 报错 UnboundLocalError: local variable 'a' referenced before assignment
```

2.当函数被调用时候，函数调用的实际参数被引入到被调用函数的局部（本地）符号表中；因此，参数传递通过 传值调用 （这里的 值 始终是对象的 引用，不是对象的值）。

```python
def fun08(a):
    print("fun08",id(a))
if __name__ == "__main__":
    s = 10
    print(__name__,id(s))
    fun08(s)
#输出结果
"__main__ 1508325776"
"fun08 1508325776"
```

从上面的例子可以看出，传递的却是是对象的引用，因为实参和形参的内存地址都是一样的。
3.事实上，没有return语句的函数也返回一个值，尽管是一个很无聊的值。此值被称为 None（它是一个内置的名称）。
4.默认值在函数定义的时刻，在定义的作用域中计算，因此下面的例子会打印 5.：

```python
i = 5
def f(arg=i):
    print(arg)

i = 6
f()
```

6.重要的警告︰默认值只初始化一次。当默认值是一个可变对象（如列表，字典或大多数类的实例）时，默认值会不同。例如，下面的函数在后续调用过程中会累积传给它的参数：

```python
def f(a, L=[]):
    L.append(a)
    return L

print(f(1))
print(f(2))
print(f(3))
```

如果你不想默认值在随后的调用中共享，可以像这样编写函数：

```python
def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L
```

7.如果在最后存在一个name形式的形式参数，它将接收一个字典（参见映射类型-字典），这个字典包含除形式参数之外的所有关键字参数。它可以与*name形式的形式参数组合（在下一节讲述），这种形式接收一个元组，这个元组包含除形式参数之外的所有位置参数。(*name必须出现在**name之前）。

8.最后，最不常用的场景是指明某个函数可以被可变个数的参数调用。这些参数将被封装在一个元组中（参见元组和序列）。在可变数量的参数之前，可能出现零个或多个正常参数。通常，这些可变的参数将位于形式参数列表的最后面，因为它们将剩下的传递给函数的所有输入参数都包含进去。出现在*args之后的任何形式参数都是“非关键字不可”的参数，意味着它们只能用作关键字参数而不能是位置参数。

9.*和**可用于打包 / 解包参数列表

10.可以使用 lambda关键字创建小的匿名函数。

# 6.模块和包

## 6.1 模块

1.在模块内部,模块名 (一个字符串) 可以通过一个全局变量 `__name__`取得：

```python
def fib(n):    # write Fibonacci series up to n
    print("__name__=",__name__)
    
from model.fibo import fib
if __name__ == "__main__":
    fib(1000)
# 输出结果
'__name__= model.fibo'
```

2.每个模块都有自己的私有符号表，它是被定义在模块中所有函数的全局符号表。因此，模块的作者可以在模块里使用全局变量，而不用担心与某个用户的全局变量有冲突。
3.下面例子中这种方式导入除下划线 (_) 开头的所有名称。大多数情况下Python程序员不要使用这个便利的方法，因为它会引入一系列未知的名称到解释器中，这很可能覆盖你已经定义的一些东西。

from fibo import *
4.模块搜索路径
当一个叫spam 的模块被导入，解释器会先在内置模块中搜索该模块。如果没有找到，它会接着到sys.path变量给出的目录中查找名为spam.py的文件。sys.path变量的初始值来自这些位置：

脚本所在的目录（如果没有指明文件，则为当前目录）。
PYTHONPATH（一个包含目录名的列表，与shell变量PATH的语法相同）。
与安装相关的默认值。
5.为了加快加载模块的速度，Python在__pycache__目录下缓存每个模块编译好的版本，名字为module.version.pyc
从.pyc文件读取的程序不会比从.py文件读取的程序运行得更快，.pyc文件唯一快的地方在于它们加载的速度。
6.有一个特别的模块值得注意：sys，它内置在每一个Python解析器中。变量sys.ps1和sys.ps2定义了主提示符和辅助提示符使用的字符串，只有在交互式模式中，这两个变量才有定义。

```python
>>> import sys
>>> sys.ps1
'>>> '
>>> sys.ps2
'... '
>>> sys.ps1 = 'C> '
C> print('Yuck!')
Yuck!
C>
```

7.dir()函数
（1）内置函数 dir 用来找出模块中定义了哪些名字。

```python
import fibo, sys
dir(sys)
# 输出结果(很多，此处省略）
"""['__displayhook__', '__doc__', '__excepthook__', '__loader__', '__name__',
 '__package__', '__stderr__', '__stdin__', '__stdout__',
 '_clear_type_cache', '_current_frames', '_debugmallocstats', '_getframe',
 '_home', '_mercurial', '_xoptions', 'abiflags', 'api_version', 'argv',..."""
```

（2）如果不带参数， dir 列出当前已定义的名称。
（3）dir 不会列出内置的函数和变量的名称。如果你想列出这些内容，它们定义在标准模块builtins中：

```python
import builtins
dir(builtins) 
```

##6.2 包

（1）目录内的__init__.py文件是必需的，这样才能使Python将目录当作包；
（2）最简单的情况，__init__.py 可以只是一个空的文件，但它也可以为包执行初始化代码或设置__all__ 变量
（3）如果包中的__init__.py代码定义了一个名为__all__的列表，那么在遇到 from package import *语句的时候，应该把这个列表中的所有模块名字导入。
__all__ = ["echo", "surround", "reverse"]

##6.3 标准库概览

1.多线程
线程是一种解耦非顺序依赖任务的技术。当其他任务在后台运行时，线程可以用来提高应用程序接受用户输入操作的响应能力。一个相关的使用场景是 I/O 操作与另一个线程中的计算并行执行。

下面的代码演示了当主程序在运行的同时，高层的 threading 模块可以在后台执行任务。

```python
import threading, zipfile

class AsyncZip(threading.Thread):
    def __init__(self, infile, outfile):
        threading.Thread.__init__(self)
        self.infile = infile
        self.outfile = outfile

    def run(self):
        f = zipfile.ZipFile(self.outfile, 'w', zipfile.ZIP_DEFLATED)
        f.write(self.infile)
        f.close()
        print('Finished background zip of:', self.infile)

background = AsyncZip('mydata.txt', 'myarchive.zip')
background.start()
print('The main program continues to run in foreground.')

background.join()    # Wait for the background task to finish
print('Main program waited until background was done.')
```

多线程应用程序的最主要挑战是协调线程间共享的数据或其他资源。为此目的，该线程模块提供了许多同步原语包括锁、 事件、 条件变量和信号量。

尽管这些工具很强大，很小的设计错误也可能导致很难复现的问题。因此，任务协调的首选方法是将所有对某个资源的访问集中在单个线程中，然后使用queue模块向该线程提供来自其他线程的请求。使用队列对象进行线程间通信和协调的应用程序更易于设计，更易于阅读和更可靠。
2.弱引用
Python执行自动内存管理（大多数对象采用引用计数和垃圾回收以消除循环）。在最后一个引用消失后，内存会立即释放。

这个方式对大多数应用程序工作良好，但是有时候会需要跟踪对象，只要它们还被其它地方所使用。不幸的是，只是跟踪它们会创建一个引用，这个引用会一直存在。weakref模块提供了用于跟踪对象的工具，而无需创建引用。当不再需要该对象时，它会自动从 weakref 表中删除并且会为 weakref 对象触发一个回调。典型的应用包括缓存创建的时候需要很大开销的对象

#7.文件

1.mode为’r’表示文件只读；w表示文件只进行写入（已存在的同名文件将被删掉）；'a’表示打开文件进行追加；写入到文件中的任何数据将自动添加到末尾。在mode后面附加’b’将以二进制模式打开文件：现在数据以字节对象的形式读取和写入。这个模式应该用于所有不包含文本的文件。
2.在文本模式中，读取的默认行为是将平台相关的换行（Unix上的\n、Windows上的\r\n）仅仅转换为\n。当在文本模式中写入时，默认的行为是将\n转换为平台相关的换行。这种对文件数据的修改对文本文件没有问题，但会损坏JPEG或EXE这样的二进制文件中的数据。使用二进制模式读写此类文件时要特别小心。
3.f.tell()返回一个整数，代表文件对象在文件中的当前的位置，在二进制模式中该数值表示自文件开头到指针处的字节数，在文本模式中则是不准确的。
4.若要更改该文件对象的位置，可以使用f.seek(offset, from_what)。位置由参考点加上offset 计算得来；参考点的选择则来自于from_what参数。当from_what的值为0，1，2 时，分别使用文件开头、当前文件位置和文件结尾作为参考点。from_what 可以省略，默认值为 0，表示以文件的开始作为参考点。
5.处理文件对象时使用with关键字是很好的做法。这样做的好处在于文件用完后会自动关闭，即使过程中发生异常也没关系。它还比编写一个等同的try-finally语句要短很多：

```python
>>> with open('workfile', 'r') as f:
...     read_data = f.read()
>>> f.closed
True
```

6.标准模块json可以接受 Python 数据结构，并将它们转换为字符串表示形式；此过程称为序列化。从字符串表示形式重新构建数据结构称为反序列化。在序列化和反序列化之间，表示对象的字符串可能已经存储在文件或数据中，或者通过网络连接发送到一些远程机器。

#8.异常

##8.1处理异常

1.try 语句按以下方式工作。

首先，执行 try 子句 （ try 和 except 关键字之间的语句）。
如果未发生任何异常，忽略 except 子句 且 try 语句执行完毕。
如果在 try 子句执行过程中发生异常，跳过该子句的其余部分。如果异常的类型与 except 关键字后面的异常名匹配, 则执行 except 子句，然后继续执行 try 语句之后的代码。
如果异常的类型与 except 关键字后面的异常名不匹配，它将被传递给上层的 try 语句；如果没有找到处理这个异常的代码，它就成为一个 未处理异常 ，程

序会终止运行并显示一条如上所示的信息。

```python
def fun20_exception():
    try:
        f = open('myfile.txt')
        s = f.readline()
        i = int(s.strip())
    except OSError as err:
        print("OS error: {0}".format(err))
    except ValueError:
        print("Could not convert data to an integer.")
    except:
        print("Unexpected error:", sys.exc_info()[0])
        raise

if __name__ == "__main__":
    fun20_exception()
# 输出结果
（1）没有myfile.txt时：OS error: [Errno 2] No such file or directory: 'myfile.txt'
（2）myfile.txt存储的文件内容是ss: Could not convert data to an integer.

```

2,try …except 语句有一个可选的 else 子句 ，其出现时，必须放在所有 except 子句的后面。如果需要在 try 语句没有抛出异常时执行一些代码，可以使用else这个子句。
3.except 子句可以在异常名之后指定一个变量。这个变量将绑定于一个异常实例，同时异常的参数将存放在 instance.args 中。为方便起见，异常实例定义了 __str__()，因此异常的参数可以直接打印而不必引用 .args 。也可以在引发异常之前先实例化一个异常，然后向它添加任何想要的属性。

```python
def fun21_exception_args():
    try:
        raise Exception('excp',456)
    except Exception as e:
        print(type(e))
        print(e.args)
        print(e)
        x,y = e.args
        print(x,y)

if __name__ == "__main__":
    fun21_exception_args()
# 输出结果
<class 'Exception'>
('excp', 456)
('excp', 456)
excp 456
```

4.不管有没有发生异常，在离开 try 语句之前总是会执行 finally 子句（此finally在所有情况下执行清理操作）当 try 子句中发生了一个异常，并且没有 except 字句处理（或者异常发生在 except 或 else 子句中），在执行完 finally 子句后将重新引发这个异常。try 语句由于 break 、contine 或return 语句离开时，同样会执行finally 子句。下面是一个更复杂些的例子：

```python
>>> def divide(x, y):
...     try:
...         result = x / y
...     except ZeroDivisionError:
...         print("division by zero!")
...     else:
...         print("result is", result)
...     finally:
...         print("executing finally clause")
...
>>> divide(2, 1)
result is 2.0
executing finally clause
>>> divide(2, 0)
division by zero!
executing finally clause
>>> divide("2", "1")
executing finally clause
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "<stdin>", line 3, in divide
TypeError: unsupported operand type(s) for /: 'str' and 'str'
```

在真实的应用程序中， finally 子句用于释放外部资源（例如文件或网络连接），不管资源的使用是否成功。

##8.2 自定义异常

1.程序可以通过创建新的异常类来命名自己的异常。异常通常应该继承 Exception 类，直接继承或者间接继承都可以。
2.大多数异常的名字都以"Error"结尾，类似于标准异常的命名。

#9.类

##9.1 Python 作用域和命名空间

global 语句可以用来指明某个特定的变量位于全局作用域并且应该在那里重新绑定； nonlocal 语句表示否定当前命名空间的作用域，寻找父函数的作用域并绑定对象。

##9.2 对象

1.能被实例对象理解的唯一操作是属性引用。有两种有效的属性名：数据属性和方法。
数据属性不需要声明；和局部变量一样，它们会在第一次给它们赋值时生成

2.可变对象（例如列表和字典）的共享数据可能带来意外的效果。

3.数据属性会覆盖同名的方法属性；
4.每个值都是一个对象，因此每个值都有一个类（也称它的类型）。它存储为 object.__class__。

##9.3 继承

1.当构建类对象时，将记住基类。这用于解析属性的引用：如果在类中找不到请求的属性，搜索会在基类中继续。如果基类本身是由别的类派生而来，这个规则会递归应用。
2.Python 有两个用于继承的函数：

使用isinstance()来检查实例类型： isinstance(obj, int) 只有 obj.__class__是 int 或者是从 int 派生的类时才为 True 。
使用issubclass()来检查类的继承： issubclass(bool, int) 是 True 因为 bool 是 int.的子类。然而， issubclass(float, int) 为 False ，因为 float 不是 int 的子类。
3.except 子句中的类如果与异常是同一个类或者是其基类，那么它们就是相容的（但是反过来是不行的——except子句列出的子类与基类是不相容的）。
