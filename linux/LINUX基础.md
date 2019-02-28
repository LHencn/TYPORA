[TOC]



# LINUX基础

源：应用市场

1. `sudo apt-get update` 更新`/etc/apt/sources.list`软件列表
2. `sudo apt-get upgrade` 更新软件
3. `sudo !!` 刚才执行的命令没有管理员权限，该命令为加上管理员权限
4. `apt-cache search` 
5. `apt-get intall` 安装软件包
6. `pip` 
7. `dpkg` 
8. `nmon` 

常用命令

### 操作系统概念：（2/5）

#### 体系结构：

1. 计算器：CPU
2. 控制器：CPU
3. ## 存储器：内部存储（内存） 寻址空间（MP3） 国家：每个国家做成一个单元，国家中的各个市为每个区
4. 输入设备：鼠标、键盘
5. 输出设备：显示器、音频等

操作系统：带有很多外围程序的系统，笔记本硬件--win7（带有计算器、画图工具），library（lib库）（Windows中有类似的库dll，linux中有`.so:shared object`）

office：word、ppt、表格等均需采用打印功能，此时可以采用系统调用调用官方已有的功能`system call` （该即直接作用到内核上，效率更高），也可直接作用到硬件上，功能均自己写。

应用程序可以随系统一起启动，也可以不随系统一起启动，则为交互式应用程序（用户使用时根据需要启动程序）

#### 操作系统历史：

1. 1969年，MIT和BELL实验室开发出MULTICS（采用汇编语言）

   1. ken开发出小游戏（类似与雷霆战机的太空遨游）
   2. ken：PDP-11 PDP-7
   3. c语言重新开发MULTICS
   4. unics---unix

2. 1977年，BSD：openbsd，freebsd netbsd

3. 1984年，谭宁邦教授，开发出minix，教学使用

4. 1984年，GNU： GNU is not unix (GCC/BASH SHELL)史特曼教授自己开发的供他人使用

5. GPL：

   1. 取得软件和源码，任何人可以根据自己的需求自由的获取软件和源码
   2. 复制：复制该软件（衍生）
   3. 修改：该源码可以自行修改（衍生）
   4. 再发行：把修改后的代码进行二次发行
   5. 修改授权：修改后的软件不可进行商业用途
   6. LGPL：基于某个内核平台开发的软件可以进行销售

6. Linux版本号（内核版本号）：三部分组成：

   A.B.C

   A：主版本号

   B：次版本号（奇数：开发版本  	偶数：发行版本）

   C：修订版本号（修订次数）

   内核版本：3.6.28  3是主版本号  6：次版本号   28修订了28次

   开发---内测（修复漏洞，开发新功能）---公测---正式版本生成（正式上线）

7. `lhc@lhc-PC: ~$  ` 

   1. lhc为当前登录的用户名
   2. lhc-PC为主机名
   3. $为当前登录用户是普通用户
   4. ～代表当前用户所处的目录（～代表当前用户宿主目录）

#### linux的设计理念(2/6)

1. ##### 远程连接linux系统：`xshell、CRT` 的使用

   1. `ifconfig` 查看IP地址
   2. `xshell` 中输入`ssh` 192.168.10.147

2. ##### shell的作用

   1. shell：人机交互接口
   2. 类似于图形用户界面的应用鼠标双击
   3. shell中输入命令，shell把命令传递给内核，内核把命令结果反馈给shell，人从shell中读取结果
   4. linux支持的shell，bash（默认的shell）、 ksh 、 csh
   5. linux图形界面
      1. GNOME：linux默认的图形界面，c语言开发
      2. KDE：C++开发
      3. xface：简化的图形界面

3. ##### 内核的作用

   1. 进程管理：要执行的任务（例：打开QQ，就是打开一个QQ进程）
   2. 内存管理：
   3. 文件系统：存储设备上存储数据的方式方法：windows：NTFS/FAT32、Linux：ext3、ext4、xfs等
   4. 网络功能：管理IP地址信息等
   5. 硬件驱动：
   6. 安全功能：
   7. linux是一个轻巧、稳定的系统

4. ##### linux设计思想

   1. 由很多的小程序组成，每个小程序完成单一的功能，实现复杂的任务（http服务需要安装很多小组件）

   2. 一切皆文件：所有的外围设备（硬件）或者其他的小程序

   3. 尽量避免捕获用户接口，用户不和内核直接接触

      用户->shell->软件->lib->kernal->硬件（cpu，内存，磁盘）

   4. 配置文件保存为纯文本格式（可以用文本编辑器编辑）

5. ##### linux终端：多用户多任务系统，可同时多个用户使用同一个系统

   1. 默认总共有6个终端：ctrl+alt+F1-F6，虚拟终端
   2. Linux界面：
      1. GUI：graphical user interface：图形用户接口（图形界面）Ctrl+alt+F7
      2. CLI：command line interface：命令行接口（字符界面）

6. ##### 命令格式等内容：

   1. 命令提示符（prompt）：`lhc@lhc-PC ~$`
   2. 退出当前终端`exit`
   3. Linux使用凭证：类似于指纹/刷脸等，用户名和密码（用户获取资源权限的凭证）
   4. root：linux默认管理员用户名
   5. 切换用户：`su（switch user）` 
      1. 当root用户切换到普通用户时，不需提供密码，而普通用户切换到root用户则需要提供密码
   6. 退出当前用户：`exit`
   7. 命令格式
      1. `命令字  【选项】  【参数】`   `ls -l`
      2. 选项：修正命令的执行方式（实现特定功能）
      3. 短选项：用`-`引导，多个短选项可以组合
      4. 长选项：用`--` 引导，后是一个单词，多个长选项不可组合 
      5. 参数：命令作用的对象
      6. 【】：可有可无

##### Linux如何高效获取命令信息

1. ###### 如何区分root用户和普通用户

   1. 系统可以区分用户的UID，不识别用户名
   2. 3A认证：
      1. 认证机制：authentication：
         1. 密码认证：
            1. 符合复杂性要求：数字，小写字母，大写字母，特殊符号至少三种
            2. 密码长度：至少7位
            3. 不要使用比较易记住的（使用随机字符）
            4. 定期更改密码
            5. 重复密码的时间要长
      2. 授权机制：authorization ：授权
      3. 审计机制：audition（日志）：监督

2. ###### Linux登录信息：`/etc/issue`

3. ###### Linux命令分类：

   1. 内部命令：shell自带的命令
   2. 外部命令：在Linux文件系统中存在一个应用程序

4. ###### `type` ：查看Linux命令类型

   1. `【command】is a shell builtin:buildin` 关键字说明该命令为内部命令
   2. `mkdir is /bin/` mkdir：有路径显示（外部命令）

5. ###### 路径：

   1. 绝对路径：从根（/）开始的路径是绝对路径，linux系统中只有一个根
   2. 相对路径：当前所处的工作目录为参照点，`.` 代表当前路径，`..`代表上一级路径，`～`代表宿主目录

6. ###### `ls（list） ` ：列出目录

   1. `-l(--long)`:以长格式显示
      1. `-rw-r--r-- 1 lhc lhc 2389 1月  30 19:07 012.binary_search_tree.c` 
      2. linux中文件名限制：
         1. 单个文件或目录的名称不能超过255个字符
         2. 文件名中不能包含特殊字符（如/，.，-，+等）
      3. 第一位：文件类型，采用`file`命令查看linux中文件类型
         1. `-` 代表普通文件（file）
            1. 纯文本文件（ASCII）：配置文件
            2. 二进制文件（binary file）：命令
            3. 数据格式文件（data）：/var/log/wtmp
         2. `d` 代表目录（directory）
         3. `b` 代表块设备（block），如硬盘，U盘等（`/dev下`）
         4. `c` 字符集设备（char）：如键盘等，一次性按顺序读取`/dev下`
            1. `s` 套接字文件（socket），通常用在网络上数据连接`IP：PORT` 
            2. 例如：`www.baidu.com`中先将`baidu`转为IP，默认端口80，则套接字为`www.baidu.com:80`
         5. `p` 命名管道（pipe）:特殊的文件类型，解决多个程序同时访问一个文件所造成的错误问题
         6. `l` 符号连接文件（symbolic link file）：软链接文件
      4. 第二位到第十位：权限位（rwx：读写执行）
         1. 234位：文件属主权限（owner）
         2. 567位：文件属组权限（group）
         3. 8910位：其他用户权限（other）
      5. 1：代表文件硬链接的次数
      6. 第一个lhc：代表文件属主（owner）
      7. 第二个lhc：代表文件属组（group）
      8. 2389：文件大小
      9. `1月 30 19:07`  文件最后被访问的时间戳
         1. `stat` 命令查看文件时间戳
         2. 文件的时间戳：
            1. access：访问的时间戳
            2. Modify：文件被修改的时间戳（修改文件数据：添加删除数据等）
            3. change：文件被更改时间戳（更改文件属性）
   2. `-h` ：为文件大小添加单位
   3. `-a` ：显示目录下所有文件（包括.， ..，以.开头的隐藏文件）
   4. `-A` ：和`-a` 相同，但不显示`.` 和 `..`
   5. `-R` ：递归显示目录中的内容（一并显示子目录中的所有内容）
   6. `-r` ：逆序显示目录下内容
   7. `-i` ：显示文件所在的inode节点（index node）

7. ###### 环境变量：内存中的命名空间

   1. PATH变量：存放系统命名路径，以冒号隔开
   2. 查看PATH变量：echo $PATH（Linux命令严格区分大小写）
   3. `lhc@lhc-PC:~$ echo $PATH /usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/sbin:/usr/sbin`
      1. 如果在以上路径中没有找到相关命令（该命令为外部命令），提示用户command not found 
      2. 如果一个命令在以上多个路径中存在，系统会按照从前往后的顺序查找，查找到该命令后，后面的路径则不再查找
   4. `hash` ：查看命令缓存及命中率（使用次数）

8. ###### Linux命令的帮助信息

   1. 内部命令：采用`help` 命令查看
   2. 外部命令：`[command] --help`
   3. **man**手册（命令的使用说明书）
      1. 语法：`man ls `
      2. man查看内部命令时，显示的是bash帮助信息，内部命令一般用type查看
      3. 可以用上下方向键翻行
      4. enter向下翻行
      5. pagedown：向下翻页
      6. pageup：向上翻页
      7. `/word` ：从上向下查找关键字
      8. `？word` ：从下向上查找关键字
      9. `q` ：退出当前帮助信息
      10. man八目录说明：
          1. `User Command`：普通用户命令（`/usr/local/bin:/usr/bin:/bin`等binary文件中的都是普通用户命令）可执行程序或shell命令
          2. `System Calls`：系统调用库（内核提供的函数）
          3. `C Library Functions`：库调用（程序库中的函数）
          4. `Devices and Special Files`：设备或特殊文件（硬件设备，(通常位于`/dev`)
          5. File Formats and Conventions：查看配置文件格式（如`/etc/passwd`）
          6. Games et. Al.：游戏
          7. Miscellanea：杂项
          8. System Administration tools and Deamons：系统管理员的工具，管理命令（`/sbin:/usr/sbin`等sbin：secret binary文件）
      11. man使用说明：
          1. NAME：命令名称及简要用法
          2. SYNOPSIS：语法格式，可能要包括一些选项的使用
          3. DESCRIPTION：命令和命令选项的一些说明
          4. Exit status：退出状态码
          5. AUTHOR：作者信息
          6. REPORTING BUGS（BUG）：发现BUG时如何反馈信息
          7. COPYRIGHT：另外参照的帮助信息
          8. SEE ALSO：另外参照的帮助信息
          9. OPTIONS：说明该命令每一个选项的详细用法
          10. EXAMPLES：使用实例
      12. man手册目录路径：`/usr/shared/doc`  工作中主要查看内核信息
          1. <>：必须使用的选项或参数
          2. []：选用的选项或参数
          3. ...：可以使用多个选项或参数
          4. |：代表多选一
          5. {}：分组，没有特殊意义
   4. info：查看帮助信息，更注重于linux的历史

9. ######  `cd ：change directory`：切换目录

   1. `cd`：不加选项，返回到当前用户的宿主目录
   2. `cd -`：返回到上次工作的路径
   3. `~username`：切换到username的宿主目录

10. ###### `which`查看

11. ###### `whatis` ：查看命令所在的帮助信息目录，该命令在系统启动大约70分钟后生成whatis的数据库，如果时间太短，该命令不回去执行，我们可以使用makewhatis初始化该命令

12. ###### `useradd` ：建立用户

#### Linux的根文件系统

1. Linux文件系统FHS（Filesystem Hierarchy Standard）标准：希望用户可以了解已经安装的程序在哪个目录下

2. 根文件文件系统（/）：rootfs：root filesystem

   1. `/bin`：二进制，存放命令，大部分和开机命令相关
   2. `/boot`：存放启动和内核相关的文件
   3. `/dev`：存放设备文件
   4. `/etc`：存放应用程序的配置文件
   5. `/home`：普通用户的宿主目录，默认为`/home/username`
   6. `/lib和/lib64`：存放系统开机时需要用的函数库及运行`/bin`和`/sbin`命令调用的函数库
      1. `/lib/modules`：存放内核相关的模块（驱动程序等）
   7. `/media和/mnt`：挂载点，`/media`挂载移动设备，`/mnt`挂载临时设备
   8. `/opt`：第三方软件存放目录（用户自行安装的软件存放处），现在一般安装到`/usr/local `
   9. `/proc`：伪文件系统，存放数据、 关于进程（以数字命名）相关的信息，存放网络状态等，以后调优可能会用到
   10. `/root`：管理员的家目录
   11. `/sbin`：存放管理员使用的命令（安全的二进制命令）
   12. `/srv`：service缩写，存放服务数据的目录，如可以把www服务的网页存放到该目录
   13. `/tmp`：存放临时文件，所有用户都可以访问创建文件，但是每个用户只能删除自己的文件，大概系统一个月自动清空一次
   14. `/sys`：伪文件系统，记录内核相关的信息，包括目前加载的内核模块以及内核检测到的硬件设备等
   15. `/usr`：UNIX Software Resource：存放安装的应用程序
       1. `/usr/bin`：普通用户使用的命令（和/bin区别是是否与开机有关）
       2. `/usr/sbin`：网络服务器命令
       3. `/usr/lib`和`/usr/lib64`：包含各种应用程序函数库
       4. `/usr/share`：存放共享文件目录（在线帮助文件，杂项，时区文件等）
       5. `/usr/include`：存放语言头文件，安装软件的头文件
       6. `/usr/src`：编译安装以后释放源代码目录
   16. `/var`：vary的缩写，存放经常变动的文件，比如日志，mail等
       1. `/var/cache`：应用程序运行时产生的缓存文件
       2. `/var/lib`：程序本身运行时需要数据文件的存放目录，比如mysql运行时的文件
       3. `/var/lock`：存放运行时的某些设备或资源一次只能被一个应用程序使用，如果多个应用使用会产生错误，存放锁文件，为设备或资源上锁
       4. `/var/log`：存放系统日志目录（系统、用户登录、服务日志等）
       5. `/var/mail`：存放个人电子邮件（系统报警产生的邮件信息等）
       6. `/var/run`：存放应用程序运行时的PID文件（进程号.pid结尾）
       7. `/var/spool`：存放队列数据，排队等待其他应用程序使用的数据，这些数据通常情况下使用完成后会被删除

3. FHS规定：`/etc, /bin, /dev, /lib, /sbin`五个目录必须要个根目录位于同一文件系统

4. `file`：查看文件类型（windows中用拓展名识别文件类型）

   1. 语法：`file [options][args]`
   2. `-b`：显示结果时，不显示文件名
   3. `-c`：显示执行file命令的的执行过程（去判断file命令是如何判断文件类型的，便于排错或分析file执行过程）
   4. `-i`：输出MIME类型的字符串 
   5. `-z`：显示压缩文件的内容
   6. `-L`：查看软链接的文件内容
   7. `-f`：查看文件中文件名的类型

5. `cat`：一次性查看整个文件，从键盘输入创建一个新文件

   1. 语法：`cat [options][args]`

   2. 从键盘输入创建一个新文件：

      1. 新建新文件

         ```shell
         cat >new_file_name << EOF  //EOF:end of file
         ```

      2. 向现有文件中追加数据：

         ```shell
         cat >> test.txt << eof
         ```

      3. 把多个文件合并到一个文件输出

         ```shell
         cat file1 file2 > file
         ```

   3. `-n`：显示文件内容时同时显示行号，包括空行

   4. `-b`：显示文件内容时显示行号，但不包括空行

   5. `-S`：当文件中有多个空行时，合并为一个空行

   6. `-E`：在显示内容时，结尾添加$符号

6. `cp` ：复制文件或目录（copy）

   1. 语法：`cp [options] [src_file] [des_file]` 
   2. `-f` ：force，强制复制文件或目录不进行提示
   3. `-r`：递归复制目录
   4. `-s`：为某个文件创建符号链接（软链接），而不是复制文件
   5. `-b`：覆盖已有的文件前，对目标文件进行备份
   6. `-l`：为文件创建硬链接，而不是复制文件
   7. `-p`：复制文件时保留文件的原有



# Shell

1. 广义上分为两类：
   1. GUI：包括GNOME，KDE，XFACE等
   2. CLI：包括sh，ksh，bash等（Linux发行版本中，bash是默认使用的shell程序）
2. shell启动：当用户登录完成后，系统会自动启动shell程序
   1. 某一个应用程序启动之后即会调用一个进程，通过PID区分（在系统中一个进程只认为自己存在）
   2. ？root、普通用户登录shell如何区分？

Linux的基本命令：

# 一.文件管理

## 1.文件查找：find

#### 使用方法

```
find [查找目录] [查找条件]

查找目录：
    .：在当前目录及子目录下查找（默认）
    A：在目录A及A的子目录下查找
查找条件：
    -name：根据文件名查找
    -regex：使用正则表达式匹配
    -type：按类型查找（f:文件，d:目录，l:链接...）
    -atime：按访问时间查找（n:n天前的一天内，+n:n天前(不含n天本身)，-n:n天内(不含n天)）
    -mtime：按修改时间查找（n:n天前的一天内，+n:n天前(不含n天本身)，-n:n天内(不含n天)）
    -size：按大小查找（单位k，+nk:"比nk更大"，-nk:"比nk更小"）
    -perm：按权限查找（644：权限等于644的文件）
    -user/-nouser：用户名等于/用户名不等于
    -group/-nogroup：组名等于/组名不等于
```

#### 示例

```
#1.在当前目录及子目录下查找后缀为cpp的文件
find . -name *.cpp

#2.使用正则表达式查找
find -regex ".*.cpp$"
```

## 2.文件拷贝：cp

#### 使用方法

```
cp [选项] 源路径 目的路径

选项：
    -a：将所有属性一起复制（包括拥有者、时间等信息）
    -i：目标文件存在时，进行询问
    -r：递归复制
```

## 3.打包解包：tar

#### 使用方法

```
tar [-j|-z] [cv] [-f 压缩包名] 目录
tar [-j|-z] [xv] [-f 解压包名] [-C 解压路径]

选项：
    -c/-x：打包/解包
    -j/-z：bzip2格式/gzip格式
    -v：显示过程
```

# 二.文本处理

## 1.(显示行号)查看文件：nl

行号计算不包括空行

## 2.文本查找：grep

#### 使用方法

```
grep [选项] 模式串 文件
输出 | grep [选项] 模式串

选项
    -e：使用多个模式串
    -i：忽略大小写
    -n：打印行号
    -c：统计次数（一行算一次）
```

#### 示例

```
#1.在test.c中搜索包含字符串”printf“或”count“的行
grep -e "printf" -e "count" test.c
```

## 3.排序：sort

#### 使用方法

```
sort [选项] 文件
输出 | sort [选项]

选项
    -d：按字典序排序（默认）
    -n：按数字排序
    -k："-k n"表示按各行第n列进行排序
    -r：反序
```

## 4.转换：tr

#### 使用方法

```
#set1、set2为字符集，可以是单个字符，也可以是字符串
输出 | tr [选项] set1 set2

选项：
    -d：删除字符
    -s：字符压缩
```

#### 示例

```
#1.删除字符':'
cat /etc/passwd | tr -d ':'

#2.将小写字母替换成大写字母
last | tr '[a-z]' 'A-Z'

#3.将'a'、'b'、'c'替换成'z'
cat test | tr “abc” 'z'

#4.将连续的'a'压缩成'b'（单个或连续出现的多个‘a’会压缩成一个‘b’）
cat test | tr -s 'a' 'b'
```

## 5.切分文本：cut

#### 使用方法

```
cut [选项] 文件
输出 | cut [选项]

选项：
    -d：分隔符（-d ':' 以’:‘为分隔符）
    -f：选择域（-f 1,2 输出分隔后第1列和第2列）
    -c：字符范围（-c n-m 输出第n到m个字符。如果没有m，输出到末尾）
```

#### 示例

```
#1.按’:‘分隔$PATH，输出第3个和第5个
echo $PATH | cut -d ':' -f 3,5

#2.输出export运行结果每行的第12-20个字符
export | cut -c 12-20
```

## 6.拼接文本：paste

#### 使用方法

```
paste [选项] file1 file2

选项：
    -d：指定拼接时使用的分隔符（默认使用tab作为分隔符）
```

## 7.统计：wc

#### 使用方法

```
wc [选项] 文件
输出 | wc [选项]

选项：
    -c：统计字符数
    -w：统计单词数
    -l：统计行数
```

## 8.数据处理：sed

> sed常用于一整行的处理。如果有一个100万行的文件，要在第100行加某些文字，此时由于文件太大，不适合用vim处理。因此使用sed是个很好的选择

#### 使用方法

```
sed [选项] '[动作]' 文件
输入 | sed [选项] '[动作]'

选项：
    -n：安静模式，只输出sed处理过的行（否则未处理行也会输出）
    -i：结果直接作用到文件（没指定时不会修改文件）
    -e：在命令行模式上输入动作
    -f：从文件中读取动作

动作：[n1[,n2]] function
function:
    a/i：在后插入/在前插入
    d：删除
    p：打印
    s：替换
```

#### 示例

```
#1.插入
nl /etc/passwd | sed '2a drink tea' #在第2行后插入一行："drink tea"
nl /etc/passwd | sed '2a aaa \
> bbb' #在第2行后插入两行："aaa"和"bbb"

#2.删除
nl /etc/passwd | sed '2,5d' #删除2~5行
sed '/^$/d' ip #将ip文件中的空行删除

#3.打印2~5行（安静模式，不使用安静模式2~5行会打印2次）
nl /etc/passwd | sed -n '2,5p'

#4.替换
nl /etc/passwd | sed '2s/daemon/root/g' #将第二行的daemon替换成root
ifconfig | grep 'inet addr' | sed 's/^.*addr://g' #将所有开头的“inet addr:”删除
```

## 9.数据处理：awk

> 相比于sed常用于一整行的处理，awk则比较倾向于将一行分成数个“字段”来处理。因此，相当适合小型的数据处理

**awk处理步骤**：

1. 读入第一行，并将第一行的数据填入$0,$1,$2等变量当中
2. 依据条件类型的限制，判断是否需要进行后面的动作
3. 做完所有的动作与条件类型
4. 若还有后续的“行”的数据，则重复1~3步，直到所有的数据都读完为止

#### 使用方法

```
awk '条件类型1{动作1} 条件类型2{动作2} ...' filename
输出 | awk '条件类型1{动作1} 条件类型2{动作2} ...'

变量：
    $0：整行
    $1：按分隔符分隔后的第1列
    $2：按分隔符分隔后的第2列
    $k：按分隔符分隔后的第k列
    NF：每一行拥有的字段数
    NR：目前所处理的行数
    FS：目前的分隔字符（默认是空格或tab）
条件判断：>、<、>=、<=、==、!=
命令分隔：使用';'或Enter
```

#### 示例

```
#1.打印last -n 5结果中每行经过分隔符(默认情况下为空格或tab)分隔后的第1列和第3列
last -n 5 | awk '{print $1 "\t" $3}'

#2.以':'作为分隔符，打印第3列小于10的所有行的第1列和第3列
cat /etc/passwd | awk '{FS=":"} $3<10{print $1 "\t" $3}'      #（第一行不会处理）
cat /etc/passwd | awk 'BEGIN{FS=":"} $3<10{print $1 "\t" $3}' #（第一行会处理）

#3.假设test文件由3列数字组成，以空格分隔。该命令会计算每行的和然后打印
awk '{total=$1+$2+$3;printf "%10d %10d %10d %10.2f\n",$1,$2,$3,total}' test
```

注意上面的示例2，awk首先是读取一行，分隔后的数据填入$0,$1,$2等变量中才开始进行条件判断和执行动作。因此第一条命令在按空格或tab分隔后才将分隔符换成':'，所以第一行显示结果不对

# 三.性能分析

## 1.进程查询：ps

man ps手册非常庞大，不是很好查阅，因此主要记住几个命令

#### 示例

```
#1.列出仅与自身环境有关的进程，最上层的父进程是允许该ps命令的bash而没有扩展到init进程中去
ps -l

#2.列出系统所有进程的信息
ps aux
ps -ef    #aux会截断COMMAND列，-ef不会。aux是BSD风格，-ef是System V风格
ps axjf   #以"进程树"的方式显示所有进程
ps -lA    #输出格式同ps -l
```

 ![img](https://github.com/ID-Q/note-1/raw/master/pic/linux-ps-1.png)

**F**：进程标志，说明进程的权限

- 4：root权限
- 1：仅能fork而不能exec
- 0：既非4也非1

# socket

1、**创建**：

```c
int socket(int domain, int type, int protocol);
domain:
	AF_INET, AF_INET6, AF_LOCAL, AF_ROUTE
type:
	SOCK_STREAM, SOCK_DGRAM, SOCK_PACKET, SOCK_SEQPACKET
protocol:
	IPPROTO_TCP, IPPTOTO_UDP, IPPROTO_STCP, IPPROTO_TIPC
返回值：socket文件描述符
```

2、**绑定：**

```c
int bind(int sockfd, const struct sockaddr *addr, socketlen_t addrlen);
	sockfd是调用socket返回的文件描述符
	add是指向数据结构struct sockaddr的指针，它保存你的地址（即端口和IP地址）信息
	addrlen设置为sizeof(struct sockaddr)
返回值：-1为错误，并设置全局变量errno
```

3、[**全局变量errno详解：**](http://c.biancheng.net/c/errno/)

4、





## 线程

转：https://blog.csdn.net/qq_38289815/article/details/82950320

### 创建及注销线程相关操作：

#### 1、**创建线程：**

```c
int pthread_create (pthread_t *thread, const pthread_attr_t *attr, void *(*start_routine) (void *), void *arg);
功能：创建一个具有指定参数的线程
形参：
	thread是要创建的线程的线程ID指针
	pthread_t类型的定义是typedef unsigned long int pthread_t;(打印时要使用%lu或%u方式)
	attr：创建线程时的线程属性(设置NULL表示使用默认线程属性)
	start_routine：指向的是新线程将运行的函数。线程一旦被创建好，内核就可以调度内核线程来执行start_routine函数指针所指向的函数了
	arg：指向的是运行函数的形参
返回值：若是成功建立线程返回0,否则返回错误的编号
```

#### 2、等待线程结束：

```c
int pthread_join(pthread_t thread, void **retval);
功能：这个函数是一个线程阻塞的函数，调用它的函数将一直等待到被等待的线程结束为止，当函数返回时，被等待线程的资源被收回
形参：
	thread是被等待的线程标识符。
	retval：一个用户定义的指针，它可以用来存储被等待线程的返回值。
返回值：成功返回0,否则返回错误的编号。
错误码：
	①EDEADLK：可能引起死锁，比如两个线程互相针对对方调用pthread_join，或者线程对自身调用pthread_join。
	②EINVAL：目标线程是不可回收的，或者已经有其他线程在回收目标线程。
	③ESRCH：目标线程不存在。
```

#### 3、线程退出：

```c
void pthread_exit(void *retval);
功能：线程函数在结束时调用此函数，以确保安全、干净地退出。
形参：
	retval是函数的返回指针，只要pthread_join中的第二个参数retval不是NULL，这个值将被传递给retval。	pthread_exit函数通过retval参数向线程的回收者传递其退出信息。他执行完之后不会返回到调用者，而且永远不会失败。
```

#### 4、线程取消：

```c
int pthread_cancel(pthread_t thread);
功能：取消某个线程的执行。
形参：thread是要取消线程的标识符ID。
返回值：若是成功返回0,否则返回错误的编号。
但是，接收到取消请求的目标线程可以决定是否允许被取消以及如何取消，这分别由如下两个函数完成。
	int pthread_setcancelstate(int state, int *oldstate);
	int pthread_setcanceltype(int type, int *oldtype);
这两个函数的第一个参数分别用于设置线程的取消状态(是否允许取消)和取消类型(如何取消)，第二个参数则分别记录线程原来的取消状态和取消类型。
state参数有两个可选值：
	PTHREAD_CANCEL_CNABLE，允许线程被取消。它是线程被创建时的默认取消状态。
	PTHREAD_CANCEL_DISABLE，禁止线程被取消。这种情况下，如果一个线程收到取消请求，则它会将请求挂起，直到该线程允许被取消。
type参数也有两个可选值：
	PTHREAD_CANCEL_ASYNCHRONOUS，线程随时都可以被取消。它将使得接收到取消请求的目标线程立即采取行动。
	PTHREAD_CANCEL_DEFERRED，允许目标线程推迟行动，直到它调用了下面几个所谓的取消点函数中的一个：pthread_join、pthread_testcancel、pthread_cond_wait、pthread_cond_timedwait、sem_wait和sigwait。根据POSIX标准，其他可能阻塞的系统调用，比如read、wait，也可以成为取消点。不过为了安全起见，最好在可能会被取消的代码中调用pthread_testcancel函数设置取消点。
```

#### 5、获取当前线程ID：

```c
pthread_t pthread_self (void);
功能：获取当前调用线程的线程ID。
返回值：当前线程的线程ID标识。
```

#### 6、分离释放线程：

```c
int pthread_detach (pthread_t thread);
功能：线程资源释放方式设置函数。
形参：thread是要释放线程的标识符ID。
返回值：若是成功返回0,否则返回错误的编号。
其他说明：linux线程执行和windows不同，pthread有两种状态joinable状态和unjoinable状态。一个线程默认的状态是joinable，如果线程是joinable状态，当线程函数自己返回退出时或pthread_exit时，都不会释放线程所占用堆栈和线程描述符（总计8K多），只有当调用了pthread_join之后这些资源才会被释放。若是unjoinable状态的线程，这些资源在线程函数退出时或pthread_exit时自动会被释放。unjoinable属性可以在pthread_create时指定，或在线程创建后在线程中pthread_detach自己设置，如：						 	pthread_detach(pthread_self())，将状态改为unjoinable状态，确保资源的释放。如果线程状态为joinable，需要在之后适时调用pthread_join。
```

#### 7、比较两个线程是否为同一线程：

```c
int pthread_equal (pthread_t thread1, pthread_t thread2);
功能：判断两个线程ID是否是同一个。
形参：
	thread1是要比较的线程的标识符ID1；
	thread2是要比较的线程的标识符ID2。
返回值：不相等返回0，相等非零。
```

#### 8、创建线程私有数据：

```c
int pthread_key_create (pthread_key_t *key, void (*destr_function) (void *));
功能：创建线程私有数据TSD，提供线程私有的全局变量。使用同名而不同内存地址的线程私有数据结构。
形参：
	Key是线程私有数据。
	第二个参数：如果第二个参数不为空，在线程退出时将以key所关联数据为参数调用其指向的资源释放函数，以释放分配的缓冲区。
其他说明：不论哪个线程调用pthread_key_create()函数，所创建的key都是所有线程可访问的，但各个线程可根据自己的需要往key中填入不同的值 相当于提供了同名不同值的全局变量,各线程对自己私有数据操作互相不影响。
```

#### 9、注销线程私有数据：

```c
int pthread_key_delete (pthread_key_t *key);
该函数并不检查当前是否有线程正是用该TSD，也不会调用清理函数(destr_function) 将TSD释放以供下一次调用pthread_key_create()使用。
```

#### 10、读写线程私有数据：

```c
int pthread_setspecific (pthread_key_t key, const void *pointer); //写
void pthread_getspecific (pthread_key_t key); //读
函数pthread_setspecific()将pointer的值(非内容)与key相关联。函数pthread_getspecific()将与key相关联的数据读出来。所有数据都设置为void *，因此可以指向任何类型的数据。
```

### 线程属性操作：

#### 1、初始化线程对象属性：

```c
int pthread_attr_init (pthread_attr_t *attr);
功能：pthread_attr_init实现时为属性对象分配了动态内存空间。
形参：attr是指向一个线程属性的指针。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 2、销毁线程对象属性：

```c
int pthread_attr_destroy (pthread_attr_t *attr);
功能：经pthread_attr_destroy去除初始化之后的pthread_attr_t结构被pthread_create函数调用，将会导致其返回错误。只有再次初始化后才能继续使用。
形参：attr是指向一个线程属性的指针。
```

#### 3、获取线程分离状态属性：

```c
int pthread_attr_getdetachstate (pthread_attr_t *attr, int *detachstate);
功能：获取线程分离状态属性；另外，pthread_detach()是分离释放线程资源函数
形参：
	attr是指向一个线程属性的指针。
	detachstate：保存返回的分离状态属性。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 4、修改线程分离状态属性：

```c
int pthread_attr_setdetachstate (pthread_attr_t *attr, int detachstate);
功能：修改线程分离状态属性。
形参：attr是指向一个线程属性的指针。
detachstate：其含义是线程的脱离状态，它有两个可选值，分别是PTHREAD_CREATE_JOINABLE（可连接）以及PTHREAD_CREATE_DETACHED(分离)。前者指定线程是可以被回收的，后者使调用线程脱离与进程中其他线程同步。脱离了与其他线程同步的线程成为”脱离线程”。脱离线程在退出时将自行释放其占用的系统资源。线程创建时该属性的默认值是PTHREAD_CREATE_JOINABL。此外，我们可以使用pthread_detach函数直接将线程设置为脱离线程。(上述detachstate的含义相同，之后相同含义的参数，都只介绍一次)
返回值：若是成功返回0,否则返回错误的编号。
```

#### 5、获取线程的CPU亲缘性：

```c
int pthread_attr_getaffinity_np (pthread_attr_t *attr, size_t cpusetsize, cpu_set_t *cpuset);
功能：获取线程的CPU亲缘属性。
形参：attr是指向一个线程属性的指针。
cpusetsize：指向CPU组的缓冲区大小。
cpuset：指向CPU组的指针。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 6、设置线程CPU亲缘性：

```c
int pthread_attr_setaffinity_np (pthread_attr_t *attr, size_t cpusetsize, const cpu_set_t *cpuset);
功能：通过指定cupset来设置线程的CPU亲缘性。
形参：attr是指向一个线程属性的指针。
cpusetsize：指向CPU组的缓冲区大小。
cpuset：指向CPU组的指针。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 7、获取线程的作用域：

```c
int pthread_attr_getscope (const pthread_attr_t *attr, int *scope);
功能：指定了作用域也就指定了线程与谁竞争资源。
形参：attr是指向一个线程属性的指针；scope是返回线程的作用域。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 8、设置线程的作用域：

```c
int pthread_attr_setscope (pthread_attr_t *attr, int scope);
功能：指定了作用域也就指定了线程与谁竞争资源
形参：attr是指向一个线程属性的指针。
scope：线程间竞争CPU的范围，即线程优先级的有效范围。POSIX标准定义了该属性可以取以下两个值：PTHREAD_SCOPE_SYSTEM和PTHREAD_SCOPE_PROCESS，前者表示目标线程与系统中所有线程一起竞争CPU的使用，后者表示目标线程仅与其他隶属于同一进程的线程竞争CPU的使用。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 9、获取线程的栈保护区大小：

```c
int pthread_attr_getguardsize (const pthread_attr_t *attr, size_t *guardsize);
功能：获取线程的栈保护区大小。
形参：
	attr是指向一个线程属性的指针。
	guardsize：返回获取的栈保护区大小。
返回值：若是成功返回0,否则返回错误的编号
```

#### 10、设置线程的栈保护区大小：

```c
int pthread_attr_setguardsize (pthread_attr_t *attr, size_t *guardsize);
功能：参数提供了对栈指针溢出的保护。默认为系统页大小。
形参：attr是指向一个线程属性的指针。
guardsize：线程的栈保护区大小。如果guardsize大于0，则系统创建线程的时候会在其堆栈的尾部额外分配guardsize字节的空间，作为保护堆栈不被错误地覆盖的区域。如果guardsize等于0，则系统不为新创建的线程设置堆栈保护区。如果使用者通过pthread_attr_setstack()或pthread_attr_setstackaddr()函数手动设置线程的堆栈，则guardsize属性将被忽略。
返回值：若是成功返回0,否则返回错误的编号。
```

11、获取栈的堆栈信息（栈地址和栈大小）：

```c
int pthread_attr_getstack (const pthread_attr_t *attr, void **stackaddr, size_t *stacksize);
功能：获取线程的堆栈地址和大小。
形参：
	attr是指向一个线程属性的指针。	
	stackaddr：返回获取的栈地址。
	stacksize：返回获取的栈大小。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 12、设置线程的堆栈区：

```c
int pthread_attr_setstack (pthread_attr_t *attr, void *stackaddr, size_t stacksize);
功能：设置堆栈区，将导致pthread_attr_setguardsize失效。
形参：
	attr是指向一个线程属性的指针。
	stackaddr：线程的堆栈地址，应该是可移植的，对齐页边距的，可以用posix_memalign来进行获取。
	stacksize：线程的堆栈大小，应该是页大小的整数倍。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 13、获取线程堆栈地址：

```c
int pthread_attr_getstackaddr (const pthread_attr_t *attr, void **stackaddr);
功能：一般用pthread_attr_getstack来代替。
形参：attr是指向一个线程属性的指针；stackaddr是返回获取的栈地址。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 14、设置线程堆栈地址：

```c
int pthread_attr_setstackaddr (pthread_attr_t *attr, void *stackaddr);
功能：一般用pthread_attr_setstack来代替。
形参：
	attr是指向一个线程属性的指针；stackaddr是设置线程堆栈地址。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 15、获取线程堆栈大小：

```c
int pthread_attr_getstacksize (const pthread_attr_t *attr, size_t *stacksize);
功能：获取线程堆栈大小。
形参：attr是指向一个线程属性的指针；stacksize是返回线程的堆栈大小。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 16、设置线程堆栈大小：

```c
int pthread_attr_setstacksize (pthread_attr_t *attr, size_t stacksize);
功能：设置线程堆栈大小。
形参：
	attr是指向一个线程属性的指针。
	stacksize：设置线程的堆栈大小,stack属性的合法值包括PTHREAD_STACK_MIN，该线程的用户栈大小将使用默认堆栈大小，为某个线程所需最小堆栈大小，但对于所有线程，这个大小可能无法接受，具体指定的大小，即使用线程的用户堆栈大小的数值，必须不小于最小堆栈大小PTHREAD_STACK_MIN。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 17、获取线程的调度策略：

```c
int pthread_attr_getschedpolicy (const pthread_attr_t *attr, int *policy);
功能：获取线程的调度策略。
形参：
	attr是指向一个线程属性的指针；
	policy是返回线程的调度策略。
返回值：若是成功返回0,否则返回错误的编号。
按照如下方法使用sched_get_priority_max()和sched_get_priority_min()，可以得到优先级的最大值和最小值。 
头文件：#include <pthread.h> #include <sched.h>
调用形式：
	#include <sched.h>
	int sched_get_priority_max(int policy);
	int sched_get_priority_min(int policy);
```

#### 18、设置线程调度策略：

```c
int pthread_attr_setschedpolicy (pthread_attr_t *attr, int policy);
头文件：
	#include <pthread.h> 
	#include <sched.h>
功能：设置线程的调度策略。
形参：
	attr是指向一个线程属性的指针。
	policy：线程的调度策略，POSIX指定了3种调度策略属性：SCHED_FIFO表示先入先出策略，SCHED_RR表示轮转调度(这两种调度方法都具备实时调度功能，但只能用于以超级用户身份运行的进程)，SCHED_OTHER是系统默认策略，SCHED_OTHER是不支持优先级使用的。SCHED_FIFO和SCHED_RR支持优先级的使用，它们分别为1和99，数值越大优先级越高。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 19、获取线程的调度参数：

```c
int pthread_attr_getschedparam (const pthread_attr_t *attr, struct sched_param *param);
头文件：#include <pthread.h> #include <sched.h>
功能：获取线程的调度参数。
形参：
	attr是指向一个线程属性的指针；
	param是返回获取的调度参数。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 20、设置线程的调度参数：

```c
int pthread_attr_setschedparam (pthread_attr_t *attr, const struct sched_param *param);
头文件：
	#include <pthread.h> 
	#include <sched.h>
功能：设置线程的调度参数，用于设置优先级。
形参：
	attr是指向一个线程属性的指针。
	param：要设置的调度参数，其类型是sched_param结构体。至少需要定义这个数据成员
struct sched_param
{ 
    int sched_priority; 
    /*该成员表示线程运行优先级*/
};
sched_param可能还有其他的数据成员，以及多个用来返回和设置最小优先级、最大优先级、调度器、参数等的函数。如果调度策略是SCHED_FIFO或SCHED_RR，那么要求具有值的唯一成员是sched_priority。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 21、获取线程是否继承调度属性：

```c
int pthread_attr_getinheritsched (const pthread_attr_t *attr, int *inheritsched);
头文件：#include <pthread.h> #include <sched.h>
功能：获取线程是否继承调度属性。
形参：attr是指向一个线程属性的指针；inheritsched是返回继承调度属性的设置。
返回值：若是成功返回0,否则返回错误的编号。
```

#### 22、设置线程继承调度属性：

```c
int pthread_attr_setinheritsched (pthread_attr_t *attr, int inheritsched);
头文件：#include <pthread.h> #include <sched.h>
功能：设置线程是否继承调度属性。
形参：
	attr是指向一个线程属性的指针。
	Inheritsched：设置线程是否继承调用线程的调度属性，可能取值如下：
	PTHREAD_INHERIT_SCHED表示新线程沿用其创建者的线程调度参数，这种情况下再设置新线程的调度参数属性将没有任何效果。PTHREAD_EXPLICIT_SCHED表示调用者要明确地指定新线程的调度参数。
返回值：若是成功返回0,否则返回错误的编号。
```







# 鸟哥的LINUX私房菜

1. 计算器：输入->处理->输出
2. 输入->主存储器->CPU->输出
3. 

