# Git分布式版本管理工具

## Git概述

​	Git是一个免费的，开源的$\textcolor{#f08d49}{分布式版本控制系统}$，可以快速高效的处理从小型到大型的各种项目。

​	Git易于学习，占地面积小，性能极快。它具有廉价的本地仓库，方便的暂存区域和多个工作流分支等特性。其性能优于Subversion，CVS，perforce 和 ClearCase等版本控制工具

​	官网：https://git-scm.com/

### 	版本控制：

​	版本控制是一种记录文件内容变化，以便将来查阅特定版本修订情况的系统。

​	版本控制其实最重要的的是可以记录文件修改历史记录，从而让用户能够查看历史版本，方便版本切换。 

### 	问什么需要版本控制：

​		是从个人开发过渡到团队协作。

![image-20230306102617492](./assets/image-20230306102617492.png)

### 	版本控制工具：

1.  集中式版本控制工具

    ​	CVS，SVN（Subversion），VSS....

    ​	集中式版本控制系统诸如CVS，SVN等，都有一个单一的集中管理的服务器，保存所有文件的修订版本，而携同工作的人们都通过科幻段连接到这台服务器，取出最新的文件或者提交更新。多年以来，这已成为版本控制系统的标准做法。

    ​	这种做法带来了许多好处，每个人都可以在一定程度上看到项目中的其他人正在做什么。而管理员也可以轻松掌控每个开发者的权限，并且管理一个集中话的版本控制系统，需要远比在各个客户端上维护本地数据库来的轻松容易

    ​	事分两面，有好有坏。这么做显而易见的缺点是中央服务器的单点故障。如果服务器宕机一小时，那么在这一小时内，准都无法提交更新，也就无法协同工作。

    ![image-20230306110200862](./assets/image-20230306110200862.png)

2.  分布式版本控制工具

    Git，Mercurial，Bazaar，Darcs......

​		像Git这种分布式版本控制工具，客户端提取的不是最新版本的文件快照，而是把代码仓库完整的镜像下来（本地库）。这样任何一处协同工作用的文件发生故障，事后都可以用其他客户端的本地仓库进行恢复。因为每个客户端的每一次文件提取操作，时机上都是一次对整个文件仓库的完整备份。

​		分布式的版本控制系统出现之后，解决了集中式版本控制系统的缺陷：

1.  服务器断网的情况下也可以进行开发（因为版本控制在本地进行的）

2.  每个客户端保存的也是整个完整的项目（包含历史记录，更加安全）

    ![image-20230306111757228](./assets/image-20230306111757228.png)

### 		Git简史

![image-20230306112253938](./assets/image-20230306112253938.png)

### 	Git工作机制：

![image-20230306112850150](./assets/image-20230306112850150.png)

### 	Git和代码托管中心：

​			代码托管中心是基于网络服务器的远程代码仓库，一般我们简单称为$\textcolor{#f08d49}{远程库}$

1.  局域网
    1.  GitLab
2.  互联网
    1.  GitHub（外网）
    2.  Gitee码云（国内网站）

## Git安装

​	官网地址：https://git-scm.com/

![image-20230306135604377](./assets/image-20230306135604377.png)

   选择Git安装位置，要求是非中文并且没有空格的目录，然后下一步。

![image-20230306135712051](./assets/image-20230306135712051.png)

Git选项配置，推荐默认设置，然后下一步。

![image-20230306135809547](./assets/image-20230306135809547.png)

Git安装目录名，不用修改，直接点击下一步

![image-20230306135936479](./assets/image-20230306135936479.png)

![image-20230306140049624](./assets/image-20230306140049624.png)

![image-20230306140457488](./assets/image-20230306140457488.png)

![image-20230306140707831](./assets/image-20230306140707831.png)

![image-20230306140801206](./assets/image-20230306140801206.png)

 																	![image-20230306140912159](./assets/image-20230306140912159.png)

![image-20230306141000847](./assets/image-20230306141000847.png)

![image-20230306155142101](./assets/image-20230306155142101.png)

![image-20230306155222702](./assets/image-20230306155222702.png)

![image-20230306155357730](./assets/image-20230306155357730.png)

![image-20230306155435452](./assets/image-20230306155435452.png)

```git
# 查看git 版本 出现则安装成功
git --version 
```

## Git常用命令

| 命令名称                             | 作用             |
| ------------------------------------ | ---------------- |
| git config --global user.name 用户名 | 设置用户签名     |
| git config --global user.email 邮箱  | 设置用户邮箱     |
| git init                             | 初始化仓库       |
| git status                           | 查看本地仓库状态 |
| git add 文件名                       | 添加暂存区       |
| git commit -m "日志信息" 文件名      | 提交到本地仓库   |
| git reflog                           | 查看历史记录     |
| git reset --hard  版本号             | 版本穿梭         |

### 设置用户签名：

```git
git config --global user.name 用户名
```

```git
git config --global user.email 邮箱
```

![image-20230306205014519](./assets/image-20230306205014519.png)

说明：

​	签名的作用是区分不同的操作者身份，用户的签名信息在每一个版本的提交信息中能够看到，一次确认被本次提交是谁做的。$\textcolor{red}{Git首次安装必须设置一下用户名。否则无法提交代码。}$

$\textcolor{red}{注意：}$这里设置用户签名和将来登录GitHub（或其他代码托管中心）的账号没有任何关系

位置：

![image-20230306205514004](./assets/image-20230306205514004.png)

### 初始化本地仓库：

基本语法：

```git
git init  （相当于是获取Git的管理权）
```

案例：（会生成一个.git文件夹，获取到Git的管理权）

![image-20230306210709776](./assets/image-20230306210709776.png)



$\textcolor{red}{注意：Git的客户端和Linux的命令是通用的}$

### 查看本地库状态：

```git
git status
```

![image-20230306211625217](./assets/image-20230306211625217.png)

添加过文件再查看状态：

![image-20230306212051750](./assets/image-20230306212051750.png)

### 添加暂存区：

```git
git add (文件)  或者  git add -A （添加全部）
```

![image-20230306212406460](./assets/image-20230306212406460.png)

查看本地库状态：（由之前的红色 变为绿色）

![image-20230306212549814](./assets/image-20230306212549814.png)

删除暂存区文件：

```git
git rm --cached （文件名称）
```

![image-20230306212807765](./assets/image-20230306212807765.png)

查看状态：

![image-20230306212901270](./assets/image-20230306212901270.png)

### 提交本地库：

将暂存区的文件提交到本地库，形成历史版本

基本语法：

```git
git commit -m "日志信息" 文件名 或者 git commit -m "日志信息" （提交全部暂存区文件）
```

![image-20230306213421100](./assets/image-20230306213421100.png)

查看本地库的状态：

![image-20230306213518775](./assets/image-20230306213518775.png)

查看版本信息：

```git
 git reflog  或者  git log
```

![image-20230306213646626](./assets/image-20230306213646626.png)

修改文件（hello.txt 模拟代码变动）

![image-20230306214552951](./assets/image-20230306214552951.png)

![image-20230306215112232](./assets/image-20230306215112232.png)

### $\textcolor{red}{历史版本:}$

查看历史版本：

​	基本语法：

```
git reflog（查看版本信息） 
git log （查看版本详细信息）
```

![image-20230306215726465](./assets/image-20230306215726465.png)

版本穿梭：

​	基本语法：

```
git reset -hard 版本号
```

![image-20230306220548104](./assets/image-20230306220548104.png)

**.git 文件中的信息**

![image-20230306221007948](./assets/image-20230306221007948.png)

![image-20230306221154592](./assets/image-20230306221154592.png)

$\textcolor{red}{在本地库内存中记录了很多日志，通过调用指针来指向不同的版本}$

## Git分支操作

![image-20230307093054780](./assets/image-20230307093054780.png)

### 什么是分支：

​		在版本控制过程中，勇士推进多个任务，为每个任务，我们就可以创建每个任务的单独分支，使用分支意味着程序员可以把自己的工作从开发主线上分离开来，开发自己分支的时候，不会影响主线分支的运行，对于初学者而言，分支可以简单的理解为副本，一个分支就是一个单独的副本。（分支底层其实也是指针的引用）

![image-20230307110159236](./assets/image-20230307110159236.png)



### 分支的好处：

​		同时并行推进多个功能开发，提高开发效率

​		各个分支在开发过程中，如果一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。

### 分支的操作：

| 命令名称              | 描述                         |
| --------------------- | ---------------------------- |
| git branch  分支名曾  | 创建分支                     |
| git branch -v         | 查看分支                     |
| git checkout 分支名称 | 切换到指定分支中             |
| git merge 分支名称    | 把指定的分支合并到当前分支上 |

#### 	查看分支

​		基本语法：

```git
git branch -v
```

![image-20230307111504385](./assets/image-20230307111504385.png)

#### 	创建分支：

​		基本语法：

```git
git branch 分支名称
```

![image-20230307111642127](./assets/image-20230307111642127.png)	

#### 切换分支以及修改分支文件：

​		基本命令：

```git
git checkout 分支名称
```

![image-20230307112134084](./assets/image-20230307112134084.png)

$\textcolor{red}{因为切换了分支，所以.git 文件夹中的HEAD 文件中的指向就会改变	}$

![image-20230307112553318](./assets/image-20230307112553318.png)

#### 	合并分支（需要在主支上进行合并）：

​			基本命令：

```git
git merge  分支名称
```

![image-20230307113524272](./assets/image-20230307113524272.png)

#### 	删除分支：

​		基本语法：

```git
git branch --delete 分支名称
或者
git branch -d 分支名称
```

![image-20230307141851567](./assets/image-20230307141851567.png)

#### 	产生冲突：

​			$\textcolor{red}{产生冲突原因：合并分支时，两个分支的同一个文件的同一个位置有两套完全不同的修改。Git无法替我们决定使用哪一个。必须人为决定新代码内容。}$

​			查看状态（检测到有文件有两处修改）

![image-20230307151536773](./assets/image-20230307151536773.png)

![image-20230307151701406](./assets/image-20230307151701406.png)	

#### 	解决冲突：

​		将文件打开进行修改  把版本信息删除，把需要的代码留下，不需要的代码进行删除

![image-20230307152046582](./assets/image-20230307152046582.png)

​			重新保存提交代码，进行添加暂存区，进行重新提交（$\textcolor{red}{此时提交的时候不能带有文件名称，只会修改合并的分支，其他分支不会收到影响}$）

![image-20230307152537571](./assets/image-20230307152537571.png)



### 创建分支和切换分支图解：

![image-20230307152744677](./assets/image-20230307152744677.png)

![image-20230307152820757](./assets/image-20230307152820757.png)

master，hot-fix其实是指向具体版本记录的指针。当前所在分支，其实是由HEAD决定的。所以创建分支的本质就是创建一个指针。

​	HEAD如果指向measter，那么叫我们就现在就在master分支上

​	HEAD 如果指向hot-fix，那么我们现在就是hot-fix分支上

​	所以切换分支的本质就是移动HEAD指针

## Git团队协作机制

### 	团队内协作：

 ![image-20230307153948891](./assets/image-20230307153948891.png)





### 	跨团队协作：

![image-20230307154002198](./assets/image-20230307154002198.png)



## GitHub操作

​		GitHub 网址：https://github.com/

​		ps：全球最大同行交友网站，技术宅男的天堂，新世界的大门

| 账号            | 姓名     | 验证邮箱               |
| --------------- | -------- | ---------------------- |
| atlyyueyue      | 岳不群   | atlyyueyue@ly.com      |
| atlylinghuchong | 令狐冲   | atlylinghuchong@ly.com |
| atlydongfang    | 东方不败 | atlydongfang@ly.com    |

此三个账号为测试使用

### 创建远程仓库：

![image-20230307155348590](./assets/image-20230307155348590.png)

![image-20230307155655320](./assets/image-20230307155655320.png)

### 创建远程库别名：

| 命令                              | 描述                                                     |
| --------------------------------- | -------------------------------------------------------- |
| git remote -v                     | 查看当前所有远程地址别名                                 |
| git remote add 别名  远程仓库地址 | 给远程仓库连接起别名                                     |
| git push 别名  分支               | 推送本地分支上的内容到远程仓库                           |
| git clone 远程地址                | 将远程仓库的内容克隆到本地                               |
| git pull 远程地址别名  远程分支名 | 将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并 |

#### 	创建远程仓库别名：

​		基本语法：

```
git remote -v 查看当权所有远程地址别名
git renote add 别名  远程地址
```

![image-20230307161007872](./assets/image-20230307161007872.png)

出现两个是既可以推送又可以拉去的

#### 	删除远程库别名：

​		基本语法：

```git
git remote remove 别名 
```

![image-20230307171348515](./assets/image-20230307171348515.png)

#### 			推送本地分支到远程仓库：

​	基本命令：

```
git push 别名 分支名称
或者
git push 仓库地址名称  分支名称
```

![image-20230307164608965](./assets/image-20230307164608965.png)

#### 		拉去远程库到本地库：

​			基本命令：

```git
git pull 别名 分支名称 
或者
git pull 远程仓库地址 分支名称
```

![image-20230307172035601](./assets/image-20230307172035601.png)

#### 		克隆远程仓库到本地：

​				基本命令：

```
git clone 别名
或者
git clone 远程地址
```

![image-20230307174451360](./assets/image-20230307174451360.png)

1.  拉去代码
2.  初始化本地仓库
3.  创建别名

### 			邀请加入团队：

​		团队内协作：

![image-20230308093328676](./assets/image-20230308093328676.png)

​			跨团队协作：

![image-20230308110546676](./assets/image-20230308110546676.png)

![image-20230308170533616](./assets/image-20230308170533616.png)

修改代码进行跨团队提交

![image-20230308170708549](./assets/image-20230308170708549.png)

![image-20230308170855782](./assets/image-20230308170855782.png)



切回管理项目账号进行审核：

![image-20230308171451045](./assets/image-20230308171451045.png)

审核通过进行合并：

![image-20230308171531464](./assets/image-20230308171531464.png)



### SHH免密登录：

​		我们可以看到远程仓库中还有一个SHH的地址，因此我们也可以使用SHH进行访问。

![image-20230308220542424](./assets/image-20230308220542424.png)

生成SHH免密登录基本语法：

```git
shh-keygen -t rsa -C 账号邮箱
输入完毕之后点击三次回车
```

![image-20230308221252916](./assets/image-20230308221252916.png)

会生成一个.shh 目录

![image-20230308221401559](./assets/image-20230308221401559.png)

![image-20230308221514044](./assets/image-20230308221514044.png)

将当前.shh目录下的公钥添加到GitHub中：

![image-20230308221717780](./assets/image-20230308221717780.png)

![image-20230308221922491](./assets/image-20230308221922491.png)

## IDEA集成Git

### 	配置Git忽略文件：	

​			idea中有部分文件与实际功能无关。不能参与服务器的部署，所以需要屏蔽IDEA工具之间的差异。

​			创建忽略规则文件xxxx.ignore（前缀随便起，建议是git.ignore）

​			这个文件的存放位置原则上在哪里都可以，为了便于让~/.gitconfig文件引用，建议也放在用户目录下：

​			git.ignor 文件模板内容如下：

```git
# Compiled class file
*.class

# Log file
*.log

# BlueJ files
*.ctxt

# Mobile Tools for Java (J2ME)
.mtj.tmp/

# Package Files #
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar

# virtual machine  crash  logs, see http://www.java.com/en/download/help/error_hotspot.xml
hs_err pid*

.classpath
.project
.settings
target
.idea
*.iml
```

![image-20230309102310749](./assets/image-20230309102310749.png)

需要在.gitconfig中引用

```
[user]
	name = jx2693648
	email = 346789129@qq.com
[core]
	excludesfile = git忽略文件绝对路径
注意：这里要使用”正斜线（/）“，不要使用”反斜线（\）“
```

![image-20230309102758906](./assets/image-20230309102758906.png)

### 	定位Git程序：

![image-20230309103014029](./assets/image-20230309103014029.png)

### 	初始化Git仓库：

![image-20230309103310334](./assets/image-20230309103310334.png)

### 	添加到暂存区：

![image-20230309103539950](./assets/image-20230309103539950.png)

### 	提交本地库：

![image-20230309103831839](./assets/image-20230309103831839.png) 

### 	切换版本：

 ![image-20230309104233072](./assets/image-20230309104233072.png)

### 	创建分支：

![image-20230309104443408](./assets/image-20230309104443408.png)

### 	切换分支：

 ![image-20230309104716328](./assets/image-20230309104716328.png)

### 	合并分支：

  ![image-20230309104917241](./assets/image-20230309104917241.png)

### 	解决冲突：

![image-20230309105227937](./assets/image-20230309105227937.png)

![image-20230309105409455](./assets/image-20230309105409455.png)

## IDEA集成GitHub

### 	设置GitHub账号：

![image-20230309105630325](./assets/image-20230309105630325.png)

​			登录不上可以使用口令登录：

![image-20230309105903933](./assets/image-20230309105903933.png)

![adb79828fda3a15f1f18c838ab57c192](./assets/adb79828fda3a15f1f18c838ab57c192.png)



![2f7579d65d1b1e80d9cef47b470e9e57](./assets/2f7579d65d1b1e80d9cef47b470e9e57.png)

### 	分享工程到GitHub：

 ![image-20230309111601257](./assets/image-20230309111601257.png)

### 	push推送本地库到远程库：

  ![image-20230309111903841](./assets/image-20230309111903841.png)

注意：push是将本地库代码推送到远程库，如果本地库代码跟远程库代码版本不一致，push的操作是会被拒绝的。也就是说，要想push成功，一定要保证本地库的版本要比远程库的版本高！因此一个成熟的程序员在动手改本地代码之前，一定会先检查下远程库跟本地代码的区别！如果本地的代码版本已经落后，切记要先pul拉取一下远程库的代码，将本地代码更新到最新以后，然后再修改，提交，推送！

### 	pull拉去远程库到本地：

![image-20230309112446927](./assets/image-20230309112446927.png)

### 	clone克隆远程库到本地：

![image-20230309112705515](./assets/image-20230309112705515.png)

## 国内代码托管中心-码云

### 	简介：

​		众所周知，GitHub服务器在国外，使用GitHub作为项目托管网站，如果网速不好的话，严重影响使用体验，甚至会出现登录不上的情况。针对这个情况，大家也可以使用国内的项目托管网站-码云。

​		码云是开源中国推出的基于Git的代码托管服务中心，网址是htps:/gitee.com/，使用方式跟GitHub一样，而且它还是一个中文网站，如果你英文不是很好它是最好的选择。

### 	IDEA 集成码云：

#### 			IDEA安装码云插件：

​				Idea默认不带码云插件，我们第一步要安装Gitee插件。
​				如图所示，在Idea插件商店搜索Gitee,然后点击右侧的Install按钮。

![image-20230309113630612](./assets/image-20230309113630612.png)

### 	码云赋值GitHub项目：

​		码云提供了直接复制GtHb项目的功能，方便我们做项目的迁移和下载。具体操作如下：

![image-20230309131926069](./assets/image-20230309131926069.png)



![image-20230309131951983](./assets/image-20230309131951983.png)





当GitHub上面有代码更新是：

![image-20230309132240399](./assets/image-20230309132240399.png)

## 自建代码托管平台-GitLab

### 	GitLab简介：

​		GitLab是由GitLabInc.开发，使用MIT许可证的基于网络的Git仓库管理工具，且具有wiki和issue跟踪功能。使用Git作为代码管理工具，并在此基础上搭建起来的web服务。
​		GitLab由乌克兰程序员 DmitriyZaporozhets 和 ValerySizov开发，它使用Ruby语言写成。后来，一些部分用G0语言重写。截止2018年5月，该公司约有290名团队成员，以及2000多名开源贡献者。GitLab被IBM，Sony，JuilichResearchCenter，NASA,Alibaba，Invincea，O'ReillyMedia，

Leibniz-Rechenzentrum(LRZ)，CERN，SpaceX等组织使用。

### 	GitLab官网地址：

​				官网地址：https://about.gitlab.com/

​				安装说明：https://gitlab.cn/install/

### 	GitLab安装：

#### 		服务器准备：

​			准备一个系统为CentOS7以上版本的服务器，要求内存4G,磁盘50G。关闭防火墙，并且配置好主机名和P,保证服务器可以上网。

#### 		安装包准备：

​			um在线安装gitlab-ce时，需要下载几百M的安装文件，非常耗时，所以最好提前把所需RPM包下载到本地，然后使用离线pm的方式安装。
下载地址：

```
https://packages.gitlab.com/gitlab/gitlab-ce/packages/el/7/gitlab-ce-13.10.2-ce.0.el7.x86_64.rpm
```

#### 		编写安装脚本：

```
# vim gitlab-install.sh

# 安装包位置
sudo rpm -ivh /opt/module/gitlab-ce-13.10.2-ce.0.e17.x86_64.rpm

sudo yum install -y curl policycoreutils-python openssh-server cronie

sudo lokkit -s http -s sshe

sudo yum install -y postfixe

sudo service postfix starte

sudo chkconfig postfix ond

curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh sudo bash

sudo EXTERNAL_URL="http://gitlab.example.com" yum -y install gitlab-ced
```

给脚本添加权限

```
chmod +x gitlab-install.sh

# 执行脚本
#  ./gitlab-install.sh
```

#### 		初始化GitLab服务：

​				执行以下命令初始化GitLab服务

```
#  gitlab-ctl reconfigure
```

#### 		启动GitLab服务：

​				执行以下命令启动GitLab服务，如果停止，执行gitlab-ctl   stop

```
# gitlab-ctl start
```

#### 		使用浏览器访问GitLab：

​				使用主机名或者IP地址即可访问GitLab服务。需要提前配以下windows的hosts文件。

![image-20230309141736516](./assets/image-20230309141736516.png)

#### 		GitLab创建远程仓库：

 			首次登录需要给root账号修改密码，并且要符合规则![image-20230309142155575](./assets/image-20230309142155575.png)

![image-20230309142309181](./assets/image-20230309142309181.png)

![image-20230309142426973](./assets/image-20230309142426973.png)

![image-20230309142451693](./assets/image-20230309142451693.png)

#### 		IDEA集成GitLab：

​				安装GitLab插件：

![image-20230309142727908](./assets/image-20230309142727908.png)

![image-20230309142859485](./assets/image-20230309142859485.png)