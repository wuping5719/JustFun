### 中国移动(苏州)研发中心秋招笔试题 ###

秋招面经： <https://github.com/wuping5719/Algorithm/blob/master/2-Java-Interview/2-36-ChinaMobile/SuZhou/Experiences/Experience20161025.md>
  
* 1.什么是java序列化？如何实现java序列化？    
&nbsp;  ` (1) 序列化就是一种用来处理对象流的机制(对象流就是将对象的内容进行流化). 可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决在对对象流进行读写操作时所引发的问题。 `   
&nbsp;  ` (2) 序列化的实现：将需要被序列化的类实现Serializable接口，该接口没有需要实现的方法，implements Serializable只是为了标注该对象是可被序列化的，然后使用一个输出流(如：FileOutputStream)来构造一个ObjectOutputStream(对象流)对象，接着，使用ObjectOutputStream对象的writeObject(Object obj)方法就可以将参数为obj的对象写出(即保存其状态)，要恢复的话则用输入流。 `
 
* 2.请解释以下两种内存溢出的原因，并写段java代码（伪代码）触发这些异常。   
&nbsp;&nbsp;  java.lang.StackOverflowError.  
&nbsp;&nbsp;  java.lang.OutOfMemoryError.    
&nbsp; ` (1) Java栈StackOverflowError： `     
&nbsp; ` JVM的运行时数据区中有一个叫做"虚拟机栈"的内存区域, 此区域的作用是: 每个方法在执行时都会创建一个栈帧, 用于存储局部变量表, 操作数栈, 方法出口等信息.因此我们可以创建一个无限递归的递归调用, 当递归深度过大时, 就会耗尽栈空间, 进而导致了StackOverflowError异常. `     
&nbsp; ` 示例代码: `
```java  
  public class OutOfMemoryErrorTest { 
       public static void main (String [] srgs) {
          stackOutOfMemoryError(1);
       }
       
       public static void stackOutOfMemoryError(int depth) {
          depth++;
          stackOutOfMemoryError(depth);
       }
  } 
```
&nbsp; ` (2) Java堆OutOfMemoryError:  `     
&nbsp; ` Java堆是用来存储对象实例的, 因此如果我们不断地创建对象, 并且保证GC Root和创建的对象之间有可达路径以免对象被垃圾回收, 那么当创建的对象过多时, 会导致heap内存不足, 进而引发OutOfMemoryError异常.`     
&nbsp; ` 示例代码: `
```java  
  public class OutOfMemoryErrorTest {
       public static void main (String[] args) {
            List<Integer> list = new ArryList<>();
            int i=0;
            while(true) {
               list.add(i++);
            }
       }
  }
```
  
* 3.192.168.0.1/24 使用掩码255.255.255.240划分子网，其可使用子网为（16）个，每个子网可用主机地址数（16）个.
&nbsp;&nbsp; ` 先将240转换为二进制是1111 0000，根据子网掩码255.255.255.240 `   
` 可知是管192.168.0.1/24借了四位主机位来表示网络，剩下四位是表示主机数.  `  
` 所以2的四次方=16.  192.168.0.1/24 使用掩码255.255.255.240划分子网，其可使用子网为（16）个，每个子网可用主机地址数（16）个.  `
   
* 4.单例模式.(输出：1,0)
```java  
  public class SingletonTest {
     public static void main(String[] args) {
        Singleton s = Singleton.getSingleton();
        System.out.print(s.counter1);  // 1
        System.out.print(",");
        System.out.print(s.counter2);  // 0
     }
  }

  class Singleton {
     private static Singleton singleton = new Singleton();
     public static int counter1;
     public static int counter2 = 0;  //静态变量赋默认值

     public Singleton() {
        counter1++;
        counter2++;
     }

     public static Singleton getSingleton() {
        return singleton;
     }
  }
```

* 5.String常量和char[]数组(传值和传引用). (输出：good and gbc)
```java  
  public class ExChangeTest {
     String str = new String("good");
     char[] ch = {'a', 'b', 'c'};
     public static void main(String args[]) {
	       ExChangeTest ex = new ExChangeTest();
        ex.change(ex.str, ex.ch);
        System.out.print(ex.str + " and ");  //good and 
        System.out.print(ex.ch);  //gbc 
     }

     public void change(String str, char ch[]) {
        str = "test ok";
        ch[0] = 'g';
     }
  }
```
 
* 6.try,catch,finally结构中return返回值问题.    
  (1) catch,finally中都有return语句，最后返回finally中的return结果(输出：2).
```java  
   public class CatchFinallyTest1 {
      public static void main(String[] args) {
        System.out.println(new Spock().test());
      }

      private int test() {
         int a = 1;
         int b;
         try {
            b = a / 0;
         } catch (Exception e) {
            return 1;
         } finally {
            return 2;   //不管是否发生异常，finally一定会执行，最后输出2
         }
      }
   }
```   
   (2) try中返回变量结果, finally中修改变量(输出：2).
```java  
   public class CatchFinallyTest2 {
     public static void main(String[] args) {
        System.out.println(new Spock().test());
     }

     private int test() {
         int i = 2;
         try {
            return i;  //finally会执行，但不会影响返回结果，仍返回未修改的值2
         } finally {
             ++i;
         }
      }
   }
```   
   
* 7.类的继承.(输出：father)
```java  
   public class Son extends Father {
      private String name = "son";
      public static void main(String[] args) {
         Son son = new Son();
         System.out.print(son.getName());  //执行父类方法，输出父类私有变量的值
         // String s;  
         // System.out.println("s=" + s);  //此处报错，s未初始化
      }
   }
   class Father {
      private String name = "father";
      public String getName() {
         return name;
      }
   }
```

* 8.静态局部变量.
 ```java 
  public class StaticLocalVariable{
     public int increase() {
         static int i = 0;  //此处报错，静态变量附属于类, 方法内不能有静态局部变量, 将static关键字去掉
         i++;
         return i;
     }
    
     public static void main(String args[]) {
        StaticLocalVariable test = new StaticLocalVariable();
        test.increase();
        int j = test.increase();
        System.out.println(j);
     }
  }
```

* 9.布尔变量.(输出：true)
```java 
  public class BooleanTest {
     public static void main(String args[]) {
	 Boolean flag = false;
	 if (flag = true) {   //此处为赋值号，相当于给flag赋值true
	    System.out.println("true");
	 } else {
	    System.out.println("false");
         }
     }
  }
```

* 10.类构造函数的执行顺序.(输出：staticA   staticB   not-staticA   HelloA   not-staticB   HelloB)
```java
  class HelloA {
    {
        System.out.println("not-staticA");  //3: 执行父类的默认构造函数
    }
    static {
        System.out.println("staticA");      //1: 执行父类的静态构造函数
    }
    public HelloA() {
        System.out.println("HelloA");       //4: 执行父类的构造函数
    }
  }

  public class HelloB extends HelloA {
    { 
        System.out.println("not-staticB");   //5: 执行子类的默认构造函数
    }
    static {
        System.out.println("staticB");     //2: 执行子类的静态构造函数
    }
    public Spock() {
        System.out.println("HelloB");      //6: 执行子类的构造函数
    }
    public static void main(String[] args) {
        new HelloB();
    }
  }
```

* 11.引用类型比较.(无输出)
```java
  public class TestLong {
    public static void main(String[] args) {
        Long tail = 2000L;
        Long distance = 1999L;
        Long story = 1000L;
        // ==运算符和equals()方法的区别
        // ==比较引用类型时注意: 即使数值相同，也不一定相等，地址可能不一样
        if((tail > distance) ^ ((story * 2) == tail)) {  
            System.out.print("1");
        }
        if((distance + 1 != tail) ^ ((story * 2) == distance)) {
            System.out.print("2");
        }
    }
  }
```

* 12.线程的执行顺序.(ChinaMobileHello)
```java
   public class Spock {
      public static synchronized void main(String[] a) {
         Thread t = new Thread() {
            public void run() {
                ChinaMobile();
            }
         };
         t.run();
         System.out.print("Hello");
      }
      static synchronized void ChinaMobile() {
         System.out.print("ChinaMobile");   
      }
   }
```
