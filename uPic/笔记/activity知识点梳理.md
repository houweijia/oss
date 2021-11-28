### 1.生命周期

#### 1.1横竖屏切换

- 不设置Activity的android:configChanges时，切屏会重新调用各个生命周期，切横屏时会执行一次，切竖屏时会执行两次。
- 设置Activity的android:configChanges="orientation"时，切屏还是会重新调用各个生命周期，切横、竖屏时只会执行一次
- 设置Activity的android:configChanges="orientation|keyboardHidden"时，切屏不会重新调用各个生命周期，只会执行onConfigurationChanged方法
- 注意：还有一点非常重要，一个Android的变更细节！当API>12时，需要加入screenSizes属性，否则屏幕切换时即时你设置了orientation系统也会重建Activity



#### 1.2将一个Activity设置成窗口的样式

只需要给我们的Activity配置如下属性即可

```xml
android:theme="@android:style/Theme.Dialog"
```

### 1.3退出已调用多个Activity的Application
通常情况下用户退出一个Activity只需按返回键，我们写代码想退出activity直接调用finish()方法就行。
1.发送特定广播：
	1在需要结束应用时，发送一个特定的广播，每个Activity收到广播后，关闭即可。
	2 给某个activity注册接受广播的意图registerReceiver(receiver,filter)
	3如果接收到的是关闭activity的广播，activity.finish()掉

2.递归退出
	1就调用finish()方法把当前的Activity退出
	2 在打开新的Activity时 使用startActivityForResult，然后自己加标志，在	onActivityResult中处理，递归关闭。

3.利用flag
	1 通过intent的flag来实现intent.setFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP)激活一个新的activity
	2 此时如果该任务栈中已经有该Activity,那么系统会把这个Activity上面的所有Activity干掉。

​	3其实相当于给Activity配置的启动模式为singleTask

4.记录打开的Activity

​	1.每打开一个Activity，就记录下来

​	2.在需要退出时，关闭每个Activity



### 1.4 锁定屏幕和解锁屏幕

- 锁屏时：会执行onPause()  onStop()
- 开屏时：会执行onStart()  onResume()

### 1.5如何处理异常退出
- Activity异常退出的时候 -->onPause() -->onSaveInstanceState() --> onStop 

- -->onDestory()，需要注意的是，onSaveInstanceState()方法与onPause并没有严格的先后关系，有可能在onPause之前，也有可能在其后面调用，但会在onStop()方法之前调用

- 异常退出后又重新启动该Activity --> onCreate() --> onStart() 

  -->onRestoreInstanceState() --> onResume()

- 搞懂这个生命周期的执行后 就可以回答了，首先要知道面试官的意思，是要重新启动并恢复这个Activity还是说直接退出整个app。如果要回复则要在onSaveInstanceState()中进行保存数据并在onRestoreInstanceState()中进行恢复；如果要退出app的话 就要捕获全局的异常信息，并退出app。

- 最好是使用UncaughtExceptionHandler来捕获全局异常进行退出app的操作，这样会减少之前崩溃所造成的后遗症。



