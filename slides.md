---
theme: default 

drawings:
  presenterOnly: true

layout: cover
---


# 稠密矩阵乘在单核上的优化

2022-07-06 满洋


<!-- 开场题外话：为什么学习计算机系统
    1. 设计计算机系统
    2. 都是写代码，你写的就比别人快
    3. 底层bug只有你能debug

 -->

---


# 稠密矩阵乘在单核上的优化

<!-- 稠密vs稀疏：
    1. 什么是稠密矩阵
    2. 图的邻接矩阵是典型的稀疏矩阵
    3. 神经网络的稀疏性

 -->

主要内容：

- 计算机系统性能评价指标
- CPU 微架构简介
- Roofline Model
- 实际优化 sgemm
    - SIMD
    - Packing
    - Cache Blocking
- 进阶资料

---


# 计算机系统性能评价指标

<!-- 延迟vs吞吐量：
    1. 买菜，1h 1份
    2. 每天买菜
    3. 同样的菜，1h，30份

 -->

- 延迟
  - 指令延迟/CPI
  - 访存延迟
  - 通信延迟
- 吞吐量
  - 每周期指令数(IPC)
  - 访存带宽
  - 通信带宽

--- 
layout: two-cols
---

<template v-slot:default>

# HPC 系统性能指标

- 峰值算力 (xxops)
  - 整数 (Ops)
  - 浮点 (Flops)
</template>

<template v-slot:right>

![](/Nvidia-H100.png)

</template>

---

## A100 Sparse Tensor core

<Transform :scale="0.9">

![](/Nvidia-A100-sparse-tensor-core.png)


</Transform>

---

## 实例

<!-- 
    1. HPC 测试报告
    2. 工作站机器 https://en.wikichip.org/wiki/intel/xeon_w/w-2123
 -->
---

# 现代 CPU 微架构简介

- 体系结构八大思想
- 冯·诺伊曼结构
- 指令和指令系统
- 流水线结构
- 超标量乱序
- 存储体系
- 分支预测

---

## 体系结构八大思想

<!-- 计组考试：
    1. 和毛概的相似性
    2. 和毛概的不同：从事此方面工作，就是重要的要牢记
 -->


- 面向摩尔定律的设计
- 抽象化设计
- 加速经常性事件
- 通过并行提升性能
- 通过冗余提高可靠性
- 存储层次
- 通过预测提高性能
- 通过流水线提高性能

---

## 冯·诺伊曼结构


冯·诺伊曼结构（英语：Von Neumann architecture）是一种将程序指令存储器和数据存储器合并在一起的电脑设计概念结构。是一种实作通用图灵机的计算装置。

本架构隐约指导了将储存装置与中央处理器分开的概念，因此依本架构设计出的计算机又称存储程序计算机。


<Transform :scale="0.3">

![](/Von-Neumann.png)
</Transform>

---

## 指令系统

<Transform :scale="1">

![](/Instr-System.png)

</Transform>

---

## 指令系统

<Transform :scale="0.7">

![](/Instr-Encode.png)

</Transform>

---

## 经典 CPU 结构

<Transform :scale="1">

![](/Five-Stage.png)

</Transform>


---

## 流水线结构

<Transform :scale="1.3">

![](/CPU-laundry1.gif)

</Transform>

---

## 流水线结构

<Transform :scale="1.2">

![](/CPU-laundry2.gif)

</Transform>

---

## 流水线结构

<Transform :scale="0.9">

![](/CPU-pipeline.svg)

</Transform>

---

## 分支预测

- 解决流水线增长带来的分支惩罚

---

## 超标量乱序

- [Intel Sunny Cove](https://en.wikichip.org/wiki/intel/microarchitectures/sunny_cove)
- [AMD Zen2](https://en.wikichip.org/wiki/amd/microarchitectures/zen_2)
- [ARM Cortex-A510](https://en.wikichip.org/wiki/arm_holdings/microarchitectures/cortex-a510)

---



## 存储体系


<Transform :scale="0.8">

![](/Storage-Hierachacy.png)

</Transform>

---
layout: two-cols
---


<template v-slot:default>

# Roofline Model

- 计算强度
- 确定瓶颈

$def:  计算强度  = \frac{峰值算力/Flops}{峰值带宽/Bps}$

</template>
<template v-slot:right>

![](/Roofline-sw26010.png)

</template>

---

# SGEMM 优化

- SIMD
- Packing
- Cache Blocking


---
layout: two-cols
---

<template v-slot:default>

## 进阶资料

- [Denis Bakhvalov's Perf Book](https://book.easyperf.net/perf_book)
- [Perf-Ninja](https://github.com/dendibakh/perf-ninja)

</template>
<template v-slot:right>

<Transform :scale="0.5">

![](/Group.jpg)

</Transform>

</template>
