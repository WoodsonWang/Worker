

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



## 参考

1. [2021年最新Java面试题，常见面试题及答案汇总](https://zhuanlan.zhihu.com/p/340894569)

