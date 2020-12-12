
## Python应用：
- *应用领域领域：*
	1. 云计算：如OpenStack
	2. WEB开发：如Django、Flask框架等
	3. 科学运算、人工智能：典型库有Numpy、Scipy等
	4. 系统运维：运维人员
	5. 金融：量化交易
	6. 图形GUI：PYQT、WxPython、TkInter
- *应用公司：*
	1. 谷歌：Google App Engine 、code.google.com 、Google earth 、谷歌爬虫、Google广告等项目都在大量使用Python开发
	2. CIA: 美国中情局网站就是用Python开发的
	3. 等等，好多好多！！！
	
## 编译型vs解释型

**编译型**
优点：编译器一般会有预编译的过程对代码进行优化。因为编译只做一次，运行时不需要编译，所以编译型语言的程序执行效率高。可以脱离语言环境独立运行。
缺点：编译之后如果需要修改就需要整个模块重新编译。编译的时候根据对应的运行环境生成机器码，不同的操作系统之间移植就会有问题，需要根据运行的操作系统环境编译不同的可执行文件。

**解释型**
优点：有良好的平台兼容性，在任何环境中都可以运行，前提是安装了解释器（虚拟机）。灵活，修改代码的时候直接修改就可以，可以快速部署，不用停机维护。

缺点：每次运行的时候都要解释一遍，性能上不如编译型语言。

##Python的优缺点
先看优点

Python的定位是“优雅”、“明确”、“简单”，所以Python程序看上去总是简单易懂，初学者学Python，不但入门容易，而且将来深入下去，可以编写那些非常非常复杂的程序。
开发效率非常高，Python有非常强大的第三方库，基本上你想通过计算机实现任何功能，Python官方库里都有相应的模块进行支持，直接下载调用后，在基础库的基础上再进行开发，大大降低开发周期，避免重复造轮子。
高级语言————当你用Python语言编写程序的时候，你无需考虑诸如如何管理你的程序使用的内存一类的底层细节
可移植性————由于它的开源本质，Python已经被移植在许多平台上（经过改动使它能够工 作在不同平台上）。如果你小心地避免使用依赖于系统的特性，那么你的所有Python程序无需修改就几乎可以在市场上所有的系统平台上运行
可扩展性————如果你需要你的一段关键代码运行得更快或者希望某些算法不公开，你可以把你的部分程序用C或C++编写，然后在你的Python程序中使用它们。
可嵌入性————你可以把Python嵌入你的C/C++程序，从而向你的程序用户提供脚本功能。
再看缺点：

速度慢，Python 的运行速度相比C语言确实慢很多，跟JAVA相比也要慢一些，因此这也是很多所谓的大牛不屑于使用Python的主要原因，但其实这里所指的运行速度慢在大多数情况下用户是无法直接感知到的，必须借助测试工具才能体现出来，比如你用C运一个程序花了0.01s,用Python是0.1s,这样C语言直接比Python快了10倍,算是非常夸张了，但是你是无法直接通过肉眼感知的，因为一个正常人所能感知的时间最小单位是0.15-0.4s左右，哈哈。其实在大多数情况下Python已经完全可以满足你对程序速度的要求，除非你要写对速度要求极高的搜索引擎等，这种情况下，当然还是建议你用C去实现的。
代码不能加密，因为PYTHON是解释性语言，它的源码都是以名文形式存放的，不过我不认为这算是一个缺点，如果你的项目要求源代码必须是加密的，那你一开始就不应该用Python来去实现。
线程不能利用多CPU问题，这是Python被人诟病最多的一个缺点，GIL即全局解释器锁（Global Interpreter Lock），是计算机程序设计语言解释器用于同步线程的工具，使得任何时刻仅有一个线程在执行，Python的线程是操作系统的原生线程。在Linux上为pthread，在Windows上为Win thread，完全由操作系统调度线程的执行。一个python解释器进程内有一条主线程，以及多条用户程序的执行线程。即使在多核CPU平台上，由于GIL的存在，所以禁止多线程的并行执行。关于这个问题的折衷解决方法，我们在以后线程和进程章节里再进行详细探讨。
 

当然，Python还有一些其它的小缺点，在这就不一一列举了，我想说的是，任何一门语言都不是完美的，都有擅长和不擅长做的事情，建议各位不要拿一个语言的劣势去跟另一个语言的优势来去比较，语言只是一个工具，是实现程序设计师思想的工具，就像我们之前中学学几何时，有的时候需要要圆规，有的时候需要用三角尺一样，拿相应的工具去做它最擅长的事才是正确的选择。之前很多人问我Shell和Python到底哪个好？我回答说Shell是个脚本语言，但Python不只是个脚本语言，能做的事情更多，然后又有钻牛角尖的人说完全没必要学Python, Python能做的事情Shell都可以做，只要你足够牛B,然后又举了用Shell可以写俄罗斯方块这样的游戏，对此我能说表达只能是，不要跟SB理论，SB会把你拉到跟他一样的高度，然后用充分的经验把你打倒。

## Python 2.x和3.x
1. python 2.x将维护到2020
2. python 3.x更加语言化

## 第一个程序
新建hello.py文件（python文件后缀为.py）：
```
# python 3.6.x
print("Hello World!")

# python 2.7.x
print "Hello World!"
```
运行：
1. 使用工具运行，如：pycharm
2. 使用指令运行：进入到文件目录，执行ptyhon hello.py

## 变量
定义规则：
1. 只能是字母，数字或下划线任意组合
2. 第一个字符不能为数字
3. 关键字不能为变量名

> 关键字有：and, as, assert, break, class, continue, def, del, elif, else, except, for, from, global, if, import, in, is, lambda, not, or, pass, print,  exec, finally, raise, return, try, while, with, yield 

```
var = "pofoo"
var1 = "test"
var_2 = 'a'
_var = 'b'

# 错误如下
2var = 'rq'
```
## 字符编码

Unicode（统一码、万国码、单一码）是一种在计算机上使用的字符编码。Unicode 是为了解决传统的字符编码方案的局限而产生的，它为每种语言中的每个字符设定了统一并且唯一的二进制编码，规定虽有的字符和符号最少由 16 位来表示（2个字节），即：2 **16 = 65536，
注：此处说的的是最少2个字节，可能更多

UTF-8，是对Unicode编码的压缩和优化，他不再使用最少使用2个字节，而是将所有的字符和符号进行分类：ascii码中的内容用1个字节保存、欧洲的字符用2个字节保存，东亚的字符用3个字节保存...

所以，python解释器在加载 .py 文件中的代码时，会对内容进行编码（默认ascill），如果是如下代码的话：
一个中文占用3bytes

```
# -*- coding:utf-8 -*-
# python 2.7 
print "中文"
# 如果不加一个行，运行报错，由于ASCII码无法表示中文

# python 3.x
print("中文")
# 运行正常
```

## 用户输入
1. 猜数字：
```
count = 0
age_of_wendy = 3

while count < 3:
    guess_age = input('Guess age:')

    if int(guess_age) == age_of_wendy:
        print('Yes, You got it.')
        break
    elif int(guess_age) > age_of_wendy:
        print('No, You are bigger.')
    else:
        print('No, you are litter.')
    count += 1
    print(count)
    if count == 3:
        continue_cofrim = input('还要继续猜吗？')
        if continue_cofrim != 'n':
            count = 0
# else:
#     print('Game Over')

```
2. 密码不显示（pycharm无法运行）：

```
import getpass

username = input('username:')
# password = input('password:')
password2 = getpass.getpass('password:')

print(username, password)
```