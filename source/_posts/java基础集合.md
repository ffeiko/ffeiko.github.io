---
title: java基础集合
date: 2017-06-08 22:22:59
categories: "java" #文章分類目錄 可以省略
tags: [java基础]

---
## 基本概念 ##
java容器类类库的用途是"保存对象",并将其划分为两个不同的概念
### 集合结构图 ###
![](http://orbsa5bc9.bkt.clouddn.com/java%E5%9F%BA%E7%A1%80%E9%9B%86%E5%90%88.png)
### Collection ###
一个独立元素的序列,这些元素多服从一条或多条规则,Set不能有重复元素,Queue按照排队规则来确定对象产生的顺序(通常与它们被插入的顺序相同)

基本操作包括：:
- 
- add(Object o)：增加元素
- addAll(Collection c)：...
- clear()：...
- contains(Object o)：是否包含指定元素
- containsAll(Collection c)：是否包含集合c中的所有元素
- iterator()：返回Iterator对象，用于遍历集合中的元素
- remove(Object o)：移除元素
- removeAll(Collection c)：相当于减集合c
- retainAll(Collection c)：相当于求与c的交集
- size()：返回元素个数
- toArray()：把集合转换为一个数组 




#### 1.List ####
- ArrayList:最有用的List集合实现,由一个整形数字或数组
存储了集合的大小()
- LinkedList:Deque实现:每一个节点都保存着上一个节点和下一个节点的指针.这就意味着数据的存取和更新具有线性复杂度
- vector:一个带有线程同步方法的ArrayList版本.


#### 2.Set ####
- HashSet:一个基于HashMap的Set实现,HashSet不是同步的,如果多个线程同时访问一个hashSet,假设有两个或者两个以上的线程同时修改了HashSet集合时,则必须通过代码来保证其同步:集合元素可以是null.
- TreeSet:TreeSet是SortedSet接口的实现类,正如SortedSet名字所暗示的.TreeSet可以确保集合处于排序状态
- enumSet是专为枚举类设计的集合类EnumSet中的所有元素都必须是指定的枚举类型的枚举值。EnumSet的集合元素也是有序的，EnumSet以枚举值在Enum类内的定义顺序来决定集合元素的顺序。


#### 3.Queue ####
Queue用于模拟队列这种数据结构，实现“FIFO”等数据结构。通常，队列不允许随机访问队列中的元素。
Queue 接口并未定义阻塞队列的方法，而这在并发编程中是很常见的。BlockingQueue 接口定义了那些等待元素出现或等待队列中有可用空间的方法，这些方法扩展了此接口。
Queue 实现通常不允许插入 null 元素，尽管某些实现（如 LinkedList）并不禁止插入 null。即使在允许 null 的实现中，也不应该将 null 插入到 Queue 中，因为 null 也用作 poll 方法的一个特殊返回值，表明队列不包含元素。

### iterator接口 ###
iterator接口,用于循环访问集合中的对象,所有实现了Collection接口的容器类都有iterator方法,用于返回一个实现了iterator接口的对象,iterator对象称做迭代器,iterator接口方法都以迭代方逐个访问集合中各个元素,并可以从Collection中除去适当的元素


### Collections ###
此类完全由在 collection 上进行操作或返回 collection 的静态方法组成。它包含在 collection 上操作的多态算法，即“包装器”，包装器返回由指定 collection 支持的新 collection，以及少数其他内容。如果为此类的方法所提供的 collection 或类对象为 null，则这些方法都将抛出 NullPointerException。


常用方法总结:


- （1）sort()排序方法
函数定义：public static <T extends Comparable<? super T>> void sort(List<T> list) 根据元素的
自然顺序对指定列表按升序进行排序。
参数：要排序的列表。
函数定义： public static <T> void sort(List<T> list,Comparator<? super T> c)，根据指定比较器产生的顺序对指定列表进行排序。此列表内的所有元素都必须可使用指定比较器相互比较。
参数：list-要排序的列表；c-确定列表顺序的比较器。


- （2）binarySearch()二分查找方法
函数定义：public static <T> int binarySearch(List<? extends Comparable<? super T>> list,T key)
使用二分搜索法搜索指定列表，以获得指定对象，在进行此方法调用前比较要将列表元素按照升序排序，否则结果不确定，此方法会执行O(n)次链接遍历和O(log n)次元素比较。
参数: list-要搜索的链表，key-要搜索的键。
函数定义： public static <T> int binarySearch(List<? extends T> list, T key, Comparator<? super T> c) 根据指定的比较器对列表进行升序排序。
参数：list-要搜索的列表，key-要搜索的键，c-排序列表的比较器。


- （3）reverse()反转方法
 函数定义：public static void reverse(List<?> list)，反转指定列表中元素的顺序，此方法以线性时间运行。
参数：list-元素要被反转的列表


- （4）shuffle()改组方法
函数定义：public static void shuffle(List<?> list)，使用默认随机源对指定列表进行置换，所有置换发生的可能性都是大致相等的。
参数：list-要改组的列表
函数定义：public static void shuffle(List<?> list,Random rnd),使用指定的随机源对指定列表进行置换。
参数：list-要改组的列表，rnd-用来改组列表的随机源。


- （5）swap()交换方法
函数定义：public static void swap(List<?> list,int i，int j)，在指定列表的指定位置处交换元素。
参数：list-进行元素交换的列表，i-要交换的一个元素的索引，j-要交换的另一个元素的索引。


- （6）fill()替换方法
函数定义：public static <T> void fill(List<? super T> list,T obj)，使用指定元素替换指定列表中的所有元素，线性时间运行。
参数:list-使用指定元素填充的列表，obj-用来填充指定列表的元素。


- （7）copy()复制方法
函数定义：public static <T> void copy(List<? super T> dest,List<? extends T> src)，将所有元素从一个列表复制到另一个列表。执行此操作后，目标列表中每个已复制元素的索引将等同于源列表中该元素的索引，目标列表的长度至少必须等于源列表。
参数：dest-目标列表，src-源列表。


- （8）min()最小值法
函数定义：public static <T extends Object & Comparable<? super T>> T min(Collection<? extends T> coll)，根据元素的自然顺序返回给定Collection的最小元素，Collection中的所有元素必须实现Comparable接口，此外，collection中的所有元素都必须是可相互比较的。
参数：coll-将确定其最小元素的collection。
函数定义：public static <T> T min(Collection<? extends T> coll,Comparator<? super T> comp),根据指定比较器产生的顺序，返回给定collection的最小元素。
参数：coll-将确定其最小元素的collection，comp-用来确定最小元素的比较器。


- （9）max()最大值方法
函数定义：public static <T extends Object & Comparable<? super T>> T max(Collection<? extends T> coll)，根据元素的自然顺序，返回给定collection的最大元素。
参数：coll-将确定其最大元素的collection。
函数定义：public static <T> T max(Collection<?extends T> coll,Comparator<? super T> comp)，根据指定比较器产生的顺序，返回给定collection的最大元素。
参数：coll-将确定其最大元素的collection，comp-用来确定最大元素的比较器


- （10）rotate()轮换方法
函数定义：public static void rotate(List<?> list，int distance)，根据指定的距离轮转指定列表中的元素。
参数：list-要轮换的列表，distance-列表轮换的距离，可以使0、负数或者大于list.size()的数。


- （11）replaceAll()替换所有函数
函数定义：public static <T> boolean replaceAll(List<T> list,T oldVal,T newVal)，使用另一个值替换列表总出现的所有的某一指定值。
参数：list-在其中进行替换的列表；oldVal-将被替换的原值；newVal-替换oldVald的新值。



### Map ###
一组成对的"键值对"对象,允许你使用键来查找值,ArrayList允许你使用数字来查找值,因此在某种意义上讲,它将数字与对象关联在了一起,映射表允许我们使用另一个对象来查找某个对象,他也被称为"关联数组",因为它将某些对象与另外一些对象关联在了一起:或者被称为"字典".Map用于保存具有映射关系的数据，因此Map集合里保存着两组值，一组值用于保存Map里的key，另外一组值用于保存Map里的value,key和value都是任何引用类型的数据。Map的key不允许重复，即同一个Map对象的任何两个key通过equals方法比较总是返回false。
 


- 1.HashMap类和Hashtable类
HashMap和Hashtable都是Map接口的典型实现类，它们之间的关系完全类似于ArrayList和Vector的关系，两者的区别如下：


----------

Hashtable是一个线程安全的Map实现，但HashMap是线程不安全的实现，所以HashMap比Hashtable的性能高一点；但如果多个线程访问同一个Map对象时，使用Hashtable实现类会更好。
Hashtable不允许使用null作为key和value，如果试图把null值放进Hashtable中，将会引发NullPointerException异常；但HashMap可以使用null作为key和value。由于HashMap里的key不能重复，所以HashMap里最多最多只有一个key-value对的key为null，但可以有无数个key-value对的value为null。


----------


- 2.TreeMap类
使用TreeMap有一个好处：TreeMap中的key-value对总是处于有序状态，无须专门进行排序操作。当TreeMap被填充之后，就可以调用keySet()，取得由key组成的Set，然后使用toArray方法生成key的数组，接下来使用Arrays的binarySearch()方法在已排序的数组中快速地寻找对象。
TreeMap通常比HashMap、HashTable要慢，尤其在插入、删除key-value对时更慢。


- 3.EnumMap类
EnumMap是一个与枚举类一起使用的Map实现，EnumMap中所有的key都必须是单个枚举类的枚举值。它具有如下特征：
EnumMap在内部以数组形式保存，所以这种实现形式非常紧凑、高效。
EnumMap根据key的自然顺序（即枚举值在枚举类中的定义顺序）来维护key-value对的顺序。当程序通过keySet()、entrySet()、values()等方法遍历EnumMap时可以看到这种顺序。
EnumMap不允许使用null作为key，但允许使用null作为value。














