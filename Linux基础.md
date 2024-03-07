# 1.Linux系统简介

## 1.1 Unix系统简介

需要从⻉尔实验室的 UNIX 说起，1969 年，AT&T 公司的⻉尔实验室与 MIT 合作开发的 Unix，旨在于创建⼀个⽤于⼤型、并⾏、多⽤户的操作系统。 

Unix 的推⼴：从学校⾛进企业

Unix 的版本主要两个： AT&T System V ——就是俗称的 “系统 5” 、Berkley Software Distribution (BSD)

Linux操作系统的组件

一个操作系统想要跑起来，需要以下组件：

## 1.2 Unix家庭树

<img src="assets/image-20240305091517860.png" alt="image-20240305091517860" style="zoom:50%;" />

## 1.3 Linux系统的诞生

Linux 是⼀种操作系统。 

1991 年，芬兰赫尔⾟基⼤学的学⽣ Linus Torvals 为了能在家⾥的 PC 机上使⽤与学校⼀样的Unix操作系统，开始编写了类 UNIX. 

1991.8.25，Linus 就在 comp.os.minix 新闻组中⾸次发布了⼀个 Linux 内核的公共版本。

<img src="assets/image-20240305091950795.png" alt="image-20240305091950795" style="zoom:50%;" />

## 1.4 Linux的发行版本

**流⾏的 Linux 版本** 

Solaris、IBM AIX、Red Hat、Fedora Core、SUSE Debian、Mac OS X、Ubuntu

## 1.5 Ubuntu的发行版本代号

对于软件来说，发行版本就是在某个时间点，开发者把所有已经完成的代码、功能、修复等打包起来，形成一个完整的、可以对外发布的版本。这个版本可以是一个新的开始，也可以是对之前版本的更新或改进。

![image-20240305092526009](assets/image-20240305092526009.png)

一般我们下载Ubuntu的时候，要下载带有LTS（长期支持）的版本，意味着 LTS 版本会收到更多的安全更新、补丁和可能的错误修复，以确保该版本的稳定性和可靠性。

## 1.6 Linux 操作系统的组件

**一个操作系统想要跑起来则需要以下组件：**

Linux 内核、Shell、⽂件系统、实⽤程序

![image-20240305093648362](assets/image-20240305093648362.png)

### 1.6.1 Linux内核

内核是 Linux 系统的最底层，提供了系统的核⼼功能并允许进程以⼀种有序的⽅式访问硬件。 ⽤于控制进程、输⼊、输出设备、⽂件系统操作、管理内存。 这些都不需要⽤户参与，系统⾃⾏完成。

**Linux 内核版本** 

主版本：1.0 2.0 2.2 2.4 2.6    2,3 年更新

稳定版：2.0.40 2.2.12 2.4.18 2.6.35    1,2 ⽉更新 

稳定版更新：2.6.18.1 ~ 2.6.18.7     1,2 周更新

**Linux 内核结构**

![image-20240305094118377](assets/image-20240305094118377.png)

### 1.6.2 Shell介绍

Shell的英文含义是“壳”，它是相对于内核来说的。在Linux中，shell是一个面向用户的命令接口，表现形式为一个可以由用户录入的界面，并且这个界面也能反馈运行信息。

Shell 是⼀个命令⾏解释器，它使得⽤户能够与操作系统进⾏交互。 

Shell 类型：Bourne Shell 最早的 Shell 、C Shell、Bourne again Shell …

# 2.Ubuntu软件包管理机制

## 2.1 简介

Ubuntu Linux 采⽤了 Debian 的软件包管理机制。由于软件包具有易⽤性、灵活性和扩展性的特点， 再加上 Internet 的⽀持，debian 软件包在 ubuntu 系统中被⼴泛使⽤。它使⽤户随时都能拥有最新的 Ubuntu 系统，这也是 Ubuntu 受到推崇的⼀个重要原因。因⽽，Deb 软件包管理也成为 Ubuntu 中最有活⼒的部分。本章将介绍 ubuntu 软件包管理器。

## 2.2 目前两种流行的软件包管理机制

最初，基于 Linux 系统的开发者在完成应⽤程序的开发之后，将很多的⼆进制⽂件发送给⽤户。因此，Debian-Linux ⾸先提出 “ 软件包” 的管理机制—— Deb 软件包，将应⽤程序的⼆进制⽂件、配置⽂档、man/info 帮助⻚⾯等⽂件合并打包在⼀个⽂件中，⽤户使⽤软件包管理器直接操作软件包，完成获取、安装、卸载、查询等操作。 

随即，Redhat Linux 基于这个理念推出了⾃⼰的软件包管理机制—— Rpm 软件包。当然，Redhat Linux 采⽤了⾃⼰的打包格式⽣成 Rpm 包⽂件，由 Rpm 包管理器负责安装、维护、查询，甚⾄软件包版本管理。由于 Redhat Linux 系统的普及，Rpm 软件包被⼴泛使⽤，甚⾄出现第三⽅开发的软件管理⼯具，专⻔管理 Rpm 格式的软件包。

ubuntu Linux 系统的软件包管理机制延续了 Debian 的包管理⽅法。

## 2.3 软件包说明

Debian 包⽂件包含了⼆进制可执⾏⽂件、库⽂件、配置⽂件和 man/info 帮助⻚⾯等⽂档。通常 Debian 包⽂件的后缀为. deb，因此称为 “ Deb 软件包” 。Ubuntu 有两种类型的软件包：⼆进制软件包（deb）和源码包（deb-src）。

⼆进制软件包（Binary Packages）：包含可执⾏⽂件、库⽂件、配置⽂件、man/info ⻚⾯、 版权声明和其他⽂档。 

源码包（Source Packages）：包含软件源代码、版本修改说明、构建指令以及编译⼯具等。 先由 tar ⼯具归档为. tar.gz ⽂件，然后再打包成. dsc ⽂件。

注：我们可以在 /etc/apt/source.list中来查看我们的两种包类型

![image-20240305104237856](assets/image-20240305104237856.png)

![image-20240305104744058](assets/image-20240305104744058.png)

**软件包组件**

main :  完全的⾃由软件。 

restricted :  不完全⾃由的软件。 

universe : ubuntu 官⽅不提供⽀持和补丁，全靠社区⽀持。 

multiverse :  ⾮⾃由软件，完全不提供⽀持和补丁。

**下面以：http://cn.archive.ubuntu.com/ubuntu/为例来讲解**

![image-20240306124325377](assets/image-20240306124325377.png)

在 Ubuntu Linux 中，软件包的命名遵循以下约定：

![image-20240305110106458](assets/image-20240305110106458.png)

例如：

![image-20240305110131201](assets/image-20240305110131201.png)

```
软件包名：g++
软件版本：4.1.2
修正版本：9
体系架构：i386
包类型：deb 包
软件包：g++_4.1.2-9ubuntu2_i386.deb
```

# 3.Ubuntu软件安装命令详解

## 3.1 软件包安装工具简介

我们常常使⽤的软件包管理⼯具有两种，⼀种叫做 dpkg 软件包管理⼯具, 它是” debian package” 的 简写，是Debian 软件包管理器的基础。它是最早的 deb 软件包管理⼯具，他在 Debian Linux——提出软件包管理模式后随即就诞⽣了。使⽤ dpkg 可以实现软件包的安装、编译、卸载、查询，以及应⽤程序打包等功能。但是由于当时 Linux 系统规模 和 Internet ⽹络条件的限制，我们使⽤ <u>dpkg 安装软件包 的时候需要考虑软件包之前的依赖关系。也有⼈把它叫做本地安装⼯具</u>。 总之，dpkg 是⼀个底层的 软件包管理系统，<u>主要⽤于对已下载到本地和已安装的软件包进⾏管理</u>。

![image-20240305125123932](assets/image-20240305125123932.png)

基于这个特性，我们的 dpkg 安装⼀般来说有可能要安装多个软件包。⽽我们 linux 系统中的依赖关系 相对复杂，因此就定义了⼀个依赖关系表以及优先级表。Ubuntu 中为每个软件包指定了⼀个优先级， 作为软件包管理器选择安装和卸载的⼀个依据。

![image-20240305125701093](assets/image-20240305125701093.png)

![image-20240305125815247](assets/image-20240305125815247.png)

## 3.2 dpkg软件包安装【本地安装】

### 3.2.1 安装软件

```bash
sudo dpkg -i 软件包 [安装单个软件包]
或
sudo apkg -i *.deb [多个软件包⼀起安装]

例如：sudo dpkg -i nano_2.2.6-1_i386.deb
```

### 3.2.2 移除已安装的软件包

```bash
sudo dpkg -r 软件包名

例如：sudo dpkg -r nano
```

### 3.2.3 移除已安装的软件包及配置文件

```bash
sudo dpkg -P 软件包名
```

### 3.2.4 列出软件包在系统所安装的文件

```bash
sudo dpkg -L 软件包名
```

### 3.2.5 列出软件包安装状态

列出软件包的安装状态以及详细信息。

```bash
sudo dpkg -s 软件包名
```

## 3.3 apt-get软件包安装【联网安装】

### 3.3.1 镜像站点服务器

APT 系列⼯具可能是 Deb 软件包管理⼯具中功能最 强⼤的。它会⾃动检测软件包之间的依赖关系。 因为它采⽤了集中式的软件仓库的机制，将各式各样 的软件包分⻔别类地存放在软件仓库中，进⾏有 效地组织和管理。然后，将软件仓库置于许许多多的镜像服务器中，并保持基本⼀致。（可理解为我们上⽹的时候，有很多的⽹站，每个⽹站中有⼀些下载的链接，每个下载的链接中就有很多的软件包，这个下载的链接就是 软件包仓库，这⾥的镜像站点服务器可理解为包含多个下载链接的⽹站）。这些镜像服务器就是它们的软件源（包含多个下载链接的⽹站的集合）。

![image-20240306134050513](assets/image-20240306134050513.png)

我们可以在 /etc/apt/source.list 中来查看我们的软件源。这个路径就叫做镜像站点服务器。

![image-20240305133259839](assets/image-20240305133259839.png)

内容如下：

![image-20240305133456769](assets/image-20240305133456769.png)

### 3.3.2 索引文件

我们的镜像站点服务器只是告诉了我们。我们的软件包应该在哪⾥去下载。但是我们这些镜像站点具体 拥有哪些资源，对我们来说，不是很清楚。如果，我们每安装⼀个软件包就到我们的服务器上去寻找⼀ 遍，这样的话效率就太低了。因此，我们提出了⼀个概念，叫做**索引⽂件**。索引文件记录了每个软件名和它对应的下载网站，它的本质就是我们为服务器上的软件资源在本地列了⼀个清单，安装软件的时候主机会先在索引文件中查找该软件名，若找到则自动在该软件所对应的网站中进行下载。（可理解为⽹站服务器在本地的缓存）。

我们可以在 **/var/lib/apt/lists/** 这个⽬录来查看

![image-20240305133830166](assets/image-20240305133830166.png)

### 3.3.3 下载的软件包所存放的路径

我们在 windows 上下载软件的时候，⼀般是会把. exe 的安装包下载到⼀个指定的路径，然后双击它进⾏安装。我们的 ubuntu 也是⼀样的，只不过这个下载路径是固定的，我们可以到 **/var/cache/apt/archives** 这个⽬录下来查看我们的软件包。

![image-20240305134653338](assets/image-20240305134653338.png)

### 3.3.4 安装命令

```bash
sudo apt-get install 软件包名

例如： sudo apt-get install sl 或 sudo apt-get install btanks
```

注意：sudo apt-get install sl执行时可能会报告以下错误：

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-headers-5.19.17-051917-generic : Depends: libc6 (>= 2.34) but 2.27-3ubuntu1.5 is to be installed
                                        Depends: libssl3 (>= 3.0.0) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

使用sudo apt --fix-broken install修复即可！

### 3.3.5 卸载命令

```bash
sudo apt-get remove 软件包名

例如: sudo apt-get remove sl
```

### 3.3.6 更新索引文件命令

```bash
sudo apt-get update
```

### 3.3.7 清空存放下载软件包的目录

```bash
sudo apt-get clean
```

## 3.4 apt-get软件包总结

### 3.4.1 三个重要路径

```tex
/etc/apt/sources.list [⽂件] -> 镜像站点服务器地址 (可以理解成软件包的下载⽹站)
/var/lib/apt/lists [⽬录] -> 每个镜像站点软件包的索引⽂件（可以理解成我们软件包下载⽹站具体内容的缓存，例如：软件版本，软件名等等）
/var/cache/apt/archives [⽬录] -> 下载下来软件包存放路径
```

### 3.4.2 原理

我们使⽤ apt-get 命令下载⽂件的时候，默认是在镜像站点软件包的索引⽂件 [缓存] /var/lib/apt/lists中查找该软件的⼀些信息。

当我们找到索引⽂件中的软件信息之后，就进⼊了我们 的镜像站点服务器[⽹站]/etc/apt/sources.list地址来下载我们需要的软件，下载的⽂件存放在/var/cache/apt/archives⽬录下。

![apt-get原理图](assets/apt-get原理图.png)

例：sudo apt-get install g++，当执行这条命令时，会先在/etc/apt/sources.list中找g++所在的网站A，然后 在/var/lib/apt/lists找到网站A对应的缓存，网站A对应的缓存中记录了g++在远程服务器的索引号，然后后台自动登录远程服务器并且拿着g++的索引号（05）找到05.g++.dep，然后再将g++.dep下载到主机的/var/cache/apt/archives目录中。

**练习**

⼤家利⽤ apt-get 命令安装⼀下 btanks，观察是什么样的现象。(把现象截图即可） 安装命令: sudo apt-get install btanks

# 4.Linux用户管理

## 4.1 原理

在 Linux 系统中，所有的⽤户和组像⼀个国家。如果国家要繁荣昌盛的话，需要治理得当，需要有主席或者总统，以及地⽅官员和⽼百姓组成。

在 linux 中如果你对安全需求⽐较苛刻，完全可以限制⽤户的各种⾏为，不同⽤户的权限是不同的。 在 linux 中系统中，它并不认识帐号名称。它认识的是我们的帐号 ID，帐号 ID 保存在 /etc/passwd ⽂件中。我们在登录 linux 主机时，在输⼊完帐号和密码时，linux 会先查找 /etc/passwd ⽂件中是 否有这个帐号，如果没有则跳出，如果有的话，他会读取该帐号的 user ID 和 group ID，同时该帐号的 根⽬录和 shell 也读了出来。然后在去核对密码表，在 /etc/shadow 中找出我们刚刚输⼊的帐号和 userID, 核对我们输⼊密码是否正确。⼀切正确我们可以登录到当前⽤户 shell。

那么，我们⾸先了解⼀ 下⼀些基本的概念。 在我们的 linux 中各个⽤户以权限来区分，Linux 中常⻅⽤户分为以下三种：

​	超级⽤户 root：具有最⾼的权限，UID=0,GID=0；

​	系统⽤户：主要服务于系统应⽤，维护系统运⾏，不能登录。例如：uucp、daema 等；

​	普通⽤户：登录的⽤户。

组：具有相同权限的⽤户的集合。例如，我们的 ubuntu 组

## 4.2 Linux用户相关路径

### 4.2.1 /etc/passwd

![image-20240307163847023](assets/image-20240307163847023.png)

第⼀⾏ root 这⼀⾏，⼀共有七项，每⼀项的含义如下：

![image-20240307165201945](assets/image-20240307165201945.png)

```tex
帐号名称：帐号名称由于对应⽤户ID，这个是系统默认⽤户root超级管理员，在同⼀个系统帐号名称是唯⼀的，⻓度根据不同的linux系统⽽定，⼀般是8位。 

密码：由于系统中还有⼀个 /etc/shadow ⽂件⽤于存放加密后的⼝令， 所以在这⾥这⼀项是 “x” 来表示，如果⽤户没有设置⼝令，则该项为空。

⽤户ID：这个是系统内部⽤于来识别不同的⽤户的，不同的⽤户识别码不同，其中⽤户ID有以下⼏种：
0代表系统管理员
1-500系统预留的ID
500以上是普通⽤户使⽤。

组ID：其实这个和⽤户ID差不多，⽤来规范群组，他与/etc/group有关。

描述信息：这个字段⼏乎没有什么作⽤，只是⽤来解释这个帐号的意义。⼀般常⻅的是⽤户全名信息。

⽤户根⽬录：就是⽤户登录系统的起始⽬录，⽤户登录系统后将⾸先进⼊该⽬录。root⽤户默认的是/root，普通⽤户的是/home。

⽤户登录shell：就是⽤户登录系统时使⽤的shell路径。
```

