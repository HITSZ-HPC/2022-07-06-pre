---
theme: default 

drawings:
  presenterOnly: true

layout: cover
---


# 稠密矩阵乘在单核上的优化

2022-07-06 满洋

---


# 计算机系统性能评价指标

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

# 现代 CPU 微架构简介

- 指令和指令系统
- 冯·诺伊曼结构
- 流水线结构
- 超标量乱序
- 存储体系
- 分支预测

---

## 指令系统

---

## 冯·诺伊曼结构

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

## 超标量乱序

---

## 存储体系

---

## 分支预测

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



