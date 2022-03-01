#

```java
//按照指定顺序排序
public static <T> Ordering<T> explicit(List<T> valuesInOrder)
public static <T> Ordering<T> explicit(T leastValue, T... remainingValuesInOrder)

//链式比较
Comparator<String> cmp = Comparator.comparingInt(String::length)
.thenComparing(String.CASE_INSENSITIVE_ORDER);

//Comparators

//序列比较
public static <T extends @Nullable Object, S extends T> Comparator<Iterable<S>> lexicographical(
      Comparator<T> comparator)

isInOrder 
isInStrictOrder//不能相等

//topK
Stream.of("foo", "quux", "banana", "elephant")
  .collect(least(2, comparingInt(String::length)))   
// returns {"foo", "quux"}

//ComparisonChain
(a,b) -> ComparisonChain.start().compare(a.x,b.x).compare(a.y,b.y).result();
```
