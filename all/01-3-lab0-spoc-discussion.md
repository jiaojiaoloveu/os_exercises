# lab0 SPOC思考题

## 个人思考题

---

能否读懂ucore中的AT&T格式的X86-32汇编语言？请列出你不理解的汇编语言。
- [x]  
- 能够读懂：）

>  可以读懂。

虽然学过计算机原理和x86汇编（根据THU-CS的课程设置），但对ucore中涉及的哪些硬件设计或功能细节不够了解？
- [x]  
- 我觉得我对中断的控制还是不十分了解 希望继续进行深入学习

<<<<<<< HEAD
<<<<<<< HEAD
>   
=======
> 中断寄存器和非通用寄存器等。
>>>>>>> 24f70cfb6a134251c8b733fa7b138f3923a52069
=======
>  对内存管理、进程调度、中断处理等方面都不是很了解。
>>>>>>> 790bc39b948c60181c85f58654a11682d075cbe2


哪些困难（请分优先级）会阻碍你自主完成lab实验？
- [x]  
- 1 对实验的细节了解的不详细 需要进一步学习ucore工作原理
- 2 硬件方面编程经验相对薄弱

>   1.对实验相关知识掌握得不够好
    2.对实验工具的使用不够熟悉
    3.调试过程不顺利

如何把一个在gdb中或执行过程中出现的物理/线性地址与你写的代码源码位置对应起来？
- [x]
- 可以使用break命令，在指定的位置停下，gdb调试中可以显示对应的物理地址

>   break + 行号 即可得到物理地址；
    list + \*物理地址 即可得到行号。

了解函数调用栈对lab实验有何帮助？
- [x]  
- 可以查看或修改相应位置上的数据内容，对调试有一定的帮助

<<<<<<< HEAD
<<<<<<< HEAD
>  
=======
> 除了错可以调试 
> 对于函数的调用过程和程序的运行过程有更好的理解。
> 便于调试以及检查。 
>>>>>>> 24f70cfb6a134251c8b733fa7b138f3923a52069
=======
>   可以帮助理解函数的调用层次和调用过程，帮助调试。
>>>>>>> 790bc39b948c60181c85f58654a11682d075cbe2

你希望从lab中学到什么知识？
- [x]  
- 学到操作系统管理系统的资源的基本原理和实现方法，争取将理论与实践相结合

>   操作系统的整体结构和各部分的实现细节；提高编程能力。

---

## 小组讨论题

---

搭建好实验环境，请描述碰到的困难和解决的过程。
- [x]  
- 无困难

> 已搭好。无。

<<<<<<< HEAD
<<<<<<< HEAD
熟悉基本的git命令行操作命令，从github上的[ucore git repo](http://www.github.com/chyyuu/ucore_lab)下载ucore lab实验
=======
熟悉基本的git命令行操作命令，从github上
的 http://www.github.com/chyyuu/ucore_lab 下载
ucore lab实验
>>>>>>> 24f70cfb6a134251c8b733fa7b138f3923a52069
=======
熟悉基本的git命令行操作命令，从github上的[ucore git repo](http://www.github.com/chyyuu/ucore_lab)下载ucore lab实验
>>>>>>> 790bc39b948c60181c85f58654a11682d075cbe2
- [x]  
- 完成

> 已完成。

尝试用qemu+gdb（or ECLIPSE-CDT）调试lab1
<<<<<<< HEAD
<<<<<<< HEAD
- [x]  
- 完成
=======
- [x]   
=======
- [x]  
>>>>>>> 790bc39b948c60181c85f58654a11682d075cbe2

> 已尝试。

对于如下的代码段，请说明”：“后面的数字是什么含义
```
/* Gate descriptors for interrupts and traps */
struct gatedesc {
    unsigned gd_off_15_0 : 16;        // low 16 bits of offset in segment
    unsigned gd_ss : 16;            // segment selector
    unsigned gd_args : 5;            // # args, 0 for interrupt/trap gates
    unsigned gd_rsv1 : 3;            // reserved(should be zero I guess)
    unsigned gd_type : 4;            // type(STS_{TG,IG32,TG32})
    unsigned gd_s : 1;                // must be 0 (system)
    unsigned gd_dpl : 2;            // descriptor(meaning new) privilege level
    unsigned gd_p : 1;                // Present
    unsigned gd_off_31_16 : 16;        // high bits of offset in segment
<<<<<<< HEAD
 };
 ```
>>>>>>> 24f70cfb6a134251c8b733fa7b138f3923a52069

- [x]  

<<<<<<< HEAD
对于如下的代码段，请说明”：“后面的数字是什么含义
```
/* Gate descriptors for interrupts and traps */
struct gatedesc {
    unsigned gd_off_15_0 : 16;        // low 16 bits of offset in segment
    unsigned gd_ss : 16;            // segment selector
    unsigned gd_args : 5;            // # args, 0 for interrupt/trap gates
    unsigned gd_rsv1 : 3;            // reserved(should be zero I guess)
    unsigned gd_type : 4;            // type(STS_{TG,IG32,TG32})
    unsigned gd_s : 1;                // must be 0 (system)
    unsigned gd_dpl : 2;            // descriptor(meaning new) privilege level
    unsigned gd_p : 1;                // Present
    unsigned gd_off_31_16 : 16;        // high bits of offset in segment
};
```
- [x]  
- 位域

>
=======
> 每一个filed(域，成员变量)在struct(结构)中所占的位数; 也称“位域”，用于表示这个成员变量占多少位(bit)。
>>>>>>> 24f70cfb6a134251c8b733fa7b138f3923a52069
=======
};
```
- [x]  

> 数字表示位域长度。
>>>>>>> 790bc39b948c60181c85f58654a11682d075cbe2

对于如下的代码段，
```
#define SETGATE(gate, istrap, sel, off, dpl) {            \
    (gate).gd_off_15_0 = (uint32_t)(off) & 0xffff;        \
    (gate).gd_ss = (sel);                                \
    (gate).gd_args = 0;                                    \
    (gate).gd_rsv1 = 0;                                    \
    (gate).gd_type = (istrap) ? STS_TG32 : STS_IG32;    \
    (gate).gd_s = 0;                                    \
    (gate).gd_dpl = (dpl);                                \
    (gate).gd_p = 1;                                    \
    (gate).gd_off_31_16 = (uint32_t)(off) >> 16;        \
}
```
如果在其他代码段中有如下语句，
```
unsigned intr;
intr=8;
SETGATE(intr, 0,1,2,3);
```
请问执行上述指令后， intr的值是多少？
<<<<<<< HEAD
<<<<<<< HEAD
=======
=======
- [x]  
>>>>>>> 790bc39b948c60181c85f58654a11682d075cbe2

> 65538

请分析 [list.h](https://github.com/chyyuu/ucore_lab/blob/master/labcodes/lab2/libs/list.h)内容中大致的含义，并能include这个文件，利用其结构和功能编写一个数据结构链表操作的小C程序
>>>>>>> 24f70cfb6a134251c8b733fa7b138f3923a52069
- [x]  
- 65538

>

请分析 [list.h](https://github.com/chyyuu/ucore_lab/blob/master/labcodes/lab2/libs/list.h)内容中大致的含义，并能include这个文件，利用其结构和功能编写一个数据结构链表操作的小C程序
- [x]  
```
#include <iostream>
#include "list.h"

int main(int argc, const char * argv[])
{
list_entry_t a0,a1,a2,a3;

<<<<<<< HEAD
list_init(&a0);
printf("%d %d %d\n",a0.prev, a0.next, &a0);

a0.prev = NULL;
a0.next = &a1;
a1.prev = &a0;
a1.next = &a2;
a2.prev = &a1;
a2.next = NULL;

list_add(&a1, &a3);

printf("%d %d %d\n",a0.prev, a0.next, &a0);
printf("%d %d %d\n",a1.prev, a1.next, &a1);
printf("%d %d %d\n",a3.prev, a3.next, &a3);
printf("%d %d %d\n",a2.prev, a2.next, &a2);


list_del(&a1);
printf("%d %d %d\n",a0.prev, a0.next, &a0);
printf("%d %d %d\n",a2.prev, a2.next, &a2);
printf("%d %d %d\n",a3.prev, a3.next, &a3);
}
```
> 
=======
> 是一个双向链表的简单实现，而且还有各种操作接口。编写的程序如下：
>>>>>>> 790bc39b948c60181c85f58654a11682d075cbe2

```
  #include <stdio.h>
  #include "list.h"

  int main(int argc, char *argv[])
  {
      list_entry_t le0, le1, le2, le3;
      list_init(&le0);
      printf("%d %d %d\n", le0.prev, le0.next, &le0);
      le0.prev = NULL;
      le0.next = &le1;
      le1.prev = &le0;
      le1.next = &le2;
      le2.prev = &le1;
      le2.next = NULL;
      list_add(&le1, &le3);
      printf("%d %d %d\n", le0.prev, le0.next, &le0);
      printf("%d %d %d\n", le1.prev, le1.next, &le1);
      printf("%d %d %d\n", le2.prev, le2.next, &le2);
      printf("%d %d %d\n", le3.prev, le3.next, &le3);
      list_del(&le1);
      printf("%d %d %d\n", le0.prev, le0.next, &le0);
      printf("%d %d %d\n", le2.prev, le2.next, &le2);
      printf("%d %d %d\n", le3.prev, le3.next, &le3);
      return 0;
  }
```
---

## 开放思考题

---

是否愿意挑战大实验（大实验内容来源于你的想法或老师列好的题目，需要与老师协商确定，需完成基本lab，但可不参加闭卷考试），如果有，可直接给老师email或课后面谈。
- [x]  

>  

---
