---
title: 👩🏼‍🏫 八股文
summary: 面试八股文
date: 2025-10-24
math: true
authors:
  - admin
tags:
  - java
  - 八股
  - Markdown
image:
  caption: 'Embed rich media such as videos and LaTeX math'
---
# 高频

# JAVA

## 数据结构

### 八种基本的数据类型

●Java八种基本数据类型的字节数：1字节(byte、boolean)、 2字节(short、char)、4字节(int、float)、8字节(long、double)  
●浮点数的默认类型为double（如果需要声明一个常量为float型，则必须要在末尾加上f或F）  
●整数的默认类型为int（声明Long型在末尾加上l或者L）  
●八种基本数据类型的包装类：除了char的是Character、int类型的是Integer，其他都是首字母大写  
●char类型是无符号的，不能为负，所以是0开始的

BigDecimal 是精确计算 , 所以一般牵扯到金钱的计算 , 都使用 BigDecimal。

### Integer相比int有什么优点？

Integer和 int 的区别：  
●基本类型和引用类型：首先，int是一种基本数据类型，而Integer是一种引用类型。基本数据类型是Java中最基本的数据类型，它们是预定义的，不需要实例化就可以使用。而引用类型则需要通过实例化对象来使用。在性能方面，基本数据类型的操作通常比相应的引用类型快。  
●自动装箱和拆箱：其次，Integer作为int的包装类，它可以实现自动装箱和拆箱。  
●空指针异常：另外，int变量可以直接赋值为0，而Integer变量必须通过实例化对象来赋值。如果对一个未经初始化的Integer变量进行操作，就会出现空指针异常。这是因为它被赋予了null值，而null值是无法进行自动拆箱的  
另一个非常重要的原因就是在Java中绝大部分方法或类都是用来处理类型对象的，如ArrayList集合类就只能以类作为他的存储对象，而这时如果想把一个int型的数据存入list是不可能的，必须把它包装成类，也就是Integer才能被List所接受。所以Integer的存在是很必要的

## 基础

### [静态变量有什么作用？](https://javaguide.cn/java/basis/java-basic-questions-01.html#%E9D%EE8F%E8F%E9C%EBB%EBEBD%9C%EA8)

静态变量也就是被 static 关键字修饰的变量。它可以被类的所有实例共享，无论一个类创建了多少个对象，它们都共享同一份静态变量。也就是说，静态变量只会被分配一次内存，即使创建多个对象，这样可以节省内存。  
静态变量是通过类名来访问的，例如StaticVariableExample.staticVar（如果被 private关键字修饰就无法这样访问了）。

\[codeblock卡片内容\]

通常情况下，静态变量会被 final 关键字修饰成为常量。
### \== 与 equals 有什么区别？

\==  
●对于基本类型：比较数值是否相等。int、double、char、boolean 这些，\== 比较的是它们存储的“值”是否相同。  
●对于引用类型：比较的是两个引用是否指向同一个对象（即地址相同）。 对象、数组、字符串（注意：字符串字面量有常量池优化 ）  
equals()  
●定义在 Object 类中，默认实现等价于 \==（比较地址）。  
●但是很多类（如 String、包装类、集合类）重写了 equals() 方法，改成比较对象内容。  
【补充：Java 对 Integer、Short、Byte、Character 等包装类做了缓存（默认范围是 -128 到 127）。】
### [#](https://xiaolincoding.com/interview/java.html#hashcode%E8Cequals%EBEBE9C%EBB%EBEBEBBB)hashcode和equals方法有什么关系？

equals相等，hashcode一定相等。hashcode相等，equals不一定相等。  
重新equals，必须要重写hashCode  
在 Java 中，对于重写 equals 方法的类，通常也需要重写 hashCode 方法，并且需要遵循以下规定：  
●一致性：如果两个对象使用 equals 方法比较结果为 true，那么它们的 hashCode 值必须相同。也就是说，如果 obj1.equals(obj2) 返回 true，那么 obj1.hashCode() 必须等于 obj2.hashCode()。  
●非一致性：如果两个对象的 hashCode 值相同，它们使用 equals 方法比较的结果不一定为 true。即 obj1.hashCode() == obj2.hashCode() 时，obj1.equals(obj2) 可能为 false，这种情况称为哈希冲突。  
hashCode 和 equals 方法是紧密相关的，重写 equals 方法时必须重写 hashCode 方法，以保证在使用哈希表等数据结构时，对象的相等性判断和存储查找操作能够正常工作。而重写 hashCode 方法时，需要确保相等的对象具有相同的哈希码，但相同哈希码的对象不一定相等。
### [#](https://xiaolincoding.com/interview/java.html#string%E81stringbuffer%E81stringbuilder%E9A%E8C%BA%EAB%E8C%EEBBB)String、StringBuffer、StringBuilder的区别和联系

1、可变性 ：String 是不可变的（Immutable），一旦创建，内容无法修改，每次修改都会生成一个新的对象。StringBuilder 和 StringBuffer 是可变的（Mutable），可以直接对字符串内容进行修改而不会创建新对象。  
2、线程安全性 ：String 因为不可变，天然线程安全。StringBuilder 不是线程安全的，适用于单线程环境。StringBuffer 是线程安全的，其方法通过 synchronized 关键字实现同步，适用于多线程环境。  
3、性能 ：String 性能最低，尤其是在频繁修改字符串时会生成大量临时对象，增加内存开销和垃圾回收压力。StringBuilder 性能最高，因为它没有线程安全的开销，适合单线程下的字符串操作。StringBuffer 性能略低于 StringBuilder，因为它的线程安全机制引入了同步开销。  
4、使用场景 ：如果字符串内容固定或不常变化，优先使用 String。如果需要频繁修改字符串且在单线程环境下，使用 StringBuilder。如果需要频繁修改字符串且在多线程环境下，使用 StringBuffer。  
对比总结如下：  
| 特性 | String | StringBuilder | StringBuffer |
| --- | --- | --- | --- |
| 特性 | String | StringBuilder | StringBuffer |
| 不可变性 | 不可变 | 可变 | 可变 |
| 线程安全 | 是（因不可变） | 否 | 是（同步方法） |
| 性能 | 低（频繁修改时） | 高（单线程） | 中（多线程安全） |
| 适用场景 | 静态字符串 | 单线程动态字符串 | 多线程动态字符串 |

例子代码如下：

\[codeblock卡片内容\]

●操作少量的数据: 适用 String  
●单线程操作字符串缓冲区下操作大量数据: 适用 StringBuilder  
●多线程操作字符串缓冲区下操作大量数据: 适用 StringBuffer
### 浅拷贝 and 深拷贝

浅拷贝只复制对象的基本类型字段和引用类型的引用地址。  
深拷贝则会递归复制引用对象，保证拷贝对象完全独立。

\[hr卡片内容\]

### 说一下 Java IO 的分类。

Java 的 IO（输入输出）体系主要分为两大类：  
1\. 传统 IO（java.io 包）  
面向 流（Stream） 的阻塞式 IO。  
2\. NIO（java.nio 包）  
面向 缓冲区（Buffer） 的非阻塞式 IO，适用于高性能网络通信。

\[hr卡片内容\]

二、传统 IO 的分类（最常考部分）  
按照数据的处理方式和方向划分：  
| 分类维度 | 类型 | 代表类 | 说明 |
| --- | --- | --- | --- |
| 分类维度 | 类型 | 代表类 | 说明 |
| 按方向 | 输入流（Input） | InputStream、Reader | 从外部读取数据到程序 |
|   | 输出流（Output） | OutputStream、Writer | 从程序写数据到外部 |
| 按数据类型 | 字节流（Byte Stream） | InputStream/ OutputStream | 处理二进制数据（图片、音频、文件） |
|   | 字符流（Character Stream） | Reader/ Writer | 处理文本（自动编码转换） |

## 集合Collection

Collection 下面主要有三大分支：List、Set 和 Queue。

\[hr卡片内容\]

### 1\. List（有序、可重复）

特点：元素有顺序，可以存放重复元素，可通过索引访问。 常用实现类：  
●ArrayList —— 底层是动态数组，查询快，增删中间元素慢。  
●LinkedList —— 底层是双向链表，插入删除快，查询慢。  
●Vector —— 线程安全，底层是数组（已过时，基本被 ArrayList 替代）。  
●Stack —— 继承 Vector，后进先出（LIFO）栈结构。

\[hr卡片内容\]

### 2\. Set（无序、不重复）

特点：元素不可重复，主要用于去重。 常用实现类：  
●HashSet —— 基于 HashMap 实现，元素无序，查找快。  
●LinkedHashSet —— 保证元素插入顺序，内部用链表维护。  
●TreeSet —— 基于 TreeMap（红黑树），元素有序（自然顺序或自定义 Comparator）。  
●EnumSet —— 专门用来存放枚举类型，性能优于 HashSet。

\[hr卡片内容\]

### 3\. Queue（队列 / 双端队列）

特点：支持队列操作，先进先出（FIFO），或者双端操作。 常用实现类：  
●PriorityQueue —— 优先队列，元素自动排序（自然顺序或自定义比较器）。  
●ArrayDeque —— 双端队列，效率比 Stack、LinkedList 更高。  
●LinkedList —— 也可以作为队列或双端队列使用。

●使用Collections类的synchronizedList方法将ArrayList包装成线程安全的List：

\[codeblock卡片内容\]

Vecotor 是线程安全的
### Arraylist和LinkedList的区别，哪个集合是线程安全的？

ArrayList和LinkedList都是Java中常见的集合类，它们都实现了List接口。  
●底层数据结构不同：ArrayList使用数组实现，通过索引进行快速访问元素。LinkedList使用链表实现，通过节点之间的指针进行元素的访问和操作。  
●插入和删除操作的效率不同：ArrayList在尾部的插入和删除操作效率较高，但在中间或开头的插入和删除操作效率较低，需要移动元素。LinkedList在任意位置的插入和删除操作效率都比较高，因为只需要调整节点之间的指针，但是LinkedList是不支持随机访问的，所以除了头结点外插入和删除的时间复杂度都是0(n)，效率也不是很高所以LinkedList基本没人用。  
●随机访问的效率不同：ArrayList支持通过索引进行快速随机访问，时间复杂度为O(1)。LinkedList需要从头或尾开始遍历链表，时间复杂度为O(n)。  
●空间占用：ArrayList在创建时需要分配一段连续的内存空间，因此会占用较大的空间。LinkedList每个节点只需要存储元素和指针，因此相对较小。  
●使用场景：ArrayList适用于频繁随机访问和尾部的插入删除操作，而LinkedList适用于频繁的中间插入删除操作和不需要随机访问的场景。  
●线程安全：这两个集合都不是线程安全的，Vector是线程安全的
### ArrayList线程安全吗？把ArrayList变成线程安全有哪些方法？

不是线程安全的，ArrayList变成线程安全的方式有：  
●使用Collections类的synchronizedList方法将ArrayList包装成线程安全的List：

\[codeblock卡片内容\]

●使用CopyOnWriteArrayList类代替ArrayList，它是一个线程安全的List实现：

\[codeblock卡片内容\]

●使用Vector类代替ArrayList，Vector是线程安全的List实现：

\[codeblock卡片内容\]

### ArrayList的创建和扩容

ArrayList 底层是数组实现的，当添加元素时，如果当前数组容量不足，会进行扩容。扩容规则是：新容量 = 旧容量 + 旧容量的一半，也就是 1.5 倍。  
默认初始容量是 10，但可以通过构造函数指定初始容量，避免频繁扩容。
### HashMap的扩容

HashMap 底层是数组+链表/红黑树  
当元素数量超过 capacity（16） × load factor（0.75） 时会扩容。  
扩容规则是容量翻倍， 据哈希值的高一位决定新位置：如果高位是 0，元素位置不变；如果高位是 1，元素位置移动到原索引 + 原容量。  
JDK 8 还会根据链表长度把链表转成红黑树来优化查询。

### 什么是 HashMap？

HashMap 是 Java 中最常用的数据结构之一，用于存储键值对（Key-Value）。它基于哈希表实现，具有快速的查找和插入性能。  
●无序存储：插入顺序不会被记录。  
●允许一个 null 键和多个 null 值。  
●非线程安全：多个线程同时访问需使用 ConcurrentHashMap 或加锁。  
●底层结构：  
○JDK 1.7：数组 + 链表  
○JDK 1.8：数组 + 链表 + 红黑树（当链表长度超过阈值时转为红黑树）  
🧩工作原理简述：  
1计算哈希值：  
○使用 key.hashCode() 生成哈希值。  
2定位数组索引：  
○使用 (n - 1) & hash 计算索引位置（n 是数组长度，必须是 2 的幂）以提高效率。  
3处理哈希冲突：  
○如果多个键映射到同一索引位置，使用链表存储。  
○当链表长度超过 8 且数组长度超过 64 时，链表转换为红黑树以提高查询效率。
### 解决 HashMap 线程安全的常见方式

#### 1\. 使用 Collections.synchronizedMap()

●将 HashMap 包装成线程安全的 Map。  
●每次访问都对整个 Map 加锁，适合低并发场景。  
java

\[codeblock卡片内容\]

●⚠️ 注意：遍历时需要手动同步：  
java

\[codeblock卡片内容\]

#### 2\. 使用 ConcurrentHashMap（推荐 ✅）

●高性能线程安全 Map，适合高并发场景。  
●JDK 1.8 之后使用 CAS（Compare-And-Swap）和synchronized。  
java

\[codeblock卡片内容\]

●支持并发读写，效率远高于同步整个 Map。
### ConcurrentHashMap —— “分段+CAS 的高并发智者”

ConcurrentHashMap 是为了解决 Hashtable 的性能瓶颈而设计的。不同版本实现略有差异：
#### JDK 1.7：分段锁（Segment Lock）

●整个 Map 被分成多个 Segment，每个 Segment 像一个小 Hashtable。  
●多个线程可以同时操作不同 Segment，提高并发性能。  
●锁粒度是 Segment 级别。默认有 16 个 Segment，也就是说理论上可以有 16 个线程同时写。  
缺点：结构相对复杂，每次操作要先定位 Segment，再定位桶。
#### JDK 1.8：取消 Segment，改用 CAS + synchronized 细粒度锁

●整个 Map 用 Node 数组 + 链表/红黑树。  
●写操作：先用 CAS（无锁原子操作）尝试占位，如果失败，再退而使用 synchronized 锁住某个桶位的链表或树节点，而不是整张表。  
●读操作大多是无锁的，只读 volatile 变量保证可见性。  
●扩容时采用多线程协助扩容机制，避免单线程扩容卡死。
### JDK1.8版本：hashmap和concurrenthashmap的区别

●内存结构：hashmap采用数组 + 链表 + 红黑树的结构，当链表长度超过一定阈值（默认为 8）时，链表会转换为红黑树，以提高查找效率。ConcurrentHashMap弃了分段锁机制，采用 CAS + synchronized 来保证线程安全，内部结构同样是数组 + 链表 + 红黑树。  
●线程安全性：hashmap仍然是非线程安全的，多线程环境下的问题依然存在。ConcurrentHashMap通过 CAS 和 synchronized 保证线程安全。在插入元素时，首先会尝试使用 CAS 操作更新节点，如果 CAS 失败，则使用 synchronized 锁住当前节点，再进行插入操作。  
●性能：hashmap在单线程环境下，由于红黑树的引入，当链表较长时查找效率会有所提高。ConcurrentHashMap在多线程环境下，由于摒弃了分段锁，减少了锁的粒度，进一步提高了并发性能。同时，红黑树的引入也提高了查找效率。
## 面向对象

### 怎么理解面向对象？简单说说封装继承多态

面向对象是一种编程范式，它将现实世界中的事物抽象为对象，对象具有属性（称为字段或属性）和行为（称为方法）。  
Java面向对象的三大特性包括：封装、继承、多态：  
●封装：封装是指将对象的属性（数据）和行为（方法）结合在一起，对外隐藏对象的内部细节，仅通过对象提供的接口与外界交互。封装的目的是增强安全性和简化编程，使得对象更加独立。  
●继承：继承是一种可以使得子类自动共享父类数据结构和方法的机制。它是代码复用的重要手段，通过继承可以建立类与类之间的层次关系，使得结构更加清晰。  
●多态：多态是指允许不同类的对象对同一消息作出响应。即同一个接口，使用不同的实例而执行不同操作。多态性可以分为编译时多态（重载）和运行时多态（重写）。它使得程序具有良好的灵活性和扩展性。
### 抽象类和普通类区别

| 特性 | 抽象类 | 普通类 |
| --- | --- | --- |
| 特性 | 抽象类 | 普通类 |
| 是否可实例化 | ❌ 不能直接实例化 | ✅ 可以直接创建对象 |
| 是否包含抽象方法 | ✅ 可以包含抽象方法（无方法体） | ❌ 不允许有抽象方法 |
| 方法实现 | ✅ 可包含已实现和未实现的方法 | ✅ 所有方法必须有实现 |
| 继承要求 | ✅ 子类必须实现所有抽象方法 | ❌ 子类可选择性重写方法 |
| 使用场景 | 模板设计、定义通用行为 | 实现具体功能、创建实际对象 |

抽象类是“蓝图”，普通类是“建筑”；抽象类定义结构，普通类实现功能。  
抽象类不能使用final修饰符
### 什么是泛型 (T)？

泛型是 Java 编程语言中的一个重要特性，它允许类、接口和方法在定义时使用一个或多个类型参数，这些类型参数在使用时可以被指定为具体的类型。  
泛型就是让你在编程时“先不确定具体的数据类型”，等使用时再指定。  
用处：  
●自定义接口通用返回结果 CommonResult<T> 通过参数 T 可根据具体的返回类型动态指定结果的数据类型  
●定义 Excel 处理类 ExcelUtil<T> 用于动态指定 Excel 导出的数据类型  
●构建集合工具类（参考 Collections 中的 sort, binarySearch 方法）。

### 如何获取私有对象？

使用公共访问器方法（getter 方法）  
反射机制。
### 什么是反射？

Java 反射 (Reflection) 是一种在程序运行时，动态地获取类的信息并操作类或对象（方法、属性）的能力。

### [反射的应用场景？](https://javaguide.cn/java/basis/java-basic-questions-03.html#%E8F%8D%EBE9A%EBA%EAE9C%BA%EAF)

我们平时写业务代码可能很少直接跟 Java 的反射（Reflection）打交道。但你可能没意识到，你天天都在享受反射带来的便利！很多流行的框架，比如 Spring/Spring Boot、MyBatis 等，底层都大量运用了反射机制，这才让它们能够那么灵活和强大。  
下面简单列举几个最场景的场景帮助大家理解。  
1.依赖注入与控制反转（IoC）  
以 Spring/Spring Boot 为代表的 IoC 框架，会在启动时扫描带有特定注解（如 @Component, @Service, @Repository, @Controller）的类，利用反射实例化对象（Bean），并通过反射注入依赖（如 @Autowired、构造器注入等）。  
2.注解处理  
注解本身只是个“标记”，得有人去读这个标记才知道要做什么。反射就是那个“读取器”。框架通过反射检查类、方法、字段上有没有特定的注解，然后根据注解信息执行相应的逻辑。比如，看到 @Value，就用反射读取注解内容，去配置文件找对应的值，再用反射把值设置给字段。  
3.动态代理与 AOP  
想在调用某个方法前后自动加点料（比如打日志、开事务、做权限检查）？AOP（面向切面编程）就是干这个的，而动态代理是实现 AOP 的常用手段。JDK 自带的动态代理（Proxy 和 InvocationHandler）就离不开反射。代理对象在内部调用真实对象的方法时，就是通过反射的 Method.invoke 来完成的。

\[codeblock卡片内容\]

4.对象关系映射（ORM）  
像 MyBatis、Hibernate 这种框架，能帮你把数据库查出来的一行行数据，自动变成一个个 Java 对象。它是怎么知道数据库字段对应哪个 Java 属性的？还是靠反射。它通过反射获取 Java 类的属性列表，然后把查询结果按名字或配置对应起来，再用反射调用 setter 或直接修改字段值。反过来，保存对象到数据库时，也是用反射读取属性值来拼 SQL。
### [重载和重写有什么区别？](https://javaguide.cn/java/basis/java-basic-questions-01.html#%EAD%EF%B8F%E8D%EBD%BD%E8C%E8D%EE9C%EBB%EBE8C%BA%EAB)

重载就是同样的一个方法能够根据输入数据的不同，做出不同的处理  
重写就是当子类继承自父类的相同方法，输入数据一样，但要做出有别于父类的响应时，你就要覆盖父类方法
#### [重载](https://javaguide.cn/java/basis/java-basic-questions-01.html#%E8D%EBD%BD)

发生在同一个类中（或者父类和子类之间），方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以不同。  
综上：重载就是同一个类中多个同名方法根据不同的传参来执行不同的逻辑处理。
#### [重写](https://javaguide.cn/java/basis/java-basic-questions-01.html#%E8D%E99)

重写发生在运行期，是子类对父类的允许访问的方法的实现过程进行重新编写。  
1方法名、参数列表必须相同，子类方法返回值类型应比父类方法返回值类型更小或相等，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类。  
2如果父类方法访问修饰符为 private/final/static 则子类就不能重写该方法，但是被 static 修饰的方法能够被再次声明。  
3构造方法无法被重写
#### [总结](https://javaguide.cn/java/basis/java-basic-questions-01.html#%EBB%EBB%93)

综上：重写就是子类对父类方法的重新改造，外部样子不能改变，内部逻辑可以改变。  
| 区别点 | 重载 (Overloading) | 重写 (Overriding) |
| --- | --- | --- |
| 区别点 | 重载 (Overloading) | 重写 (Overriding) |
| 发生范围 | 同一个类中。 | 父类与子类之间（存在继承关系）。 |
| 方法签名 | 方法名必须相同，但参数列表必须不同（参数的类型、个数或顺序至少有一项不同）。 | 方法名、参数列表必须完全相同。 |
| 返回类型 | 与返回值类型无关，可以任意修改。 | 子类方法的返回类型必须与父类方法的返回类型相同，或者是其子类。 |
| 访问修饰符 | 与访问修饰符无关，可以任意修改。 | 子类方法的访问权限不能低于父类方法的访问权限。（public > protected > default > private） |
| 绑定时期 | 编译时绑定或称静态绑定 | 运行时绑定 (Run-time Binding) 或称动态绑定 |

方法的重写要遵循“两同两小一大”（以下内容摘录自《疯狂 Java 讲义》，[issue#892](https://github.com/Snailclimb/JavaGuide/issues/892) ）：  
●“两同”即方法名相同、形参列表相同；  
●“两小”指的是子类方法返回值类型应比父类方法返回值类型更小或相等，子类方法声明抛出的异常类应比父类方法声明抛出的异常类更小或相等；  
●“一大”指的是子类方法的访问权限应比父类方法的访问权限更大或相等。  
⭐️ 关于 重写的返回值类型 这里需要额外多说明一下，上面的表述不太清晰准确：如果方法的返回类型是 void 和基本数据类型，则返回值重写时不可修改。但是如果方法的返回值是引用类型，重写时是可以返回该引用类型的子类的。

\[codeblock卡片内容\]

## 多线程

### Java有几种创建线程的方式

Java创建线程有很多种方式，像实现Runnable、Callable接口、继承Thread类、创建线程池 ExecutorService 等等，不过这些方式并没有真正创建出线程，严格来说，Java就只有一种方式可以创建线程，那就是通过new Thread().start()创建。  
1\. 继承Thread类并重写run方法。 2\. 实现Runnable接口并实现run方法。 3\. 使用Callable接口配合FutureTask实现带返回值的线程。 4\. 通过线程池（如Executor框架）创建管理线程。

### [述线程与进程的关系,区别及优缺点？](https://javaguide.cn/java/concurrent/java-concurrent-questions-01.html#%EAD%EF%B8F%EAF%BEAE%EAE8F%8F%EBF%BEBA%BF%EA8B%EB8E%EBF%9B%EA8B%E9A%EBEBBB-%E8C%BA%EAB%E8F%8A%EBC%EBC%BA%EB9)

下图是 Java 内存区域，通过下图我们从 JVM 的角度来说一下线程和进程之间的关系。

从上图可以看出：一个进程中可以有多个线程，多个线程共享进程的堆和方法区 (JDK1.8 之后的元空间)资源，但是每个线程有自己的程序计数器、虚拟机栈 和 本地方法栈。  
总结： 线程是进程划分成的更小的运行单位。线程和进程最大的不同在于基本上各进程是独立的，而各线程则不一定，因为同一进程中的线程极有可能会相互影响。线程执行开销小，但不利于资源的管理和保护；而进程正相反。  
背）  
进程是操作系统资源分配的最小单位；线程是进程中负责执行的最小单位。  
●进程：有自己独立的内存空间和资源，互不干扰，但切换开销大。  
●线程：共享进程的资源，创建和切换开销小，但容易出现数据竞争。
### [Thread#sleep() 方法和 Object#wait() 方法对比](https://javaguide.cn/java/concurrent/java-concurrent-questions-01.html#thread-sleep-%EBEBE8C-object-wait-%EBEBEAF%BEAF%94)

共同点：两者都可以线程的执行。  
区别：  
●sleep() 方法没有释放锁，而 wait() 方法释放了锁 。  
●wait() 通常被用于线程间交互/通信，sleep()通常被用于执行。  
●wait() 方法被调用后，线程不会自动苏醒，需要别的线程调用同一个对象上的 notify()或者 notifyAll() 方法。sleep()方法执行完成后，线程会自动苏醒，或者也可以使用 wait(long timeout) 超时后线程会自动苏醒。  
●sleep() 是 Thread 类的静态本地方法，wait() 则是 Object 类的本地方法。为什么这样设计呢？下一个问题就会聊到。
### [为什么 wait() 方法不定义在 Thread 中？](https://javaguide.cn/java/concurrent/java-concurrent-questions-01.html#%EBBA%EBB%EB88-wait-%EBEBEB8D%EAE%9A%EBE9C%A8-thread-%EBAD)

wait() 是让获得对象锁的线程实现等待，会自动释放当前线程占有的对象锁。每个对象（Object）都拥有对象锁，既然要释放当前线程占有的对象锁并让其进入 WAITING 状态，自然是要操作对应的对象（Object）而非当前的线程（Thread）。  
类似的问题：为什么 sleep() 方法定义在 Thread 中？  
因为 sleep() 是让当前线程执行，不涉及到对象类，也不需要获得对象锁。
### [可以直接调用 Thread 类的 run 方法吗？](https://javaguide.cn/java/concurrent/java-concurrent-questions-01.html#%E8F%AF%EBB%AE9B%BE8E%AEBEA8-thread-%EBBB%E9A%84-run-%EBEBE97)

这是另一个非常经典的 Java 多线程面试问题，而且在面试中会经常被问到。很简单，但是很多人都会答不上来！  
new 一个 Thread，线程进入了新建状态。调用 start()方法，会启动一个线程并使线程进入了就绪状态，当分配到时间片后就可以开始运行了。 start() 会执行线程的相应准备工作，然后自动执行 run() 方法的内容，这是真正的多线程工作。 但是，直接执行 run() 方法，会把 run() 方法当成一个 main 线程下的普通方法去执行，并不会在某个线程中执行它，所以这并不是多线程工作。  
总结：调用 start() 方法方可启动线程并使线程进入就绪状态，直接执行 run() 方法的话不会以多线程的方式执行。

### 如何创建线程池？线程池常见参数有哪些？

在 Java 中，创建线程池主要通过 java.util.concurrent.Executors 工具类或直接使用 ThreadPoolExecutor 类。推荐使用 ThreadPoolExecutor，因为 Executors 提供的工厂方法（如 newFixedThreadPool、newCachedThreadPool）存在潜在风险（如无界队列可能导致 OOM）。

\[codeblock卡片内容\]

### 线程池常用的阻塞队列包括

1\. ArrayBlockingQueue（基于数组的有界队列）； 2\. LinkedBlockingQueue（基于链表的可选有界/无界队列）； 3\. SynchronousQueue（不存储元素，直接传递任务）； 4\. PriorityBlockingQueue（支持优先级排序的无界队列）。 此外，ScheduledThreadPoolExecutor使用延迟队列DelayedWorkQueue处理定时任务。  
●无界队列（如 LinkedBlockingQueue）：可以无限堆任务，但容易导致内存膨胀；线程数不会超过核心线程数。  
●有界队列（如 ArrayBlockingQueue）：有容量限制，任务过多时会触发新线程的创建，直到最大线程数。  
●同步队列（SynchronousQueue）：不存任务，必须立即交给线程执行，否则创建新线程。这通常用于“直接移交”策略，像 Java 的 CachedThreadPool。
### 线程同步方式

#### 线程同步是多线程编程中保证数据一致性和操作原子性的关键机制。当多个线程并发访问共享资源（如变量、对象、文件等）时，若不加控制，会导致竞态条件（Race Condition）、数据错乱、状态不一致等问题。

背）  
●synchronized：关键字。保证原子性和可见性，进入同步块会阻塞其他线程，退出时自动释放锁。简单易用但开销相对大。  
●Lock（ReentrantLock 等）：显式锁，功能比 synchronized 强大。支持可重入、可中断、公平锁、tryLock 超时等特性。需要手动 lock() 和 unlock()，灵活但容易用错。  
●volatile：轻量级修饰符。只保证可见性和禁止指令重排，不保证原子性。常用在状态标志、配置刷新、双重检查单例。性能比锁好，但不能用于复合操作。  
synchronized vs lock  
1机制：synchronized是Java关键字，基于JVM实现自动锁管理；Lock是接口，需手动加锁解锁。  
2灵活性：Lock支持非阻塞尝试锁（tryLock）、可中断锁、超时锁，synchronized无法实现。  
3公平性：Lock可设置公平/非公平策略，synchronized仅支持非公平锁。  
4条件变量：Lock可通过Condition绑定多个条件，synchronized仅一个等待队列。  
5性能：高并发时Lock更高效，synchronized优化后差距缩小，但Lock需显式释放避免死锁。  
可重入性：使用计数器和持有线程记录 实现  
synchronization vs volatile：  
1.synchronization是同步锁，可以保证数据可见性和原子性；volatile不是锁，只能保证数据可见性，不能保证原子性  
2.synchronization可以修饰方法、代码块，volatile只能修饰变量  
3.volatile可以禁止指令重排，synchronization不能禁止指令重排
#### 1️⃣synchronized 关键字（最常用）

作用：  
●保证同一时刻只有一个线程可以执行某个代码块或方法。  
●自动加锁、释放锁（异常时也会释放）。  
●可用于方法或代码块。  
●悲观锁：默认认为会有冲突，直接加锁。  
示例：

\[codeblock卡片内容\]

#### 2️⃣ ReentrantLock（显式锁，java.util.concurrent.locks）

作用：  
●比 synchronized 更灵活，支持：  
○尝试获取锁（tryLock()）  
○可中断获取锁（lockInterruptibly()）  
○超时获取锁  
○公平锁/非公平锁  
○多个条件变量（Condition）  
示例：

\[codeblock卡片内容\]

（补充)  
ReentrantReadWriteLock（可重入读写锁）是 Java 并发包中用于解决“读多写少”场景下并发问题的工具，其核心设计是分离读锁和写锁：读锁（ReadLock）支持多线程共享，写锁（WriteLock）独占。
#### 3️⃣ volatile 关键字（轻量级同步）

volatile 是 Java 中的一个轻量级同步机制，保证变量的可见性和禁止指令重排序，但不保证原子性。  
作用：  
●保证变量的可见性（一个线程修改，其他线程立即看到）  
●禁止指令重排序（保证有序性）  
●❗ 不保证原子性  
示例：

\[codeblock卡片内容\]

#### 4️⃣ 原子类（AtomicXXX，基于 CAS）

作用：  
●利用 CPU 的 CAS（Compare-And-Swap） 指令实现无锁线程安全操作。  
●高性能，适用于高并发计数、状态更新等场景。  
示例：

\[codeblock卡片内容\]

#### 5️⃣ ThreadLocal（线程本地存储）

作用：  
●为每个线程提供变量的独立副本，避免共享，自然线程安全  
●不是“同步”，而是“隔离”  
示例：

\[codeblock卡片内容\]

适用场景：  
●数据库连接、Session 管理（如 Spring 事务）  
●用户上下文、请求 ID 透传  
●SimpleDateFormat 等非线程安全对象的线程隔离
### 说一下ThreadLocal

ThreadLocal可以理解为线程本地变量，他会在每个线程都创建一个副本，那么在线程之间访问内部副本变量就行了，做到了线程之间互相隔离，相比于synchronized的做法是用空间来换时间。  
ThreadLocal有一个静态内部类ThreadLocalMap，ThreadLocalMap又包含了一个Entry数组，Entry本身是一个弱引用，他的key是指向ThreadLocal的弱引用，Entry具备了保存key value键值对的能力。  
弱引用的目的是为了防止内存泄露，如果是强引用那么ThreadLocal对象除非线程结束否则始终无法被回收，弱引用则会在下一次GC的时候被回收。  
但是这样还是会存在内存泄露的问题，假如key和ThreadLocal对象被回收之后，entry中就存在key为null，但是value有值的entry对象，但是永远没办法被访问到，同样除非线程结束运行。  
但是只要ThreadLocal使用恰当，在使用完之后调用remove方法删除Entry对象，实际上是不会出现这个问题的。
#### 注意事项（坑点 ⚠️）

●内存泄漏问题：  
○ThreadLocalMap 的 key 是弱引用，但 value 是强引用。  
○如果线程池中线程长期存在，ThreadLocal 没有 remove()，可能导致 value 无法释放。  
●最佳实践：  
○用完记得 threadLocal.remove()。  
○避免在线程池长生命周期线程中无限积累数据。
### synchronized和reentrantlock区别？

synchronized 和 ReentrantLock 都是 Java 中提供的可重入锁：  
●用法不同：synchronized 可用来修饰普通方法、静态方法和代码块，而 ReentrantLock 只能用在代码块上。  
●获取锁和释放锁方式不同：synchronized 会自动加锁和释放锁，当进入 synchronized 修饰的代码块之后会自动加锁，当离开 synchronized 的代码段之后会自动释放锁。而 ReentrantLock 需要手动加锁和释放锁  
●锁类型不同：synchronized 属于非公平锁，而 ReentrantLock 既可以是公平锁也可以是非公平锁。  
●响应中断不同：ReentrantLock 可以响应中断，解决死锁的问题，而 synchronized 不能响应中断。  
●底层实现不同：synchronized 是 JVM 层面通过监视器实现的，而 ReentrantLock 是基于 AQS 实现的。
### Java 程序在运行时出现 CPU 占用率过高

使用 top 命令查看进程  
使用 jstack 导出线程堆栈  
jstat：查看 GC 情况，是否频繁 Full GC 导致 CPU 飙高。  
jmap + MAT：导出堆快照，分析内存泄漏或对象膨胀。  
先找线程 → 再看堆栈 → 最后分析代码或资源瓶颈。

### 保证数据的一致性有哪些方案呢？

●事务管理：ACID  
●锁机制：synchronized  
●版本控制：乐观锁 CAS
### 死锁

形成死锁需要同时满足4个条件：  
1.互斥：任意时刻只能由一个线程持有  
2.请求与保持：线程获取资源阻塞时不释放已经获取到的资源  
3.循环等待：多个线程之间形成一个循环等待资源的关系  
4.不可剥夺：已经获取到资源的线程其它线程无法剥夺，只能等待线程主动释放资源  
预防死锁就是破坏死锁形成的条件之一即可  
1.互斥：无法破坏，因为锁互斥是线程安全的基础条件  
2.请求保持：可以破坏，一次性申请所有资源，申请不到资源的时候就释放已占有的资源，比如两个ReentrantLock锁，线程都使用tryLock获取锁，然后在finaly中对两个锁进行unlock，这样即使先申请lock1成功，lock2申请失败也会将lock1释放  
3.循环等待：可以破坏，线程按照一定顺序申请锁即可，从而不会出现线程之间互相等待的情况  
4.不可剥夺：可以破坏，lock允许中断线程  
如何检测死锁？  
1.可以用JDK提供的jstak命令转成栈块照进行分析，如果存在死锁一般会有相关提示  
2.使用JDK提供的图形化界面jconsole的检测死锁功能  
3.其它第三方提供的检测死锁工具

### 乐观锁和悲观锁

1悲观锁的实现  
数据库层面：  
通过SELECT ... FOR UPDATE对查询结果加排他锁，其他事务需等待锁释放才能修改数据  
BEGIN;  
SELECT \* FROM orders WHERE id = 1 FOR UPDATE; -- 加锁  
UPDATE orders SET status = 'paid' WHERE id = 1;  
COMMIT; -- 释放锁  
java层面：  
使用synchronized关键字或ReentrantLock实现线程级互斥。  
2乐观锁的实现  
• 版本号机制：  
数据库表中增加version字段，更新时校验版本一致性。

• CAS（Compare and Swap）：  
通过原子操作比较预期值与实际值，若一致则更新（AtomicInteger.incrementAndGet()）。

## JVM

### JVM 内存结构分为哪几个区域？

（堆、方法区、虚拟机栈、本地方法栈、程序计数器）

### JVM内存模型里的堆和栈有什么区别？

用途：  
●栈主要用于存储局部变量、方法调用的参数、方法返回地址以及一些临时数据。  
●堆用于存储对象的实例（包括类的实例和数组）。当你使用new关键字创建一个对象时，对象的实例就会在堆上分配空间。  
生命周期：  
●栈中的数据具有确定的生命周期，当一个方法调用结束时，其对应的栈帧就会被销毁，栈中存储的局部变量也会随之消失。  
●堆中的对象生命周期不确定，对象会在垃圾回收机制（Garbage Collection, GC）检测到对象不再被引用时才被回收。  
存取速度：  
●栈的存取速度通常比堆快，因为栈遵循先进后出（LIFO, Last In First Out）的原则，操作简单快速。  
●堆的存取速度相对较慢，因为对象在堆上的分配和回收需要更多的时间，而且垃圾回收机制的运行也会影响性能。  
可见性：  
●栈中的数据对线程是私有的，每个线程有自己的栈空间  
●堆中的数据对线程是共享的，所有线程都可以访问堆上的对象。
### 内存泄漏和内存溢出的理解？

内存泄露：内存泄漏是指程序在运行过程中不再使用的对象仍然被引用，而无法被垃圾收集器回收，从而导致可用内存逐渐减少。  
内存泄露常见原因：  
●静态集合：使用静态数据结构（如HashMap或ArrayList）存储对象，且未清理。  
●事件监听：未取消对事件源的监听，导致对象持续被引用。  
●线程：未停止的线程可能持有对象引用，无法被回收。

内存溢出：内存溢出是指Java虚拟机（JVM）在申请内存时，无法找到足够的内存，最终引发OutOfMemoryError。这通常发生在堆内存不足以存放新创建的对象时。  
内存溢出常见原因：  
●大量对象创建：程序中不断创建大量对象，超出JVM堆的限制。  
●持久引用：大型数据结构（如缓存、集合等）长时间持有对象引用，导致内存累积。  
●递归调用：深度递归导致栈溢出。
### 类的加载

我们把 Java 的类加载过程分为三个主要步骤：加载、链接、初始化。  
首先是加载阶段（Loading），它是 Java 将字节码数据从不同的数据源读取到 JVM 中，并映射为 JVM 认可的数据结构（Class 对象），这里的数据源可能是各种各样的形态，如 jar 文件、class 文件，甚至是网络数据源等；如果输入数据不是 ClassFile 的结构，则会抛出 ClassFormatError。  
加载阶段是用户参与的阶段，我们可以自定义类加载器，去实现自己的类加载过程。  
第二阶段是链接（Linking），这是核心的步骤，简单说是把原始的类定义信息平滑地转化入 JVM 运行的过程中。这里可进一步细分为三个步骤：  
●验证（Verification），这是虚拟机安全的重要保障，JVM 需要核验字节信息是符合 Java 虚拟机规范的，否则就被认为是 VerifyError，这样就防止了恶意信息或者不合规的信息危害 JVM 的运行，验证阶段有可能触发更多 class 的加载。  
●准备（Preparation），创建类或接口中的静态变量，并初始化静态变量的初始值。但这里的“初始化”和下面的显式初始化阶段是有区别的，侧重点在于分配所需要的内存空间，不会去执行更进一步的 JVM 指令。  
●解析（Resolution），在这一步会将常量池中的符号引用（symbolic reference）替换为直接引用。  
最后是初始化阶段（initialization），这一步真正去执行类初始化的代码逻辑，包括静态字段赋值的动作，以及执行类定义中的静态初始化块内的逻辑，编译器在编译阶段就会把这部分逻辑整理好，父类型的初始化逻辑优先于当前类型的逻辑。
### 双亲委派原则

当类加载器（Class-Loader）试图加载某个类型的时候，只有当父类加载器无法完成加载请求时，子类加载器才会尝试自己去加载。  
使用委派模型的目的是避免重复加载 Java 类型。
### 垃圾回收的判定算法

引用计数法和可达性分析算法。
### 垃圾回收算法有哪些？

●标记-清除算法：标记-清除算法分为“标记”和“清除”两个阶段，首先通过可达性分析，标记出所有需要回收的对象，然后统一回收所有被标记的对象。标记-清除算法有两个缺陷，一个是效率问题，标记和清除的过程效率都不高，另外一个就是，清除结束后会造成大量的碎片空间。有可能会造成在申请大块内存的时候因为没有足够的连续空间导致再次 GC。  
●复制算法：为了解决碎片空间的问题，出现了“复制算法”。复制算法的原理是，将内存分成两块，每次申请内存时都使用其中的一块，当内存不够时，将这一块内存中所有存活的复制到另一块上。然后将然后再把已使用的内存整个清理掉。复制算法解决了空间碎片的问题。但是也带来了新的问题。因为每次在申请内存时，都只能使用一半的内存空间。内存利用率严重不足。  
●标记-整理算法：复制算法在 GC 之后存活对象较少的情况下效率比较高，但如果存活对象比较多时，会执行较多的复制操作，效率就会下降。而老年代的对象在 GC 之后的存活率就比较高，所以就有人提出了“标记-整理算法”。标记-整理算法的“标记”过程与“标记-清除算法”的标记过程一致，但标记之后不会直接清理。而是将所有存活对象都移动到内存的一端。移动结束后直接清理掉剩余部分。  
●分代回收算法：分代收集是将内存划分成了新生代和老年代。分配的依据是对象的生存周期，或者说经历过的 GC 次数。对象创建时，一般在新生代申请内存，当经历一次 GC 之后如果对还存活，那么对象的年龄 +1。当年龄超过一定值(默认是 15，可以通过参数 -XX:MaxTenuringThreshold 来设定)后，如果对象还存活，那么该对象会进入老年代。
### G1 回收器

G1(Garbage First)收集器 (标记-整理算法)：  
Java堆并行收集器  
G1收集器基于“标记-整理”算法实现，也就是说不会产生内存碎片。  
G1回收的范围是整个Java堆(包括新生代，老年代)，而前六种收集器回收的范围仅限于新生代或老年代

### 出现full gc的情况都有哪些？

full gc是全局垃圾回收，同时对新生代、老年代、元空间进行垃圾回收，出现full gc的场景：  
1.老年代内存空间不够，比如大对象无法在老年代分配足够空间、新生代的对象存活时间达到一定年龄进入老年代时空间不够  
2.显示调用System.gc()  
3.元空间内存不够

### 常见的jvm参数都有哪些？

\[codeblock卡片内容\]

解释：  
●\-Xms512m ：堆初始大小 512MB  
●\-Xmx2g ：堆最大大小 2GB  
●\-Xmn256m ：年轻代大小 256MB  
●\-XX:+UseG1GC ：使用 G1 垃圾回收器  
●\-XX:+PrintGCDetails ：打印 GC 详细信息  
●\-XX:+HeapDumpOnOutOfMemoryError ：OOM 时生成堆转储文件  
●\-XX:HeapDumpPath=/tmp/heapdump.hprof ：堆转储保存路径  
常见JVM参数包括： 内存设置：-Xms（初始堆）、-Xmx（最大堆）、-Xss（线程栈） 垃圾回收器：-XX:+UseG1GC（G1回收器）、-XX:+UseParallelGC（并行回收） 监控调试：-XX:+HeapDumpOnOutOfMemoryError（OOM生成堆转储） 性能优化：-XX:MaxMetaspaceSize（元空间上限） 日志参数：-Xloggc（GC日志路径）

# Spring

### AOP

AOP（面向切面编程），把横切关注点（日志、事务、权限、缓存等）从业务逻辑中抽离出来，集中管理。
### IOC

●IoC（Inversion of Control，控制反转）：将对象的创建、依赖管理交给容器，而不是在类内部自己 new 对象。

依赖注入  
（DI，Dependency Injection）：IoC 的实现方式，通过构造器、Setter 或注解 （@Autowired / @Resource ） 注入依赖对象。
### IoC 和 DI 的区别？

答：  
●IoC 是思想，控制反转，把对象的控制权交给容器。  
●DI 是 IoC 的实现方式，容器通过注入依赖实现对象解耦。
### Spring Bean 生命周期步骤

1实例化（Instantiation）  
○Spring 通过反射创建 Bean 对象（相当于 new）。  
2属性赋值（Populate Properties / Dependency Injection）  
○Spring 进行依赖注入，把其他 Bean 注入进来（通过构造方法 / setter）。  
3BeanNameAware / BeanFactoryAware / ApplicationContextAware 回调  
○如果实现了这些接口，Spring 会把容器信息注入进来。  
4BeanPostProcessor 前置处理