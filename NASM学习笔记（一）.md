#NASM学习笔记

## 一、计算机组成基础知识

### 1、处理器

处理器是计算机的大脑，负责执行所有逻辑运算操作，是执行程序的部件。它管理计算机资源、执行进程调度

### 2、寄存器

X86的体系架构下，有八个通用寄存器：EAX, EBX, ECX, EDX, EBP, ESI, EDI, ESP。这些寄存器的低16位可以单独使用，去掉E就可以，目的是可以向下兼容。

这些寄存器主要可以用于处理器存储计算当中的立即数或者地址信息。

通常情况下，这些寄存器的功能如下：

EAX：Accumulator Register 保存一些操作的操作数，比如multiplication

EBX：Base Register 数据段的指针，一般指向数据段的首地址

ECX：Counter Register 计数器，通常用于循环计数和字符串操作

EDX：用做指向I/O端口的指针

ESI：Source Index-源变址寄存器，用做字符串操作中的源地址指针，也可以用做指向数据段的指针（Data Segment）

EDI：Destination Index-目的变址寄存器，字符串操作中用做目的地址指针，也可以用做多余的段地址（Extra Segment）

ESP：Stack Pointer 总是指向栈顶

EBP：Base Pointer 总是指向栈基

EIP是指令寄存器，它指向下一个要被执行的指令

计算机上当中还包含一些描述CPU状态的/CPU最近执行的计算操作的特殊寄存器。称为FLAGS

CarryFlag：如果计算中有进位，此bit被置为1

ZeroFlag：如果最近的计算结果是0，此位置为1

SignFlag：如果最近的有符号计算结果是负的，此位置为1

ParityFlag：如果最近的计算结果为奇数，此位置为1

InterruptFlag：如果此位被置为1，而后它将只会监听外部中断

### 3、总线

Bus表示一切CPU当中在两个部件间传递数据的通信媒介，分为数据总线、地址总线和控制总线。

### 4、系统时间

微处理器当中最基础的单元是逻辑门，他们表示逻辑上的0/1，而这些01串需要同步处理，所以产生时钟。控制总线上有一位用于时钟。

一条指令理论上可以分为四个处理阶段。

取指、译码、执行、写回

### 5、中断

中断可能产生于外部源或者是内部操作，在Linux系统中，80h 是OS进入中断处理例程的调用号，在windows系统中是21h。当中断发生的时候，处理器将会保存当前的上下文，然后调用ISR（中断处理例程）。

