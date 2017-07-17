# Item 6: 消除过期引用

过期引用（obsolete reference）: 指的是那些无法被重新引用的引用。

例子：
```java
public class Stack {
    //...

    public Object pop() {
        if(size == 0)
            throw new EmptyStackException();
        return elements[--size];
    }
}

// fix
public class Stack {
    //...

    public Object pop() {
        if(size == 0)
            throw new EmptyStackException();
        Object result = elements[--size];
        element[size] = null; // Eliminate obsolete references
        return result;
    }
}
```

其实，消除过期引用的最好方式是在 narrowest posible scope 里定义 variables.
