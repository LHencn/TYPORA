##### 语言简介：

- 动态解释型语言（字节码编译）
- 运行时边理解执行，边判断是否有错误（无需提前编译）

##### 语言特点：

- 变量、参数、函数（方法）在声明时无需说明类型

```python
//变量无需类型声明
a=6
print a
b = 'hello world'
print b
a = b
print a, b
```

##### 输入函数`raw_input()`

```python
name = raw_input('What is your name:')
print 'Your name is ' + name
```

##### 数学运算

```python
a = 1
b = 2
print a + b
print b * 3
print b + a * 2
```

##### 传统除法运算

```python
print 3 / 2 	#取整除
print 3.0 / 2.0	#精确除
print 2. / 2.	#小数点后为0可省略
```

##### 全局精确除法运算

若我们希望全局都是精确除法结果，可操作如下：

```python
from __future__ import division #导包声明
print 3 / 2 					#1.5
print 3.0 / 2.0					#1.5
print 2. / 2.					#1.0
print 3 // 2					#1
```

##### 字符串运算

```python
a = 'love '
b = 'China'
print a + b			#love China
print a * 3 + b		#love love love China
```

##### 字符串长度`len()`和整型转字符串`str`

```python
a = 'China'
a_len = len(a)			#a_len = 5
b = 'length of a is '
print b + str(a_len)	#str作用是把整型a_len转为字符串
```

##### 函数输出hello world

```python
def main():
    print 'Hello World'
    
if __name__ == '__main__':
    main()
```

##### 函数定义关键字`def`及行缩进

```python
def max_pow(a, b): 
    if a > b:
        pow_ab = a ** b
        return pow_ab
    pow_ba = b ** a
    return pow_ba
```

起始缩进：函数的开始会有起始缩进

命名方式：给变量和函数命名时采用下划线命名

##### help和dir

```python
import sys
help(len) 	
#输出关于系统内建的 len 这个函数的形式和它的作用说明
#请注意,这里写的是len,而不是调用 len 这个函数的写法len()
print dir(sys)	#在sys下所有的被定义的函数方法的列表。
help(sys.exit)
help('china'.split)
print dir(list)
```

dir和help很类似,只不过它返回的不是一个函数的定义,而是返回一个模组中一系列的被定义过的方法的列表。

##### 注释#：

无需注释情况：

- 怪异的逻辑，需要重构成简单易读的
- 显而易见的
- 程序的运行过程

需要注释情况：

- 文档性的，模组的开源证书说明、非极短函数或者类的说明
- 复杂算法
- 需要完善的代码（TODO）

用于代码的注释：

```python
​```
print '注释'
​```
```

##### python知多少

- 通过使用 help 和 dir 可以快速了解大多数 Python 模组和方法的信息
- python函数的参数可以是其他函数
- python程序中不按照规范，统一使用3个空格进行缩进也是不会出现错误的
- Python程序几乎所有的错误都是在程序运行到含有错误的那行的时候被报出
- 函数的参数形式需要可以简单代表“函数可接受参数，及其在函数具体定义中的意义”
- Python的函数是可以没有return语句的

##### A+B+C问题：读数字

```python
a, b, c = (int(x) for x in raw_input().split(' '))
print a + b + c
```

#### 字符串问题

- 若在字符串中包含单引号或双引号，需要使用转义字符`\`，但双引号内可直接使用单引号，单引号内也可直接使用双引号
- 字符串可分多行书写，只需在每行末尾添加`\`
- 字符串一经创建即不可变，比如

```python
a = 'hello' + 'there' 	#不是在前一个字符串末尾添加后一个字符串，而是又新创建了一个字符串
```

- 可通过`[]`来访问每一个字符，从0开始，访问位置不存在时，会报错“超出合法范围”错误

##### 取消转义符功能：

在字符串前加上字母`r`，`raw`的缩写，未经加工的，取消转义字符的功能

##### 大写upper()和小写lower()

```python
a = 'In\na line'
b = r'In\na line'			#输出字符串中不在换行
print a.lower()
print b.upper()
```

##### 字符串相关判断函数

```python
s = 'HelloabcdWord'
print s.isalpha()			#判断是否均是字母
print s.isdigit()			#判断是否均是数字
print s.startswith('Hello')	#判断是由某个字符串开始
print s.endswith('World')	#判断是否由某个字符串结束
```

##### 位置索引和逆序索引

每个字符的逆序索引的值等于它的位置索引的值减去字符串的长度。

|  H   |  e   |  l   |  l   |  o   |
| :--: | :--: | :--: | :--: | :--: |
|  0   |  1   |  2   |  3   |  4   |
|  -5  |  -4  |  -3  |  -2  |  -1  |

##### 切取字符串

```python
tower = 'abcdefg'
print tower[1:4]	#bcd
print tower[3:]		#defg
print tower[:-2]	#abcde
```

##### 条件判断 if--elif--else

##### 运算符in

对于列表类型使用

```python
ans = 'a' in list
print ans			#'a'在list列表中，返回'真'的True
```

##### 与and、或or、非not

```python
a = 5
if 2 < a < 13:  	#python中可以直接这么写
    print a
```



##### 字符串的查找find、替换replace

```python
weather = 'rainy day'
bag = 'nothing in the bag'
if weather.find('rain') != -1:
    bag = bag.replace('nothing', 'umbrella')
print bag
```

##### 字符串格式化输出

```python
name = 'Wangmu Niangniang'
age = 9000
height = 1.73
print name + ' is a ' + str(age) + '-year-old woman with height ' + str(height)
print '%s is a %d-year-old woman with height %g' % (name, age, height)
```

在这里, 单引号外的 % 前定义了输出字符串的格式,其中的 %s 表示字符串变量嵌入占位,%d 表示整数变量嵌入占位、%g 表示浮点数变量(高精度小数)嵌入占位。相应的,在% 后的括号内,我们按照前面的格式中的占位顺序,依次列出希望将值进行嵌入的变量。

##### 字符串编码

在 Python 的字符串中,默认编码方式并不是 Unicode。 对于一些特殊的字符,在大多数的 Python 解释器中,是无法正常的直接被使用的。

- 字符串赋值前加`u`
- 在有些情况下,这个程序会让你得到一个错误提示,那是因为我们没有对 s 进行字符串的编码类型指定,只是将它的值标记成了 Unicode。这时你就需要用这条语句来指定它

```python
s = s.encode('utf-8')
```

```python
s = u'I want to say \u4e2d\u56fd\u4e07\u5c81'
s = s.encode('utf-8')
print s
```

##### 丰富的字符串

- 对于字符串s和整数n（可能为负），s[:n]+s[n:]与s[:]和s都一致
- 格式化字符串的时候%f和%g都是浮点数变量的占位符
- Python（2.x版本）字符串默认是ASCII编码
- 字符串的replace函数会替换所有符合第一个参数定义的子字符串而不是只替换第一个
- python中允许`if 2 < a < 13`

##### 批量替换字符串

- 由于 Python 默认采用 ASCII 编码，若在代码中需要使用 中文，请在第一行声明：`#code=utf-8`

- 在网络编程中,如果 URL 中含有特殊字符,如空格、“#”等,服务器将无法识别导致无法获得正确的参数值,我们需要将这些特殊字符转换成服务器可以识别的字符,例如将空格转换成“%20”。给定一个字符串,将其中的空格转换成“%20”。

```python
a = raw_input()
a = a.replace(' ', '%20')
print a
```

#### 列表

- Python内建的结构，用于储存一系列的数据。
- 字符串是特殊列表（但不是真正的列表，不能使用列表的函数方法），可以看做一系列的长度为1的子字符串组成的特殊列表
- 对于列表，len函数给出列表的元素数量（列表长度）

##### 列表尾部元素添加`append`和`extend`函数

```python
hello = ['hi', 'hello']
world = ['earth', 'field', 'universe']
hello.append('nihao')	
print hello		#['hi', 'hello', 'nihao']
hello.extend(world)
print hello		#['hi', 'hello', 'nihao', 'earth', 'field', 'unverese']
```

##### 插入数据`insert`与元素定义`index`

```python
hello = ['hi', 'hello']
hello.insert(0, 'nihao')
print hello		#['nihao', 'hi', 'hello']
print hello.index('hi')		#1
```

##### 列表弹出`remove`与删除`pop`

```python
hello = ['nihao', 'hi', 'hello']
hello.remove('nihao')
print hello 	#['hi', 'hello']
hello.pop(0)
print hello		#['hello']
```

##### 字符串的切割`split`与列表合成`join`

```python
manager = 'tuotatianwang,taibaijinxing,juanliandajiang'
manager_list = manager.split(',')	#字符串切割形成列表
print manager_list	
new_manager = ' '.join(manager_list)#采用空格字符串的join方法将列表中的元素连接起来形成字符串
print new_manager
```

##### 列表的应用题：

- 将`list=['a', 'b', 'c']`合成字符串`'a|b|c'`并输出可以写成`print '|'.join(list)`
- 将字符串`'a b c'`按空格进行切割后并输出结果可以写成`print 'a b c'.split()`
- 对于`list = ['a', 'b', 'c', 'd']`来说，`list.insert(3, 'x')`后，list的值为`['a', 'b', 'c', 'x', 'd']`
- 对于`list = ['a', 'b', 'c', 'd']`来说，`print list.pop(3)`将得到输出结果d

##### 列表求和

```python
gardens = [7204, 3640, 1200, 1240, 71800, 3200, 604]
total = 0
for num in gardens:		#采用for--in循环
    total += num
print total
print sum(gardens)		#采用内置函数sum求列表和
```





