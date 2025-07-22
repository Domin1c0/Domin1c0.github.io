---
layout: post
title: "setistimer"
tags: [进程 信号]  # 自动添加标签
---

# setitimer 函数

函数原型：

- `int setitimer(int which,const struct itimerval *new_value, strut itimerval *old_value)`

函数描述：

- 设置定时器（闹钟），可代替 alarm 函数，精度微秒 us，可以实现周期定时

函数返回值；

- 成功：0
- 失败：-1,设置 errno 值

函数参数：

- which：指定定时方式

  - **自然定时：ITIMER_REAL -> 14）SIGALRM 计算自然时间**
  - 虚拟空间计时（用户空间）：ITIMER_VIRTUAL -> 26）SIGVTALRM 只计算进程占用 cpu 时间
  - 运行时计时（用户+内核）：ITIMER_PROF -> 27）SIGPROF 计算占用 cpu 及执行系统调用的时间

- new_value: struct itimerval， 负责设定 timeout 时间

  - itimerval.it_value：设定第一次执行 function 所延迟的秒数
  - itimerval.it_interval：设定以后每几秒执行function

```c
struct itimerval
{
    struct timerval it_interval;    //闹钟触发周期
    struct timerval it_value;       //闹钟触发时间
}
```

```c
struct timeval
{
    long tv_sec;    #秒
    long tv_usec;   #微秒
}
```
