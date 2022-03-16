---
# try also 'default' to start simple
# theme: seriph
theme: bricks
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
---

# 前端观察

2022-03-17

---

# 数据结构与算法图解

<img src="/images/p1.jpg" class="h-100 rounded shadow" />

---

# 数据结构

数据的组织形式

- 数组
  - 有序数组
- 散列表
- 栈
- 队列
- 链表
  - 双向链表
- 树
  - 二叉树
- 图

---

# 时间复杂度

操作数据结构的速度，并不按时间计算，而是按步数计算

操作在数组上的运行速度

- 读取 - 1 步
- 查找 - N 步
- 插入 - N + 1 步
- 删除 - N 步

---

# 大O记法


- 常数时间 O(1)
- 线性时间 O(N)
- 对数时间 O(log N)
- 二次时间 O(N²)

---

# 算法

解决某个问题的一套流程

- 线性查找
- 二分查找
- 冒泡排序
- 选择排序
- 插入排序
- 广度优先搜索