#

```java
Cache<String, String> cache = CacheBuilder.newBuilder()
                .concurrencyLevel(1)
//                .maximumSize(100)
                .weigher((String k, String v) -> v.length())
                .maximumWeight(100)
                .expireAfterAccess(1, TimeUnit.SECONDS)
                .expireAfterWrite(1, TimeUnit.SECONDS)
                .recordStats()
                .refreshAfterWrite(1, TimeUnit.SECONDS)
                .removalListener(System.out::println)
                .build(CacheLoader.from(() -> ""));
```
