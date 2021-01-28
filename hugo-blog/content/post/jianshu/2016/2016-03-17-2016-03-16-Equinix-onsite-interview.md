---
title: "2016.03.16.Equinix-onsite-interview"
date: "2016-03-17 06:08:09"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
#面试问题
1.在多线程情况下的Singleton写法
```java
// version 1.4 
public class Singleton {
     private volatile static Singleton singleton = null;
     private Singleton() { }
     public static Singleton getInstance() {
          if (singleton == null ) {
               synchronized(Singleton.class)  {
                    if (singleton == null ) {
                         singleton = new Singleton();
                    }
              }
          }
          return singleton;
     }
}
```
使用 volatile 有两个功用：
1）这个变量不会在多个线程中存在复本，直接从内存读取。
2）这个关键字会禁止指令重排序优化。也就是说，在 volatile 变量的赋值操作后面会有一个内存屏障（生成的汇编代码上），读操作不会被重排序到内存屏障之前。
但是，这个事情仅在Java 1.5版后有用，1.5版之前用这个变量也有问题，因为老版本的Java的内存模型是有缺陷的。
```java
// version 1.6
// ref: <<Effective Java>> 
public class Singleton {
     private static class SingletonHolder {
         private static final Singleton INSTANCE = new Singleton(); 
     }
     private Singleton () { }
     public static final Singleton getInstance() {
          return SingletonHolder.INSTANCE;
     }
}
```
上面这种方式，仍然使用JVM 本身机制保证了线程安全问题； 由于SingletonHolder是私有的，除了
getInstance()  之外没有办法访问它，因此它只有在getInstance() 被调用时才会真正创建；同时读取实例的时候不会进行同步，没有性能缺陷；也不依赖jdk  版本。

**Singleton 优雅版本**
```java
 public enum Singleton {
     INSTANCE;
}
```
居然用枚举！！看上去好牛，通过EasySingleton.INSTANCE来访问，这比调用getInstance()方法简单多了。

默认枚举实例的创建是线程安全的，所以不需要担心线程安全的问题。但是在枚举中的其他任何方法的线程安全由程序员自己负责。还有防止上面的通过反射机制调用私用构造器。

Reference
[深入浅出单实例Singleton设计模式 | 酷壳 - CoolShell.cn](http://coolshell.cn/articles/265.html)
