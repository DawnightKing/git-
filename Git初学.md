---
typora-root-url: ..\01.Git初学图片
---

# 版本控制

版本控制就是*版本迭代*，新的版本

>常见的版本控制工具

主流版本控制器：

 - Git
 - SVN(Subversion)
 - CVS(Concurrent Versions System)
 - VSS(Microsoft Visual SourceSafe)
 - TFS(Team Foundation Server)
 - Visual Studio Online


现在影响最广的是Git与SVN

>版本控制分类

 1. 本地版本控制
记录文件每次更新，可以对每个版本做一会快照，或记录补丁文件，适用于个人，如RCS。
 2. 集中版本控制 SVN
所有数据都保存在服务器上，必须联网，协同开服者从**中央服务器**上同步更新或上传自己的修改。
 3. 分布式版本控制 Git
每个人都拥有全部的代码！有安全隐患！但不会因为服务器问题造成无法工作的现象。

>Git和SVN的区别

SVN是集中式版本控制系统，版本库是集中放置在中央服务器的，而工作的时候用的都是自己的电脑，所以首先要中心服务器得到最新的版本，然后工作，完成工作后，需要把自己做完活推送到中央服务器中。集中式版本控制系统必须要在联网的条件下进行，对网络需求非常高。

Git是分布式版本控制系统，没有中央服务器，每个人的电脑就是一个完整的版本库，工作的时候不需要联网，因为版本都在自己的电脑里。协同的方法是：比如说自己的电脑上该了文件A，其他人也在电脑上改了文件A，这时，只需要把各自的修改推送给对方，相互之间就可以看到了。Git可以直接看到更新了哪些代码和文件。

# Git历史

Git是目前世界上最先进的**分布式版本**控制系统。

Git的免费的，开源的，最初Git是为赋值Linux内核开发的，来代替BitKeeper

Linux和Git之父李纳斯·托沃兹（Linux Benedic Torvalds）1969 芬兰

# Git配置

> 下载Git

搜索Git官网，直接下载，或者寻找国内镜像网站下载http://npm.taobao.org/mirrors/git-for-windows/（速度较快）

无脑下一步安装

>先卸载

反安装

清理环境变量相关配置

卸载软件，Git

> 启动Git

安装成功后，右击可以看到

Git GUI 和 Git Bush

或者

![image-20210711180624900](F:\笔记\01.Git初学\Git初学\image-20210711180624900.png)

**Git Bash：**Unix与Linux风格命令行，使用最多，推荐最多

**Git CMD：**Windows风格的命令行

**Git GUI：**图形界面的Git，不建议销售使用，优先熟悉命令行语句

> 基本的Linux命令学习

1. cd ：改变目录

2. cd  .. :回退到上级目录

3. pwd :显示当前所在目录路径

4. ls(ll) :都是列出当前目录，含ll的更加具体

5. touch :新建一个文件夹，如touch index.js会在当前目录新建一个为index.js的文件夹

6. rm :删除文件夹，用法rm index.js

7. mkdir :新建一个新的文件夹

8. rm -r :删除一个文件夹

   `rm -rf / 切勿在Linus中尝试！递归删除系统中所有文件`

9. mv :移动文件夹，用法：`mv index.html test /把index.html移动到同根目录下的test文件夹下`

   `mv hello.txt src index.html /把hello.txt文件移动到src所指向的目标文件夹中，这样写必须保证文件和目标文件夹同名`

10. reset :重新初始化终端/清屏

11. clear :清屏

12. history :查看命令历史

13. help :帮助

14. exit :退出

15. #表示注释

> Git的配置

查看配置 `git config -l`

![image-20210711212402030](F:\笔记\01.Git初学\Git初学\image-20210711212402030.png)

查看不同级别的配置信息

```
#查看系统config
git config --system --list
#查看当前用户配置信息（global）
git config --global --list
```

**Git相关的配置信息：**

1.Git\etc\gitconfig:Git安装目录下的gitconfig --system 系统级

![image-20210711215548779](F:\笔记\01.Git初学\Git初学\image-20210711215548779.png)

2.C: \Users\Administrator\.gitconfig 当前登录用户的配置 --global 全局

> 设置用户名和邮箱（用户标识必须要配置）

当我安装Git后首先要做的事情是设置我的用户名和email信息。这非常重要，每次Git提交时，都会嵌入到提交的数据中去：

```
git config --global user.name "Dawnight_King" #名称

git config --global user.email Dawnight_King@163.com #邮箱
```

--global为全局变量配置设置，设置完一次后可以一劳永逸。如果有些特定项目需要制定邮箱地址或不同的名称，不要加--global就可以

![image-20210711214121380](F:\笔记\01.Git初学\Git初学\image-20210711214121380.png)

linux中所以的配置文件都在etc中

# Git基本理论（核心）

>工作区域

![image-20210805174803217](F:\笔记\01.Git初学\Git初学\image-20210805174803217.png)

- Workspace：工作区，平时存放项目代码的地方

- Index / Stage : 暂存区，就是一个文件，保存变动后内容的文件

- Repository ： 仓库区（本地仓库区），有提交到所有版本的数据，head指向的是最新放入仓库版本。

- Remote ：远程仓库，托管代码的服务器

>工作流程

Git工作流程：

1.在工作目录中添加修改文件； UserMapper.xml

2.将需要进行版本管理的文件放入暂存区域；git add

3.将暂存区域的文件提交到仓库； git commit

> 常用语句

- `git init`

  在电脑创建全新的仓库![image-20210818150442296](/../01.Git初学/Git初学/image-20210818150442296.png)

- `git clone [url]`

  远程克隆仓库

# git文件版本变更&回退

## 添加文件

```
#查看指定文件状态
git status [filer]

#查看所有文件状态
git status

#添加入暂存区
git add .

#添加到仓库
git commit -m "[new file ]"

#显示提交日志信息
git log
```

1.git add .**添加到暂存区**

![image-20210818153218235](F:\笔记\01.Git初学\Git初学\image-20210818153218235.png)

2.git status查看文件状态

![image-20210818153344884](/../01.Git初学/Git初学/image-20210818153344884.png)

3.git commit -m **提交到git仓库**

![image-20210818153715225](/../01.Git初学/Git初学/image-20210818153715225.png)

4.再次常看git仓库状态

![image-20210818153815040](/../01.Git初学/Git初学/image-20210818153815040.png)

## 版本回退

1.查看日志查找版本标识

`git log`

![image-20210818171930810](/../01.Git初学/Git初学/image-20210818171930810.png)

简化日志显示方式

`git log -5 --pretty=oneline`

![image-20210818181935272](/../01.Git初学/Git初学/image-20210818181935272.png)

```
git reset HEAD #默认回退
```

![image-20210818165916525](/../01.Git初学/Git初学/image-20210818165916525.png)

```
#表达方法一：
git reset --hard HEAD^ #回退到上一个操作版本
git reset --hard HEAD^^ #回退到上上个操作版本

#表达方法二：
git reset --hard HEAD~5#回退到上第五个版本

#从过去的版本回到未来的版本就应用版本标识符
git reset --hard [版本标识符]
```

![image-20210818170611773](/../01.Git初学/Git初学/image-20210818170611773.png)

回退到指定版本

![image-20210818182523946](/../01.Git初学/Git初学/image-20210818182523946.png)

![image-20210818182540005](/../01.Git初学/Git初学/image-20210818182540005.png)

## 查看文件变更足迹

1.执行`git diff HEAD -- [filer]`与版本内容进行比较。

差异比较说明：

’---‘ ：表示变动前的文件

'+++'：表示变动后的文件

变动位置用两个@作为起始和结束

![image-20210818164606612](/../01.Git初学/Git初学/image-20210818164606612.png)

2.查看记录在本地的Head和分支引用过去指向的位置

​	`git reflog`

![image-20210818182821658](/../01.Git初学/Git初学/image-20210818182821658.png)

## 删除文件

1.在本地文件中对已有文件进行删除

查看状态：![image-20210818183531746](/../01.Git初学/Git初学/image-20210818183531746.png)

此时只是本地的一个误删除，但Git中并未删除，可通过`git checkout -- [filer]`对文件进行修复

![image-20210818183835115](/../01.Git初学/Git初学/image-20210818183835115.png)

2.对Git执行删除操作`git rm [文件名]`

![image-20210818184241943](/../01.Git初学/Git初学/image-20210818184241943.png)

#  远程仓库

1.克隆远程项目到本地



## 忽略文件

上传git可忽略内容：数据库文件，临时文件，设计文件

在主目录下创建“`.gitignore`”文件规则如下：

```md
#为注释内容
*.txt  #忽略所有以txt结尾的文件
!lib.txt  #但lib.txt除外
/temp  #仅忽略项目根目录下的TODO文件，不包括其他目录temp
build/  #忽略build/目录下所有的文件
doc/*.txt    #会忽略 doc/notes.txt但不包括 doc/server/arch.txt
```



