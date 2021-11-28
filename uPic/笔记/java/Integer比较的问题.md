##### 现象

```java
Integer i = new Integer(100); 
Integer j = new Integer(100); 
System.out.println(i==j); 
打印结果是：false
```

创建了两个Integer型的对象，对象之间的“==”符是用来比较是否是一个对象的两个引用（即比较地址是否相同）

基本类型和包装类之间可以自由转换，但不能简单的用包装类型代替基本类型比较大小

```
Integer i = Integer.valueOf(100); 
Integer j = Integer.valueOf(100); 
System.out.println(i==j); 
 
打印结果是：true

Integer i = Integer.valueOf(400); 
Integer j = Integer.valueOf(400); 
System.out.println(i==j); 
 
打印结果是：false

查看Integer.valueOf方法的源码，如下：
public static Integer valueOf(int i) {   
    if(i >= -128 && i <= IntegerCache.high)   
        return IntegerCache.cache[i + 128];   
    else   
        return new Integer(i);   
}
Integer在比较value大小时，Integer对象有个缓存，如果value的值在-128到127之间时，直接返回固定对象的引用，是同一个，所以是true。但是超过这个范围，就是两个对象了，自然是false。
```

#### 解决方案

即便两个Integer.valueOf(100)比较得到的结果是true，也是因为两个本身就是同一个对象（地址相同），而不能简单的理解为是两个Integer的value相同

##### 方案一

- 一个Integer一个int可以直接比较大小
- 两个Integer需要用Integer.intValue()方法是否相等

```java
例如：i.intValue()==j.intValue()

private final int value;
 
public Integer(int value) {
    this.value = value;
}
 
// Integer.intValue():
public int intValue() {
    return value;
}
```

1.intValue()是java.lang.Number类的方法，Number是一个抽象类。Java中所有的数值类都继承它。也就是说，不单是Integer有intValue方法，Double，Long等都有此方法。 
2.此方法的意思是：输出int数据。每个数值类中具体的实现是不同的。例如： 
Float类和Double类的intValue方法，就是丢掉了小数位

##### 方案二

包装类对象不可使用"=="符号做比较运算，如果要进行比较运算时，最好使用java类库中的compareTo方法

```java
// Integer.compareTo()
public int compareTo(Integer anotherInteger) {
    return compare(this.value, anotherInteger.value);
}

public static int compare(int x, int y) {
    return (x < y) ? -1 : ((x == y) ? 0 : 1);
}
```



##### 方案三

Integer.equals(Integer i)

其实 实现也是用的inValue比较

```java
public boolean equals(Object obj) {
    if (obj instanceof Integer) {
        return value == ((Integer)obj).intValue();
    }
    return false;
}
```

### 注意

1.

```java
Map<Character,Integer>.get('c') == Map<Character,Integer>.get('c')
```

这种情况下，可能会毫无察觉地判断两个Integer是否相等

2.把entity字段定义为Integer 也可能 判断Integer是否相等 但自己也没意识到

#### 以上问题只存在于比较Integer是否相等，大于、小于不会出现该问题，因为==比较的是Integer对象的地址，而><比较的是value(会使用inValue自动拆箱进行比较)



#### 常见的比较问题

1.int和int之间，用==比较，肯定为true。基本数据类型没有equals方法

2.int和Integer比较，Integer会自动拆箱，== 和 equals都肯定为true

3.int和new Integer比较，Integer会自动拆箱，调用intValue方法, 所以 == 和 equals都肯定为true

4.Integer和Integer比较的时候，由于直接赋值的话会进行自动的装箱。所以当值在[-128,127]中的时候，由于值缓存在IntegerCache中，那么当赋值在这个区间的时候，不会创建新的Integer对象，而是直接从缓存中获取已经创建好的Integer对象。而当大于这个区间的时候，会直接new Integer。

5.当Integer和Integer进行==比较的时候，在[-128,127]区间的时候，为true。不在这个区间，则为false

6.当Integer和Integer进行equals比较的时候，由于Integer的equals方法进行了重写，比较的是内容，所以为true

7.

- Integer和new Integer ： new Integer会创建对象，存储在堆中。而Integer在[-128,127]中，从缓存中取，否则会new Integer，所以 Integer和new Integer 进行==比较的话，肯定为false ; Integer和new Integer 进行equals比较的话，肯定为true
- new Integer和new Integer进行==比较的时候，肯定为false ; 进行equals比较的时候，肯定为true
  原因是new的时候，会在堆中创建对象，分配的地址不同，==比较的是内存地址，所以肯定不同