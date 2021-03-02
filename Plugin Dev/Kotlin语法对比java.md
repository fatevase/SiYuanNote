本章介绍部分 Kotlin 定义对应的 Java 定义，以帮助 Java 使用者理解 Mirai 的源代码。
{: id="20210228192214-27fol86"}

每部分第一个代码块为 Kotlin 代码，第二个代码块为 Java 代码。
{: id="20210228192214-hwfa2cf"}

预计阅读时间：5 分钟
{: id="20210228192214-ef8rnvo"}

#### 通用
{: id="20210228192214-6rj6g0p"}

- {: id="20210228192214-hdn20i5"}Kotlin 的定义都默认是 `public` 和 `final`
  {: id="20210228192214-2ydjp6r"}
- {: id="20210228192214-yo37twr"}Kotlin 不需要句末分号，通常以换行作为一个语句的结束
  {: id="20210228192214-4merl8s"}
{: id="20210228192214-dichp4c"}

#### `class`
{: id="20210228192214-xi7by39" updated="20210228192248"}

```kotlin
class A
```
{: id="20210228192214-ns43uy7"}

```java
public final class A {
}
```
{: id="20210228192118-gbqd2cy"}

#### 构造器定义
{: id="20210228192118-ok41d44"}

以下几种 Kotlin 定义是等价的。
{: id="20210228192118-zlrebbi"}

```kotlin
class A {
    private val value: String
  
    constructor(value: String) {
        this.value = value
    }
  
    constructor(integer: Int) {
        this.value = integer.toString()
    }
}
```
{: id="20210228192118-tfer0m0"}

```kotlin
class A(val value: String) { // 类定义后面的括号表示主构造器
    constructor(integer: Int) : this(integer.toString())
}
```
{: id="20210228192118-16ugx5k"}

对应的 Java 定义为：
{: id="20210228192118-m00l8gd"}

```java
public final class A {
    private final String value;
  
    public A(String value) {
        this.value = value;
    }
  
    public A(int integer) {
        this.value = String.valueOf(integer);
    }
}
```
{: id="20210228192118-o7e0t88"}

通常 Kotlin class 都会有一个主构造器。
{: id="20210228192118-z8rghxv"}

#### 构造器调用
{: id="20210228192118-1zxmjfa"}

Kotlin 不需要 `new` 关键字。
{: id="20210228192118-zb63jvb"}

```kotlin
val a = A("test")
```
{: id="20210228192118-jojicrb"}

```java
A a = new A("test");
```
{: id="20210228192118-ir360p8"}

#### 函数
{: id="20210228192118-obekl60"}

```kotlin
class A {
    fun test(string: String): Int = 1
}
```
{: id="20210228192118-cd98o7s"}

```java
public final class A {
    public int test(String string) {
        return 1;
    }
}
```
{: id="20210228192118-jp93yr8"}

#### 属性 `val`
{: id="20210228192118-g39qo72"}

- {: id="20210228192118-cv5yhd1"}Kotlin 的 `val` 是不可变的，只能被赋值一次
  {: id="20210228192118-c9vgbcx"}
- {: id="20210228192118-9k8gfxo"}编译器为 `val` 创建 `getter`
  {: id="20210228192118-z6v1981"}
{: id="20210228192118-6z7e22q"}

```kotlin
class A {
    val value: String = "test"
}
```
{: id="20210228192118-s2gf6rk"}

```java
public final class A {
    private final String value = "test";
    public final String getValue() {
        return value;
    }
}
```
{: id="20210228192118-qpiq4p2"}

#### 属性 `var`
{: id="20210228192118-i10ey2h"}

- {: id="20210228192118-9lomw2k"}Kotlin 的 `var` 相较于 `val` 是可变的，可以被多次赋值。
  {: id="20210228192118-4urehbd"}
- {: id="20210228192118-57rh1gj"}编译器为 `var` 创建 `getter` 和 `setter`
  {: id="20210228192118-trawhbt"}
{: id="20210228192118-16nsagn"}

```kotlin
class A {
    var value: String = "test"
}
```
{: id="20210228192118-mlei2td"}

```java
public final class A {
    private String value = "test";
    public final String getValue() {
        return value;
    }
    public final String setValue(String value) {
        this.value = value;
    }
}
```
{: id="20210228192118-clgrafx"}

#### 顶层定义和 `const`
{: id="20210228192118-k0u2rki"}

- {: id="20210228192118-85afwr4"}Kotlin 的定义不一定需要在 `class` 中，允许直接存在于文件中的「顶层函数」和「顶层属性」
  {: id="20210228192118-jye6q2c"}
- {: id="20210228192118-9o80eew"}`XXX.kt` 中的顶层定义会被编译为名为 `XXXKt` 的 `class`
  {: id="20210228192118-yq516rb"}
- {: id="20210228192118-dft58qi"}顶层定义会被编译为 `static`
  {: id="20210228192118-vg62rbk"}
- {: id="20210228192118-stb4e6n"}`const` 可以修饰一个属性，编译器会把它编译为 Java 静态字段。
  {: id="20210228192118-4cplilu"}
{: id="20210228192118-j40f7n5"}

```kotlin
// Test.kt
val x: String = "xx"

const val CONST_VALUE: String = "cc"

fun foo() { }
```
{: id="20210228192118-sxhzy0j"}

```java
// TestKt.java
public final class TestKt {
    public static final String CONST_VALUE = "cc"; // const val 没有 getter
  
    private static final String x = "xx";
    public static String getX(){
        return x; 
    }
  
    public static void foo() { }
}
```
{: id="20210228192118-5ynnwpp"}

#### 单例对象
{: id="20210228192118-onjqe0p"}

- {: id="20210228192118-d393eik"}Kotlin `object` 定义一个单例对象
  {: id="20210228192118-wb6cx8b"}
{: id="20210228192118-xrqykb7"}

```kotlin
object Test
```
{: id="20210228192118-9zssybb"}

```java
public final class Test {
    public static final Test INSTANCE = new Test();

    private Test() {}
}
```
{: id="20210228192118-416j8sw"}

#### 静态
{: id="20210228192118-82ttdii"}

```kotlin
object Test {
    val x = "x"             // public String getX()
    @JvmField val y = "y"   // public static final String y;
    @JvmStatic val z = "z"  // public static String getZ()
} 
```
{: id="20210228192118-t6x6lfx"}

```java
public final class Test {
    public static final Test INSTANCE = new Test();
    private Test() {}

    private final String x = "x";       // val
    public String getX() {
        return x;
    }
  
    public static final String y = "y"; // @JvmField val
  
    private final String z = "z";       // @JvmStatic val
    public static String getZ() {
        return z;
    }
} 
```
{: id="20210228192118-v55uh6f"}

#### 静态
{: id="20210228192118-8x9ch2j"}

- {: id="20210228192118-demu650"}Kotlin 没有 `static` 关键字，但可以通过 `@JvmStatic` 将一个函数编译为 `static`
  {: id="20210228192118-8jvtl3p"}
{: id="20210228192118-l7dtgrx"}

```kotlin
object Test {
    fun a() { }
    @JvmStatic
    fun b() { }
} 
```
{: id="20210228192118-vi9ts0r"}

```java
public final class Test {
    public static final Test INSTANCE = new Test();
    private Test() {}
  
    public void a() { }
    public static void b() { }
} 
```
{: id="20210228192118-my9mn0a"}

#### 伴生对象
{: id="20210228192118-cn3kpym"}

- {: id="20210228192118-6wonb98"}`class` 可以拥有 `companion object`
  {: id="20210228192118-uxvk9sz"}
- {: id="20210228192118-xihef1z"}伴生对象内的 `@JvmField` 定义将会被编译到外部 `class`
  {: id="20210228192118-4uy093j"}
- {: id="20210228192118-fvrmpcs"}伴生对象内的 `@JvmStatic` 函数以成员方法编译到伴生对象，然后以静态方法编译到外部 `class`
  {: id="20210228192118-g8si0e1"}
{: id="20210228192118-0nrnums"}

```kotlin
class Test {
    companion object {
        @JvmField
        val CONST: String = ""
  
        fun a() { }
        @JvmStatic
        fun b() { }
    }
} 
```
{: id="20210228192118-8ci3n45"}

```java
public final class Test {
    public static final Companion Companion = new Companion();
    public static final String CONST = "";
  
    public static void b() { 
        Companion.b();
    }

    public static final class Companion {
        public void a() { }
        public void b() { }
    }
} 
```
{: id="20210228192118-g9561hz"}

#### 协程
{: id="20210228192118-ph9a2pc"}

Kotlin 协程是语言级特性，`suspend` 修饰的函数会在编译期被处理。
{: id="20210228192118-vrczl4k"}

```kotlin
class A {
    suspend fun getValue(): String { /* ... */ } 
}
```
{: id="20210228192118-8w42uzf"}

```java
public final class A {
    public Object getValue(Continuation<? super String> $completion) {
        // 由 Kotlin 编译器生成非常复杂的方法体
    }
}
```
{: id="20210228192118-z5fw1b4"}

`$completion` 参数类似于一个回调。需要熟悉 Kotlin 协程原理才能实现。为帮助 Java 用户，mirai 使用编译器插件处理 `suspend` 函数。
{: id="20210228192119-ywmn1za"}

```kotlin
class A {
    @JvmBlockingBridge
    suspend fun getValue(): String { /* ... */ } 
}
```
{: id="20210228192119-uhlcahs"}

```java
public final class A {
    public Object getValue(Continuation<? super String> $completion) {
        // 由 Kotlin 编译器生成非常复杂的方法体
    }
  
    // 通过 @JvmBlockingBridge 生成的方法
    public String getValue() {
        // 由 @JvmBlockingBridge 的编译器生成方法体，调用 getValue(Continuation)
    }
}
```
{: id="20210228192119-60u9vku"}

Java 使用者可以认为 `@JvmBlockingBridge suspend fun getValue(): String` 相当于 `fun getValue(): String`。
{: id="20210228192119-t09joa1"}

---

> [回到 Mirai 文档索引](README.md#jvm-平台-mirai-开发)
> {: id="20210228192119-vjae6ry"}
{: id="20210228192119-cyiix7u"}

```

```
{: id="20210228192116-mhjj2ue" updated="20210228192118"}

{: id="20210301213950-36nz1gn"}

{: id="20210301213951-utucubp"}

### 坑
{: id="20210301213951-6co6fgn" updated="20210301214004"}

`java.lang.NoClassDefFoundError: kotlin/jvm/internal/Intrinsics`
{: id="20210301214004-4vu2cfs" updated="20210301214045"}

在移植java到kotlinn的时候,用idea自动编译和网上查找的语法查看
{: id="20210301214047-cdwuyeu" updated="20210301214112"}

以为函数定义中传参只需要指定对应的类型,实际上并不,Kotlin需要去判断传入的值是否存在,
{: id="20210301214112-amjepxw" updated="20210301214612"}

问号?，表示该变量是Nullable，不加表示该变量不可为null,
{: id="20210301214615-qm098z8" updated="20210301214713"}

也就是不加问号,在赋值的时候会进一步进行判空,
{: id="20210301214713-4o1a8hp" updated="20210301214757"}

而这一步判空在mc脚本开发过程中导致报错, 而在我自己进行测试的时候并没有任何问题,
{: id="20210301214757-mpgbux9" updated="20210301214849"}

暂时没有断点查看,之后会考虑进一步断点调试
{: id="20210301214851-46u6kx2" updated="20210301214919"}

在遇到这个问题的时候我从环境到软件在到编译器各种都找了,没想到是一个问号的问题
{: id="20210301214610-pyma5wh" updated="20210301214610"}

```kotlin
fun FunctionName(p1: String, p2:Int){
}

// 这样是对的
fun FunctionName(p1: String?, p2:Int?){
}

```
{: id="20210301214120-s9u42nh" updated="20210302181538"}

更正:问题确实出在导出包的问题上,kotlin导出的jar包中需要包含kotlin运行的库文件,但是目前并不想让kotlin调用自身的库文件,而是完全的调用java的库文件,
{: id="20210302181539-9a28r82" updated="20210302182407"}

kotlin中定义的String等数据类型默认是Kotlin.String 等 这时候使用String.contains() 或者相关数据类型下的方法时,就会遇到冲突,因为并没有导入相关的kotlin包,故在使用kotlin类的时候会出现相关错误
{: id="20210302182408-9rw50pk" updated="20210302182523"}

解决方法1:在build.gradle.kts中添加打包(将依赖全部打包到jar中)
{: id="20210302182642-jbxs9af" updated="20210302182727"}

```
tasks.withType<Jar> {
    // Otherwise you'll get a "No main manifest attribute" error


    // To add all of the dependencies
    from(sourceSets.main.get().output)

    dependsOn(configurations.runtimeClasspath)
    from({
        configurations.runtimeClasspath.get().filter { it.name.endsWith("jar") }.map { zipTree(it) }
    })
}
```
{: id="20210302182649-o0e6hbg" updated="20210302182649"}

解决方法2:
{: id="20210302182729-dq8c0y7" updated="20210302182736"}

在使用对应String or Int类型等提前导入 java.lang.*
{: id="20210302182736-jniupic" updated="20210302182800"}

{: id="20210302182801-j5wa81i"}


{: id="20210228192115-adk1min" type="doc"}
