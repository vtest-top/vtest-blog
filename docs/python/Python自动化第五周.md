# 1. import导入模块
1. improt导入模块
    1.1 定义
        a. 模块：用来从逻辑上组织python代码（变量、函数、类、逻辑：实现一个功能），本质是.py结尾的python文件（文件名：test.py，对于模块名为test）

2. 导入方法：
    import module_name
    import module_name1, module_name2
    from module_name import *
    from module_name import m1, m2
    from module_name import mm as ms

3. import本质：（路径搜索和搜索路径）
    导入模块的本质是把python文件解释一遍
    import test #  test = 'test.py all code'

4. 导入优化：
    from module_name import test

5. 模块分类：
    a.标准库
    b.开源库
    c.自定义库
# 2. time与datetime
* **time**：
	时间相关的操作，时间有三种表示方式：
	时间戳               1970年1月1日之后的秒，即：time.time()
	格式化的字符串    2014-11-11 11:11，    即：time.strftime('%Y-%m-%d')
	结构化时间          元组包含了：年、日、星期等... time.struct_time    即：time.localtime()
	

```
import time

x = time.time()
print(time.time())     # 时间戳 ，从1970-01-01 00:00:00 到现在的时间，单位为秒

print(time.localtime())     # 当前时间，结构体时间，元组

print(time.timezone)    # 东八区

print(time.sleep(0.1))    # 等待几秒

# 时间戳转化成元组
print(time.gmtime(x))     # 结果为UTC时区
print(time.localtime(x))  # 结果为当前时区的时间

# 元组转成时间戳
print(time.mktime(time.gmtime(x)))

# 获取元组的年月日时分秒
y = time.localtime()
print(y)
print(y.tm_year)

# 2017-11-14 10:15:00
print(time.strftime('%Y-%m-%d %H:%M:%S'))
print(time.strftime('%Y-%m-%d %H:%M:%S', y))    # 将时间戳转成格式时间
print(time.strptime('2017-11-14 10:15:00', '%Y-%m-%d %H:%M:%S'))    # 将格式化字符串时间转成元组

print(time.asctime())   # 元组转成string，如果未传时间则传当前时间
print(time.ctime())     # 传入秒、不传则当前时间，转格式化时间```
```
* **datetime**

```
import datetime

print(datetime.datetime.now())  #  获取当前时间
print(datetime.datetime.now() + datetime.timedelta(3))  # 获取未来N天的时间
print(datetime.datetime.now() + datetime.timedelta(-3)) # 获取过去N天的时间
print(datetime.datetime.now() + datetime.timedelta(hours=3))  # 获取未来N小时的时间
print(datetime.datetime.now() + datetime.timedelta(hours=-3)) # 获取过去N小时的时间
```
![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZy5ibG9nLmNzZG4ubmV0LzIwMTcxMTIyMTUxMTUxNzU4?x-oss-process=image/format,png)
# 3. random模块
	得到随机数
```
import random

print(random.random())  # 不传参，随机0-1的浮点数
print(random.randint(1, 3)) # 随机[1,3]的整数
print(random.randrange(1, 3)) # 随机[1,3)的整数
print(random.choice('hello'))   # 从object随机取值，参数可以为list、str、dict、
print(random.sample('hello', 2))  # 从object随机取2个值，参数可以为list、str、dict、
print(random.uniform(1, 5)) # 随机1-5的浮点数
l = [1, 2, 3, 4, 5, 6, 7]   # 随机打乱顺序
random.shuffle(l)
print(l)
```
	获取随机验证码：
	

```
# 实现一
import random

check_code = 'qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM1234567890'

check_code = random.sample(check_code, 5)
check_code = ''.join(check_code)
print(check_code)

print(chr(random.randrange(65, 122)))
```

```
# 实现二
import random
checkcode = ''
for i in range(4):
    current = random.randrange(0,4)
    if current != i:
        temp = chr(random.randint(65,90))
    else:
        temp = random.randint(0,9)
    checkcode += str(temp)
print checkcode
```

# 4. os模块
用于对于系统级别的操作：

```
os.getcwd() #获取当前工作目录，即当前python脚本工作的目录路径
os.chdir("dirname")  #改变当前脚本工作目录；相当于shell下cd
os.curdir  #返回当前目录: ('.')
os.pardir  #获取当前目录的父目录字符串名：('..')
os.makedirs('dirname1/dirname2')    #可生成多层递归目录
os.removedirs('dirname1')    #若目录为空，则删除，并递归到上一级目录，如若也为空，则删除，依此类推
os.mkdir('dirname')    #生成单级目录；相当于shell中mkdir dirname
os.rmdir('dirname')    #删除单级空目录，若目录不为空则无法删除，报错；相当于shell中rmdir dirname
os.listdir('dirname')    #列出指定目录下的所有文件和子目录，包括隐藏文件，并以列表方式打印
os.remove()  #删除一个文件
os.rename("oldname","newname")  #重命名文件/目录
os.stat('path/filename')  #获取文件/目录信息
os.sep    #输出操作系统特定的路径分隔符，win下为"\\",Linux下为"/"
os.linesep    #输出当前平台使用的行终止符，win下为"\t\n",Linux下为"\n"
os.pathsep    #输出用于分割文件路径的字符串
os.name    #输出字符串指示当前使用平台。win->'nt'; Linux->'posix'
os.system("bash command")  #运行shell命令，直接显示
os.environ  #获取系统环境变量
os.path.abspath(path)  #返回path规范化的绝对路径
os.path.split(path)  #将path分割成目录和文件名二元组返回
os.path.dirname(path)  #返回path的目录。其实就是os.path.split(path)的第一个元素
os.path.basename(path)  #返回path最后的文件名。如何path以／或\结尾，那么就会返回空值。即os.path.split(path)的第二个元素
os.path.exists(path) # 如果path存在，返回True；如果path不存在，返回False
os.path.isabs(path)  #如果path是绝对路径，返回True
os.path.isfile(path)  #如果path是一个存在的文件，返回True。否则返回False
os.path.isdir(path)  #如果path是一个存在的目录，则返回True。否则返回False
os.path.join(path1[, path2[, ...]])  #将多个路径组合后返回，第一个绝对路径之前的参数将被忽略
os.path.getatime(path)  #返回path所指向的文件或者目录的最后存取时间
os.path.getmtime(path)  #返回path所指向的文件或者目录的最后修改时间
```

# 5. sys、shutil和zipfile模块

* **sys模块**
	* 用于提供对解释器相关的操作
```
import sys
print(sys.argv)     # 命令行参数List，第一个元素是程序本身路径
print(sys.version)  # python版本信息
print(sys.path)     # 返回模块的搜索路径
print(sys.platform) # 返回系统平台名称
sys.stdout.write('good lucky')  # 打印、输出
x = sys.stdin.readline()[:-1]   # 输入
print(x)
print(sys.exit())   # 退出程序
```

*  **shutil模块**
	* 主要用于copy文件及信息
	

```
import shutil

shutil.copy('a', 'a_copy')  # 将a文件拷贝成a_copy，包括文件和权限
shutil.copy2('a', 'a_a')    # 将a文件拷贝成a'a_a.txt，包括文件和状态信息，主要用于linux系统
shutil.copyfileobj('a', 'a_copy1')    # 将文件内容拷贝到另一个文件中，可以部分内容
shutil.copymode('a', 'a_a')   # 仅拷贝权限。内容、组、用户均不变
shutil.copystat('a', 'a_a')     # 拷贝状态的信息，包括：mode bits, atime, mtime, flags
shutil.copytree('11', 'a1')   # 递归的去拷贝文件,存在则无法新建
shutil.rmtree('a1')
shutil.ignore_patterns('11', 'a2')    # 递归的去拷贝文件
shutil.move('a', 'a3')       # 递归的去移动文

"""
shutil.make_archive(base_name, format,...)

创建压缩包并返回文件路径，例如：zip、tar

base_name： 压缩包的文件名，也可以是压缩包的路径。只是文件名时，则保存至当前目录，否则保存至指定路径，
如：www                        =>保存至当前路径
如：/Users/wupeiqi/www =>保存至/Users/wupeiqi/
format：	压缩包种类，“zip”, “tar”, “bztar”，“gztar”
root_dir：	要压缩的文件夹路径（默认当前目录）
owner：	用户，默认当前用户
group：	组，默认当前组
logger：	用于记录日志，通常是logging.Logger对象
"""
shutil.make_archive('a_a', 'zip')
shutil.copyfile('a', 'b')   # 复制文件a到b，包括内容和权限
```

* **zipfile和tarfile模块**
	* **zipfile**
	
```
import zipfile

# 压缩
z = zipfile.ZipFile('a_copy.zip', 'w')
z.write('a_a.txt')
z.close()

# 解压
z = zipfile.ZipFile('a_copy.zip', 'r')
z.extractall()
z.close()
```
* **tarfile**

```
import tarfile

# 压缩
tar = tarfile.open('your.tar','w')
tar.add('/Users/wupeiqi/PycharmProjects/bbs2.zip', arcname='bbs2.zip')
tar.add('/Users/wupeiqi/PycharmProjects/cmdb.zip', arcname='cmdb.zip')
tar.close()

# 解压
tar = tarfile.open('your.tar','r')
tar.extractall()  # 可设置解压地址
tar.close()
```

# 6. json、pickle、shelve模块
* **json、pickle**
	用于序列化的两个模块
	json，用于字符串 和 python数据类型间进行转换
	pickle，用于python特有的类型 和 python的数据类型间进行转换
	Json模块提供了四个功能：dumps、dump、loads、load	
	pickle模块提供了四个功能：dumps、dump、loads、load
	[查看这里](img2.png)
***shelve**
	shelve是一个简单的k,v将内存数据通过文件持久化的模块，可以持久化任何pickle可支持的python数据格式
```

import shelve, datetime

d = shelve.open('shelve_test')  # 打开一个文件

info = {'age': 22, 'job': 'it'}
name = ["alex", "rain", "test"]
d["name"] = name  # 持久化列表
d["info"] = info  # 持久化类
d['date'] = datetime.datetime.now()

d.close()
```
	
# 7. xml处理

```
# xml文件
<data>
    <country name="Liechtenstein">
        <rank updated="yes">2</rank>
        <year updated="yes">2010</year>
        <gdppc>141100</gdppc>
        <neighbor direction="E" name="Austria" />
        <neighbor direction="W" name="Switzerland" />
    </country>
    <country name="Singapore">
        <rank updated="yes">5</rank>
        <year updated="yes">2013</year>
        <gdppc>59900</gdppc>
        <neighbor direction="N" name="Malaysia" />
    </country>
    <country name="Panama">
        <rank updated="yes">69</rank>
        <year updated="yes">2013</year>
        <gdppc>13600</gdppc>
        <neighbor direction="W" name="Costa Rica" />
        <neighbor direction="E" name="Colombia" />
    </country>
</data>
```

```
# 获取xml数据
from xml.etree import ElementTree as ET

tree = ET.parse('test12_xml.xml')
root = tree.getroot()
print(root.tag)

# 遍历xml文档
for child in root:
    print(child.tag, child.attrib)
    for i in child:
        print(i.tag, i.text)

# 遍历year节点
for node in root.iter('year'):
    print(node.tag, node.text)

# 修改
for node in root.iter('year'):
    new_year = int(node.text) + 1
    node.text = str(new_year)
    node.set('updated', 'yes')
tree.write('test12_xml.xml')

# 删除
for country in root.findall('country'):
    rank = int(country.find('rank').text)
    if rank > 50:
        root.remove(country)
tree.write('test12_xml_bak.xml')
```
新建xml文件：

```
from xml.etree import ElementTree as ET

new_xml = ET.Element('namelist')
info = ET.SubElement(new_xml, 'info', attrib={'enrolled': 'yes'})
name = ET.SubElement(info, 'name', attrib={'checked': 'yes'})
age = ET.SubElement(info, 'age', attrib={'checked': 'no'})
sex = ET.SubElement(info, 'sex')
name.text = 'test'
age.text = '22'
sex.text = 'man'
info = ET.SubElement(new_xml, 'info', attrib={'enrolled': 'yes'})
name2 = ET.SubElement(info, 'name2', attrib={'checked': 'yes'})
age2 = ET.SubElement(info, 'age2', attrib={'checked': 'no'})
sex2 = ET.SubElement(info, 'sex2')
name2.text = 'test2'
age2.text = '222'
sex2.text = 'man2'

et = ET.ElementTree(new_xml)
et.write('test13_xml.xml', encoding='utf-8', xml_declaration=True)
```
新建xml且内容为：

```
<?xml version='1.0' encoding='utf-8'?>
<namelist>
    <info enrolled="yes">
        <name checked="yes">test</name>
        <age checked="no">22</age>
        <sex>man</sex>
    </info>
    <info enrolled="yes">
        <name2 checked="yes">test2</name2>
        <age2 checked="no">222</age2>
        <sex2>man2</sex2>
    </info>
</namelist>
```

# 8. PyYAML、configparser模块
* configparser模块
	用于生成和修改常见配置文档。
	新建配置文件：
	

```
import configparser

config = configparser.ConfigParser()

config['DEFAULT'] = {
    'TEST1': 45,
    'TEST2': 'T2',
}

config['SERVER'] = {}
config['SERVER']['ip'] = '172.16.10.1'
config['SERVER']['port'] = '8888'

config['mysql'] = {}
new_config = config['mysql']
new_config['host'] = '127.0.0.1'
new_config['port'] = '3306'

with open('test14.ini', 'w', encoding='utf-8') as f:
    config.write(f)
```
	获取配置信息：
	

```
import configparser

conf = configparser.ConfigParser()
conf.read('test14.ini')
print(conf.sections())

print(conf['mysql']['host'])
```

# 9. hashlib模块
# 10. logging模块
# 11. re模块