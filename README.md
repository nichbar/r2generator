# r2generator
[![](https://jitpack.io/v/nichbar/r2generator.svg)](https://jitpack.io/#nichbar/r2generator)

R2generator is a gradle plugin that generate R2.java for android library.

## Overview

Inside android library, we usually use`getResources().getIdentifier("res_name", "res_type", "package_name")`to access resources.

This plugin provide an easier way to handle the "res_name" above by generating R2.java file during build time.

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

## Usage

Add this to your `bulidscript`:

```groovy
buildscript {
    repositories {
        maven { url 'https://jitpack.io' }
    }
    dependencies {
        classpath 'com.github.nichbar:r2generator:1.0.5'
    }
}
```

then apply it in your module:

```groovy
apply plugin: 'r2generator-plugin'
```

## Development

If you wanna modify this plugin, you may follow these procedure.

1. Clone this project.
2. Remove `maven { url 'https://jitpack.io' } ` from root `build.gradle` file.
3. Apply your changes to r2generator library.
4. Execute `./gradlew publish` to generate plugin.
5. Run the demo project to check your changes.

## License

[Apache-2.0](https://github.com/nichbar/r2generator/blob/master/LICENSE)