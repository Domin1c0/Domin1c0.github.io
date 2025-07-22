---
layout: post
title: "abort&arise"
tags: [进程 信号]  # 自动添加标签
---

# abort & raise 函数

## raise 函数

- 函数描述：给当前进程发送指定信号（自己）
- 函数原型：`int raise(int sig)`
- 函数返回值：成功为 0, 失败非0值
- 函数拓展：`raise(signo) == kill(getpid(), signo)`

## abort 函数

- 函数描述：给自己发送异常终止信号 6）SIGABRT，并产生core文件
- 函数原型：`void abort(void)`
- 函数拓展：`abort() == kill(getpid(), SIGABRT)`
