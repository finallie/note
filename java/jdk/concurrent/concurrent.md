#

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
