---
layout: post
title: "process_cmd"
tags: [进程, 进程相关函数]  # 自动添加标签
---

# 进程管理常用命令

## ps 命令

- `ps aux | grep "xxx"` -- 列出所有正在运行的 bash 进程（包括你当前使用的 shell）
- `ps ajx | grep "xxx"`
  
  - -a:当前系统所有用户的进程
  - -u:查看进程所有者及其他信息
  - -x:显示没有控制终端的进程--不能与用户进行交互的进程
  - -j:列出与作业控制相关的信息

## kill 命令

- `kill -l` 查看系统有哪些信号
- `kill -9 pid` 杀死某个线程
