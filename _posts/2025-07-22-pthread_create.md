---
layout: post
title: "pthread_create"
tags: [进程, 线程相关函数]  # 自动添加标签
---

# pthread_create 函数

函数作用：

- 创建一个新线程

函数原型：

```c
int pthread_create(pthread_t *thread, const pthread_attr_t *attr, 
                    void *(*start_routine)(void *), void*arg)
```

返回值：

- 成功：返回0
- 失败：返回错误号

函数参数:

- pthread_t：传出参数，保存系统为我们分配好的线程 ID

  - 当前linux中可以理解为：`typedef unsigned long int pthread_t`

- attr：通常传NULL,表示使用线程默认属性;若想使用具体属性也而已修改该参数
- start_routine：函数指针，指向线程主函数（线程体），该函数运行结束，则线程结束
- arg：线程主函数执行期间所使用的参数

**注意点**：

- 由于pthread_create的错误码不保存在 errno 中，因此不能直接用perror()打印错误信息，可以先用 strerror()把错误码转换成错误信息再打印
- 如果任意一个线程调用了 exit 或 _exit，则整个进程的所有线程终止
