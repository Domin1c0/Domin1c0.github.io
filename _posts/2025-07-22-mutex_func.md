---
layout: post
title: "mutex_func"
tags: [线程 线程同步]  # 自动添加标签
---

# 互斥锁主要相关函数

## pthread_mutex_t 类型

- 其本质是一个结构体，为简化理解，应用时可忽略其实现细节，简单当成整数看待
- `pthread_mutex_t mutex` 变量mutex只有两种取值 1, 0

### pthread_mutex_init 函数

函数描述：

- 初始化一个互斥锁（互斥量） ---> 初值可看作1

函数原型：

```c
int pthread_mutex_init(pthread_mutex_t *restrict mutex,
                        const pthread_mutexattr_t *restrict attr)`
```

函数参数：

- mutex：传出参数，调用时传 &mutex
- attr：互斥锁属性，是一个传入参数，通常传 NULL,选用默认属性（线程间共享）
- **restrict**关键字：只用于限制指针，告诉编译器，所有修改该指针指向内存中内容的操作，只能通过本指针完成;不能通过除本指针以外的其他变量或指针修改互斥量 mutex 的两种初始化方式:
  
  - 静态初始化：如果互斥锁 mutex 是静态分配的（定义在全局，或加了 static 关键字修饰），可以直接使用宏进行初始化
  - 动态初始化：局部变量应采用动态初始化
    - `pthread_mutex_init(&mutex, NULL)`

### pthread_mutex_destroy 函数

- 函数描述：

  - 销毁一个互斥锁
- 函数原型：

  - `int pthread_mutex_destroy(pthread_mutex_t *mutex)`
- 函数参数：

  - mutex -- 互斥锁变量

### pthread_mutex_lock 函数

- 函数描述：

  - 对互斥锁加锁，可理解为将 mutex--（减一）
- 函数原型：

  - `int pthread_mutex_lock(pthread_mutex_t *mutex)`
- 函数参数

  - mutex -- 互斥锁变量

### pthread_mutex_unlock 函数

- 函数描述：

  - 对互斥锁解锁，可理解为将 mutex++（加一）
- 函数原型：

  - `int pthread_mutex_unlock(pthread_mutex_t *mutex)`
- 函数参数

  - mutex -- 互斥锁变量

### pthread_mutex_trylock 函数

- 函数描述：

  - 尝试加锁
- 函数原型：

  - `int pthread_mutex_trylock(pthread_mutex_t *mutex)`
- 函数参数

  - mutex -- 互斥锁变量
