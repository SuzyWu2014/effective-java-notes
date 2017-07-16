# Item 1: 考虑用 static factory 代替 constructors

```java
// Constructors
public class Foo {
    public Foo(boolean withBar) {
        //...
    }
}

// Static factory method 长这样
public class Foo {
    private Foo() {}

    public static Foo createWithBar() {
        //...
    }
    public static Foo createWithoutBar() {
        //...
    }
}

```

## Benefits
+ 方法名可以更有描述性，提高了 readibility，
+ 不会每次都强制 new 一个新的对象. 如：enum, singleton. (TODO: add singleton example)
+ 可以返回子类
+ 语法更简洁。下面是例子：

```java
# constructors version
Map<String, List<String>> map = new HashMap<String, List<String>>();

# Static factory method

public static <K, V> HashMap<K. V> newInstance() {
    return new HashMap<K, V>();
}
Map<String, List<String>> map = HashMap.newInstance();
```

## Disadvantages
+ 阻止用户继承该类
+ 需要额外的 documentation 来说明这个 static factory method 是用来 contrunct object 的。

