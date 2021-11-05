

## 1. == 和 equals区别

== 

基本类型：比较值是否相同

引用类型：比较引用是否相同

equals

默认情况是比较引用，有些常用类重写了equals，所以比较的是值是否相同

## 2. Java基本数据类型

byte  boolean char 

short int float long double

String 属于对象

## 3. HashTable 和 HashMap区别

https://blog.csdn.net/sunshine_silence/article/details/80263935

- 扩容方式。
  - HashTable默认11，增加方式2N+1（N为初始）
  - HashMap默认16，增加方式2N

- 哈希值使用不同

  - HashTable直接使用对象的hashcode

    hashCode是jdk根据对象的地址或者字符串或者数字算出来的int类型的数值。

  - HashMap重新计算hash值

- key和value是否允许null值

  - HashTable不允许key和value出现null值，包含contains，containsValue和containsKey三个方法，其中contains和containsValue功能相同

  - HashMap允许空键值

    containsValue和containsKey

- 继承父类 都实现Map接口

  - HashTable继承Dictionary类
  - HashMap继承AbstractMap类

- 线程安全

  - HashTable线程安全，Synchronize
  - HashMap线程不安全





## 4. final 的作用

- 修饰的类不能被继承
- 修饰的方法不能被重写
- 修饰的变量必须初始化，以后不能修改

## 5. String StringBuffer StringBuilder区别？

String声明的对象是不可变的对象，每次操作都会创建新的String对象。

StringBuffer和StringBuilder可以在原有的对象基础上进行操作，在经常对字符串进行更改时，最好不使用String类。

StringBuffer是线程安全的，多线程下使用。

StringBuilder是线程不安全的，性能高于StringBuffer，单线程下推荐使用StringBuilder。

## 6. String str="i"与 String str=new String("i")一样吗？

不一样，因为内存的分配方式不一样。String str="i"的方式，java 虚拟机会将其分配到常量池中；而 String str=new String("i") 则会被分到堆内存中。

## 7. 接口和抽象类的区别？

- 实现：抽象类使用extends继承，接口使用implements实现。
- 构造函数：抽象类可以有构造函数，接口不能有
- main方法：抽象类可以有，接口不能有
- 实现数量：类可以实现多个接口，只能继承一个抽象类
- 访问修饰符：接口中方法默认是public修饰，抽象类中的方法可以是任意修饰符

## 8. BIO、NIO、AIO区别？



## 9. Collection和Collections区别？

Collection是一个集合接口，直接继承接口有List、Set

Collections是一个工具类，提供静态方法对集合元素进行操作。

## 10. ArrayList和Array的区别？

- ArrayList长度可变，Array创建时必须指定数据类型和数组长度

- ArrayList可以容纳不同类型对象，Array存放数据类型相同

## 11. 并行和并发区别

- 并行是指多个事件同一时刻一起执行。
- 并发是指多个事件一起发生交替执行。

## 12. 线程和进程的区别

进程是程序运行和资源分配的基本单位，一个程序至少一个进程，一个进程至少一个线程。

进程在执行过程中拥有独立的内存单元，而多个线程共享内存资源，减少切换次数，从而效率更高。

同一个进程中的多个线程可以并发执行。

## 13. 创建线程的方式

https://www.cnblogs.com/songshu120/p/7966314.html

- 继承Thread类
  - 重写该类的run()方法（线程执行体），调用start()启动线程
- 实现Runnable接口
  - 重写接口的run()方法
  - 创建Runnable实例，以此作为Thread的target创建Thread对象。
  - 调用线程对象的start()启动线程
- 通过Callable和FutureTask创建
  - 创建Callable接口的实现类，实现call()方法
  - 创建Callable实现类的实例，使用FutureTask类包装Callable对象
  - 将FutureTask对象作为Thread的target
  - 调用FutureTask对象的get()方法来获得子线程执行结束后的返回值

```java
package com.thread;  
  
import java.util.concurrent.Callable;  
import java.util.concurrent.ExecutionException;  
import java.util.concurrent.FutureTask;  
  
public class CallableThreadTest implements Callable<Integer>  
{  
  
    public static void main(String[] args)  
    {  
        CallableThreadTest ctt = new CallableThreadTest();  
        FutureTask<Integer> ft = new FutureTask<>(ctt);  
        for(int i = 0;i < 100;i++)  
        {  
            System.out.println(Thread.currentThread().getName()+" 的循环变量i的值"+i);  
            if(i==20)  
            {  
                new Thread(ft,"有返回值的线程").start();  
            }  
        }  
        try  
        {  
            System.out.println("子线程的返回值："+ft.get());  
        } catch (InterruptedException e)  
        {  
            e.printStackTrace();  
        } catch (ExecutionException e)  
        {  
            e.printStackTrace();  
        }  
  
    }  
  
    @Override  
    public Integer call() throws Exception  
    {  
        int i = 0;  
        for(;i<100;i++)  
        {  
            System.out.println(Thread.currentThread().getName()+" "+i);  
        }  
        return i;  
    }  
  
}
```

## 14. runnable和callable区别

callable的call方法有返回值

runnable的run方法返回值为void

## 15. 线程的状态

- 创建状态：创建线程对象，没有调用start方法
- 就绪状态：调用start方法，处于就绪状态，等待调度
- 运行状态：开始运行run代码
- 阻塞状态：线程运行的时候，被暂停，等待某个时间的发生（比如资源）再继续运行。sleep、suspend、wait等都可以导致线程阻塞
- 死亡状态：run执行结束，或者调用stop，线程就会死亡，无法再调用start另其进入就绪状态。

## 16. 重写和重载区别

https://blog.csdn.net/qunqunstyle99/article/details/81007712

重载（Overload）具有具有多个不同参数或者类型的同名函数（不能以返回值作为区分重载函数的标准）

重写（Override）是父类与子类之间的多态性。重写的方法名、参数列表、返回类型必须与重写方法一致。



## 参考

1. [2021年最新Java面试题，常见面试题及答案汇总](https://zhuanlan.zhihu.com/p/340894569)

