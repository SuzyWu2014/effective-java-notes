# Item 3: 用 private constructor 或者 enum 来强化 singleton

一般来说，Singleton 是不好的。 使用 dependency injection 可以让你避免使用 singleton，同时也让你的代码更加模块化和可测试化。

一种比较好的 singleton 的实现方式是遵照 (Initialization-on-demand holder idiom)[https://www.wikiwand.com/en/Initialization-on-demand_holder_idiom], which initialize a singleton in athread-safe way with minimal locking.

```java
public class Something {
    private Something() {}

    private static class LazyHolder {
        static final Something INSTANCE = new Something();
    }

    public static Something getInstance() {
        return LazyHolder.INSTANCE;
    }
}
```