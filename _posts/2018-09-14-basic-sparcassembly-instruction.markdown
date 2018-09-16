---
layout: post
title:  Spark Assembly Instructions
date:   2018-09-14 10:09:48 +0800
description: Basic Sparc Instructions # Add post description (optional)
img: sparclogo.jpg # Add image post (optional)
tags: [Blog, Tech, Assembly]
author: Zhang # Add name author (optional)
---
## Registers ##
    - First 6 integer arguments passed in %o0 – %o5
        - Other or additional arguments passed on stack
    - %g0 reads as zero, writes ignored
    - Put return value in %i0
    - Return address in %i7，but need to add 8
    - Stack Pointer in %sp, it points to current stack top
    - Frame Pointer in %fp, it points to current stack buttom


<h2>Instructions</h2>

| Instruction | Meaning |
|:----------------|:--------------------|
| ld addr, %reg   | 从addr中加载一个字的数据(32位)放入reg   |
| st %reg, addr   | 把reg中的32位字数据存储到addr   |
| sethi const22,%reg | 设置%reg的高22位 |
| %hi(X) | 取X的高22位 |

| Synthetic Instruction | SPARC-V9 instruction(s) | Meaning |
|:----------------|:--------------------|:--------------------|
| save/restore |  save/restore %g0, %g0, %g0 | 用来操控寄存器窗口,详细见[Save and Restore](http://www.mathcs.emory.edu/~cheung/Courses/255/Syllabus/8-SPARC/save+restore.html) |
| ret | jmpl %i7+8, %g0 | 从子程序返回 |
| clr [addr] | st %g0,[address] | [addr] = 0x0 |
| clr %reg | or %g0,%g0,%reg | [%reg] = 0x0 |
| cmp %reg1, %reg2/const, %g0 | subcc %reg1,%reg2/const,%g0 | %reg1 - %reg2/const = %g0 |

## Resource
[Knowledge Prepare (pdf)]({{site.basurl}}/assets/doc/prepare_knowledge.pdf)<br>
[Sparc V9 Brief Introduction (pdf)]({{site.basurl}}/assets/doc/sparcV9_brief_introduction.pdf)<br>
[Sparc Overview (pdf)]({{site.basurl}}/assets/doc/spark_overview.pdf)<br>
[Sparc Basic Instruction Set](http://moss.csc.ncsu.edu/~mueller/codeopt/codeopt00/notes/sparc.html)
[Sparc Instruction Set (xls)]({{site.basurl}}/assets/doc/sparc_instruction_set.xls)<br>
[Sparc Subroutine Analysis](http://blog.sina.com.cn/s/blog_4b46cfa801011eiz.html)

## More
[WIKI Online Book - SPARC Assembly](https://en.wikibooks.org/wiki/SPARC_Assembly)<br>
[Sparc V9 (pdf)]({{site.basurl}}/assets/doc/sparcV9.pdf)<br>

![steinsgate]({{site.baseurl}}/assets/img/steinsgate.jpg)