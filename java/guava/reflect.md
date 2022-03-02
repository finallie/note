#

## TypeToken

```java
TypeToken<String> stringTok = TypeToken.of(String.class);
TypeToken<List<String>> stringListTok = new TypeToken<List<String>>() {};
TypeToken<Map<?, ?>> wildMapTok = new TypeToken<Map<?, ?>>() {};

static <K, V> TypeToken<Map<K, V>> mapToken(TypeToken<K> keyToken, TypeToken<V> valueToken) {
  return new TypeToken<Map<K, V>>() {}
    .where(new TypeParameter<K>() {}, keyToken)
    .where(new TypeParameter<V>() {}, valueToken);
}
...
TypeToken<Map<String, BigInteger>> mapToken = mapToken(
   TypeToken.of(String.class),
   TypeToken.of(BigInteger.class));
```

## Invokable

```java
public static Invokable<?, Object> from(Method method)
public static <T> Invokable<T, T> from(Constructor<T> constructor)
```
