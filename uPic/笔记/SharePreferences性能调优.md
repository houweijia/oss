#####  SharePreferences是Android上一种非常易用的轻量级存储方式，由于其API及其友好，得到了很多很多开发者的青睐。但是，SharedPreference并不是万能的，如果把它用在不合适的使用场景，那么将会带来灾难性的后果



#### 1.存储超大的value

之所以说SharePreferences是一种轻量级的存储方式，是它的设计所决定的：sp在创建的时候会把整个文件加载进内存,如果你的sp文件比较大，那么会带来几个严重问题：

- 第一次从sp中获取值的时候，有可能阻塞主线程，使界面卡顿、掉帧
- 解析sp的时候会产生大量的临时对象，导致频繁GC，引起界面卡顿
- 这些key和value会永远存在于内存之中，占用大量内存



也许有童鞋会说，sp的加载不是在子线程么，怎么会卡住主线程？子线程IO就一定不会阻塞主线程吗？

下面是默认的sp实现SharedPreferenceImpl这个类的getString函数：

```java
public String getString(String key, @Nullable String defValue) {
    synchronized (this) {
        awaitLoadedLocked();
        String v = (String)mMap.get(key);
        return v != null ? v : defValue;
    }
}
```

继续看看这个awaitLoadedLocked：

```java
private void awaitLoadedLocked() {
    while (!mLoaded) {
        try {
            wait();
        } catch (InterruptedException unused) {
        }
    }
}
```

一把锁就是挂在那里！！这意味着，如果你直接调用getString()，主线程会等待加载sp的那么线程加载完毕！这不就把主线程卡住了么？



更为严重的是，被加载进来的这些大小对象，会永远存在于内存中，不会被释放，这是在ContextImpl这个类，在getSharedPreference的时候会把所有的sp放到一个静态变量中缓存起来：

```java
private ArrayMap<File, SharedPreferencesImpl> getSharedPreferencesCacheLocked() {
  //sSharedPrefsCache 静态变量
    if (sSharedPrefsCache == null) {
        sSharedPrefsCache = new ArrayMap<>();
    }

    final String packageName = getPackageName();
    ArrayMap<File, SharedPreferencesImpl> packagePrefs = sSharedPrefsCache.get(packageName);
    if (packagePrefs == null) {
        packagePrefs = new ArrayMap<>();
        sSharedPrefsCache.put(packageName, packagePrefs);
    }

    return packagePrefs;
}
```

注意这个static的sSharedPrefsCache，它保存了你所有使用的sp，然后sp里面有一个成员mMap保存了所有的键值对，这样你程序中使用到的那些sp永远就呆在内存中了。



#### 2.多次edit多次apply

```java
SharedPreferences sp = getSharedPreferences("test", MODE_PRIVATE);
sp.edit().putString("test1", "sss").apply();
sp.edit().putString("test2", "sss").apply();
sp.edit().putString("test3", "sss").apply();
sp.edit().putString("test4", "sss").apply();
```

每次edit都会创建一个Editor对象，额外占用内存