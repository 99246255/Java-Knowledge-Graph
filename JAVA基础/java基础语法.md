#java 基础语法
这儿不记录很基础的东西，只记录一些知识点

大部分内容参考
https://github.com/CyC2018/Interview-Notebook/blob/master/notes/Java%20%E5%9F%BA%E7%A1%80.md

## String, StringBuffer and StringBuilder
1. 可变性
    String 不可变
    StringBuffer 和 StringBuilder 可变
2. 线程安全
    String 不可变，因此是线程安全的
    StringBuilder 不是线程安全的
    StringBuffer 是线程安全的，内部使用 synchronized 来同步
3. 实现原理都是通过数组
    String:  final char value[]; 
    StringBuilder  AbstractStringBuilder, char[] value; 
    StringBuffer transient char[] toStringCache; 
   
JVM StringBuffer实现
    JVM内部采用了StringBuffer来连接字符串了，那么我们自己就不用用StringBuffer，直接用”+“就行了吧！“。是么？当然不是了。俗话说”存在既有它的理由”，让我们继续看后面的循环对应的字节码。
    因为每次执行“+”操作时jvm都要new一个StringBuffer对象来处理字符串的连接，这在涉及很多的字符串连接操作时开销会很大。
    
## 重写 重载
    override（重写）
>* 1、方法名、参数、返回值相同。
>* 2、子类方法不能缩小父类方法的访问权限。
>* 3、子类方法不能抛出比父类方法更多的异常(但子类方法可以不抛出异常)。
>* 4、存在于父类和子类之间。
>* 5、方法被定义为final不能被重写。

    overload（重载）
>* 1、参数类型、个数、顺序至少有一个不相同。 
>* 2、不能重载只有返回值不同的方法名。
>* 3、存在于父类和子类、同类中。

## jdk1.7 try-with-resources 
AutoCloseable或Closeable接口的类或接口，都可以使用try-with-resource来实现异常处理和资源关闭

## 异常
参考： http://www.importnew.com/26613.html

## java 泛型
参考： http://www.importnew.com/24029.html







