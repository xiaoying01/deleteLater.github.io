---
layout: post
title:  Spark Assembly Instructions
date:   2018-09-14 10:09:48 +0800
description: Basic Sparc Instructions # Add post description (optional)
img: sparclogo.jpg # Add image post (optional)
tags: [Blog, Tech, Assembly]
author: Zhang # Add name author (optional)
---
## Sparc
&nbsp;&nbsp;Sparc,意为可拓展处理器架构(Scalable Processor Architecture),是RISC(精简指令集)微处理架构之一。
更多待补充...

## Registers
  ![Registers]({{site.baseurl}}/assets/img/sparc_integer_regs.png)
  
{::options parse_block_html="true" /}
<div class="panel panel-default">
<div class="panel-heading">![Tip]({{site.baseurl}}/assets/img/tip.png)&nbsp;&nbsp;&nbsp;&nbsp;**NOTE**
</div>
<div class="panel-body">
  - 函数的前6个参数通过 寄存器o0~05来传递,第七个参数及以后的参数通过栈空间传递
    - 第七个参数开始于 %sp+0x5c(32位环境) 或者 %sp+0x8af(64位环境) 参阅[参数传递][sparc_args_pass]
  - 有关寄存器窗口,简要参阅[寄存器窗口][sparc_register_windows]
  - 子程序一般把返回值放在i0,因为窗口重叠,相应的调用者通过o0获取该返回值,请务必参阅[Sparc子程序调用分析][sparc_subroutine_analysis]
  - 子程序返回地址在 %i7+8
  - %sp,看作栈顶指针
  - %fp,看作栈底指针
</div>
</div>

## Stack Frame
  ![Stack Frame]({{site.baseurl}}/assets/img/stack_frame.png)

## Instructions

| 指令 | 意思 |
|:----------------|:--------------------|
| ld addr, %reg   | 从addr中加载一个字的数据(32位)放入reg   |
| st %reg, addr   | 把reg中的32位字数据存储到addr   |
| sethi const22,%reg | 设置%reg的高22位 |
| %hi(X) | 取X的高22位 |
{:.table .table-striped}

| 合成指令 | 对应的实际指令 | 意思 |
|:----------------|:--------------------|:--------------------|
| save/restore |  save/restore %g0, %g0, %g0 | 用来操控寄存器窗口,请务必参阅[Save and Restore](http://www.mathcs.emory.edu/~cheung/Courses/255/Syllabus/8-SPARC/save+restore.html) |
| ret | jmpl %i7+8, %g0 | 从子程序返回 |
| clr [addr] | st %g0,[address] | 清空addr所放的值 |
| clr %reg | or %g0,%g0,%reg | 清空reg里所放的值 |
| cmp %reg1, %reg2/const, %g0 | subcc %reg1,%reg2/const,%g0 | 看这个等式,%reg1 - %reg2/const = %g0 |
| clrx [address] | stx %g0, [address] | 清空一个拓展字(8字节) |
| setuw/set value,%reg |Sparc V9 (pdf) P320 | 给reg设字(4字节)值 |
{:.table .table-striped}

## Resource
[知识准备 (pdf)]({{site.basurl}}/assets/doc/prepare_knowledge.pdf)<br>
[简要概述 (pdf)]({{site.basurl}}/assets/doc/sparcV9_brief_introduction.pdf)<br>
[架构概述 (pdf)]({{site.basurl}}/assets/doc/sparc_overview.pdf)<br>
[基本指令](http://moss.csc.ncsu.edu/~mueller/codeopt/codeopt00/notes/sparc.html)<br>
[指令集 (xls)]({{site.basurl}}/assets/doc/sparc_instruction_set.xls)<br>

## More
[Sparc汇编 (Wiki书籍)](https://en.wikibooks.org/wiki/SPARC_Assembly)<br>
[Sparc完整介绍 (pdf)]({{site.basurl}}/assets/doc/sparcV9.pdf)

[sparc_subroutine_analysis]: http://blog.sina.com.cn/s/blog_4b46cfa801011eiz.html
[sparc_register_windows]: https://en.wikipedia.org/wiki/Register_window
[sparc_args_pass]: https://docs.oracle.com/cd/E36784_01/html/E36858/gmado.html