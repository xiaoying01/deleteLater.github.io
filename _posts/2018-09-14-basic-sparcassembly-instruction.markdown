---
layout: post
title:  Spark Assembly Instructions
date:   2018-09-14 10:09:48 +0800
description: Basic Sparc Instructions # Add post description (optional)
img: sparclogo.jpg # Add image post (optional)
tags: [Blog, Tech, Assembly]
author: Zhang # Add name author (optional)
---
Basic sparc instruction set

Instruction   | Meaning
------------- | -------------------------
ld addr, %reg | 从addr中取32位字数据放人reg
st %reg, addr | 把reg中的32位字数据保存到addr

> Please visit [oracle-sparcassembly-manual][oracle-sparcassembly-docs] for more details.

![SteinsGate_Christina]({{site.baseurl}}/assets/img/SteinsGate_Christina.jpg)

[oracle-sparcassembly-docs]: https://docs.oracle.com/cd/E18752_01/html/816-1681/toc.html
