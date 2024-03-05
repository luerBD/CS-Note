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

