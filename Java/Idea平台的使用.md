### Idea（Java集成）平台的使用

### 1、优化IDEA开发环境

![1551318586487](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318586487.png)

![1551318608746](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318608746.png)

#### 1.1、自动提示

关闭代码提示的大小写匹配，提高开发效率；启动方法参数名称提示

![1551318632906](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318632906.png)

启动鼠标悬浮在代码时的API文档提示

![1551318644566](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318644566.png)

#### 1.2、字体样式

自定义代码字体样式及尺寸

![1551318669509](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318669509.png)

#### 1.3、Maven

基于Maven的项目第三方库依赖管理，maven首先从本地仓库查找依赖，没有则通过网络从远程仓库下载，因此，**第一次添加某依赖时，保持联网状态**

创建maven本地仓库目录，例如，D:/m2/repository，复制setting.xml配置文件至m2目录

![1551318769413](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318769413.png)

用记事本打开配置文件，并修改localRepository标签中的本地仓库目录。配置中添加了国内阿里镜像服务器

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    
<mirror>  
    <id>nexus-aliyun</id>  
    <mirrorOf>central</mirrorOf>    
    <name>Nexus aliyun</name>     				              <url>http://maven.aliyun.com/nexus/content/groups/public</url> 
</mirror>
  <localRepository>D:/m2/repository</localRepository>
</settings>
```

Idea默认集成maven，直接导入maven配置即可；默认的本地仓库目录变为了配置中声明的目录

![1551318853836](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318853836.png)

当添加依赖声明时，自动从远程服务器仓库下载![1551318871331](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318871331.png)	

#### 1.4、绑定github

![1551318903952](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318903952.png)

#### 1.5、安装Lombok插件

Lombok可极大的简化开发代码，但需与开发工具结合使用。因此idea需安装lombok插件

![1551318932516](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318932516.png)

重启idea

#### 1.6、重置

关闭idea，删除以下文件夹，即可重置设置 ；C:\Users\你的用户名\IntelliJIdea2018.3

![1551318975192](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551318975192.png)

### 2、第一个Java工程

创建合适的工作区目录，例如，d:/workspace-2019，用于存放工程文件，目录不要使用中文命名

#### 2.1、创建一个基本的idea工程

![1551319037920](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319037920.png)

Idea中，一个project(工程)由若干独立的module(模块)组成。

例如，一个project可以包含一个基于移动端android的module，一个基于前端vue的module，以及一个同时为移动端前端提供支持，基于springboot的后端微服务module。分别的开发测试部署可以极大的提高应用的复用性，同时降低应用的耦合性。

因此，即使当前project仅包含一个module，也养成创建独立module的习惯，也便于后期扩展

无任何依赖框架的基本java工程

![1551319067156](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319067156.png)

无需模板

![1551319076057](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319076057.png)

声明project名称，声明一个与project名称不同的module名称

创建module javaexamples，自动在工作区下/工程下下，创建拥有独立目录的module，后期可平行创建更多module

![1551319087182](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319087182.png)

打开project中javaexamples module，在src下，右键创建java class，在名称中直接声明包与类名称

![1551319095771](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319095771.png)

main()主函数快捷代码，psvm；输出快捷代码，sout；主函数左侧的运行箭头，运行程序

![1551319110513](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319110513.png)

构建，编译，运行程序后，在控制台输出

![1551319119894](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319119894.png)

#### 2.2、添加git版本控制支持

在工程下创建，README.md，工程描述文件，非module描述文件，因此应创建在工程下

切换到project file视图模式

![1551319154578](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319154578.png)

输入工程描述信息，具体md文件语法

<https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>

为本工程添加支持git版本控制的本地代码仓库

![1551319178648](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319178648.png)

定位到project，而非module

![1551319192806](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319192806.png)

Idea下部工具条，出现version control视图，可查看工程版本控制历史，当前提交/未提交文件等等

![1551319203214](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319203214.png)

提交本次修改

![1551319211513](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319211513.png)

确定本次需记录的修改文件，默认需全部选中。未选中的文件，将不再本次版本控制中记录；同时必须输入本次提交描述

![1551319219669](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319219669.png)

提交后，可查看到本次提交的节点

![1551319226759](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319226759.png)

Git会生成隐藏目录，维护监测代码变化

![1551319235155](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319235155.png)

#### 2.3、push到github

当前代码仅在本地仓库，需要推送到支持git的远程代码仓库，与他人分享协作开发

1.可以在github创建代码仓库，再通过idea提交更新；与clone相同

2.也可以通过idea直接在github创建仓库 

通过浏览器登录github查看，当前没有springbootproject工程仓库

​         ![1551319306847](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319306847.png)                                         

 选择share project on github

![1551319321180](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319321180.png)

确定github远程仓库名称，不能冲突，建议与工程名称相同

​                       ![1551319329828](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319329828.png)                          

Push成功后(可能连接超时，重试)，github自动创建指定仓库

![1551319352707](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319352707.png)

可通过浏览器查看工程代码已同步到github远程仓库

![1551319360793](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319360793.png)

#### 2.4、删除工程

关闭当前工程，返回idea主页面

![1551319385098](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319385098.png)

删除指定工程。但idea不会删除磁盘上的工程文件，也不会删除github远程仓库

![1551319411823](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319411823.png)

进入工作区目录，手动删除工程文件目录

![1551319420349](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319420349.png)

#### 2.5、Clone工程

本地已删除springbootproject工程，将github远程仓库中的工程clone到本地

通过浏览器查看github仓库，选中通过URL地址clone到本地，复制地址

![1551319442619](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319442619.png)

在idea主页面，选中通过版本控制方式导入工程，提供github仓库地址，以及本地工作区目录，测试工程连接

![1551319449791](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319449791.png)

远程下载代码，并创建本地目录

![1551319459820](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319459820.png)

通过左侧project窗口打开查看从github远程仓库加载的工程

![1551319467070](C:\Users\tiger\AppData\Roaming\Typora\typora-user-images\1551319467070.png)