## Ultimate Reflection Util

### Some Example
```java
public class Example {

    private static void test(String s)
    {
        System.out.println(s);
    }

    public static void main(String[] args)
    {
        Reflector.For(
                        Example.class
                )
                .name("test")
                .findAll(true)
                .usingArgs(String.class)
                .exists((self) -> self
                        .withStatic()
                        .invoke("Test")
                )
                .orElseThrow("WTF??");
    }

}
```
