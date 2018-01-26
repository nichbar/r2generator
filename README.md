# r2generator
A gradle plugin that generate R2.java for android library.

Inside android library, we usually use`getResources().getIdentifier("res_name", "res_type", "package_name")`to access resources.

This plugin provide an easier way to handle the "res_name" above by generatiting R2.java file during build time.

Here's a sample of auto generated R2.java :

```java
public final class R2 {
  public static final class anim {
    @AnimRes
    public static final String abc_fade_in = "abc_fade_in";
  }
  //...
}
```

After applying this gradle plugin, you can simply use `R2.anim.abc_fade_in ` to replace your hardcoded `"abc_fade_in"`.

If you take a look at the source code, you may find out that this library is nothing but a [Butterknife Library project](https://github.com/JakeWharton/butterknife#library-projects) copycat. But it does make some difference : ) .

## Download

Add this to your `bulidscript`:

```groovy
buildscript {
    repositories {
        maven { url 'https://jitpack.io' }
    }
    dependencies {
        classpath 'com.github.nichbar:r2generator:1.0.2'
    }
}
```

then apply it in your module:

```groovy
apply plugin: 'r2generator-plugin'
```

## License

[Apache-2.0](https://github.com/nichbar/r2generator/blob/master/LICENSE)
