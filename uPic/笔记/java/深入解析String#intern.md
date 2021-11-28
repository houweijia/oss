https://tech.meituan.com/2014/03/06/in-depth-understanding-string-intern.html

在Java中有8种基本类型和一种比较特殊的类型String。这些类型为了使他们在运行过程中速度更快，更节省 内存，都提供了中常量池的概念。常量池就类似一个Java系统级别提供的缓存。

8种基本类型的常量池都是系统协调的，String类型的常量池比较特殊，它的主要是用方法有两种：

- 直接使用双引号声明出来的String对象会直接存储在常量池中

```java
String str = "1";
```

- 如果不是双引号声明的String对象，可以使用String提供的intern方法。Intern方法会从字符串常量池中查询当前字符串是否存在，若不存在就会将当前字符串放入常量池中

```java
String str = new String("1");
str.intern();
```



首先深入看一下String的intern()的实现原理

##### 1.java代码

```java
/** 
 * Returns a canonical representation for the string object. 
 * <p> 
 * A pool of strings, initially empty, is maintained privately by the 
 * class <code>String</code>. 
 * <p> 
 * When the intern method is invoked, if the pool already contains a 
 * string equal to this <code>String</code> object as determined by 
 * the {@link #equals(Object)} method, then the string from the pool is 
 * returned. Otherwise, this <code>String</code> object is added to the 
 * pool and a reference to this <code>String</code> object is returned. 
 * <p> 
 * It follows that for any two strings <code>s</code> and <code>t</code>, 
 * <code>s.intern()&nbsp;==&nbsp;t.intern()</code> is <code>true</code> 
 * if and only if <code>s.equals(t)</code> is <code>true</code>. 
 * <p> 
 * All literal strings and string-valued constant expressions are 
 * interned. String literals are defined in section 3.10.5 of the 
 * <cite>The Java&trade; Language Specification</cite>. 
 * 
 * @return  a string that has the same contents as this string, but is 
 *          guaranteed to be from a pool of unique strings. 
 */  
public native String intern(); 
```

String#intern方法中看到，这个方法是一个native的方法，但注释写的非常明了。“r如果常量池中存在当前字符串，就会直接返回当前字符串，如果常量池中没有此字符串，会将此字符串放入常量池中后，再返回”

##### 2.native代码

在jdk7之后，oracle接管了java的源码后就不对外开发了，根据jdk的主要开发人员声明 openJdk7和jdk7使用的是同一份主代码，只是分支代码会有些许的变动，所以可以直接跟踪openJdk7的源码来探究intern的实现。

native实现代码:\openjdk7\jdk\src\share\native\java\lang\String.c

```c++
Java_java_lang_String_intern(JNIEnv *env, jobject this)  
{  
    return JVM_InternString(env, this);  
}  
```

\openjdk7\hotspot\src\share\vm\prims\jvm.h

```c++
/* 
* java.lang.String 
*/  
JNIEXPORT jstring JNICALL  
JVM_InternString(JNIEnv *env, jstring str); 
```

\openjdk7\hotspot\src\share\vm\prims\jvm.cpp

```c++
// String support  
JVM_ENTRY(jstring, JVM_InternString(JNIEnv *env, jstring str))  
  JVMWrapper("JVM_InternString");  
  JvmtiVMObjectAllocEventCollector oam;  
  if (str == NULL) return NULL;  
  oop string = JNIHandles::resolve_non_null(str);  
  oop result = StringTable::intern(string, CHECK_NULL);
  return (jstring) JNIHandles::make_local(env, result);  
JVM_END   
```

\openjdk7\hotspot\src\share\vm\classfile\symbolTable.cpp

```c++
oop StringTable::intern(Handle string_or_null, jchar* name,  
                        int len, TRAPS) {  
  unsigned int hashValue = java_lang_String::hash_string(name, len);  
  int index = the_table()->hash_to_index(hashValue);  
  oop string = the_table()->lookup(index, name, len, hashValue);  
  // Found  
  if (string != NULL) return string;  
  // Otherwise, add to symbol to table  
  return the_table()->basic_add(index, string_or_null, name, len,  
                                hashValue, CHECK_NULL);  
}   
```

\openjdk7\hotspot\src\share\vm\classfile\symbolTable.cpp

```c++
oop StringTable::lookup(int index, jchar* name,  
                        int len, unsigned int hash) {  
  for (HashtableEntry<oop>* l = bucket(index); l != NULL; l = l->next()) {  
    if (l->hash() == hash) {  
      if (java_lang_String::equals(l->literal(), name, len)) {  
        return l->literal();  
      }  
    }  
  }  
  return NULL;  
}  
```

它的答题实现结构就是：Java使用jni调用c++实现的StringTable的intern方法跟Java中的HashMap的实现差不多，只是不能自动扩容，默认大小是1009。

要注意的是，String的String Pool是一个固定大小的HashTable,默认值大小长度是1009，如果放进String Pool的String非常多，救护造成Hash冲突严重，从而导致链表会很长，而链表唱了之后直接会造成的影响就是当调用String.intern()时性能会大幅下降(因为需要一个一个查找)

在Jdk6中StringTable是固定的，也就是1009的长度，所以如果常量池中的字符串过多就会导致效率下降很快，而在jdk7中，StringTable的长度可以通过一个参数指定：

```
-XX:StringTableSize=99991
```



相信很多java程序员都做过类似 String s = new String("abc")这个语句创建了几个对象的题目。这种题目主要是为了考察程序员对字符串对象的常量池掌握与否。上述的语句中是创建了2个对象，第一个对象是"abc"字符串存储在常量池中，第二个对象在Java Heap中的String对象。



##### 来看一段代码

```java
public static void main(String[] args){
		String s = new String("1");
  	String s2 = "1";
  	System.out.println(s == s2);

    String s3 = new String("1") + new String("1");
    s3.intern();
    String s4 = "11";
    System.out.println(s3 == s4);
}
打印结果是

jdk6 下false false
jdk7 下false true
```



```java
public static void main(String[] args) {
    String s = new String("1");
    String s2 = "1";
    s.intern();
    System.out.println(s == s2);

    String s3 = new String("1") + new String("1");
    String s4 = "11";
    s3.intern();
    System.out.println(s3 == s4);
}

打印结果为：

jdk6 下false false
jdk7 下false false
```



- jdk6的解释

![jdk6](https://cdn.jsdelivr.net/gh/houweijia/oss@main/uPic/jdk6.png)

注：图中绿色线条代表string对象的内容指向。黑色线条代表地址指向。

如上图所示，首先说一下jdk6的情况，在jdk6中上述的所有打印都是false，因为jdk6中的常量池是放在Perm区中，Perm区和正常的JAVA Heap区域是完全分开的。上面说过如果是使用引号声明的字符串都是ui直接在字符串常量池中生成，而new出来的String对象是放在JAVA Heap区域，所以拿一个Java Heap区域的对象地址和字符串常量池的对象地址进行比较肯定是不相同的，即使调用了String.intern方法也是没有任何关系的。



- jdk7的解释

这里要明确一点的是，在jdk6以及以前的版本中，字符串的常量池是放在堆的Perm区，Perm区试试一个类静态的区域，主要存储一些加载类的信息、常量池、方法片段等内容，默认大小只有4m，一旦常量池中大量使用intern会直接产生java.lang.OutofMemoryError:PermGen space的错误

![jdk7](https://cdn.jsdelivr.net/gh/houweijia/oss@main/uPic/jdk7.png)