---
layout: post
title: "semaphore"
tags: [线程 线程同步]  # 自动添加标签
---

# 信号量

## 信号量介绍

信号量相当于多把锁，可以理解为是加强版的互斥锁

## 相关函数

- 定义信号量 `sem_t sem`
- `int sem_init(sem_t *sem, int pshared, unsigned int value)`

  - 函数描述：初始化信号里
  - 函数参数：
  
    - sem：信号量变量
    - pshared：0 表示线程同步，1 表示进程同步
    - value：最多有几个线程操作共享数据
  - 函数返回值：成功返回 0, 失败返回 -1, 并设置 errno 值

- `int sem_wait(sem_t *sem)`

  - 函数描述：调用该函数一次，相当于 sem--，当 sem 为 0 的时候，引起阻塞
  - 函数参数：信号量变量
  - 函数返回值：成功返回 0,失败返回 -1,并设置 errno 值

- `int sem_post(sem_t *sem)`

  - 函数描述：调用一次，相当于 sem++
  - 函数参数：信号量变量
  - 函数返回值：成功返回 0,失败返回 -1,并设置 errno 值

- `int sem_trywait(sem_t *sem)`

  - 函数描述：尝试加锁，若失败直接返回，不阻塞
  - 函数参数：信号量变量
  - 函数返回值：成功返回 0,失败返回 -1,并设置 errno 值

- `int sem_destroy(sem_t *sem)`

  - 函数描述：销毁信号量
  - 函数参数：信号量变量
  - 函数返回值：成功返回 0,失败返回 -1,并设置 errno值

```c
//生产者线程处理函数
void *producter(void *arg)
{
    NODE * pNode = NULL;
    while(1)
    {
        pNode = (NODE*)malloc(sizeof(NODE));
        if(pNode == NULL)
        {
            perror("malloc error\n");
        }
        pNode -> data = rand()%1000;

        //sem_producter--，若为0则阻塞
        sem_wait(&sem_producter);

        pNode -> next = head;
        head = pNode;

        //sem_consumer++
        sem_post(&sem_consumer);
        sleep(rand()%3);
    }
}
```

```c
//消费者线程处理函数
void *consumer(void *arg)
{
    NODE *pNode = NULL;
    while(1)
    {
        //sem_consumer--，若为0则阻塞
        sem_wait(&consumer);

        pNode = head;
        head = head -> next;

        //sem_producter++
        sem_post(&producter);

        free(pNode);
        pNode = NULL;

        sleep(rand()%3);
    } 
}
```
