1. 集合
	作用：
		a. 去重
		b. 关系测试，交集、差集、并集、对此差集等
```
list_1 = set([1, 2, 3, 4, 5, 6])
list_2 = set([4, 6, 7, 8, 9, 10])

# 交集
print(list_1.intersection(list_2))
print(list_1 & list_2)

# 并集
print(list_1.union(list_2))
print(list_1 | list_2)

# 差集
print(list_1.difference(list_2))
print(list_1 - list_2)

# 反向差集
print(list_1.symmetric_difference(list_2))
print(list_1 ^ list_2)

# 子集、父集
list_3 = set([2, 3, 4])
print(list_3.issubset(list_1))
print(list_1.issuperset(list_3))

print(list_1.pop())     # 随机删除
# print(list_1.clear())   # 删除集合
print(list_1.remove(2))    # 删除，如果不存在则报错，建议用discard方法
print(list_1.discard(3))    # 删除几个成员，输入成员存在则删除，无则不删除，不报错
print(list_1.copy())    # 拷贝
print(list_1.difference_update(list_2))     # set in list_1 , not in list_2
print(list_2.intersection_update(list_3))   # set in list_2 and in list_3
print(list_3.add(1222))     # 增加单个元素
print(list_3.symmetric_difference_update([1, 11]))      # 增加多个元素
print(list_3.isdisjoint(list_1))    # 判断2个集合是否有交集，无返回true，有则返回false
print(list_3)
# 循环
for i in list_3:
    print(i)
```
2. 元组
	只读列表，只有count, index 2 个方法
	作用：如果一些数据不想被人修改， 可以存成元组，比如身份证列表
```
tuple1 = (1, 2, 3)
print(tuple1.index(1))
print(tuple1.count(2))
```

输出

```
0 
1
```

3. 字典：key:value
	特性：
	1. 无顺序
	2. 去重
	3. 查询速度快，比列表快
	4. 比列表占用内存大
```
person = {
    'name': 'joy',
    'age': 18,
    'job': 'tester',
    'salary': 100000
}
print('字典的方法'.center(30, '-'))
person['en_name'] =  'QA'   # 如果键有值则更新键的值，没有值则新建键和值
person['name'] = 'Kate'
print(person)

person_cp = person.copy()  # 复制dict
print(person.clear())   # 删除字典，返回None
person_cp.pop('name')   # 删除键的值,需要输入键
print(person_cp)
person_cp.popitem()   # 随机删除键的值,无传参
print(person_cp)
print(person_cp.keys())     # 获取dict的键
print(person_cp.get('age'))     # 获取某个键的值，如果无则返回None
print(person_cp['age'])     # 获取某个键的值，如果无则报错，故一般用dict.get()方法
print(person_cp.values())   # 返回字典的值
print(dict.fromkeys('a', 1))    # 返回新的字典的键和值
print(dict.fromkeys(['a', 'b', 111], 1))    # 返回新的字典的键和值
c = dict.fromkeys(['a', 'b', 111], [1, {'name': 'joy'}, 888])   # 返回新的字典的键和值
print(c)
c['a'][1]['name'] = 'wendy'     # 与浅copy一致
print(c)
print(person_cp.items())  # 返回字典dict的(key，value)元组对的列表
print(person_cp)
new_person = {
    'age': 88,
    'company': 'Mopon',
    1: 'test',
    4: 12
}
person_cp.update(new_person)    # 2个合并，如果键相同，则更新到字典person_cp中，如果键不同则新建
print(person_cp)
person_cp.setdefault('height', 172)     # 在dict中查找键，未找到则新建，找到了键值不变
person_cp.setdefault('age', 72)
print(person_cp)

print('循环'.center(30, '-'))
# 循环
for i in person_cp:         # 效率更高，速度快
    print(i, person_cp[i])

for k, v in person_cp.items():  # 占用内存，速度慢
    print(k, v)
```
	
4. 文件操作

```
# 文件修改
f_old = open('yes', 'r+', encoding='utf-8')
f_new = open('yes.bak', 'w', encoding='utf-8')

for line in f_old:
    if '我2在踢足球.' in line:
        line = line.replace('我2在踢足球.', '我2在踢足球.1231231231')
    f_new.write(line)

f_new.close()
f_old.close()

# 文件操作
f = open('yes', 'r+', encoding='utf-8')     # 读写权限，先读后写
# for i in f.readlines():
#     print(i)
# print(f.read()) # 读取整个文件
# print(f.readline()) # 一行一行读
# print(f.readlines())    # 读取全部,为list
f.close()

f_write = open('yes_1', 'w+', encoding='utf-8')     # 写读权限。先写后读,新建文件再写
print(f_write.write('11111111111111111123123123'))
```

```
# 进度条
import sys
from time import sleep

for i in range(100):
    sys.stdout.write('#')
    sys.stdout.flush()
    sleep(0.5)
```



5. 字符编码
	1. python2
		1. 默认ASCII
		2. 如果有声明#-*-coding:utf-8-*-，则py文件就支持utf-8编码，也支持中文
	2. python3
		1. 默认为utf-8，支持Unicode
		2. gbk <-> Unicode <-> utf-8
6. 函数（def）
	定义：函数是指将一组语句的集合通过一个名字(函数名)封装起来，要想执行这个函数，只需调用其函数名即可
	特性：
		1. 减少重复代码
		2. 使程序可以扩展
		3. 使程序变动易维护
```
def hello():	#函数名
	print('hello world!')
hello()	# 调用函数hello()


def test(x, y):
    print(x)
    print(y)

x = 1
y = 2
# 关键参数不能写在位置参数前面的
test(x, y)  # 位置调用，与形参一一对应
test(y=y, x=x)  # 关键字调用，与形参顺序无关
# test(x=3, 3)    # 执行报错
# test(3, x=2)    # 执行报错，x传了多个值
test(x=3, 2)    # z正常，第一个是x值，第二个为y位置的值

# 默认参数特点：调用函数的时候，默认参数非必须传递
# 用途：1. 默认安装， 2 连接数据库port 等，主要用于默认参数
def test1(x, y=2):
    print(x)
    print(y)

test1(1)
test1(1, 3)

# 参数组，参数组一定放在最后
# 传元组,接收N个位置参数，转换成元组
def test2(*args):
    print(args)
    print(args[1])

test2(1, 3, 4)
test2(*[1, 2, 3])

def test3(x, *args):
    print(x)
    print(args)

test3(1, 2, 3, 6)

# 传字典
# 把N个关键字参数，转换成字典的方式
def test4(**kwargs):
    print(kwargs)
    print(kwargs['name'])
test4(name='pofoo', age=11)
test4(**{'name': 'pofour', 'age': 11})

def test5(name, **kwargs):
    print(name)
    print(kwargs)

test5('pofour', username='pofourr', age=111)
# test5('pofour', name='pofourr', age=111)  # 报错，有2个name，

def test6(name, age=18, **kwargs):
    print(name, age, kwargs)

test6('pofour', user='pofoo', sex='m')
test6('pofour', user='pofoo', age=13)   # age关键字调用
test6('pofour', user='pofoo', age=13, sex='m')   # age关键字调用

def test7(name, age=18, *args, **kwargs):
    print(name)
    print(age)
    print(args)
    print(kwargs)

test7('test', sex='m', work='it')
```


7. 全局变量和局部变量
	在子程序中定义的变量称为局部变量，在程序的一开始定义的变量称为全局变量。
	全局变量作用域是整个程序，局部变量作用域是定义该变量的子程序。
	当全局变量与局部变量同名时：
	在定义局部变量的子程序内，局部变量起作用；在其它地方全局变量起作用
```
goods_name = 'iphone x' 

def change_goods(name):
    print('befor goods name is ', name)
    name = 'mac pro'
    print('after name is ', name)

change_goods(goods_name)
print(goods_name)
```

输出：

```
befor goods name is  iphone x
after name is  mac pro
iphone x
```

8. 返回值return
要想获取函数的执行结果，就可以用return语句把结果返回
注意:
    函数在执行过程中只要遇到return语句，就会停止执行并返回结果，so 也可以理解为 return 语句代表着函数的结束
    如果未在函数中指定return,那这个函数的返回值为None 
```
def add(x, y):
    return x + y    # 返回 x + y
a = add(3, 6)   # add函数返回值x+y赋给a
print(a)
```

 输出：

```
9
```

9. 递归
	定义：在函数内部，可以调用其他函数。如果一个函数在内部调用自身本身，这个函数就是递归函数。
	特性：
	1. 必须有一个明确的结束条件
	2. 每次进入更深一层递归时，问题规模相比上次递归都应有所减少
	3. 递归效率不高，递归层次过多会导致栈溢出（在计算机中，函数调用是通过栈（stack）这种数据结构实现的，每当进入一个函数调用，栈就会加一层栈帧，每当函数返回，栈就会减一层栈帧。由于栈的大小不是无限的，所以，递归调用的次数过多，会导致栈溢出）
```
def calc(x):
    print(x)
    if int(x/2) == 0:
        return x
    return calc(int(x/2))
calc(10)
```

输出：

```
10
5
2
1
```

10. 高阶函数：
	定义：变量可以指向函数，函数的参数能接收变量，那么一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。
```
def add(x,y,f):
    return f(x) + f(y)
res = add(8,-6,abs)
print(res)
```

输出：

```
14
```
11. 作业：工资管理系统

```

def select_info(username):	# 查询用户信息
    with open('info.txt', 'r+', encoding='utf-8') as f:
        for line in f:
            get_user = line.split(' ')[0]
            get_salary = line.split(' ')[1].strip()
            if get_user == username:
                print('{user}的工资是：{salary}'.format(user=username, salary=get_salary))

def alter_info(alter_data):		# 修改用户信息
    with open('info.txt', 'r+', encoding='utf-8') as f, \
            open('info_bak.txt', 'w+', encoding='utf-8') as f_bak:
        alter_name = alter_data.split(' ')[0]
        # alter_salary = alter_data.split(' ')[-1]
        for line in f:
            if alter_name in line:
                line = line.replace(line, alter_data)
                line = line + '\n'
            f_bak.write(line)
    replace_file()
    print('修改成功！')

def add_info(add_data):		# 增加用户信息
    with open('info.txt', 'r+', encoding='utf-8') as f, \
            open('info_bak.txt', 'w+', encoding='utf-8') as f_bak:
        for line in f:
            f_bak.write(line)
        f_bak.write('\n' + add_data)
    replace_file()
    print('增加成功！')

def replace_file():		# 将新保存的数据的文件数据复制到旧文件中
    with open('info.txt', 'w+', encoding='utf-8') as f, \
            open('info_bak.txt', 'r+', encoding='utf-8') as f_bak:
        for line in f_bak:
            f.write(line)

print('欢迎来到工资管理系统'.center(50, '-'))
print('1. 查询员工工资')
print('2. 修改员工工资')
print('3. 增加新员工记录')
print('4. 退出')

while True:
    input_data = input('>>:')
    if input_data.isdigit():
        input_data = int(input_data)
        if input_data == 1:
            username = input('请输入要查询的员工姓名：')
            select_info(username)
        elif input_data == 2:
            alter_data = input('请输入要修改的员工姓名和工资，用空格分隔：')
            alter_info(alter_data)
        elif input_data == 3:
            add_data = input('请输入要增加的员工的姓名和工资，用空格分隔：')
            add_info(add_data)
        elif input_data == 4:
            print('再见！')
            exit()

```
