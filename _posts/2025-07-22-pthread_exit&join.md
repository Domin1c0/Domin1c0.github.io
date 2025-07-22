---
layout: post
title: "pthread_exit&join"
tags: [线程 线程相关函数]  # 自动添加标签
---

# 线程的退出和回收

## pthread_exit 函数

在线程中禁止调用 exit 函数，否则会导致整个进程退出，取而代之的是调用 pthread_exit 函数，这个函数是使一个线程退出，**如果主线程调用 pthread_exit 函数也不会使整个进程退出，不影响其他线程的执行**

函数描述：

- 将单个进程退出

函数原型：

- `void pthread_exit(void *retval)`

函数参数：

- retval 表示线程退出状态，通常传 NULL

## pthread_join 函数

函数描述：阻塞等待线程退出，获取线程退出状态;其作用对应进程中的 waitpid() 函数

函数原型：

- `int pthread_join(pthread_t thread, void **retval)`

函数返回值

- 成功：返回 0
- 失败：返回错误号

函数参数：

- thread：线程 ID
- retval：存储线程结束状态，整个指针和 pthread_exit 的参数是同一块内存
