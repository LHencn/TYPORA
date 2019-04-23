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

###### 取消转义符功能：

在字符串前加上字母`r`，`raw`的缩写，未经加工的，取消转义字符的功能

###### 大写upper()和小写lower()

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



