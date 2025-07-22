---
layout: post
title: "pthread_attr"
tags: [线程 线程相关函数]  # 自动添加标签
---

# 创建线程时的线程属性设置

- 第1步：定义线程属性类型的变量

  - `pthread_attr_t attr`
- 第2步：对线程属性变量进行初始化

  - `int pthread_attr_init(pthread_attr_t *attr)`
- 第3步：设置线程为分离属性

  - `int pthread_attr_setdetachstate(pthread_attr_t *attr, int detachstate)`

- 参数：

  - attr：线程属性
  - detachstate：

    - PTHREAD_CREATE_DETACHED（分离）
    - PTHREAD_CREATE_JOINABLE（非分离）
  - **注意**：上述三步就是为 pthread_create 的第二个参数做准备工作
- 第4步：释放线程属性资源

  - `int pthread_attr_destroy(pthread_attr_t *attr)`
