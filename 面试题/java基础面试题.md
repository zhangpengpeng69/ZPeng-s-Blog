# java基础面试题
## 1、面向对象都有哪些特性以及你对这些特性的理解 ？


答：面向对象的三大特征：1.继承  2.封装 3.多态性<br/>
  （1）继承：就是保留父类的属性，开扩新的东西。通过子类可以实现继承，子类继承父类的所有状态和行为，同时添加自身的状态和行为。<br/>
  （2）封装：就是类的私有化。将代码及处理数据绑定在一起的一种编程机制，该机制保证程序和数据不受外部干扰。<br/>
  （3）多态：是允许将父对象设置成为和一个和多个它的子对象相等的技术。包括重载和重写。重载为编译时多态，重写是运行时多态。<br/>


## 2、什么是自动装箱和拆箱？

  答：自动装箱就是Java自动将原始类型值转换成对应的对象，比如将int的变量转换成Integer对象，这个过程叫做装箱，反之将Integer对象转换成int类型值，这个过程叫做拆箱。因为这里的装箱和拆箱是自动进行的非人为转换，所以就称作为自动装箱和拆箱。<br/>
  原始类型byte,short,char,int,long,float,double和boolean对应的封装类为Byte,Short,Character,Integer,Long,Float,Double,Boolean。自动装箱和拆箱从Java 1.5开始引入，目的是将原始类型值转自动地转换成对应的对象。自动装箱与拆箱的机制可以让我们在Java的变量赋值或者是方法调用等情况下使用原始类型或者对象类型更加简单直接。<br/>


## 3、什么是 java 序列化，如何实现 java 序列化？
  答：序列化就是一种用来处理对象流的机制，所谓对象流也就是将对象的内容进行流化。可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决在对对象流进行读写操作时所引发的问题。<br/>
  序 列 化 的 实 现 ： 将 需 要 被 序 列 化 的 类 实 现 Serializable 接 口 ， 该 接 口 没 有 需 要 实 现 的 方 法 ，implements Serializable 只是为了标注该对象是可被序列化的，然后使用一个输出流(如： FileOutputStream)来构造一个 ObjectOutputStream(对象流)对象，接着，使用 ObjectOutputStream 对象的 writeObject(Object obj)方法就可以将参数为 obj 的对象写出(即保存其状态)，要恢复的话则用输入流。<br/>
## 4、char 型变量中能不能存储一个中文汉字，为什么？
  答：char 类型可以存储一个中文汉字，因为 Java 中使用的编码是 Unicode（不选择任何特定的编码，直接使用字符在字符集中的编号，这是统一的唯一方法），一个 char 类型占 2 个字节（16 比特），所以放一个中文是没问题的。


## 5、List 和 Map、 Set 的区别？
  答：List 和 Set 是存储单列数据的集合， Map 是存储键和值这样的双列数据的集合； List 中存储的数据是有顺序，并且允许重复； Map 中存储的数据是没有顺序的，其键是不能重复的，它的值是可以有重复的， Set 中存储的数据是无序的，且不允许有重复，但元素在集合中的位置由元素的 hashcode 决定，位置是固定的（Set 集合根据 hashcode 来进行数据的存储，所以位置是固定的，但是位置不是用户可以控制的，所以对于用户来说 set 中的元素还是无序的） 。

## 6、HashMap 和 HashTable 有什么区别? 
  HashMap 是线程不安全的,HashMap 是一个接口,是 Map 的一个子接口,是将键映射到值得对象,不允许键值重复允许空键和空值;由于非线程安全,HashMap 的效率要较 HashTable 的效率高一些.HashTable 是线程安全的一个集合,不允许 null 值作为一个 key 值或者 Value 值;HashTable 是 sychronize,多个线程访问时不需要自己为它的方法实现同步,而 HashMap 在被多个线程访问的时候需要自己为它的方法实现同步。
## 7、谈谈 JVM 的内存结构和内存分配？
a)Java 内存模型 <br/>
	Java 虚拟机将其管辖的内存大致分三个逻辑部分：方法区(Method Area)、 Java 栈和 Java 堆。<br/>
  1、方法区是静态分配的，编译器将变量绑定在某个存储位置上，而且这些绑定不会在运行时改变。常数池，源代码中的命名常量、 String 常量和 static 变量保存在方法区。<br/>
  2、 Java Stack 是一个逻辑概念，特点是后进先出。一个栈的空间可能是连续的，也可能是不连续的。最典型的 Stack 应用是方法的调用， Java 虚拟机每调用一次方法就创建一个方法帧（frame），退出该方法则对应的 方法帧被弹出(pop)。栈中存储的数据也是运行时确定的。<br/>
  3、 Java 堆分配(heap allocation)意味着以随意的顺序，在运行时进行存储空间分配和收回的内存管理模型。堆中存储的数据常常是大小、数量和生命期在编译时无法确定的。 Java 对象的内存总是在 heap 中分配。<br/>
	b) java 内存分配<br/>
  1、基础数据类型直接在栈空间分配;<br/>
  2、方法的形式参数，直接在栈空间分配，当方法调用完成后从栈空间回收;<br/>
  3、引用数据类型，需要用 new 来创建，既在栈空间分配一个地址空间，又在堆空间分配对象的类变量;<br/>
  4、方法的引用参数，在栈空间分配一个地址空间，并指向堆空间的对象区，当方法调用完后从栈空间回收;<br/>
  5、局部变量 new 出来时，在栈空间和堆空间中分配空间，当局部变量生命周期结束后，栈空间立刻被回收，堆空间区域等待 GC 回收;<br/>
  6、方法调用时传入的实际参数，先在栈空间分配，在方法调用完成后从栈空间释放;<br/>
  7、字符串常量在 DATA 区域分配 ， this 在堆空间分配;<br/>
  8、数组既在栈空间分配数组名称， 又在堆空间分配数组实际的大小。<br/>

## 8、wait()与sleep()的区别

a)sleep()来自Thread类，和wait()来自Object类.调用sleep()方法的过程中，线程不会释放对象锁。而 调用 wait 方法线程会释放对象锁。<br/>
  b)sleep()睡眠后不出让系统资源，wait让其他线程可以占用CPU。<br/>
  c)sleep(milliseconds)需要指定一个睡眠时间，时间一到会自动唤醒.而wait()需要配合notify()或者notifyAll()使用。<br/>

## 9、说说你对 Java 中反射的理解 ？
JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法；这种动态获取的信息以及动态调用对象的方法的功能称为java语言的反射机制。

## 10、写出常见的5个RuntimeException

     (1)java.lang.NullPointerException空指针异常，出现原因：调用了未经初始化的对性爱那个或者不存在的对象。<br/>
       (2)ClassNoFoundException 指定类找不到，出现原因：类的名称和路径加载错误，通常是试图通过字符串来加载某个类时可能引发异常。<br/>
       (3)NumberFormatException字符串转换为数字异常，出现原因：字符串数据中包含非数字型字符。<br/>
       (4)IndexOutOfBoundsException数组下标越界异常<br/>
       (5)IllegalArgumentException 方法传递参数错误<br/>
       (6)ClassCastException数据类型转换异常<br/>
       (7)NoClassDefFoundExcetion 未找到类定义错误<br/>
       (8)SQLException SQL异常<br/>
       (9)InstantiationException实例化异常<br/>
       (10)NoSuchMethodExceptioin 方法不存在异常<br/>