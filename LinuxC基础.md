# 1.Linux基础命令

## 1.1 开发环境搭建

安装VM，安装ubuntu18.04

## 1.2 Windows和Linux

微软 Windows 操作系统将硬盘上的⼏个分区，⽤ A：、B：、C：、D：等符号标识。存取⽂件时⼀定要清楚存放在哪个磁盘的哪个⽬录下。

<img src="assets/image-20240216111629607.png" alt="image-20240216111629607" style="zoom:33%;" />

Linux 的⽂件组织模式犹如⼀颗倒置的树，这与 Windows ⽂件系统有很⼤差别。所有存储设备作为这颗树的⼀个⼦⽬录。存取⽂件时只需确定⽬录就可以了，⽆需考虑物理存储位置。

<img src="assets/image-20240216111850048.png" alt="image-20240216111850048" style="zoom: 33%;" />

## 1.3 Linux路径含义

**/bin**：bin 是⼆进制（binary）英⽂缩写。 

**/boot**：存放的都是系统启动时要⽤到的程序。 

**/dev**：包含了所有 Linux 系统中使⽤的外部设备。 

**/etc**：存放了系统管理时要⽤到的各种配置⽂件和⼦⽬录。 

**/lib**：存放系统动态连接共享库的。 

**/home**：普通⽤户的主⽬录。

**/root**：根⽤户（超级⽤户）的主⽬录。

## 1.4 常用快捷键

开启一个新的终端：ctrl + alt + t

虚拟机全屏：ctrl + alt + 回⻋

清屏：Ctrl + l

终端字体变大：Ctrl 加 shift 加 +

终端字体缩小：ctrl + - 

鼠标退出虚拟机控制：ctrl + alt

## 1.5 Linux基础命令

| 命令  | 功能                                                         | 参数及格式                                                   |
| ----- | :----------------------------------------------------------- | ------------------------------------------------------------ |
| pwd   | print work directory 的缩写, 显示当前⽬录的绝对路径          |                                                              |
| cd    | change directory 的缩写, 切换⽬录；<br />绝对路径：以 / 为起点，遍历到⼦⽬录；<br />相对路径：以当前⽬录为起点，遍历到⼦⽬录。 | .   当前⽬录<br />..  上层⽬录 <br />-   上⼀次操作所在路径 <br />~   相当于 /home/ ⽤户名的路径 |
| ls    | list 单词的缩写, 列出当前⽬录的内容                          |                                                              |
| touch | 新建⼀个⽂件                                                 |                                                              |
| clear | 清屏                                                         |                                                              |
| mkdir | 在当前⽬录下新建⽂件夹                                       |                                                              |
| rm    | 默认删除⽂件，加上指定参数后，可删除⽂件夹                   | -r   删除文件夹<br />-f   强制执行                           |
| cp    | 复制⽂件 / ⽂件夹到指定⽬录                                  | 拷贝源文件到指定目录：   cp   源文件   目标路径<br />创建文件副本：   cp   源文件   目标文件<br />拷贝源文件夹：   cp   源文件夹   目标文件夹   -a |
| mv    | 移动文件                                                     | 把源文件移动到指定目录：mv   源文件   目标路径<br />把源文件重命名为目标文件：mv   源文件   目标文件<br />把源文件夹移动到指定目录：mv   原文件夹   目标文件夹 |

**例1：cd用法**

```shell
cd  /home/linux/Desktop   		#绝对路径的⽤法
cd  /home/linux           		#相对路径的⽤法
cd  ./Desktop
cd  ../                   		#返回上层⽬录
cd  -                     		#返回上次操作的路径
```

**例2：ls和pwd用法**

```shell
pwd                          	#显示当前⽬录
cd   /home/linux             	#进⼊linux⽂件夹中
ls                           	#列出当前⽬录下的内容
pwd
cd   ..                      	#进⼊上层⽬录
pwd
cd  ./linux                  	#进⼊当前⽬录下的linux⽂件夹中
 
```

**例3：mkdir、touch、rm用法**

```shell
cd     /home/linux                      #进⼊/home/linux⽂件夹
mkdir  Cbase                            #新建⽂件Cbase⽂件夹
cd    ./Cbase                           #进⼊Cbase⽂件夹
touch  log1.txt  log2.txt log3.txt      #创建log1.txt log2.txt log3.txt⽂件
mkdir  dirTest                          #新建dirTest⽬录
clear                                   #清屏
rm     log1.txt log2.txt                #删除log1.txt log2.txt⽂件
rm  -rf dirTest                         #删除dirTest⽂件夹
```

**例4：cp用法**

```shell
cp  hello.c   /home/linux/Cbase          #把hello.c拷⻉到Cbase⽂件夹中
cp  hello.c   world.c                    #把hello.c复制⼀份命名为world.c
cp  Cbase   ../    -a                    #把Cbase⽂件夹拷⻉到上层⽬录
```







**练习**5

①进⼊ / home/linux ⽬录, 利⽤ ls 查看当前⽂件下的内容，⽤ pwd 命令观察路径。

②再次进⼊ / etc ⽬录, 利⽤ ls 查看当前⽬录下的内容。

③再次进⼊到 / home/linux ⽬录下新建⼀个 first ⽂件夹

④进⼊ first ⽂件夹中新建⼀个 log1.txt 和 log2.txt, ⿏标双击打开写⼊ "Hello World"

⑤然后把 log1.txt 拷⻉到上层⽬录.

⑥然后把 log2.txt 重命名为 log.c

**答案**

①cd /home/linux；   ls；    pwd；

②cd /etc；ls

⑥cd /home/linux

mkdir first

cd first

touch log1.txt log2.txt

cp log1.txt ../

mv log2.txt log.c

# 2.Vim编辑器

## 2.1 Vim编辑器的介绍及使用

我们想要编写 C 语⾔代码，可以使⽤ linux 系统提供的⼯具才能进⾏代码的编写。代码编写完成之后，我们还需要验证书写的代码是否正确。这就需要编译器来进行验证。linux 系统为我们提供了⽐较好的开发⼯具。

Vim编辑器：书写代码的工具；

Gcc编译器：编译代码的工具。

## 2.2 Vim编辑器的基本操作

| 模式     | 使用方法                                                     |
| -------- | ------------------------------------------------------------ |
| 命令模式 | vim + hello.c 默认打开的默认, 不能书写代码, 只能进⾏复制, 粘贴等命令操作 |
| 插⼊模式 | 按下⼩写的 “ i" 键, 在终端的左下⻆会出现⼀个叫 做 "insert ”  的关键字, <br />便是进⼊插⼊模式, 可以书写代码了 |
| 底⾏模式 | 代码书写完毕键，按下 esc 键，退出插⼊模式。<br/>再按下 shift + “ :” 键, 可以使⽤以下指令：<br />w保存（write 的缩写）、 q 退出（quit 的缩写）、a 所有（all的缩写）、 ! 强制执⾏ |

常⽤指令： wq , q!

注：若是⽤⽼师提供的 linux 系统，可直接⽤空格键, 在终端的做左下脚出现**":"**, 表示进⼊底⾏模式。

# 3.GCC编译器

## 3.1 GCC编译器的介绍及使用

GCC 它是由 GNU 开发的编程语⾔编译器。它是 GNU Compiler Collection（GNU编译器集合）的缩写。可以⽤来编译C,C++,Object-C 等多种语⾔。它是 Linux 下提供⼀般⽤户使⽤的标准编译器。

### 3.1.1 安装GCC编译器

```shell
sudo apt-get install gcc
```

### 3.1.2 GCC编译器的用法

**方法1：使用系统生成的可执行文件**

 gcc hello.c 编译代码, 系统默认会在当前⽬录下，⽣成⼀个叫做 a.out 的⽂件.【all out】
./a.out 执⾏ a.out ⽂件，输出对应的结果.

**方法2：用户自定义可执行文件**

 gcc hello.c -o exec 编译代码, ⽤户⾃定义⽣成的可执⾏⽂件名字。
./exec 执⾏./exec ⽂件，输出对应的结果.

### 3.1.3 GCC编译的流程

<img src="assets/image-20240218102141721.png" alt="image-20240218102141721" style="zoom: 67%;" />

预处理 ----> 把编写好的xx.c源代码⽣成我预处理过得 C 代码 xx.i

编译 ----> 把我们预处理过的代码⽣成我们的汇编代码 xx.s

汇编 ----> 把汇编代码⽣成我们的⽬标⽂件 xx.o

链接 ----> 把我们的⽬标⽂件⽣成我们的可执⾏⽂件

**练习：⾃⼰把下列代码写出来，⽤ GCC 编译器运⾏，运⾏查看结果。**

```c
#include <stdio.h>
int main()
{
	int a = 10;
    int sum = 0;
    sum = sum + 1;
    sum = sum + 2;
    sum = sum + 3;
    sum = sum + 4;
    sum = sum + 5;
    printf("sum = %d\n",sum);
    return 0;
}
```

