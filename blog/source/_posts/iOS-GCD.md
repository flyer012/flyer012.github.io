title: iOS+GCD总结
date: 2015-12-08 16:14:15
categories: iOS
tags: [iOS,技术,多线程,GCD]
---

### 基本概念

队列：存放任务,决定执行方式（分为并发、队列）。

任务：执行具体的操作。

队列决定任务的执行顺序，是否异步决定是否开启新线程。
##### 执行线程
同步：当前线程执行，不开启新线程。

异步：另一个条线程执行，开启新线程。

##### 执行顺序
串行：一个任务执行完毕后，再执行下一个任务

并发：多个任务同时执行,仅在dispatch_async异步情况有效。

### GCD用法

##### 创建队列

```
// label:队列名称    attr:队列属性  
dispatch_queue_t  dispatch_queue_create(const char *label,  dispatch_queue_attr_t attr); 

eg:
dispatch_queue_t queue = dispatch_queue_create("com.que.name", DISPATCH_QUEUE_SERIAL); // 创建串行队列

dispatch_queue_t queue = dispatch_queue_create("com.que.name", DISPATCH_QUEUE_CONCURRENT); // 创建并行队列

```

##### 系统提供的队列
系统默认可使用的队列

```
//主线程队列
dispatch_queue_t queue = dispatch_get_main_queue();

//并发队列，由系统控制，不一定只创建一条线程
//DISPATCH_QUEUE_PRIORITY_DEFAULT 优先度，可选
dispatch_queue_t queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);


```

##### 同步与异步


```
//同步执行
dispatch_sync(dispatch_queue_t queue, dispatch_block_t block);

//异步执行
dispatch_async(dispatch_queue_t queue, dispatch_block_t block);

```

##### 关系
![](http://7xp069.com1.z0.glb.clouddn.com/201607240001.png)


### 线程同步

##### Group的使用
用于完成一组并发任务后执行后续的操作，串行没必要！

```
dispatch_group_t group = dispatch_group_create();//创建组队列
dispatch_group_async(group, queue, block);//添加任务到队列
dispatch_group_async(group, queue, block1);//添加任务到队列
//可添加多个任务到组队列

dispatch_group_notify(group, OtherQueue, otherBlock);//前面组任务执行完后再执行该任务

```

##### Barrier的使用  

并行队列中，等待前面操作并行操作完成后再执行

//等待前面任务执行完在执行，其中后续任务不会等待barrierBlock执行完。
dispatch_barrier_async(dispatch_queue_t queue, barrierBlock);

//等待前面任务执行完再单独执行，需要barrierBlock执行完再继续后续任务
dispatch_barrier_sync(dispatch_queue_t queue, barrierBlock);


##### 信号等待
用于同步线程，也可以用lock.

```
//创建一个信号，其中数值代表控制数，为0暂停，大于0执行
dispatch_semaphore_t semaphore = dispatch_semaphore_create(1);
//信号值-1
dispatch_semaphore_wait(semaphore, DISPATCH_TIME_FOREVER);
//信号值+1
dispatch_semaphore_signal(semaphore);
    
```

##### 挂起恢复

dispatch_suspend(queue);//挂起

dispatch_resume(queue);//恢复

dispatch_suspend会挂起dispatch queue，但并不意味着当前正在执行的任务会停下来，这只会导致不再继续执行还未执行的任务。dispatch_resume会唤醒已挂起的dispatch queue。你必须确保它们成对调用.

##### 延迟执行

```
dispatch_time_t time = dispatch_time(DISPATCH_TIME_NOW, 3*NSEC_PER_SEC);
dispatch_after(time, dispatch_queue_t queue, block);

```

dispatch_set_target_queue(<#dispatch_object_t object#>, <#dispatch_queue_t queue#>)


dispatch_set_context方法

 
dispatch_set_context(queue, @"xxx");

 
为特定的dispatch queue提供自定义的上下文信息（数据）,注意：必须自己手动为该上下文信息（数据）分配和释放资源。
如果定义的上下文信息（数据）为空，那么dispatch_set_finalizer_f，指定的方法将不会被调用。
也就时说，当上下文信息（数据）为NULL时，myFinalizerFunction方法将不会被调用

dispatch_set_finalizer_f方法

 
dispatch_set_finalizer_f(queue, &myFinalizerFunction);
 
void myFinalizerFunction(){
    NSLog(@"xxx");
    // 该方法可以用来释放上下文信息（数据）
}

 
定义当dispatch queue完成时，要调用的函数。
该函数可以完成一些release响应资源的操作。


### 其他用法

推荐：
[线程读写安全](http://www.cnblogs.com/ziyi--caolu/p/4900650.html)





























