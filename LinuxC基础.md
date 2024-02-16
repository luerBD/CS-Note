# 第一章 开发环境搭建

## 1.VM软件简介

VMware Workstation Pro 是 VMware（威睿公司）发布的⼀代虚拟机软件，中⽂名称⼀般称为 "VMware ⼯作站". 它的主要功能是可以给⽤户在单⼀的桌⾯上同时运⾏不同的操作系统，它也是可进 ⾏开发、测试、部署新的应⽤程序的最佳解决⽅案。Vmware WorkStation 可在⼀部实体机器上模拟 完整的⽹络环境，以及可便于携带的虚拟机器。对于企业的 IT 开发⼈员和系统管理员⽽⾔，Vmware 在虚拟⽹络，实时快照，拖拽共享⽂件夹等⽅⾯的特点使它成为必不可少的⼯具。

## 2.软件安装

<img src="assets/image-20240216102724619.png" alt="image-20240216102724619" style="zoom: 33%;" />

<img src="assets/image-20240216102836779.png" alt="image-20240216102836779" style="zoom: 33%;" />

<img src="assets/image-20240216102945184.png" alt="image-20240216102945184" style="zoom: 33%;" />

<img src="assets/image-20240216103016568.png" alt="image-20240216103016568" style="zoom: 33%;" />

<img src="assets/image-20240216103034846.png" alt="image-20240216103034846" style="zoom: 33%;" />

<img src="assets/image-20240216103048467.png" alt="image-20240216103048467" style="zoom: 33%;" />

<img src="assets/image-20240216103213943.png" alt="image-20240216103213943" style="zoom: 33%;" />

点击许可证，许可证自行搜索，都可以搜到的。

<img src="assets/image-20240216103252309.png" alt="image-20240216103252309" style="zoom: 33%;" />

输入秘钥后安装就完成了！

<img src="assets/image-20240216103421907.png" alt="image-20240216103421907" style="zoom: 33%;" />



# 第二章 Linux基础命令

微软 Windows 操作系统将硬盘上的⼏个分区，⽤ A：、B：、C：、D：等符号标识。存取⽂件时⼀定要清楚存放在哪个磁盘的哪个⽬录下。

<img src="assets/image-20240216111629607.png" alt="image-20240216111629607" style="zoom:33%;" />

Linux 的⽂件组织模式犹如⼀颗倒置的树，这与 Windows ⽂件系统有很⼤差别。所有存储设备作为这颗树的⼀个⼦⽬录。存取⽂件时只需确定⽬录就可以了，⽆需考虑物理存储位置。

<img src="assets/image-20240216111850048.png" alt="image-20240216111850048" style="zoom: 33%;" />

## 2.1路径含义

**/bin**：bin 是⼆进制（binary）英⽂缩写。 

**/boot**：存放的都是系统启动时要⽤到的程序。 

**/dev**：包含了所有 Linux 系统中使⽤的外部设备。 

**/etc**：存放了系统管理时要⽤到的各种配置⽂件和⼦⽬录。 

**/lib**：存放系统动态连接共享库的。 

**/home**：普通⽤户的主⽬录。

**/root**：根⽤户（超级⽤户）的主⽬录。

## 2.2常用快捷键

开启一个新的终端：ctrl + alt + t

虚拟机全屏：ctrl + alt + 回⻋

清屏：clear命令、Ctrl + l

终端字体变大：Ctrl 加 shift 加 +

终端字体缩小：ctrl + - 

鼠标退出虚拟机控制：ctrl + alt