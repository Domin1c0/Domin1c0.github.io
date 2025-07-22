---
layout: post
title: "condition"
tags: [进程, 线程同步]  # 自动添加标签
---

# 条件变量

条件变量本身不是锁，但它可以造成线程阻塞，通常与互斥锁配合使用

- 使用互斥量保护数据
- 使用条件变量可以使线程阻塞，等待某个条件的发生，当条件满足的时候接触阻塞

条件变量的两个动作：

- 条件不满足--阻塞进程
- 条件满足--通知阻塞的线程解除阻塞开始工作

## 条件变量相关函数

- `pthread_cond_t cond`

  - 定义一个条件变量
- `int pthread_cond_init(pthread_cond_t *restrict cond, const pthread_condattr_t *restrict attr)`

  - 函数描述：初始化条件变量
  - 函数参数：

    - cond：条件变量
    - attr：条件变量属性，通常传NULL
  - 函数返回值：成功返回0,失败返回错误号
- `int pthread_cond_destroy(pthread_cond_t *cond)`

  - 函数描述：销毁条件变量
  - 函数参数：条件变量
  - 函数返回值：成功返回0,失败返回错误号
- `int pthread_cond_wait(pthread_cond_t *restrict cond, pthread_mutex_t *restrict mutex)`

  - 函数描述：
  
    - 条件不满足，引起线程阻塞并解锁
    - 条件满足，解锁线程阻塞并加锁
  - 函数参数：
  
    - cond：条件变量
    - mutex：互斥锁变量
  - 函数返回值：成功返回0,失败返回错误号
- `int pthread_cond_signal(pthread_cond_t *cond)`

  - 函数描述：唤醒至少一个阻塞在该条件变量上的线程
  - 函数参数：条件变量
  - 函数返回值：成功返回0,失败返回错误号
