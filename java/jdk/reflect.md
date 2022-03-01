# Modifier

```java
Class.getModifiers()
Member.getModifiers()

public static boolean isPublic(int mod)
public static String toString(int mod)
```

# Array

```java
public static Object newInstance(Class<?> componentType, int... dimensions)
public static native int getLength(Object array)
public static native void set(Object array, int index, Object value)
```

# class

```java
//Returns:the immediately enclosing method of the underlying class, if that class is a local or anonymous class; otherwise null
public Method getEnclosingMethod()

//Returns:the declaring class for this class
public Class<?> getDeclaringClass() 

public Field[] getFields()//public 包括父类
public Class<?>[] getDeclaredClasses()// 所有 不包括父类

```
