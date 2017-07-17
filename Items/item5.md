# Item 5: 避免创建不必要的 objects

一些典型的例子：

```java
String s = new String("stringette"); // Dont do this!
String s = "stringette";

// Avoid unecessary autoboxing
Long l = 0L;
l++; // l 是 Long 的对象，每次加一都会新建一个新的 Long 对象

//TODO: example of using calendar as static field
```
