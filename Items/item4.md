# Item 4: 用 private constructor 来强制 noninstantiability

``` java
// Noninstantiable utility class
public class UtilityClass {
    private UtilityClass(){
        throw new AssertionError();
    }

    // ...
}
```