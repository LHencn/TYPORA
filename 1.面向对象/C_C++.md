### 在C++中处理字符串string

![字符串](./pic/字符串.png)

![字符串2](./pic/字符串2.png)

![](./pic/字符串3.png)

![](./pic/字符串4.png)

![](./pic/字符串5.png)

![](./pic/字符串6.png)

![](./pic/字符串7.png)

![](./pic/字符串8.png)

```c
void Replace(char* str, const char* toFind, const char* toReplace)
{
    int s = strlen(str);
    int f = strlen(toFind);
    int r = strlen(toReplace);
    int counter = 0;

    while (char* found = strstr(str, toFind))
    {
        counter++;
        if (f < r)
        {
            int size = (s + 1) - (found + f - str);
            if (size > 0)
            {
                memmove(found + r, found + f, (s + 1) - (found + f - str));
            }
            strncpy(found, toReplace, r);
        }
        else
        {
            strncpy(found, toReplace, r);
            int size = (s + 1) - (found + f - str);
            if (size > 0)
            {
                memmove(found + r, found + f, (s + 1) - (found + f - str));
            }
        }
    }

    str[s + counter*(r - f)] = '\0';
}
```

##### string对象的几种构造方法

转：https://www.cnblogs.com/ahcc08/p/3691072.html

```c
a) string s; //生成一个空字符串s 
b) string s(str) //拷贝构造函数 生成str的复制品 
c) string s(str, stridx) //将字符串str内"始于位置stridx"的部分当作字符串的初值 
d) string s(str, stridx, strlen) //将字符串str内"始于stridx且长度顶多strlen"的部分作为字符串的初值 
e) string s(cstr) //将cstr字符串作为s的初值 
f) string s(chars, chars_len) //将C字符串前chars_len个字符作为字符串s的初值。 
g) string s(num, c) //生成一个字符串，包含num个c字符 
h) string s(beg, end) //以区间beg;end(不包含end)内的字符作为字符串s的初值
```

转：https://www.cnblogs.com/HanEichy/p/4172718.html

在某种程度上，可以将string类型视为字符容器，支持很多容器操作。与vector相似，string的字符也是连续存储的，因此也有capacity和reserve操作。另外，也可用迭代器输出字符串，如下例：

```c
string s("Hello world!");
string :: iterator iter = s.begin();
while(iter!=s.end())
{
    cout << *iter;
}
```

在创建一个string对象并初始化时，有以下几种方法(ch1、ch2、ch3为定义的字符数组)：

```c
char *ch1 = "hello world!";
char ch2[] = "goodbye";
char ch3[] = {'a','b','c'};

string s1;　　
string s2(2,'a');
string s3(s2);
string s4(s3.begin(),s3.end());
string s5(ch1);
string s6(ch2,7);
string s7(ch2+4,2);
string s8(ch3);
string s9(ch3,2);
string s10(s6,2);
string s11(s6,0,4);
string s12(s6,0,10);
```

上述代码中s1-s9的创建中，s8的创建string对象是错误的！！！！下面分析每个对象：

1. s1：没有采用其它对象进行初始化，而是调用了默认构造函数，因此，s1为空字符对象，即s1=""；
2. s2：采用2个字符a初始化s2，因此s2="aa"；
3. s3：s3是s2的一个副本，因此s3="aa"；
4. s4：采用两个迭代器之间的元素进行初始化s4，s3.begin()存放s3的第一个元素，s3.end()指向s3最后一个元素的下一个，但初始化为左闭合，因此不包括s3.end()，因此。s4="aa"；
5. s5：使用只有一个指针参数的构造函数定义s5,该指针指向以空字符结束的数组ch1的第一个自读，这个数组的所有字符，但不包括null(C风格字符串是以null结尾的)，都被复制到新创建的s5中,s5="hello world!"；
6. s6：s6的初始化是通过一个指针和一个计数器来实现的，从这个指针指向的字符开始，复制该指针后面连续计数器个数的字符到新创建的string对象中，s6="goo"；
7. s7：s7的初始化与s6类似，但传进的指针是ch2数组中指向b的指针，s7="by"；
8. s8：s8并不是采用C风格字符串，调用这种形式的初始化式，必须是以空字符结束的数组。将不包含null的数组传递给此构造函数，将导致编译器无法检测的严重错误，只有当遇到null时，s8的初始化才会停止；
9. s9：然而，s9的初始化是正确的，初始化包含了一个计数器，指明了需要复制的元素的个数，该元素个数必须小于数组长度，无论数组是否以null结尾都没有什么关系。s9="ab"；
10. s10：将s10初始化为s6的一个子串，第二个参数指定了开始复制的位置，从制定位置复制到最后，因此s10="odbye"；
11. s11：s11与s10是同种初始化方式，其中，第二个参数制定了开始复制字符的位置，第三个参数制定了复制的长度，因此s11="good"；
12. s12：当复制的长度超过字符串的结尾时，标准库规定只能复制到与被复制string对象结尾处，s12="goodbye"。

#####  使用`string`类

计蒜客训练读官方英语API文档

### lambda表达式

![](./pic/lambda1.png)

![](./pic/lambda2.png)

![](./pic/lambda3.png)

```c
int Count(vector<int>& numbers, bool(*filter)(int))
{
    int counter = 0;
    for (int x : numbers)
    {
        if (filter(x))
        {
            counter++;
        }
    }
    return counter;
}

bool Odd(int x)
{
    return x % 2 == 1;
}

bool Even(int x)
{
    return x % 2 == 0;
}

int CountOdds(vector<int>& numbers)
{
    return Count(numbers, &Odd);
}

int CountEvens(vector<int>& numbers)
{
    return Count(numbers, &Even);
}
```

![](./pic/lambda4.png)

```c
template<typename U>
int Count(vector<int>& numbers, U filter)
{
    int counter = 0;
    for (int x : numbers)
    {
        if (filter(x))
        {
            counter++;
        }
    }
    return counter;
}

int CountOdds(vector<int>& numbers)
{
    return Count(numbers, [](int x){ return x % 2 == 1; });
}

int CountEvens(vector<int>& numbers)
{
    return Count(numbers, [](int x){ return x % 2 == 0; });
}
```

![](./pic/lambda5.png)

![](./pic/lambda6.png)

![](./pic/lambda7.png)

![](./pic/lambda8.png)

```c
int Count(vector<int>& numbers, bool(*filter)(int, void*), void* context)
{
    int counter = 0;
    for (int x : numbers)
    {
        if (filter(x, context))
        {
            counter++;
        }
    }
    return counter;
}

bool GreaterThan(int x, void* context)
{
    return x > *reinterpret_cast<int*>(context);
}

int CountGreaterThan(vector<int>& numbers, int y)
{
    return Count(numbers, &GreaterThan, &y);
}
```

![](./pic/lambda9.png)

```c
bool Odd(int x, void*)
{
    return x % 2 == 1;
}

bool Even(int x, void*)
{
    return x % 2 == 0;
}

int CountOdds(vector<int>& numbers)
{
    return Count(numbers, &Odd, nullptr);
}

int CountEvens(vector<int>& numbers)
{
    return Count(numbers, &Even, nullptr);
}
```

![](./pic/lambda10.png)

![](./pic/lambda11.png)

```c
// Count函数不用改
template<typename U>
int Count(vector<int>& numbers, U filter);

int CountGreaterThan(vector<int&> numbers, int y)
{
    return Count(numbers, [=](int x){ return x > y; });
}
```

![](./pic/lambda12.png)

![](./pic/lambda13.png)

![](./pic/lambda14.png)

```c
template<typename U>
void Traverse(vector<int>& xs, U process)
{
    for (int x : xs)
    {
        process(x);
    }
}

void CopyGreaterThan(vector<int>& a, vector<int>& b, int y)
{
    Traverse(a, [&, y](int x){
        if (x > y)
        {
            b.push_back(x);
        }
    });
}
```



![](./pic/lambda15.png)

再见，`void *context;`

![](./pic/lambda16.png)

```cpp
/*
*这段代码有问题，因为 lambda 表达式在使用全局变量的时候，不能够选择要复制它还是引用它。因为 lambda 表达式肯定可以修改全局变量。
*/
#include <iostream>

using namespace std;

int a = 0;

int main()
{
    auto inc = [&a](){ a++; };
    inc();
    inc();
    cout << a << endl;
    return 0;
}
```

ss

















## C语言标准库

#### string.h

##### strncpy

strncpy是 [C语言](https://baike.baidu.com/item/C%E8%AF%AD%E8%A8%80)的库函数之一，来自 C语言标准库，定义于 [string.h](https://baike.baidu.com/item/string.h)，char *strncpy(char *dest, const char *src, int n)，把src所指向的字符串中以src地址开始的前n个字节复制到dest所指的数组中，并返回被复制后的dest。

```c
函数原型char *strncpy(char *dest,char *src,int size_t);
```

##### 一些常用的字符串函数

```c
 
void *memset(void *s,int c,size_t n);
 
size_t strlen(const char *s);
 
void *memcpy(void *dest,const void *src,size_t n);
void *memmove(void *dest,const void *src,size_t n);
 
char *strcat(char *dest,const char *src);
char *strncat(char *desk,const char *src,size_t n);
 
//大小写敏感
int memcmp(const void *s1,const void *s2,size_t n);
int strcmp(const char *s1,const char *s2);
int strncmp(const char *s1,const char *s2,size_t n);
 
//大小写不敏感
int strcasecmp(const char *s1,const char *s2);
int strncasecmp(const char *s1,const char *s2,size_t n);
 
//正反向查询
char *strchr(const char *s,int c);
char *strrchr(const char *s,int c);
char *strstr(const char *haystack,const char *needle);
 
//分割字符串
char *strtok(char *str,const char *delim);
char *strtok_r(char *str,const char *delim,char **saveptr);
```



## STL

#### #include《string》

#### **popen**函数：

1、popen原型：

```c
FILE * popen ( const char * command , const char * type );
int pclose ( FILE * stream );
```

C语言中的`I/O`函数，调用输入（输出）流执行command路径下的文件。

2、与system区别：

```c
int system(const char *command);
```

system源代码中最后一步会等待该子进程的结束，直到结束才返回（**串行**），而popen则直接返回，若不使用pclose关闭刚刚popen创建的管道，则刚刚的子进程变为僵尸进程（**并行**）。

3、网站链接：

1、system函数总结：

#### getline函数：

获取整行输入

#### malloc函数：

机制：malloc函数的实质体现在，它有一个将可用的内存块连接为一个长长的列表的所谓**空闲链表**（**堆**）。调用malloc函数时，它沿**空闲链表**寻找一个大到足以满足用户请求所需要的内存块。然后，将该内存块一分为二（一块的大小与用户请求的大小相等，另一块的大小就是剩下的字节）。接下来，将分配给用户的那块内存传给用户，并将剩下的那块（如果有的话）返回到连接表上。调用free函数时，它将用户释放的内存块连接到空闲链上。到最后，空闲链会被切成很多的小内存片段，**如果这时用户申请一个大的内存片段，那么空闲链上可能没有可以满足用户要求的片段了。于是，malloc函数请求延时，并开始在空闲链上翻箱倒柜地检查各内存片段，对它们进行整理，将相邻的小空闲块合并成较大的内存块**。如果无法获得符合要求的内存块，malloc函数会返回`NULL指针`，因此在调用malloc动态申请内存块时，一定要进行返回值的判断。

Linux Libc6采用的机制是在free的时候试图整合相邻的碎片，使其合并成为一个较大的free空间。

##### **与new的区别：**

从本质上来说，malloc（Linux上具体实现可以参考`man malloc`，glibc通过`brk()&mmap()`实现）是libc里面实现的一个函数，如果在source code中没有直接或者间接`include过stdlib.h`，那么gcc就会报出`error：‘malloc’ was not declared in this scope`。如果生成了目标文件（假定动态链接malloc），如果运行平台上没有libc（Linux平台，手动指定`LD_LIBRARY_PATH`到一个空目录即可），或者libc中没有`malloc函数`，那么会在运行时（`Run-time`）出错。**new则不然，是c++的关键字，它本身不是函数**。new不依赖于头文件，C++编译器就可以把new编译成目标代码（g++4.6.3会向目标中插入_Znwm这个函数，另外，编译器还会根据参数的类型，插入相应的构造函数）。

- 在使用上，malloc 和 new 至少有两个不同: new 返回指定类型的指针，并且可以自动计算所需要大小。而 malloc 则必须要由我们计算字节数，并且在返回后强行转换为实际类型的指针。

##### **堆与栈区别**：

堆与栈实际上是操作系统对进程占用的内存空间的两种管理方式，主要有如下几种区别：
（1）**管理方式不同**。栈由操作系统自动分配释放，无需我们手动控制；堆的申请和释放工作由程序员控制，容易产生内存泄漏；

（2）**空间大小不同**。每个进程拥有的栈的大小要远远小于堆的大小。理论上，程序员可申请的堆大小为虚拟内存的大小，进程栈的大小64bits的Windows默认1MB，64bits的Linux默认10MB；

（3）**生长方向不同**。堆的生长方向向上，内存地址由低到高；栈的生长方向向下，内存地址由高到低。

（4）**分配方式不同**。堆都是动态分配的，没有静态分配的堆。栈有2种分配方式：静态分配和动态分配。静态分配是由操作系统完成的，比如局部变量的分配。动态分配由alloca函数进行分配，但是栈的动态分配和堆是不同的，他的动态分配是由操作系统进行释放，无需我们手工实现。

（5）**分配效率不同**。栈由操作系统自动分配，会在硬件层级对栈提供支持：分配专门的寄存器存放栈的地址，压栈出栈都有专门的指令执行，这就决定了栈的效率比较高。堆则是由C/C++提供的库函数或运算符来完成申请与管理，实现机制较为复杂，频繁的内存申请容易产生内存碎片。显然，堆的效率比栈要低得多。

（6）**存放内容不同**。栈存放的内容，函数返回地址、相关参数、局部变量和寄存器内容等。当主函数调用另外一个函数的时候，要对当前函数执行断点进行保存，需要使用栈来实现，首先入栈的是主函数下一条语句的地址，即扩展指针寄存器的内容（EIP），然后是当前栈帧的底部地址，即扩展基址指针寄存器内容（EBP），再然后是被调函数的实参等，一般情况下是按照从右向左的顺序入栈，之后是被调函数的局部变量，注意静态变量是存放在数据段或者BSS段，是不入栈的。出栈的顺序正好相反，最终栈顶指向主函数下一条语句的地址，主程序又从该地址开始执行。堆，一般情况堆顶使用一个字节的空间来存放堆的大小，而堆中具体存放内容是由程序员来填充的。

### map

1、插入排序时键值按从小到大排序

```c
for (auto i : arr) {
        cout << i.first << " " << i.second << endl;
    }

```

２、如何在map中判断某个键值是否存在？

```
if (arr.find("hello") == arr.end()) {//如果没有找到，find就会返回该map的最后一个值即end
    cout << "not found" << temp << endl;
}
```

３、当给map设置的key为自定义的类时，

- 需要手动重载`<`，因为插入时需要根据键值大小来进行插入调整。
- 手动重载`<<`，因为`x.first`表示的键值为自定义的类型，无法输出。





## C++11新特性

原自：https://www.cnblogs.com/harlanc/p/6504431.html

### 1、auto



### 2、智能指针

### 3、nullptr

### 4、rand for

### 5、非成员begin和end

### 6、Lambda表达式

### 7、Move/&&

### 8、统一的初始化和初始化列表

