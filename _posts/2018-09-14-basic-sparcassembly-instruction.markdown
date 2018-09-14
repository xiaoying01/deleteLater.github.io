---
layout: post
title:  Spark Assembly Instructions
date:   2018-09-14 10:09:48 +0800
description: Basic Sparc Instructions # Add post description (optional)
img: sparclogo.jpg # Add image post (optional)
tags: [Blog, Tech, Assembly]
author: Zhang # Add name author (optional)
---
## Registers
    - First 6 integer arguments passed in %o0 – %o5
        - Other or additional arguments passed on stack
    - Return value in %i0
    - Return address in %i7，but need to add 8


<h2>Basic sparc instruction set</h2>

| Instruction | Meaning |
|:----------------|:--------------------|
| ld addr, %reg   | 从addr中取32位字数据放人reg   |
| st %reg, addr   | 把reg中的32位字数据保存到addr   |
| save %sp, -imm, %sp | 分配一个大小为imm的内存堆栈 |
| restore %sp, imm, %sp | 与save相反,释放大小为imm内存堆栈 |

## Resource Reference
[Sparc V9 (pdf)]({{site.basurl}}/assets/doc/sparcV9.pdf)<br>
[Sparc V9 Brief Introduction (pdf)]({{site.basurl}}/assets/doc/sparcV9_brief_introduction.pdf)<br>
[Sparc Overview (pdf)]({{site.basurl}}/assets/doc/spark_overview.pdf)<br>
[Sparc Instruction Set (xls)]({{site.basurl}}/assets/doc/sparc_instruction_set.xls)<br>

![SteinsGate_Christina]({{site.baseurl}}/assets/img/SteinsGate_Christina.jpg)

