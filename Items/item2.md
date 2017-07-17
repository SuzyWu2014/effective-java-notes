# Item 2: 当 Constructor 的参数列表很长的时候，考虑使用 Builder 模式

```java
//Builder Pattern
public class Foo {
    private final int bar1;
    private final int bar2;
    private final int bar3;
    //...

    public static class Builder {
        // required parameters
        private final int bar1;

        // optional parameters - initialized to default value
        private final int bar2 = 0;
        private final int bar3 = 0;

        public Builder(int bar1) {
            this.bar1 = bar1;
        }

        public Builder Bar2(int bar2) {
            this.bar2 = bar2;
        }

        public Builder Bar3(int bar3) {
            this.bar3 = bar3;
        }

        public Foo build() {
            return new Foo(this);
        }
    }

    private Foo(Builder builder) {
        bar1 = builder.bar1;
        bar2 = builder.bar2;
        bar3 = builder.bar3;
    }
}

Foo foo = new Foo.Builder(1).bar2(2).bar3(3).build();

```