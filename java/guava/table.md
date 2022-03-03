#

```java
HashBasedTable
TreeBasedTable
ArrayTable

ImmutableTable

    Collector<T, ?, ImmutableTable<R, C, V>> toImmutableTable(
          Function<? super T, ? extends R> rowFunction,
          Function<? super T, ? extends C> columnFunction,
          Function<? super T, ? extends V> valueFunction)

    Collector<T, ?, ImmutableTable<R, C, V>> toImmutableTable(
          Function<? super T, ? extends R> rowFunction,
          Function<? super T, ? extends C> columnFunction,
          Function<? super T, ? extends V> valueFunction,
          BinaryOperator<V> mergeFunction)

    ImmutableTable<String, String, String> table = ImmutableTable.<String, String, String>builder()
        .put("a", "b", "c")
        .build();

Tables

Collector<T, ?, I> toTable
Table<C, R, V> transpose(Table<R, C, V> table)
Table<R, C, V> synchronizedTable(Table<R, C, V> table)
```
