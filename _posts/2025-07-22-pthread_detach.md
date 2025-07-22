---
layout: post
title: "pthread_detach"
tags: [线程 线程相关函数]  # 自动添加标签
---

# 设置子线程为分离属性

## pthread_detach 函数

线程分离状态：指定该状态，线程主动与主控线程断开关系。线程结束后，其退出状态不由其他线程获取，而直接自己主动释放。网络、多线程服务器常用

函数描述：

- 实现线程分离

函数原型：

- `int pthread_detach(pthread_t thread)`

函数返回值：

- 成功：返回0
- 失败：返回错误号
