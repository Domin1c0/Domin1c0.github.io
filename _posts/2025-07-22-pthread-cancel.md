---
layout: post
title: "pthread-cancel"
tags: [进程, 线程相关函数]  # 自动添加标签
---

# 取消线程

## pthread_cancel 函数

函数描述：

- 杀死（取消）线程;其作用对应进程中的kill()函数

函数原型

- `int pthread_cancel(pthread_t thread)`

函数返回值：

- 成功：返回0
- 失败：返回错误号

**注意**：线程的取消并不是实时的，而有一定的延时，需要等待线程到达某个取消点（检查点）

##

取消点设置：

- `void pthread_testcancel(void)`
