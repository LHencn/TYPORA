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

###### 1、内存越界的几种可能：

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

###### 2、内存越界的后果：

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

###### 3、错误排查



