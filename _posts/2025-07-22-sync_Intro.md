---
layout: post
title: "sync_Intro"
tags: [线程 线程同步]  # 自动添加标签
---

# 线程同步

## 线程同步概念

线程同步，指一个线程发出某一功能调用时，在没有得到结果之前，该调用不返回，同时其他线程为保证数据一致性，不能调用该功能

## 线程同步例子

创建两个线程，让两个线程共享一个全局变量 int number,然后让每个线程数 5000 次数，看最后打印出这个 number 值是多少

```c++
//宏和全局变量
#define NUM 5000
int number = 0;

//线程执行函数1
void *mythread1(void *arg)
{
    int i = 0;
    int n;
    for(i = 0; i < NUM; i++)
    {
        n = number;
        n++;
        number = n;
    }
}
//线程执行函数2
void *mythread2(void *arg)
{
    int i = 0;
    int n;
    for(i = 0; i < NUM; i++)
    {
        n = number;
        n++;
        number = n;
    }
}
```
