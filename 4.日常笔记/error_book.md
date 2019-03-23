[TOC]



# C++

#### 类

##### 初始化列表

###### 优点：节省时间开销

###### 初始化变量顺序：

调用内嵌对象的构造函数,调用顺序按照内嵌对象在组合类中的定义中出现的顺序。需要注意的是,我们写在初始化列表中的内嵌对象顺序,跟内嵌对象构造函数的调用顺序无关。

###### 四个必须使用情况

- 类的成员变量是const类型，必须在初始化时赋值
- 类成员为引用类型
  - 原因：只能初始化而不能赋值

```c
class A
{
    public:
        A(int &v) : i(v), p(v), j(v) {}
        void print_val() { cout << "hello:" << i << "  " << j << endl;}
    private:
        const int i;
        int p;
        int &j;
};
```



- 类成员为没有默认构造函数的类类型
  - 原因：创建对象无法初始化该成员

```c
class Base
{
    public:
        Base(int a) : val(a) {}
    private:
        int val;
};

class A
{
    public:
        A(int v) : p(v), b(v) {}
        void print_val() { cout << "hello:" << p << endl;}
    private:
        int p;
        Base b;
};
```



- 如果类存在继承关系，派生类必须在其初始化列表中调用基类的构造函数

```c
class Base
{
    public:
        Base(int a) : val(a) {}
    private:
        int val;
};

class A : public Base
{
    public:
        A(int v) : p(v), Base(v) {}
        void print_val() { cout << "hello:" << p << endl;}
    private:
        int p;
};

int main(int argc ,char **argv)
{
    int pp = 45;
    A b(pp);
    b.print_val();
}
```

##### 组合

​	使用过程中，调用类之前必须进行类的声明。当互相调用时可以前向引用声明。

```c
class B;
class A{
public:
    void function  (B b);
};
class B{
public:
    void function2 (A a);
};
```

###### 注意：

- 在前向引用声明时，类只进行了声明没有定义时，不可定义该类的对象，也不能在成员函数中使用该类的对象
- 但可以声明前向引用声明类的指针或引用，因为此时仅为声明，并没有初始化。
  - 即使声明引用，也不可以调用，因为没有进行初始化。

##### 相似的结构体

- 与类基本相同，唯一区别是默认成员类型为公有。

#### 数组

数组元素为对象时的初始化

```c
Point p[2]={Point(1,2),Point(3,4)};//假设Point有对应的构造函数
```

#### 字面量

```c
char string[] = "Hello"; //内存栈区
char *string2 = "Hello"; //字面量池
```

注意：字符串的内部表示都会以空字符'\0'作为结尾。

#### vector

动态数组模板

```c
vector<int>arr; //调用默认构造函数
vector<int>arr(10);//长度为10数组元素为整型的动态数组
vector<类型>数组对象名(数组长度,元素初值);
vector<int> v(10,1);//建立一个有10个元素的vector整型对象v，初值全设置为1
```

注意：vector数组对象的名字表示的就是一个数组对象,跟数组地址无关——事实上,vector是一个被封装的数组对象,它不会让你直接访问它的地址的(封装的意义就在于此)。

#### 指针

```c
int a[3] = {0};
int *p = &a;
p + 1; //表示&a[1] 
```

2、数组名：也可以当做是一个值不能改变的指针，但它不是指针。

3、只有指向同类型地址区域的指针才可以进行比较，指针可以和0进行比较，0表示空地址。

4、空指针：0、NULL、nullptr

5/





# 算法

## 牛顿法：求方程近似解

- 有着[广泛的应用](https://blog.csdn.net/qq_36330643/article/details/78003952)

```cpp
#define EPSILON 1e-6
double f(double x) {
    return 2 * pow(x, 3) - 4 * pow(x, 2) + 3 * x - 6;
}

double f_prime(double x) {
    return 6 * pow(x, 2) - 8 * x + 3;
}
double newton(double (*f)(double), double (*f_prime)(double)) {
    double x = 1.5;
    while (fabs((*f)(x)) > EPSILON){
        x = x - (*f)(x) / (*f_prime)(x);
    }
    return x;
}
```

## 二进制位

正数的原码、反码、补码均相同；

负数的原码为将符号为更为1；反码为符号位改为1，其余位按位取反；补码为反码加1





# 操作系统

#### 常见编译错误总结

##### 一、栈溢出：

​	因程序向栈中某个变量中写入的字节数超过了这个变量本身所申请的字节数，因而导致栈中与其相邻的变量的值被改变。

常见的危险函数：

- 输入：gets（），直接读取一行，忽略'\x00'；scanf（）；vscanf（）；
- 输出：sprintf（）；strcpy 字符串复制，遇到'\x00'停止；strcat 字符串拼接，遇到'\x00'停止；bcopy

##### 二、段错误

​	1、访问系统不存在的内存地址

```c
#include<stdio.h>
#include<stdlib.h>
void main()
{
  int *ptr = NULL;
  *ptr = 0;
}
```

​	2、访问系统保护的内存地址

```c
#include<stdio.h>
#include<stdlib.h>
void main()
{
  int *ptr = (int *)0;
  *ptr = 100;
}
```

​	3、访问只读的内存地址

```c
#include<stdlib.h>
#include<string.h>
void main(){
{
  char *ptr = "test";
  strcpy(ptr, "TEST");
}
```

​	4、栈溢出

```c

```

​	5、delete的错误使用

```c
char *p = new char[10];
p = "test";
delete[] p;
```

错误原因：delete只能删除new得来的内存，上面的p指向了新的内存，原先new来的内存已找不到了，内存泄漏；

```c
char *p = new char[10];
*p = 'a';
printf("%c\n",)
```

错误原因：释放两次new来的内存；

​	6、数组内存越界

##### 三、内存问题

1.内存重复释放，出现double free时，通常是由于这种情况所致；

2.内存泄露，分配的内存忘了释放；

3.内存越界使用，使用了不该使用的内存；

4.使用了无效指针；

5.空指针，对一个空指针进行操作；

（第四种情况，通常是指操作已释放的对象，如： 1.已释放对象，却再次操作该指针所指对象。 2.多线程中某一动态分配的对象同时被两个线程使用，一个线程释放了该对象，而另一线程继续对该对象进行操作。）

1、内存越界的几种可能：

```c
char buf[32]= {0};
for(int i=0;i<n; i++)// n < 32 or n > 32
{
    buf[i] = 'x';
}
```

```c
char buf[32]= {0};
string str ="this is a test sting !!!!";
sprintf(buf,"this is a test buf!string:%s", str.c_str()); //out of buffer space
```

```c
string str ="this is a test string!!!!";
char buf[16]= {0};
strcpy(buf,str.c_str()); //out of buffer space
```

2、内存越界的后果：

1.破坏了堆中的内存分配信息数据，特别是动态分配的内存块的内存信息数据，因为操作系统在分配和释放内存块时需要访问该数据，一旦该数据被破坏，以下的几种情况都可能会出现。

```c
* glibcdetected * free(): invalid pointer:
* glibcdetected * malloc(): memory corruption:
* glibcdetected * double free or corruption (out): 0x00000000005c18a0 ***
* glibcdetected * corrupted double-linked list: 0x00000000005ab150***        
```

2.破坏了程序自己的其他对象的内存空间，这种破坏会影响程序执行的不正确性，当然也会诱发coredump，如破坏了指针数据。
3.破坏了空闲内存块，很幸运，这样不会产生什么问题，但谁知道什么时候不幸会降临呢？

​	通常，代码错误被激发也是偶然的，也就是说之前你的程序一直正常，可能由于你为类增加了两个成员变量，或者改变了某一部分代码，coredump就频繁发生，而你增加的代码绝不会有任何问题，这时你就应该考虑是否是某些内存被破坏了。

3、错误排查





