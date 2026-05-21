# 二〇二五

***



## 11.28

### 位运算
1. 算术右移 >> 低位溢出,符号位不变,并用符号位补溢出的高位
2. 算术左移 << 符号位不变,低位补0
3. 逻辑右移 >>> 也叫无符号右移,运算规则是: 低位溢出，高位补 0
4. 特别说明:没有 <<< 符号

### 原码，反码，补码（hsp网课
1. 正数的原码，反码，补码都一样(三码合一
2. 负数的反码=它的原码符号位不变，其它位取反(0->1,1->0)
3. 负数的补码=它的反码+1
4. 0的反码，补码都是0
5. java没有无符号数，换言之，java中的数都是有符号的
6. 在计算机运算的时候，都是以补码的方式来运算的
7. 当我们看运算结果的时候，要看他的原码

### 补码（王爽 《汇编语言
1. 计算机中，为了使十进制数字0表达的二进制码不重复，或使十进制数字0仅有一个二进制码表示，创造了补码来表示对应的十进制数
2. 正数的补码由0开头，负数的补码由1开头
3. 正数的补码，可以直观看出。比如，0000 0000代表0，0000 0001代表1，0111 1111代表127
4. 负数的补码，由正数的补码取反并加一得到。这样，十进制数字0，0000 0000取反加一后，仍然为0000 0000，可以统一
5. 负数的补码不能直观地看出对应的十进制数，不过只要将其取反加一，便能得到该负数的绝对值。如，0111 1111，取反加一得1000 0001，这是-127的补码，再次取反加一得0111 1111，这是-127的绝对值。
6. 总的来说，正数的补码取反加一，得到负数的补码。负数的补码取反加一，得到的一串二进制数不再定义为补码，可以直接读取，表示的是该负数的绝对值。补码1000 0000，取反加一得二进制数1000 0000，大小为128，是-128的绝对值。因此，一个字节能表示有符号数的范围是-128~127。
7. 原码，反码，补码，第一次听像是一个十进制数转为二进制数的三种形态，了解过补码的来历后，感觉更像是计算机二进制数表达十进制数的三个版本，而补码就是最终版。

### this
1. 哪个对象调用，this就代表哪个对象



## 12.3

### 继承的内存
1.	继承内存细节:三个类,Son, Father, Grandf.初始化一个son对象时,首先顺序初始化Object,Grandf,Father,Son类,然后开始初始化对象,先初始化父类中的属性,方法,默认构造器,这时,如果父类中的属性有赋值,也会初始化进son对象中.如果子类和父类中都有名为name的属性,则由近及远地调用.

### 继承的细节
1. 子类继承了所有的属性和方法，非私有的属性和方法可以在子类直接访问,但是私有属性和方法不能在子类直接访问，要通过父类提供公共的方法去访问
2. 子类必须调用父类的构造器,完成父类的初始化
3. 当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中用 super 去指定使用父类的哪个构造器完成对父类的初始化工作，否则，编译不会通过
4. 如果希望指定去调用父类的某个构造器，则显式地调用一下
5. super在使用时，需要放在构造器第一行
6. super()和 this()都只能放在构造器第一行，因此这两个方法不能共存在一个构造器
7. java中所有类都是Object的子类
8. 父类构造器的调用不限于直接父类!将一直往上追溯直到Object类(顶级父类)
9. 子类最多只能继承一个父类(指直接继承)，即java中是单继承机制。
10. 不能滥用继承，子类和父类之间必须满足 is-a 的逻辑关系
###### 观至p296wan



# 二〇二六

---



## 4.1

### 单例模式,只有一个实例

- 饿汉式: 1.将构造器私有化; 2.在类的内部实例化私有静态的对象来作为属性; 3.提供一个返回对象的公共静态方法。
- 为什么叫懒汉式：使用该类中的其他静态属性时，会顺便初始化对象类型的属性，运行该方法需要不判断对象是否已被创建。
- 懒汉式: 1.将构造器私有化; 2.在类的内部定义私有静态的对象; 3.提供一个返回对象的公共静态方法。
- 该方法需要判断对象是否已被创建,若未创建,才创建对象。

###### p392wan



## 4.2

### final关键字

- 用于修饰类，方法，属性，局部变量，修饰后，类不可被继承，方法不可被重写，属性和局部变量不可被修改
- final修饰普通属性后，普通属性要在以下位置之一进行初始化：1.定义时，2.构造器中，3.代码块中
- final修饰静态属性后，静态属性要在以下位置之一进行初始化：1.定义时，2.静态代码块中
- final和static往往搭配使用，效率更高，不会导致类的初始化

###### p395wan



## 5.5

### 抽象类

- 定义：用abstract修饰，一个通常拥有抽象方法的父类。抽象方法没有方法体，用于被子类继承重写
- 细节：1 抽象类中不一定有抽象方法，含有抽象方法的类一定要定义为抽象类。2 abstract只能用于修饰类和方法。3 抽象类不能被实例化。4 继承了抽象类的类，一定要实现父类的所有抽象方法，除非这个类也声明为抽象类。5 private，final和static不能修饰抽象类
- 最佳实践：模板设计模式

```java
abstract public class Template{
    public abstract void job();
    
    public void calculateTime(){
        long start = System.currentTimeMillis();
        job();
        long end = System.currentTimeMillis();
        sout("task excute time" + (end - start));
    }
}
```

###### p401wan



## 5.6

### 接口

- 和抽象类有相似之处，接口的实现类则对应抽象类的子类。能够使协作的程序更规范。
- 细节：1 接口不能被实例化。2 接口中，方法public abstract void say(); 可以直接写成 void say();。3  接口中的属性int a=1;，实际上是public static final int a=1; ，接口中属性的访问形式为接口名.属性名。 4 一个非抽象类实现接口，就必须实现接口的所有方法。5一个类能同时实现多个接口。一个接口不能继承其他的类，但能继承多个别的接口。6 接口的修饰符只能是public和默认

```java
public class Computer{
    public void work(Interface interface){
        interface.start();
        interface.stop();
    }
}
```

其他三个类为Interface，Phone，Camera，类Phone，Camera实现了Interface，实例化Computer，Phone，Camera类后，通过computer.work(phone)和computer.work(camera)，能借助动态绑定机制调用Phone，Camera里的具体方法，体现了接口的多态。

###### p406wan



## 5.7

### 接口与继承

- 继承用于解决复用性和可维护性。接口用于设计好规范，让其他类实现抽象方法。

- 子类继承了父类，便自动拥有了父类的功能。如果子类需要额外的功能，则可以通过实现接口来获取。接口可以看做对单继承机制的一种补充。

###### p408



## 5.8

### 接口的多态数组

```java
interface Usb{
    void work();
}

class Phone implements Usb{
    public void call() {
        sout("手机可以打电话。");
    }
    @Override
    public void work() {
        sout("手机工作中。");
    }
}

class Camera implements Usb() {
    @Override
    public void work() {
        sout("相机工作中。");
    }
}

public class InterfacePolyArr {
    public static void main(String[] args) {
        Usb[] usbs = new Usb[2];
        usbs[0] = new Phone();
        usbs[1] = new Camera();
        for(int i=0; i<usbs.length; i++){
            usbs[i].work;
            if(usb[i] instansof Phone){
                ((Phone)usbs[i]).call();
            }
        }
    }
}
```

### 接口的多态传递

```java
Interface IA(){
    void hi();
}
Interface IB extends IA(){}
Class A implements IB(){
    @Override
    public void hi(){};
}
```

### 内部类

定义：一个类中嵌套着的类。

特点：直接访问所属外部类的私有属性。

分类：共4种，定义在局部位置上的**局部内部类**和**匿名内部类**，定义在成员位置上的**成员内部类**和**静态内部类**。

局部内部类细节：1.定义在方法体\代码块中。2.作用域在方法体\代码块中。3.本质上还是一个类。4.外部其他类不能访问局部内部类。5.外部类和内部类的成员重名时，遵循就近原则访问。

```java
class Outer{
    private n1 = 1;
    private void m1(){
        sout("Outer m1()");
    };
    private void m2(){
        class Inner{
            public void f1(){
                sout("n1" + n1);
                m1();
            }
        };
        Inner inner = new Inner();
        inner.f1();
    }
}
public class OuterOtherClass{
    public static void main(String[] args){
        Outer outer = new Outer();
        outer.m2();
    }
}
```

### 补充知识

1. 类被final修饰后，不可被继承。



## 5.9

### 匿名内部类

用于简化实现类，抽象子类，子类的写法。其实是在底层创建了一个Outer$1，然后直接new了赋给tiger，这个类new后就销毁了。

```java
interface IA(){
    void cry();
}
class Outer(){
    public void m(){
        IA tiger = new IA(){
            @Override
            public void cry(){
                sout("老虎叫。");
    		}
		};
        tiger.getClass();
        tiger.cry();
    }
}

```

### 补充知识

1.对象名.getClass()得到的是运行类型。



## 5.11

### 匿名内部类最佳实践

```java
public class OuterClass(){
    public static void main(String[] args){
       	Phone phone = new Phone();
        Phone.clock(new Bell(){
            @Override
            public void ring(){
                sout("懒猪起床了。");
            }
        });
        /*
        class OuterClass$2 implements Bell{
            @Override
            public double cal(double n5, double n6){
                return n5 + n6;
            }
        }
        下面的new Bell(){...}在底层是如上形式的
        */
        Phone.re(new Bell(){
            @Override
            public double cal(double n5, double n6){
                return n5 + n6;
            }
        }, 10, 20);
    }
}
interface Bell(){
    void ring();
    double cal(double n1, double n2);
}
class Phone(){
    public void clock(Bell bell){
        bell.ring();
    }
    public void re(Bell bell, double n3, double n4){
        double result = bell.cal(n3, n4);
        sout("计算结果=" + result);
    }
}
```

### 成员内部类

定义在外部类的成员位置上，当成类的一个成员用就行。

```java
//使用方法1
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
//使用方法2
在Outer类里定义一个方法，返回Inner的一个实例
Outer.Inner inner = outer.f();
```

### 静态内部类

定义在外部类的成员位置上，当成类的一个静态成员用就行。

```java
//同理，不过可以用静态的特性，可以不用实例化Outer了
//1
Outer.Inner inner = new Outer.Inner();
//2
在Outer类里定义一个静态方法，返回Inner的一个实例
Outer.Inner inner = Outer.f();
```

### 枚举

- 细节：1.使用enum关键字开发一个类时，这个类其实继承了java.lang.Enum类，而且是一个final类，通过javap这个类可以看出。2.枚举类不能继承其他的类，因为java单继承，枚举类已经继承了java.lang.Enum类了，但可以实现接口。

```java
enum Season(){
    //枚举的内容要写在类的开头
    SPRING("春天","暖"), SUMMER("夏天","热"), AUTUNM("秋天","凉"), WINTER("冬天","冷");
    private name;
    private desc;
    public Season(String name, String desc){
        this.name = name;
        this.desc = desc;
    }
}
```

### 补充

1. 静态方法只能访问静态成员，静态的类同理。
2. 非静态方法能访问静态和非静态的。
3. final修饰的属性通常大写。
4. 一个类的无参构造器默认存在，不用写出来。不过写了一个有参构造器后，有参构造器会覆盖默认存在的无参构造器，如果还要用到无参构造器，则要显式地声明出来。

###### p426wan



## 5.12

### 枚举常用方法

1. name()返回对象名。
2. ordinal()返回次序，从0开始计数。
3. values()返回所有枚举对象。
4. valueOf("枚举对象名")根据枚举对象名，匹配到就返回枚举对象，没有匹配到就报错。
5. compareTo(枚举对象)将调用此方法的枚举对象次序减去作为实参的枚举对象次序。

###### p430wan



## 5.13

### 注解Annotation之@Override

- 用于检测所注解的方法是否真的重写了。没有重写就报错。

### 注解Annotation之@Deprecated

- 标记过时的类，方法，属性等。

### 注解Annotation之@SuppressWarning

- 抑制报出的错误，更好看。

### 元注解，修饰注解的注解

### 异常

- 分为运行时异常和编译异常。

### 补充

1. 静态的含义；一个类的所有对象共有的属性。

###### p445wan



## 5.14

### 异常及处理方法try-catch-finally

- 机制：1.如果try中的代码异常，则try中异常后的代码不在执行，转而跳到catch继续执行。2.如果try中的代码无异常，则执行完try的代码后跳过catch。3.finally的代码每次都执行。4.可以写多个catch，子异常类要写在父异常类Exception的前面。5.可以不写catch，只写try和finally，这样，如果try中代码异常，程序就会先把finally里的代码执行完，异常则会一直向上传递到jvm，jvm会直接输出异常信息，然后报错。
- 常见异常：1.NullPointerException空指针。2.ArithmeticException算数。3.ArrayIndexOutOfBoundsException数组越界。4.ClassCastException类投射。5.NumberFormatException格式转换。

```java
try{
    //Person person = null;
    Person person = new Person();
    person.getName();
    int n1 = 1;
    //int n2 = 0;
	int n2 = 2;
}catch(NullPointerException e){
    sout(e.getMessage());
}catch(ArithmeticException e){
    sout(e.getMessage());
}catch(Exception e){
    sout(e.getMessage());
}
finally{
    sout("无论try中是否异常都会执行。");
}


```

- 最佳实践：配合循环，让用户输入固定类型，否则输出提示，一直循环。

### throws

抛出异常，方法抛出异常，则由调用该方法的调用者处理该异常。

- 细节：1.编译异常必须处理，用try-catch或throws。2.运行时异常如果没处理，则默认throws。3.子类抛出的异常的类型必须是父类抛出异常类型的子类或同类。

### 补充

1. int a的值默认为零。

###### p458wan



## p459-p497暂时跳过



## 5.16

### 集合

- 单列集合Collection，一个储存对象：1. List（有序）	1.1. ArrayList	1.2. LinkedList	1.3. Vector	2. Set（无序）	2.1. Hashset	2.2. TreeSet
  - 1.1. ArrayList	1.2. LinkedList	1.3. Vector是List接口的常用实现类。2.1. Hashset	2.2. TreeSet同理。
- 双列集合Map，储存键值对：1. HashMap	1.1. LinkedHashMap	2. TreeMap	3. HashTable	3.1. Properties
  - 1. HashMap是Map接口的实现类，2. TreeMap，3. HashTable同理。
  - 1.1. LinkedHashMap是1. HashMap类的子类。3.1. Properties同理。
- Collection常用方法：
  - add添加单个元素
  - remove删除指定元素
  - contains查找元素是否存在
  - size获取元素个数
  - isEmpty判断是否为空
  - clear清空
  - addAll添加多个元素
  - containsAll查找多个元素是否都存在
  - removeAll删除多个元素
- 迭代器iterator：利用循环关键字，hasNext()和next()可以遍历list里的元素。增强for循环底层用的也是这个方法。

###### p503wan



## 5.17

### 泛型，用于表示数据类型的数据类型（p553-p555）

- 对比旧方法

  - 两点优势：1. 对传入的对象进行类型检测。2. 减少类型转换次数。

  ```java
  //旧方法
  ArrayList arrayList = new ArrayList();
  arrayList.add(new Dog("小白"));
  arrayList.add(new Dog("小黄"));
  arrayList.add(new Cat("小花"));//检测不出
  for (Object o : arrayList){
      Dog dog = (Dog)o;
      sout(dog.getName());
  }
  
  //新方法
  ArrayList<Dog> arrayList = new ArrayList<Dog>();
  arrayList.add(new Dog("小白"));
  arrayList.add(new Dog("小黄"));
  arrayList.add(new Cat("小花"));//能检测出，编译报错
  for (Dog o : arrayList){
      //Dog dog = (Dog)o;可以直接取出Dog类，不再需要类型转换
      sout(dog.getName());
  }
  ```

- 在类中的应用，尖括号中的可以是任意字母，通常用E,T,V,K，这些字母不代表值，而是表示类型。

  ```java
  class Person<E>{
      E s;
      public Person(E s){
          this.s = s;
      }
      public E f(){
          return s;
      }
  }
  ```

### 转回第集合篇，从p504开始

### List接口

- 容器规则：
  - 元素在容器内是有序的，添加和取出顺序一致，可以重复。
  - 支持索引，能通过下标访问。object get(int index)

- 常用方法
  - void add(int index, Object ele)：在index位置添加ele元素
  - boolean addAll(int index, Collection eles)：从index位置开始将eles中的所有元素添加进来
  - Object get(int index)：返回index位置的元素
  - int indexOf(Object obj)：返回obj在集合中首次出现的位置
  - int lastIndexOf(Object obj)：返回obj在集合中末次出现的位置
  - Object remove(int index)：移除index位置的元素，并返回此元素
  - Object set(int index, Object ele)：替换index位置的元素为ele，若index越界，则报异常

###### p506wan



## 5.18

### ArrayList和Vector底层源码解读

- 比较：
  1. 前者线程不安全，效率高；后者相反。
  2. 扩容机制：前者无参构造默认给10个大小，超过后每次扩容1.5倍；后者无参构造默认给10个大小，若定义时构造器里没设置increment（每次扩容时增加大小）变量，超过后每次扩容2倍。
  3. ArrayList基本等同于Vector，二者主要在于线程安全的区别。



## 5.20

### List集合的选择

- ArrayList，增删慢，改查快，线程不安全。
- Vector，增删慢，改查快，线程安全。
- LinkedList，增删快，改查慢，线程不安全。

### Set接口

- 特点；
  - 能放null，只能一个。
  - 无序，添加和取出顺序不一致，取出顺序固定，没有索引。数组+单向链表
  - 重复对象添加无效。

- 常用方法；add(), remove(), iterator()

### HashSet最佳实践

- 通过从写hashCode()和equals()方法，决定自定义类中某些属性相同的对象是否能再加入HashSet中。hashCode()决定在那条链表上，equals()决定是否能插入。可以通过alt+insert快捷键写。

### LinkedHashSet

- 特点：
  - 能放null，只能一个。
  - 添加和取出顺序一致。数组+双向链表
  - 重复对象添加无效。

### Map接口

- jdk8的Map特点：
  - Map与Collection并列存在。
  - Map中的key和value可以是任何引用数据类型。
  - key不能重复，value可以重复。
  - Map中的key和value都可以为null，key为null只能有一个，value能有多个。
  - 常用String类作为key。
  - 能通过key取出value。
  - HashSet和LinkedHashSet底层都用到了HashMap，HashSet和LinkedHashSet其实是只有key的Map，value位置用PRESENT常量替代，是一个new Object()。

###### p530wan



## 5.21

### Map接口

- 常用方法：put，remove，get，size，isEmpty，clear，containsKey
- 遍历方式：
  - 取出Set类型的keySet，通过迭代器遍历key，配合get方法得到value
  - 取出Collection类型的values，迭代器直接遍历。
  - 取出Set类型的entrySet，转型为Map.Entry后，配合getKey和getValue方法迭代器遍历。

### HashMap

- key，value可以为空。key只能一个null。
- 线程不安全。效率高。

### HashTable

- key和value都不能为null，否则报错。
- 线程安全。效率较低。
- 扩容机制：乘2加1。

### Properties extends HashTable

- 继承HashTable
- 还可以用于从xxx.properties文件中，加载数据到Properties类对象，并进行读取和修改。

### 补充

- 树化条件：数组大小达到64，链表长度大于8，红黑树化。

###### p5wan（跳过了一些源码解读）

二次

