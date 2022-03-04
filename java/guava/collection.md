#

[guide](https://github.com/google/guava/wiki/NewCollectionTypesExplained)

## Immutable Collections

|Interface| JDK or Guava?| Immutable Version|
|---|---|---|
|Collection| JDK| ImmutableCollection|
|List| JDK| ImmutableList|
|Set| JDK| ImmutableSet|
|SortedSet/NavigableSet| JDK| ImmutableSortedSet|
|Map| JDK| ImmutableMap|
|SortedMap| JDK| ImmutableSortedMap|
|Multiset| Guava| ImmutableMultiset|
|SortedMultiset| Guava| ImmutableSortedMultiset|
|Multimap| Guava| ImmutableMultimap|
|ListMultimap| Guava| ImmutableListMultimap|
|SetMultimap| Guava| ImmutableSetMultimap|
|BiMap| Guava| ImmutableBiMap|
|ClassToInstanceMap| Guava| ImmutableClassToInstanceMap|
|Table| Guava| ImmutableTable|

## Multiset

相当于Map<E, Integer>

|Method |Description|
|---|---|
|count(E)| Count the number of occurrences of an element that have been added to this multiset.|
|elementSet()| View the distinct elements of a Multiset\<E> as a Set\<E>.|
|entrySet()| Similar to Map.entrySet(), returns a Set<Multiset.Entry\<E>>, containing entries supporting getElement() and getCount().|
|add(E, int)| Adds the specified number of occurrences of the specified element.|
|remove(E, int)| Removes the specified number of occurrences of the specified element.|
|setCount(E, int)| Sets the occurrence count of the specified element to the specified nonnegative value.|
|size() |Returns the total number of occurrences of all elements in the Multiset.|

|Map| Corresponding Multiset| Supports null elements|
|---|---|---|
|HashMap| HashMultiset| Yes|
|TreeMap| TreeMultiset| Yes|
|LinkedHashMap| LinkedHashMultiset| Yes|
|ConcurrentHashMap| ConcurrentHashMultiset| No|
|ImmutableMap |ImmutableMultiset| No|

## Multimap

- ListMultimap Map\<K, List\<V>>
- SetMultimap Map\<K, Set\<V>>

|Implementation| Keys behave like| Values behave like|
|---|---|---|
|ArrayListMultimap| HashMap| ArrayList|
|HashMultimap| HashMap| HashSet|
|LinkedListMultimap | LinkedHashMap`` | LinkedList`` |
|LinkedHashMultimap**| LinkedHashMap| LinkedHashSet|
|TreeMultimap| TreeMap| TreeSet|
|ImmutableListMultimap| ImmutableMap| ImmutableList|
|ImmutableSetMultimap| ImmutableMap| ImmutableSet|

```java
  ListMultimap<String, Integer> treeListMultimap = MultimapBuilder.treeKeys().arrayListValues().build();   
  SetMultimap<Integer, MyEnum> hashEnumMultimap = MultimapBuilder.hashKeys().enumSetValues(MyEnum.class).build();
```

## BiMap

|Key-Value Map Impl| Value-Key Map Impl| Corresponding BiMap|
|---|---|---|
|HashMap| HashMap| HashBiMap|
|ImmutableMap| ImmutableMap| ImmutableBiMap|
|EnumMap| EnumMap| EnumBiMap|
|EnumMap| HashMap| EnumHashBiMap|

## ClassToInstanceMap

## RangeSet

## RangeMap

## MinMaxPriorityQueue

双端优先队列
