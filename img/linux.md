# ubuntu设置共享文件夹

sudo vmhgfs-fuse .host:/ /mnt/hgfs/ -o allow_other -o uid=1000 

# 查看所有进程

ps -elf

# 杀死pid的进程

sudo kill -9 (pid)

# nasm

## 寄存器

rbx, rcx, rdx, rsi, rdi, rbp 寄存器保存系统调用的参数

rax保存系统调用号

rcx可以用于计数，与loop循环指令有关

rbp基址寄存器，保存栈的起始地址

rsp栈顶寄存器，保存栈的顶部地址。始终指向栈顶

r8-r15

AX和al通常称为累加器，用累加器进行的操作可能需要更少时间，累加器可用于乘、除、输入/输出等操作

BX称为基地址寄存器，它可作为存储器指针来使用

CX称为计数寄存器，在循环和字符串操作时，要用它来控制循环次数；在位操作中，当移多位时，要用cl来

DX称为数据寄存器，在进行乘、除运算时，它可以为默认的操作数参与运算，也可用于存放I/O的端口地址

EAX是32位寄存器，AX是16位寄存器，AH, AL是8位寄存器 AH,AL分别为组成AX的高8位和低8位寄存器

1.EAX——累加寄存器（Accumulator Register）
低16位（AX=AH&AL）
作用：实现乘除运算、中间结果缓存
2.EBX——基址寄存器（Base Register）
低16位（BX=BH&BL）
作用：存储器指针
3.ECX——计数寄存器（Count Register）
低16位（CX=CH&CL）
作用：实现循环控制、进行串操作
4.EDX——数据寄存器（Data Register）
低16位（DX=DH&DL）
作用：实现乘除运算、中间结果缓存（与EAX类似）

## 

文件描述符0，1，2对应标准输入（stdin），（stdout），（stderr）

## 数据类型

| 类型 | 含义 | 长度（字节） |
| ---- | ---- | ------------ |
| db   | 字节 | 1            |
| dw   | 字   | 2            |
| dd   | 双字 | 4            |
| dq   | 四字 | 8            |

# 编译

```
nasm -f elf32/64 -g -o xxxxx.o xxxxx.asm

ld -m elf_i386 -o xxxxxx xxxxx.o
```



# 跳转

跳转指令分三类:
一、无条件跳转: JMP;
二、根据 CX、ECX 寄存器的值跳转: JCXZ(CX 为 0 则跳转)、JECXZ(ECX 为 0 则跳转);
三、根据 EFLAGS 寄存器的标志位跳转, 这个太多了.

根据标志位跳转的指令:

JE   ;等于则跳转
JNE  ;不等于则跳转

JZ   ;为 0 则跳转
JNZ  ;不为 0 则跳转

JS   ;为负则跳转
JNS  ;不为负则跳转

JC   ;进位则跳转
JNC  ;不进位则跳转

JO   ;溢出则跳转
JNO  ;不溢出则跳转

JA   ;无符号大于则跳转
JNA  ;无符号不大于则跳转
JAE  ;无符号大于等于则跳转
JNAE ;无符号不大于等于则跳转

JG   ;有符号大于则跳转
JNG  ;有符号不大于则跳转
JGE  ;有符号大于等于则跳转
JNGE ;有符号不大于等于则跳转

JB   ;无符号小于则跳转
JNB  ;无符号不小于则跳转
JBE  ;无符号小于等于则跳转
JNBE ;无符号不小于等于则跳转

JL   ;有符号小于则跳转
JNL  ;有符号不小于则跳转
JLE  ;有符号小于等于则跳转
JNLE ;有符号不小于等于则跳转

JP   ;奇偶位置位则跳转
JNP  ;奇偶位清除则跳转
JPE  ;奇偶位相等则跳转
JPO  ;奇偶位不等则跳转

# 读写

ssize_t read(int fd,void *buf,size_t count)
ssize_t write(int fd,const void *buf,size_t count)

# 标志位

CF（Carry Flag）进位标志

PF（Parity Flag）奇偶标志，如果“1”的个数为偶数，则PF的值为1，否则其值为0。

AF（Auxiliary Carry Flag）辅助进位标志：

​	在发生下列情况时，辅助进位标志AF的值被置为1，否则其值为0：

(1)在字操作时，发生低字节向高字节进位或借位时；
(2)在字节操作时，发生低4位向高4位进位或借位时。

ZF（Zero Flag）零标志，结果为0则ZF为1

OF（Overflow Flag）溢出标志，溢出为1，否则被清为0

SF（Sign Flag）

# CMP

CMP(比较)指令执行从目的操作数中减去源操作数的隐含减法操作，并且不修改任何操作数。

指令格式：CMP 目的操作数，源操作数

# ROS

```
roscore

rosrun turtlesim turtlesim_node

rosrun turtlesim turtle_teleop_key
```

# 将一个文件夹下的所有内容复制到另一个文件夹下

`cp -r /home/packageA/* /home/cp/packageB/`
或
`cp -r /home/packageA/. /home/cp/packageB/`
这两种方法效果是一样的。