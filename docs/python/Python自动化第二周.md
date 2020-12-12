1. 数据模块
----

      a. sys
          i. sys.path
          ii. sys.argv
      b. os
          i. os.system('cmd')
          ii. os.popen('cmd')
          iii. os.mkdir('new_dir')
      c. 导入自己的模块
       
  


> os和sys的应用
> `
> import sys
print('1 ', sys.path)	# 输出查找模块路径
print('2 ', type(sys.path))	# 输出类型
print('3', sys.argv)	# 输出改文件的相对路径
print('4', type(sys.argv))	# 输入类型
`



  2. pyc是什么：
pyc是执行python文件时生成的，python语音需要先编译后解释，pyc主要起到编译的作用。
执行程序步骤：1. 首先在.py文件同目录下查找是否与改文件同名且后缀为.pyc的文件
2. 如无则重新编译并生成.pyc文件，如有则检查.pyc与.py文件的最后修改时间是一致
3. 如果一致则直接解释，不再编译；如果不一致则重新编译并修改.pyc文件
  3. 数据类型：
int：整型，整数；python 2.x版本有long； python 3.x没有long，都为int
float：浮点型，带有小数点的数字
复数：复数包括实数和虚数，一般为x+yj（x为实数部分，yj为虚数部分，虚数数学里面用i表示，python里面用j来表示（j来自工程学里的说话））
布尔值：
真和假
1或0
字符串： 没创建一个字符串时需要在内存中开辟一块连续的空间，并且一旦需要修改字符串的话需要再次开辟一块空间。
  4. betys数据类型
 

```
# str.decode() 编码：用来将数据转换成二进制，
# str.encode() 解码：用来将二进制转换成utf-8

str_decode = '百度一下'
print(str_decode.encode('utf-8'))  # str.encode() 默认为UTF-8，可以不加UTF-8，但是建议加上

str_encode = b'\xe7\x99\xbe\xe5\xba\xa6\xe4\xb8\x80\xe4\xb8\x8b'
print(str_encode.decode('utf-8'))   # str.decode() 默认与运行系统一直，如果不是uft-8的系统则会保存，故建议加上utf-8
```

  5.list列表的方法
  

```
names_str = '晨龙 成龙 程龙 辰龙 陈龙'
print('1  ', names_str.split(' ')[0])

names_list = ['晨龙', '成龙', '程龙', '辰龙', '陈龙', '陈龙', '陈龙']
# list查询
print('2  ', names_list[0])
print('3  ', names_list[2])
print('4  ', names_list[-1])
print('5  ', names_list[1:3])    # 切片：[1:3] 顾前不顾后
print('6  ', names_list[-2:])    #
print('7  ', names_list[-2:0])   # 错误
print('8  ', names_list[:3])

# list插入
names_list.append('诚隆')     # list.append加在后面
print('9  ', names_list)
names_list.insert(1, '陈隆')  # list.insert插入到list某个位置   注：不能批量插入
print('10 ', names_list)

# list修改
names_list[2] = '小强'    # 将某个位置替换
print('11 ', names_list)

# list删除
names_list.remove('小强')
print('12 ', names_list)  # 删除某个元素
del names_list[1]   # 删除某个位置的元素
print('13 ', names_list)
print('14 ', names_list.pop())  # 删除最后一个元素或输入位置删除某个位置元素

# list查询某个元素位置
print('15 ', names_list.index('晨龙'))    # 获取元素的位置
print('16 ', names_list[names_list.index('陈龙')])
print('17 ', names_list.count('陈龙'))    # 获取元素出现次数
# names_list.clear()  # 清空list
# print('18 ', names_list)
names_list.reverse()    # 反转list
print('19 ', names_list)

names_list = ['A晨龙', 'a陈隆', '#!成龙', 'B程龙', 'd辰龙', 'q陈龙', '陈龙', '2陈龙', '3诚隆']
names_list.reverse()     # 反转list
names_list.sort()   # list排序，安装ASCII码顺序排序
print('20 ', names_list)

names_2 = ['A', 2, 3, 4]
names_2.extend(names_list)
print('21 ', names_2)
```
6.str字符串的方法

```
str = '  my test one Tw o'
print(str.count('o'))   # 某个字符在str里出现次数
print(str.capitalize())     # 首字母为大写
print(str.center(20, '#'))  # 补全
print(str.endswith(' '))    # 以某字符串结尾
print(str.startswith('m'))  # 以某字符串开头
print(str.encode())     # 编码，转成二进制
print('my \t test one Two '.expandtabs(tabsize=10))     # \t之前占有tabsize个字符
print(str.replace('o', 'AA', 1))    # 将字符串的o替换成AA，count=1代表替换个数，不填则全部
print(str.rfind('t'))   # 找右边第一个字符所在位置
print(str.find('t'))    # 找左边第一个字符所在位置
print(str.rindex('o'))  # 查到最右边字符在字符串的位置
print(str.index('o'))   # 查到最左边字符在字符串的位置
print(str.rjust(20, '+'))   # 字符串占20个字符，不够补+号，默认为空格
print(str.ljust(20, '-'))   # 字符串占20个字符，不够补+号，默认为空格
print(str.rpartition('o'))  # 右边第一个符合字符串的分段成元组
print(str.partition('o'))   # 左边第一个符合字符串的分段成元组
print(str.rsplit('t', 1))   # 从右边开始切片，变成list
print(str.rsplit('t'))      # 从右边开始切片，变成list
print(str.split('m'))       # 从左边开始切片，变成list
print('omy test one Tw o'.rstrip('o'))      # 删除最右边第一个同等的字符串
print('omy test one Tw o'.strip('o'))       # 删除首尾第一个同等的字符串
print('omy,test one Tw o'.title())  # 字符串的首字母大写
str1 = str.maketrans('abcdt', '12245')
print(str.translate(str1))  # 将制定字符串替换
print(str.upper())  # 全部大写
print(str.lower())  # 全部小写
print(str.isupper())    # 首字符大写，返回bool
print(str.islower())    # 首字符小写，返回bool
print(str.isdigit())    # 纯数字
print('omy,test one T\nw o'.splitlines())   # 根据行转成list
print('omy,test one Tw o what'.strip('at'))   # 删除结尾符合条件的字符串
print(str.swapcase())   # x小写变大写，大写变小写
print('omy,test one Tw o what'.join(['1', 'A', 'b', 'c']))   # 用于将序列中的元素以指定的字符连接生成一个新的字符串
print(str.zfill(20))  # 回指定长度的字符串，原字符串右对齐，前面填充0


```
7.dict字典的方法

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
8.练习购物车

```
"""
1 输入工资，打印商品信息
2 选择商品编号，购买商品
3 如钱不够则提示，
4 任何时候都可以退出，退出时打印购买商品和余额
"""

goods_info = [
    ('移动电源', 99),
    ('冰淇淋', 8),
    ('电影票大话西游', 48),
    ('新鲜盒装羊肉', 68),
    ('空调', 1099),
    ('床上四件套', 108),
    ('三段奶粉', 320),
    ('iPhone X', 6888)
]
shopping_cart = []

salary = input('请输入存款：')

if salary.isdigit():
    salary = int(salary)
    init_money = salary
    for index, item in enumerate(goods_info):
        print(index, item)
    while True:
        goods_no = input('请选择购买商品编号：')

        if goods_no.isdigit():
            goods_no = int(goods_no)
            if goods_no < len(goods_info) and goods_no >= 0:
                goods_price = goods_info[goods_no][1]
                if goods_price <= salary:
                    salary -= goods_price
                    shopping_cart.append(goods_info[goods_no])
                    print('剩余%s元，已购买了商品有：%s ' % (salary, shopping_cart))
                else:
                    print('金额不足，购买失败，还有 %s 元' % salary)
            else:
                print('输入商品编号未找到，请重新输入！')
        elif goods_no == 'q' or goods_no == 'Q':
            if salary != init_money:
                print('余额为 %s 元， 购买的商品有： %s' % (salary, shopping_cart))
            else:
                print('出来逛逛，不买东西！！！')
            exit()
        else:
            print('输入的商品编号有误，请重新输入！')
else:
    print('输入存款有误！')




```
9.优化购物车

```
"""
购物车程序：
1、启动程序后，输入用户名密码后，如果是第一次登录，让用户输入工资，然后打印商品列表
2、允许用户根据商品编号购买商品
3、用户选择商品后，检测余额是否够，够就直接扣款，不够就提醒
4、可随时退出，退出时，打印已购买商品和余额	ok
5、在用户使用过程中， 关键输出，如余额，商品已加入购物车等消息，需高亮显示
6、用户下一次登录后，输入用户名密码，直接回到上次的状态，即上次消费的余额什么的还是那些，再次登录可继续购买
7、允许查询之前的消费记录
"""

f_buy = open('buy_info', 'a+', encoding='UTF-8')
f_buy.seek(0)

goods = [
    ('pc', 2888),
    ('mac pro', 8888),
    ('book', 46),
    ('ticket', 190)
]

shopping = []
username = 'admin'
password = 'admin11'

_username = input('登录名：')
_password = input('密  码：')

if username == _username and password == _password:
    print("登录成功！！！")
    # print(type(len(f_buy.readlines())))
    if len(f_buy.readlines()) > 0:  # 判断buy_info文件有数据
        f_buy.seek(0)   # 将光标移动0位置
        for x in f_buy.readlines(): # 逐行读数据
            # print(x.strip())
            if username == x.split(';')[0]:     # 判断是否已经登录的登录名
                salary = int(x.split(';')[1])   # 获取金额，转成int
                buy_goods = x.split(';')[2]     # 获取之前购买的商品信息
                balance = salary
                choice_list = input('C/c:查询历史订单，Q/q:退出，否则继续：')
                if choice_list == 'c' or choice_list == 'C':
                    print('余额为：\033[1;31;0m {balance} \033[0m，已购买了\033[1;31;0m {buy_goods} \033[0m'.format(balance=salary, buy_goods=buy_goods))
                elif choice_list == 'q' or choice_list == 'Q':
                    exit()

    else:   # 如果在buy_info没有找到用户则需要输入工资
        salary = input('工  资：')
        if salary.isdigit():
            salary = int(salary)
            balance = salary
        else:
            print('输入工资错误！！！')

    while True:
        for index, item in enumerate(goods):    # 获取商品信息及编号
            print(index, item)
        user_choice = input('选择购买商品编号>>> ')
        if user_choice.isdigit():   # 判断输入是否为int
            user_choice = int(user_choice)
            if user_choice < len(goods) and user_choice >= 0:   # 判断输入的编号是否存在商品
                p_item = goods[user_choice]
                if p_item[1] <= salary:     # 判断是否能够购买
                    salary = salary - p_item[1]
                    # print('your balance is %d ' % salary)
                    shopping.append(p_item)
                    print('购买清单： \033[1;31;0m %s \033[0m' % shopping)
                else:
                    print('余额不足，你的余额为：\033[1;31;0m %d \033[0m' % salary)
            else:
                print('输入商品编号不存在！！！')
        elif user_choice == 'q':
            if salary == balance:
                print('本次什么也没买！！！')
            else:
                print('余额为：\033[1;31;0m %d \033[0m, 购买了商品有：\033[1;31;0m %s \033[0m' % (salary, shopping))
                f_buy.write(username)
                f_buy.write(';')
                f_buy.write(str(salary))
                f_buy.write(';')
                f_buy.write(str(shopping))
                # f_buy.write('\n')
            exit()
        else:
            print('输入错误！！！')
    else:
        print('工资输入错误！！！')
```