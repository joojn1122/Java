## Ultimate Reflection Util

### Some Example
```java
import com.joojn.hackclient.util.Reflector;

public class Example {

    private static void test(String s, int c)
    {
        System.out.println(s);
    }

    private static final String test = "Ahoj";

    public static void main(String[] args)
    {
        String value = Reflector.For(
                        Example.class
                )
                .name("test")
                .searchAll(true)
                .exists((self) -> self
                        .withStatic()
                        .get()
                )
                .orElseThrow("Something went wrong..")
                .build();

        System.out.println(value);

        Reflector.For(
                        Example.class
                )
                .name("test")
                .searchAll(true)
                .returning(void.class) // or .usingArgs(String.class, int.class)
                .exists((self) -> self
                        .withStatic()
                        .invoke("test", 1)
                )
                .orElse((self) -> {
                    System.exit(1);
                })
                .build();
    }

}
```
