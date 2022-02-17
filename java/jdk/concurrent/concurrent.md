#

## volatitle

```block
作用：
1.从内存而不是缓存读取写入数据
2.禁止指令重排序，禁止编译器和CPU对被修饰变量赋值相关语句进行重排序

使用场景：
1.只有一个写线程
2.写少读多线程安全要求不高
3.写操作不依赖于该变量的当前值
4.单例模式双重验证
```

## synchronized

```block
特点：可重入 非公平 排他锁

缺点：
1.Mutex Lock性能消耗大
2.释放锁不灵活
3.不灵活 没有try操作 获取不到锁就会阻塞

优点：
1.有优化，单线程优化为自旋锁
2.代码比较优雅
```

## 悲观锁与乐观锁

```block
悲观乐观：访问数据时是否倾向于加锁
乐观锁多用于读多写少的环境，避免频繁加锁影响性能；而悲观锁多用于写多读少的环境，避免频繁失败和重试影响性能
```

## CompletableFuture

```java
//多数情况下使用上级CompletableFuture线程
public <U> CompletableFuture<U> thenApply(
        Function<? super T,? extends U> fn)

//使用ForkJoinPool
public <U> CompletableFuture<U> thenApplyAsync(
        Function<? super T,? extends U> fn)

//使用executor参数
public <U> CompletableFuture<U> thenApplyAsync(
        Function<? super T,? extends U> fn, Executor executor)

//使用异步api
public <U> CompletionStage<U> thenCompose
        (Function<? super T, ? extends CompletionStage<U>> fn)

//处理异常
public <U> CompletionStage<U> handle
        (BiFunction<? super T, Throwable, ? extends U> fn)
public CompletionStage<T> whenComplete
        (BiConsumer<? super T, ? super Throwable> action)
public CompletionStage<T> exceptionally
        (Function<Throwable, ? extends T> fn)
public default CompletionStage<T> exceptionallyCompose
        (Function<Throwable, ? extends CompletionStage<T>> fn)
```

## JUC框架

### JUC锁

```block
可重入：synchronized、ReentrantLock、ReentrantReadWriteLock
不可重入：StampedLock

可公平：ReentrantLock、ReentrantReadWriteLock（默认非公平）
非公平：synchronized

读写锁：ReentrantReadWriteLock、StampedLock
排他锁：synchronized、ReentrantLock

ReentrantLock优点：
1.可公平
2.可创建多个condition
3.有tryLock、lockInterruptibly，更灵活

ReentrantReadWriteLock：
1.可能会写饥饿
2.readlock不支持condition，writelock支持

StampedLock：
适用于读多写少对性能要求高的场景，对程序员要求高
非可重入，非公平，乐观+悲观
```

### JUC工具库

```java
// 构造方法：
public CountDownLatch(int count)

// 等待
public void await()

// 限时等待
public boolean await(long timeout, TimeUnit unit)

// 计数减一
public void countDown()

// 获取当前计数
public long getCount()
```

```java
public CyclicBarrier(int parties, Runnable barrierAction)

public int await()
```

```java
Phaser
public int register()

public int arriveAndDeregister()

public int arriveAndAwaitAdvance() 
```

```java
// 构造方法，permits是最大许可计数，即Semaphore最多允许多少个线程同时访问
public Semaphore(int permits)

// 试图申请一个许可permit，每有一个线程申请到，permits计数就减一；
// permits计数为0时，申请线程被阻塞，直到有线程释放Semaphore资源，permits计数大于0了，被阻塞的线程会重新竞争Semaphore资源
public void acquire()

// 释放一个许可，每有一个线程释放，permits计数就加一
public void release()
```

```java
// 构造方法，声明Exchanger变量时指定泛型，该泛型就是交换的数据类型
// Exchanger<String> exchanger = new Exchanger<>();
public Exchanger()

// 两个线程交换数据，传入参数是当前线程计划交换给目标线程的数据，
// 返回值是从目标线程交换来的数据。
// 先到达此处的线程将阻塞，直到目标线程也执行到该方法。
public V exchange(V x)
```

### JUC容器

- ConcurrentHashMap
- ConcurrentSkipListMap
- Collections.newSetFromMap(new ConcurrentHashMap())
- ConcurrentSkipListSet
- CopyOnWriteArrayList CopyOnWriteArraySet 注重迭代操作
- ConcurrentLinkedQueue fifo 并发性能优于BlcokingQuene
- ConcurrentLinkedDeque
