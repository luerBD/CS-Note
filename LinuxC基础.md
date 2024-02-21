

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

注：以下操作要求在命令模式进⾏。 【按下 esc 键后，可进⼊命令模式】

| 命令 | 功能                                                         |
| ---- | ------------------------------------------------------------ |
| u    | 英文全称为undo，取消上一次操作（及恢复功能），相当于windows中的Ctrl+z |
| v    | v+↑or↓键，选中多行<br />v+←or→键，选中多个字符<br />相当于windows中的shift键 |
| y    | 复制                                                         |
| p    | 粘贴                                                         |
| x    | 剪切                                                         |



# 3.GCC编译器

## 3.1 GCC编译器的介绍及使用

GCC 它是由 GNU 开发的编程语⾔编译器。它是 GNU Compiler Collection（GNU编译器集合）的缩写。可以⽤来编译C,C++,Object-C 等多种语⾔。它是 Linux 下提供⼀般⽤户使⽤的标准编译器。

### 3.1.1 安装GCC编译器

```shell
sudo apt-get install gcc
```

### 3.1.2 GCC编译器的用法

**方法1：使用系统生成的可执行文件**

```shell
gcc hello.c 			#以64位的微处理器编译代码
gcc -m32 hello.c 		#以32位的微处理器编译代码
```

 系统默认会在当前⽬录下，⽣成⼀个叫做 a.out 的⽂件.【all out】

```shell
./a.out			#执⾏ a.out ⽂件，输出对应的结果.
```

**方法2：用户自定义可执行文件**

```shell
gcc hello.c -o exec 		#以64位的微处理器编译代码
gcc -m32 hello.c -o exec	#以32位的微处理器编译代码
```

⽤户⾃定义⽣成的可执⾏⽂件名字。

```shell
./exec 			#执⾏./exec ⽂件，输出对应的结果.
```

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

# 4.c语言中的常量

## 4.1 整形常量

10、20、-5、-100

## 4.2 浮点型常量

3.1415926、-2.5、1e5、314e-2

## 4.3 字符常量

在 C 语⾔中规定，每个字符有个对应的 ascii 的整数值与之对应。  ⼀个字符常量占 1bytes， 1bytes = 8bit。

linux 中查询 ascii 码的⽅法 ： man ascii。

例如：'a'、‘b’、‘c’、‘d’、'A'、‘1’、‘8’。

## 4.4 字符串常量

字符串常量用 "" 括起来，等价于多个字符的结合 + '\0。

例如："hello"等价于'h'+'e'+'l'+'l'+'o'+'\n'

## 4.5 标识常量（宏定义）

⽤宏名来代替某些常量数据，在某些特殊的场合可以提⾼程序的可读性。  宏名替换后为常量，常⼤写。

**格式：**

```c
#define 标识符号名 常量数据
```

**例：**

```c
#define	MAX	100
#define	STR	"This is a example"
```

**课后任务：**

请⼤家说出 "88.88" 是下列哪种常量？ () 

A. 整型常量   B. 浮点型常量  C. 字符串常量  D. 字符常量

# 5.c语言中的输出函数

```c
printf("字符串 + 格式控制串",参数1,参数2,...);
```

**功能：**向屏幕上输出 " " 中的内容， " " 中字符串原样输出，格式控制串会被后⾯的参数给替换掉，参数的个数由格式控制串的个数来决定。

**参数：**

| 格式控制串 | 功能                                                |
| ---------- | --------------------------------------------------- |
| %d         | 输出⼗进制数，把后⾯参数当作⼗进制数据输出          |
| %c         | 输出字符                                            |
| %s         | 输出字符串                                          |
| %f         | 输出⼩数                                            |
| %e         | 以科学计数法的形式输出⼩数 ，3.14e10                |
| %o         | 输出⼋进制数, 若是加上 #, 会输出对应的标志位 0      |
| %x         | 输出⼗六进制数据, 若是加上 #, 会输出对应的标志位 0x |

**例1：**

```c
 #include <stdio.h>
 int main()
 {
        printf("int = %d %d %d\n",10,20,30);
        printf("char = %c %c %c\n",'X','Y','Z');
        printf("string = %s\n","welcome to china!");
        printf("float = %f\n",3.14159267);
        printf("float = %e\n",131492834.23234323);
        printf("=================================\n");
        printf("dec = %d\n",10); 
        printf("oct = %#o\n",10); 
        printf("hex = %#x\n",10); 
        return 0;
 }
```

 **输出：**

```output
int = 10 20 30
char = X Y Z
string = welcome to china!
float = 3.141593
float = 1.314928e+08
=================================
dec = 10
oct = 012
hex = 0xa
```

**例2：**

```c
#include <stdio.h>
 int main()
 {
        printf("%c = %d\n",'A','A');
        printf("%c = %d\n",'A' + 32,'A' + 32);
        printf("%c = %d\n",'1','1' - 48); 
        printf("%c = %d\n",'\141','\141'); 
        printf("%c = %d\n",'\x61','\x61'); 
        return 0;
 }
```

**输出：**

```
 A = 65
 a = 97
 1 = 1
 a = 97
 a = 97
```

**例3：**

```c
 #include <stdio.h>
 #define N  10
 #define M  N + N
 #define SUM  M * M
 int main()
 {
        printf("M = %d\n",M);  
        printf("SUM = %d\n",SUM);
        return 0;
 }
```

**输出：**

```
120
```

**练习：**

①要求利⽤ "%c : %d" 这种格式，向屏幕上输出’a’,‘m’,’ '对应的字符形式和⼗进制数形式。
	要求利⽤ %f 输出 3.14159287
	要求利⽤ %e 输出 31455452232.88232

```c
#include<stdio.h>
int main()
{
	printf("%c = %d\n", 'a', 'a');
	printf("%c = %d\n", 'm', 'm');
	printf("%f\n", 3.14159287);
	printf("%e\n", 31455452232.88232);

}
```

②printf(“data1 = %c : %d”,?,?); //? 中包含’A’思考如何变成’a’
	printf(“data2 = %d”, ?); //? 中包含’1’，思考如何通过’1’要求输出⼗进制数 1

```c
#include<stdio.h>
int main()
{
	printf("%c:%d\n", 'A'+32, 'A' + 32);
	printf("%d\n", '1' - 48);
	return 0;
}
```

# 6.c语言中的变量

在实际编程和⽣活中, 某些数据并不是⼀成不变的，⽽是根据实际的需求，可以时时改变。这样变量的应运⽽⽣。数据可以变量的量，我们叫做变量。本质是系统在内存中申请⼀块空间，根据⽤户的需求，随时改变申请空间中的数据。

| 数据类型  | 大小（Byte） |
| --------- | ------------ |
| short     | 2            |
| int       | 4            |
| long      | 4            |
| long long | 8            |
| float     | 4            |
| double    | 8            |
| char      | 1            |

变量名由字符、数字、下划线组成，⾸个单词⼀定要是字⺟或下划线。

**sizeof()函数：**

格式：sizeof(变量名) or sizeof(数据类型)

作用：获取某个变量或数据类型在内存中所占的大小

注意：sizeof()的返回值输出时用%ld占位

**例：**

```c
int a;
printf("sizeof(a) = %ld\n",sizeof(a));  
printf("sizeof(int) = %ld\n",sizeof(int))
```

**练习：**

要求⾃⼰设计 3 个变量 a,b,c。分别⽤来保存 10、3.14、'M’这 3 个数据；分别利⽤ sizeof 输出 a,b,c 的⼤⼩；然后输出 a,b,c 的值。

```c
#include<stdio.h>
int main()
{
	int a = 10;
	double b = 3.14;
	char c = 'M';
	printf("sizeof(a) = %ld\n", sizeof(a));
	printf("sizeof(b) = %ld\n", sizeof(b));
	printf("sizeof(c) = %ld\n", sizeof(c));
	printf("a = %d\n", a);
	printf("b = %lf\n", b);
	printf("c = %c\n", c);
	return 0;
}

```

# 7.c语言中的输入函数

## 7.1 获取变量内存地址的方法

**格式**：& + 变量名

**说明**：& 是取地址符号，获得 a 变量在内存中的地址。使用%p 打印变量在内存中的地址信息

**例：**

```c
#include<stdio.h>
int main()
{
	int a;
	printf("%p\n", &a);
	return 0;
}
```

**使用 gcc 编译：默认以64位输出**

```
0x7ffcee2869d4
```

**使用 gcc -m32 编译：以32位输出（推荐）**

```
0xff829a98
```

## 7.2 scanf()函数

格式：scanf(“格式控制串”, 变量 1 的地址，变量 2 的地址…);

功能：从键盘输⼊数据存放到变量 1，变量 2…, 变量 n 所表示的内存单元。

### 7.2.1 ⼗进制数的输⼊ [%d]

格式：scanf("%d%d...",变量1的地址，变量2的地址....);

功能：⽤户从键盘输⼊整数赋值给变量,以空格，回⻋，tab键作为输⼊的分隔符号。

### 7.2.2 ⼩数的输⼊ [%f], [%lf]

格式：scanf("%f%f...",变量1的地址，变量2的地址....);

功能：⽤户从键盘输⼊⼩数赋值给变量，以空格，回⻋，tab键作为输⼊的分隔符号。

### 7.2.3 字符的输⼊ [%c]

格式：scanf("%c%c...",变量1的地址，变量2的地址....);

功能：⽤户从键盘输⼊字符赋值给变量。字符数据必须连续写，没有对应的分隔符号。

[注: '\n','\t',' '这些也都是有效的字符]

**练习：**

①要求⽤从键盘输⼊两个整形数据，赋值给 a 和 b，并输出a和b的值；利⽤ %p 输出 a 和 b 的地址观察结果。

```c
#include<stdio.h>
int main()
{
	int a, b;
	printf("please input two number:");
	scanf("%d%d", &a, &b);
	printf("a = %d, b = %d\n", a, b);
	printf("&a = %p, &b = %p\n", &a, &b);
}
```

②要求⽤从键盘输⼊两个字符型数据，赋值给 a 和 b，并输出a和b的值；利⽤ %p 输出 a 和 b 的地址观察结果。

```c
#include<stdio.h>
int main()
{
	char a, b;
	printf("please input two character:");
	scanf("%c%c", &a, &b);
	printf("a = %c, b = %c\n", a, b);
	printf("&a = %p, &b = %p\n", &a, &b);
	return 0;
}
```

# 8.数据在内存中的存储

数据类型中，整形和字符型都可以分为两种, 分别⽤两个关键字对应。

|          | signed                       | unsigned               |
| -------- | ---------------------------- | ---------------------- |
| 含义     | 有符号数据 【正数, 0, 负数】 | ⽆符号数据 【正数，0】 |
| 常⽤写法 | signed int                   | unsigned int           |
| 特点     | 可省略                       | 不可省略               |

**例：**

```c
signed char  a ;   
unsinged char b;
signed int c;     
unsinged int  d;
```

**8bit数据的存储：**

char，有符号类型，占 1bytes。 可以表示负数、0、正数。范围 [-128~127] 

unsigned char，⽆符号类型，占 1bytes。可以表示 0、正数。范围 [0~255]

**超出范围数据的计算方法：**

①范围

char [-128 ~ 127] 正数、负数、0

unsigned char [0 ~ 255] 正数、0

②设计规则

⽆符号类型的数原码、反码、补码是它本身。[正数和 0]

有符号类型的数的最⾼位表示符号位，0 表示为正数，1 表示为负数。

负数的反码 = 符号位不变，其他位按位取反

负数的补码 = 反码 + 1

③计算方法

先计算整数的补码 (即 = 右边的数)

把补码赋值给变量，然后观察变量的数据类型，若是为 unsinged char 类型，⼀定为正数或0，原、反、补⼀样，%d输出的原码就是补码，直接转换为元素输出即可。若是为 char 类型，观察变量内存存储数据的最⾼位，1表示为负数，%d输出需要转换为原码输出。

**例1：**

```c
#include <stdio.h>
int main()
{
    char  a = 200; 
    printf("a = %d\n",a);  
    return 0;
}         
```

分析：

200=128+64+8 ===> 1100	1000

因为以补码方式存储，所以200直接转换成二进制就得到补码，补码占8位，赋值给a，a为char类型占8位，所以不会被截断

a的补码：1100	1000，

a的原码：1011	1000

输出时候以原码输出，故需要将补码转换成原码，所以为-56

**例2：**

```c
 #include <stdio.h>
 int main()
 {
    unsigned char b = 280;
    printf("b = %d\n",b); 
    return 0;
 } 
```

分析：

280=256+16+8===>1	0001	1000，

因为以补码方式存储，所以280直接转换成二进制就得到补码，补码占9位，赋值给b，b为char类型占8位，所以会被截断，高位的1会被砍掉.

b的补码：0001	1000

b的原码：0001	1000

输出时候以原码输出，故需要将补码转换成原码，所以为24。

**练习：**

char a = 180;
unsigned char b = 300;
要求以上数据⽤ %d 输出，请⼤家⽤笔算了之后，在通过代码验证。

分析a：

180 = 128 + 32 + 16 + 4 ===> 1011	0100

a的补码：1011	0100

b的原码：1100	1100

输出：-76

分析b：

300 = 256 + 32 + 8 + 4 ===> 1	0010	1100

b的补码：0010	1100

b的原码：0010	1100

输出：44

# 9.强制数据类型转换

## 9.1 显式强转

采⽤某⽅⽅式将某种数据类型强制转换位我们需要的数据类型。

注：强转只是临时强转，本身的数据类型没有改变。

格式：(需要强制的数据类型) 变量名

**例：**

```c
#include <stdio.h>
int main()
{
        int a = 0;
        float b = 3.1415926;
        a = (int)b;
        printf("a = %d\n",a);
        return 0;
}
```

输出：a=3

## 9.2 隐式强转

若是⽤户使⽤运算符两边的类型不匹配，并且⽤户没有显示的指定匹配那种类型。系统会默认触发隐式的强转, 强转规则如下：

```
double ←←←←←← float			⾼
↑
↑
long
↑
↑
unsigned 
↑
↑
int ←←←←←← char,short		低
```

**例：**

```c
#include <stdio.h>
int main()
{
    int a = -20;            
    unsigned int b = 6;     
    if((a + b) > 0)
    {
    	printf("a + b > 0\n");        
    }
    else
    {
    	printf("a + b <= 0\n");        
    }
    printf("result = %u\n",a + b); 
    return 0;
}
```

输出：

a + b > 0
result = 4294967282

分析：int和unsigned int相遇，int会自动转换成unsigned int，所以-20变20与6进行相加，故a+b>0.

# 10.c语言中的数组

**数组**：相同数据类型变量的集合。数组是为⽤户处理多个数据⽽设计, 使⽤数组可以给多个变量分配多个连续的内存，节省变量名的消耗.

## 10.1 一维数组的定义

```
数据类型 数组名 [元素的个数];
```

**注意：**

①数据类型：char、short、int、float、double、long、long long ；

②数组名：合法的标识符，以数字，字符，下划线组成，⾸个单词要是字⺟或下划线；

③元素个数：要求是⼀个确定的常量值。

**例：int  t[5];**

①数组的成员：t[0]、t[1]、t[2]、t[3]、t[4]

②每个成员的类型：int 

③数组a的类型：int [5]

④整个数组的⼤⼩：sizeof(int [5]) 或 sizeof(a)

⑤数组⼀个元素的⼤⼩：sizeof(a[0])

⑥元素的个数：sizeof(a)/sizeof(a[0])

⑦数组名代表数组⾸元素的地址a <======> &a[0]

**思考：数组⾸地址t编译器是如何找到对应t[0]、t[1]、t[2]、t[3]内存块的数据呢？**

t[0]=====>表示数组的⾸地址a偏移0个元素的⼤⼩，[]取该地址中的内容

t[1]=====>表示数组的⾸地址a偏移1个元素的⼤⼩，[]取该地址中的内容

t[2]=====>表示数组的⾸地址a偏移2个元素的⼤⼩，[]取该地址中的内容

t[3]=====>表示数组的⾸地址a偏移3个元素的⼤⼩，[]取该地址中的内容

## 10.2 一维数组的初始化

在定义数组的同时，给数组中的每⼀个成员变量，赋予⼀个初始的值。

例如：

```c
int a[5] = {10,20,30,40,50};
```

例如：

```c
int a[5] = {10,20,30}; 
// 这种叫部分初始化，未初始化的值，系统默认为0，故全部元素为{10,20,30,0,0}
```

例如：

```c
int  a[] = {10,20,30,40,50,60,70};
int len = sizeof(a)/sizeof(a[0]);
// 特点：系统会根据⽤户初始化的元素个数来分配对应的内存空间。
```

错误写法：

```c
int a[5] = 1,2,3,4,5; //没加大括号

int a[5];     
a[5] = {1,2,3,4,5}; //数组下标最大到a[4]

int m = 5;
int a[m]; //数组定义时的大小为一个常量，而不是变量
```

练习：

int a[ ] = {10,15,27,33,78,65};

①要求⽤户输出上述数组的内容；

②要求求上述数组中奇数的和；

③求上述数据中所有元素的平均值，省略⼩数，输出整数。

```c
#include<stdio.h>
int main()
{
	int a[] = {10, 15, 27, 33, 78, 65};
	int len = sizeof(a) / sizeof(a[0]);
	int i, sum = 0;
	printf("数组中各元素为：\n");
	for(i = 0; i < len; i++)
	{
		printf("%d ", a[i]);
		if(a[i] % 2 != 0)
		{
			sum += a[i];
		}
	}
	printf("\n");
	printf("数组中所有元素的和为：%d\n", sum);
	printf("数组中所有元素的平均值为：%d\n", sum / len);
	return 0;
}

```

输出：

```
数组中各元素为：
10 15 27 33 78 65 
数组中所有元素的和为：140
数组中所有元素的平均值为：23
```



## 10.3 字符数组和字符串

### 10.3.1 字符数组

它是⼀个 char/unsigned char 类型的数组，常⽤来存放字符或字符串。

**例如：**

```c
char  buf[5] = {'A','B','C','D','E'};
// 这代表定义了一个字符数组，并不是字符串
// 字符串必须要在末尾加上元素'\0'
```

**思考：**字符数组中只能存放字符或字符串 , 这句话对不对？ 

不对，还可以存放整数。

```c
char buf[5] = {65,66,67,68,69};  
```

### 10.3.2 字符串

**三种写法：**

```c
 char buf1[30] = "welcome";
 char buf2[30] = {"welcome"};
 char buf3[30] = {'w','e','l','c','o','m','e','\0'};
```

**例：用这三种写法，分别输出。**

```c
#include <stdio.h>
int main()
{
        char buf1[] = {"hello"};
        char buf2[] = "hello";
        char buf3[] = {'h','e','l','l','o','\0'};
        int i = 0;
        printf("buf1 : ");
        for(i = 0;buf1[i] != '\0';i++)
        {
                printf("%c ",buf1[i]); 
        }
        printf("\n");
        printf("===============================\n");
        printf("buf2 : ");
        for(i = 0;buf2[i] != '\0';i++)
        {
                printf("%c ",buf2[i]);        
        }
        printf("\n");
        printf("===============================\n");
        printf("buf3 : ");
        for(i = 0;buf3[i] != '\0';i++)
        {
                printf("%c ",buf3[i]);        
        }
        printf("\n");
        return 0;
}
```

运⾏结果：

```
buf1 : h e l l o 
===============================
buf2 : h e l l o 
===============================
buf3 : h e l l o 
```

**字符串的输入：**

```c
char buf[100] = {0}; // 表示初始化一个空字符串，所有元素都是'\0'
scanf("%s",字符数组的⾸地址);   
```

功能：⽤户从键盘输⼊任意⼀段字符串，存放到buf中。以回⻋，空格，tab键盘作为⽤户输⼊的结束符号。

**字符串的输出：**

```c
char buf[] = {"hello world"};
printf("%s\n",字符数组的⾸地址); 
```


功能：输出数组中第⼀个'\0'之前所有的字符，并显示到屏幕上。若是⽤户对应字符数组中没有'\0'，则⽤户输出乱码。

例：输入一个字符串，并输出（测试一下输入的字符串中有空格的情况）。

```c
#include <stdio.h>
int main()
{
        char name[100];
        printf("please input your name : ");
        scanf("%s",name);
        printf("NAME\n");
        printf("%s\n",name); 
        return 0;
}
```

运行结果：

```
please input your name : jack
NAME
jack
```

例：定义一个长度为16的字符数组，不要初始化，分别将'h'、'e'、'l'、‘l'、'o'四个字符赋值给下标为0到4的元素，下标为5的元素不要赋值'\0'，用字符串的形式%s输出看看是否会乱码。

```c
#include<stdio.h>
int main()
{
	char buf[16];
	buf[0] = 'h';
	buf[1] = 'e';
	buf[2] = 'l';
    buf[3] = 'l';
	buf[4] = 'o';
	printf("%s\n", buf);
	return 0;
}
```

例：一个字符串中有多个’\0‘的时候，会输出第一个’\0‘之前的字符串。

```c
 #include <stdio.h>
 int main()
 {
	char buf[100] = {'h','e','l','\0','X','Y','Z','\0'};
	printf("buf = %s\n",buf);
	return 0;
 }
```

运行结果：

```
hello
```

**练习：**

char buf[100] = {0};

要求⽤户从键盘输⼊字符数串存放到buf中，若是⽤户输⼊的字符数组中存在⼤写字符，则转换为⼩写字符，若是⼩写字符则不管，然后输出⽤户输⼊的数据。

```c
#include<stdio.h>
int main()
{
	char buf[100] = {0};
	int i;
	printf("please input a string:\n");
	scanf("%s", buf);
	printf("your string:\n%s\n", buf);
	for(i = 0; buf[i] != '\0'; i++)
	{
		if(buf[i] >= 'A' && buf[i] <= 'Z')
		{
			buf[i] += 32;
		}
	}
	printf("after converting:\n%s\n", buf);
	return 0;
}

```

运行结果：

```
please input a string:
AbCdEfGh! 
your string:
AbCdEfGh!
after converting:
abcdefgh!
```

## 10.4 二维数组的定义

⼀维数组是相同数据类型元素的集合，但是只能表示⼀⾏数据。 若是存在⾏和列相关的信息 (例如矩阵)，我们就需要⽤⼆位数组来表示。

```
数据类型 数组名 [⾏数][列数];
```

**例：**

```c
int a[3][2];
//在内存中按照还是按照⼀维数组的顺序排序的。只不过，为了⽅便⼈们识别，我们是按照⼆维的来理解。
```

①数组在内存中所占大小：sizeof(a) or 元素个数 * 一个元素大小；

②内存的存放方式：按行优先存放；

③定义⼆维数组的时候，⾏数可以省略不写，系统会根据默认初始化元素的个数来分配对应的内存空间。但是列数⼀定要写。(因为⼆维数组默认按⾏来进⾏优先存放的)

# 11.c语言中的指针基础

## 11.1 指针基础

```
      write
 data ------>ram
      read
 ram  ------> data
```

**把数据写入内存，把数据从内存中读取出来，通常有两种方式：**

①通过操作变量名来实现

```c
int  a; 
a = 100;  
printf("a = %d\n",a); 
```

②通过内存地址来进行读写操作

```c
int  a;
```

内存地址的获得⽅法:  &a

规则：*  +  地址：访问地址中的内存

```c
*(&a) = 100 ;
printf("*(&a) = %d\n",*(&a));
```

**例：**

```c
#include <stdio.h>
int main()
{
    int a = 80;
    *(&a) = 66; 
    printf("*(&a) = %d\n",*(&a));
    printf("a = %d\n",a); 
    return 0;
}
```

运⾏结果：

```shell
*(&a) = 66
a = 66
```

**指针类型的变量：**

```
常量				 变量的类型
-------------------------------
10					int 
3.15				float 
'A'					char 
0xdff88				?
(内存地址)
```

思考：内存地址该⽤什么样的类型来保存呢？

答：为了解决这样的问题，C语⾔的设计者创建了指针类型，来保存内存地址。

## 11.2 指针的定义

```c
数据类型 * 指针变量名;
```

**例：**

```c
char * p;  
short * q;  
int * m;    
int  data = 10;
int * p = &data;
*p = 88;
printf("*p = %d\n",*p)
```

<img src="assets/image-20240220113449959.png" alt="image-20240220113449959" style="zoom:50%;" />

**例：**

```c
#include <stdio.h>
int main()
{
        int data1 = 0,data2 = 0;
        int * p = &data1;  
        int * q = &data2;  
        int sum = 0;
        printf("please input two data : ");
        scanf("%d%d",p,q);
        printf("data1 = %d data2 = %d\n",data1,data2);
        sum = *p + *q;
        printf("data1 + data2 = %d\n",sum);
        sum = *p - *q;
        printf("data1 - data2 = %d\n",sum);
        sum = data1 * data2;
        printf("data1 * data2 = %d\n",sum);
        sum = data1 / data2;
        printf("data1 / data2 = %d\n",sum);
        return 0;
}
```

运⾏结果：

```
please input two data : 20 10
data1 = 20 data2 = 10
data1 + data2 = 30
data1 - data2 = 10
data1 * data2 = 200
data1 / data2 = 2
```

## 11.3 c语言中的特殊指针

### 11.3.1 野指针

**野指针**：野指针指的是指针中保存的是⽆效的内存地址。⽤户直接使⽤，系统会提示段错误。

**例如：**

```c
int *p;
*p = 800;
```

Segmentation fault (core dumped) 

段错误：⼀般由⽤户访问了⾮法的内存所导致。

**例：**

```c
#include <stdio.h>
int main()
{
    int * p;
    *p = 800;
    printf("*p = %d\n", *p);
    return 0;
}
```

运行结果：

```
Segmentation fault (core dumped)
```

### 11.3.2 void * 指针

void * 是⼀种特殊的指针类型，可⽤于存放任意对象的地址。

**例如：**

```c
int  a = 10;
void *p = &a; 
```

**缺点**：由于不知道地址中存放的是何种类型的数据，因此不能直接操作void*指针所指的对象。

**例：**

```c
#include <stdio.h>
int main()
{
    int data = 100;
    void *p = &data;
    printf("result = %d\n", *(int *)p);
    return 0;
}
```

运⾏结果：

```
result = 100
```

### 11.3.3 NULL指针

```c
#define	NULL (void *)0 
```

**⽤户习惯：**

```c
int *p = NULL;
```

含义：定义指针的时候，⼀般会把指针的值初始化为0地址，仅仅⽤于初始化，0地址我们⽤户⼀般没有执⾏权限。直接对0地址操作操作，系统会提示段错误。例如：

```c
int *p = NULL; 
*p = 800;
```

Segmentation fault (core dumped) 

段错误：⼀般由⽤户访问了⾮法的内存所导致。

**例：**

```c
#include <stdio.h>
int main()
{
    int data = 800;
    int *p = NULL;
    p = &data;
    printf("result = %d\n", *p);
    return 0;
}
```

## 11.4 一级指针简介

```c
int m = 20;
int *p = &m;
// 指针变量 p 本身的数据类型：int *
// 指针变量保存的对象的数据类型： int
```

### 11.4.1 大小端模式

不同系统使⽤的CPU不同，对数据的存储形式也有不同，分为以下两种。

⼤端模式：ARM、摩托罗拉
⼩端模式：intel、MIPS

**⼤端模式：**内存的⾼地址存储数据的低位，内存的低地址存储数据的⾼位。（低地址存⾼位---低对⾼）
**⼩端模式：**内存的低地址存储数据的低位，内存的⾼地址存储数据的⾼位。（低地址存低位---低对低）

例：int x = 0x12345678; 

```tex
               ⼩端模式                  大端模式
===================================================================
低地址
0xdff30        0x78                     0x12                <-----
0xdff31        0x56                     0x34
0xdff32        0x34                     0x56
0xdff33        0x12                     0x78
⾼地址
```

注意：

1位十六进制数 = 4位二进制数

1byte = 8位二进制数

1byte = 2位十六进制数

### 11.4.2 指针的结论

在 32bit 的操作系统中，所有类型的指针变量都占用4bytes。[因为地址为 4bytes]

**示例代码：**

```c
#include <stdio.h>
int main()
 {
        char *x;
        short *y;
        int *z;
        printf("sizeof(x) = %d\n",sizeof(x));
        printf("sizeof(y) = %d\n",sizeof(y));
        printf("sizeof(z) = %d\n",sizeof(z));
        return 0;
}
```

