#

- Stopwatch 时间测试
- Suppliers

```java
  public static <T extends @Nullable Object> Supplier<T> memoize(Supplier<T> delegate)

  //充当缓存
  public static <T extends @Nullable Object> Supplier<T> memoizeWithExpiration(
      Supplier<T> delegate, long duration, TimeUnit unit)
```

- AbstractIterator

```java
public static Iterator<String> skipNulls(final Iterator<String> in) {
  return new AbstractIterator<String>() {
    protected String computeNext() {
      while (in.hasNext()) {
        String s = in.next();
        if (s != null) {
          return s;
        }
      }
      return endOfData();
    }
  };
}
```

- Splitter

```java
Map<String, String> map = Splitter.fixedLength(8)
                .omitEmptyStrings()
                .trimResults()
                .limit(5)
                .withKeyValueSeparator(':')
                .split(s)
```

- CharMatcher

```java
any none whitespace ascii is isNot anyOf noneOf inRange forPredicate
CharMatcher.is('/')
                .trimAndCollapseFrom("//a//b/", '/')
```

- Defaults

```java
  public static <T> T defaultValue(Class<T> type) {
```

- CaseFormat

```java
String s = "lowerCamel";
        System.out.println(CaseFormat.LOWER_CAMEL.to(CaseFormat.LOWER_HYPHEN, s))
```

- Hashing

```java
Hashing.md5().hashString("abc", StandardCharsets.UTF_8)
```
