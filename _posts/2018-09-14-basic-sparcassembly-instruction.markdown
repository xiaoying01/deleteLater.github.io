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
    - Return value in %i0
    - Return address in %i7，but need to add 8
    - Stack Pointer in %sp, it points to current stack top
    - Frame Pointer in %fp, it points to current stack buttom


<h2>Instruction set</h2>

| Instruction | Meaning |
|:----------------|:--------------------|
| ld addr, %reg   | 从addr中取32位字数据放人reg   |
| st %reg, addr   | 把reg中的32位字数据保存到addr   |
| save | 保存当前窗口并创建一个新窗口 |
| ret | 从函数返回 |
| restore | 恢复上一个保存的窗口 |

## Resource Reference
[Knowledge Prepare (pdf)]({{site.basurl}}/assets/doc/prepare_knowledge.pdf)<br>
[Sparc V9 Brief Introduction (pdf)]({{site.basurl}}/assets/doc/sparcV9_brief_introduction.pdf)<br>
[Sparc Overview (pdf)]({{site.basurl}}/assets/doc/spark_overview.pdf)<br>
[Sparc Instruction Set (xls)]({{site.basurl}}/assets/doc/sparc_instruction_set.xls)<br>
[Sparc Subroutine Analysis](http://blog.sina.com.cn/s/blog_4b46cfa801011eiz.html)

## More Details
[WIKI Online Book - SPARC Assembly](https://en.wikibooks.org/wiki/SPARC_Assembly)<br>
[Sparc V9 (pdf)]({{site.basurl}}/assets/doc/sparcV9.pdf)<br>

![steinsgate]({{site.baseurl}}/assets/img/steinsgate.jpeg)
