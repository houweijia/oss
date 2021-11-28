# 5年Android开发面试问什么？

yechaoa 鸿洋 *今天*

本文作者



作者：**yechaoa**

链接：

https://blog.csdn.net/yechaoa/article/details/119714009

本文由作者授权发布。





**前言**



前段时间在看机会，本文就是我对求职过程的一个总结。



同时，也作为一个面试官，来说说求职中需要注意的点：



各大厂的面试会考核哪些知识点。



5年开发应该具备哪些技术要点。



当下市场行情如何，真的很卷吗。



写简历需要注意什么。



自我介绍怎么准备。



关于为什么离职。



未来职业规划问题如何避坑。



被问到自闭，如何调整心态。



我个人的学习方法。



其他注意事项。



*1*

面试题



先上主菜：



**一面技术**



**京东**



GC原理，有哪几种GC方式。



HashMap原理。



Hybrid开发流程、机制。



WebView内存泄露。



包体积优化。



自定义View需要注意哪些。



事件分发机制。



ViewModel原理。



屏幕旋转ViewModel怎么做到保存数据的。



LiveData原理。



Flutter线程机制，单线程多线程。



组件化开发。



介绍一个自己的开源项目。



有参与过别人的开源项目吗。



**字节跳动**



浏览器输入一个地址，按下回车，这个过程是什么样的。



简单介绍一下TCP。



简单介绍一下Https。



说说对称加密和非对称加密，说说公钥。



并发操作如何保证线程安全。



锁有哪些。



简单介绍一下HashMap。



Arraylist是线程安全的吗。



知道CAS、原子性吗。



AtomicBoolean和boolean的区别。



用过哪些设计模式。



介绍一下观察者模式。



用过哪些排序算法。



介绍一下贪心算法。



介绍一下快排原理。



算法，给定一个有序不重复数组，使用时间复杂度小于N方的方法，找到所有两两相加等于target值的组合:



```
int[] a={1,2,3,4,5,6,7,8}
int target=7
```



**美团**



Java对象生命周期。



GC机制。



Glide缓存机制。



Glide对Bitmap是怎么优化的。



Okhttp请求流程。



Retrofit中的设计模式。



App启动流程。



Apk打包流程。



重构做了哪些工作。



内存泄露，举例场景。



LeakCanary实现原理。



Handler消息机制。



线程有哪些状态。



Hybrid开发介绍。



Js功底怎么样。



未来职业规划。



**哔哩哔哩**



MVC，MVP，MVVM的区别。



使用MVVM有遇到什么问题吗。



协程原理。



协程并发怎么处理的。



热修复原理。



用热修复的过程中有遇到什么问题吗。



启动优化。



包体积优化。



绘制优化。



全埋点是怎么做的。



Apk更新流程。



多渠道打包。



怎么辨别华为的包更新别的应用市场的包。



算法，插入排序原理。



**声网**



觉得做的最好的项目。



Jetpack用了哪些组件。



ViewModel如何数据共享。



ViewModel在Activity旋转时如何保存数据的。



ViewModel怎么创建的，存在哪。



使用ViewModel过程中有没有遇到什么问题。



LiveData原理，怎么派发数据的。



postValue是怎么执行的。



使用LiveData的过程中有没有遇到什么问题。



自定义View有哪些注意事项。



简单介绍一下协程。



多个协程怎么保证数据安全的。



算法，输入(H₂O) ×2，输出h4o2。



**掌门教育**



笔试逻辑题。



Java有哪些数据结构。



Arraylist是线程安全的吗。



String，StringBuilde，StringBuffer的区别。



Java中的锁介绍一下，同步锁举例。



四大引用区别，场景举例。



Activity生命周期。



Fragment生命周期。



Fragment销毁生命周期执行顺序。



自定义流程，举例。



自定义View刷新方式有哪些，执行流程。



事件分发原理，举例，延伸。



滑动冲突怎么解决。



怎么自己实现一个长按事件。



Service是哪个线程，怎么通信。



Handler消息机制。



Handler发送消息是一定立即执行的吗。



Handler运行在哪个线程。



子线程可以创建Handler吗，写法有哪些区别。



Kotlin定义变量的方式有哪些。



lateinit怎么确保使用时已经初始化。



let,run,apply介绍，区别。



inline原理。



简单介绍下协程。



协程并发怎么处理。



协程底层是怎么实现的。



内存泄露原理，举例场景。



启动优化。



**传音控股**



做的最有成就感的项目是哪个。



印象最深刻的项目是哪个。



LiveData底层实现原理。



启动优化。



包体积优化。



自定义View流程。



View异步加载。



有用过哪些设计模式。



介绍一下单例，饿汉式，懒汉式，双重锁。



代理模式和装饰模式的区别。



策略模式和状态模式的区别。



说说观察者模式。



有看过哪些三方库的源码。



Glide四层缓存机制。



AMS了解多少。



**得物**



简单介绍一下HashMap。



HashMap调用put的执行流程。



Activity启动流程。



Binder机制。



Handler消息机制。



Handler是怎么实现主线程和子线程的通信的。



Looper卡死为什么不会造成主线程的阻塞。



了解过内存泄露吗。



是怎么发现内存泄露的，怎么处理的。



线上的内存泄露是怎么监控的。



LeakCanary实现原理。



软引用和弱引用的区别。



了解过ANR吗。



什么原因会造成ANR。



Activity的响应时间为什么是5s。



事件分发机制。



怎么解决滑动冲突的。



录音功能是怎么做的。



编码解码相关。



包体积优化做了哪些工作。



**哈啰出行**



挑一个项目详细说一下，以及相关技术栈。



介绍一下协程机制。



说一下Dispatchers，withContext，Scope他们的作用。



说一下你理解的MVP，MVVM。



Flutter相关。



性能优化做了哪些工作。



编译速度怎么提升的。



内存泄露。



LeakCanary检测原理。



热修复，Sophix原理，ClassLoader。



Apk打包流程。



多线程并发，如何保证线程安全。



synchronized修饰方法和修饰代码块有什么区别。



**小红书**



技术调研你是怎么做的，会考虑哪些因素。



说一下MVVM。



用过Jetpack中的哪些组件。



LiveData是怎么做数据派发的。



ViewModel屏幕旋转的时候怎么做到不丢失数据的。



使用MVVM的过程中有遇到什么问题吗。



性能优化做了哪些工作。



内存泄露有哪些场景。



LeakCanary检测原理。



如果让你做一个自动化的工具去检测图片过大并自动压缩你会怎么做。



自定义View画板是怎么做的。



怎么检测页面的FPS。



Handler在onCreate中发送大量数据会导致主线程卡顿吗。



LayoutInflater.inflate有几个参数，分别是什么意思。



**其他厂整理补充**



Android中的Context了解多少。



Application里面可以弹窗吗。



Activity、Window、View三者的关系。



OkHttp中有哪些设计模式。



Retrofit中有哪些设计模式。



Retrofit.create做了哪些工作。



自定义一个圆角View。



协程launch有哪些参数。



说说by关键字。



代理和委托的区别。



双亲委托模式。



有几种获取view宽高的方式。



view.post为什么可以获取到。



getWidth和getMesureWidth的区别。



手写遍历二叉树。



手写双重锁单例。



手写插入排序。



手写双数组去重并排序。



如何判断链表有环。



还有一些公司的没有记，比如蔚来、中欧基金、阿里等，如果上面这些你能掌握大部分，自然也不在话下。



**二面、三面技术**



都是偏项目和综合能力，因人而异就直接整理了。



你负责项目中的哪些模块。



介绍一下xx功能的流程。



项目的架构是怎样的。



Kotlin和Java混编有哪些需要注意的。



项目中有遇到哪些难点。



如果让你重构，你会怎么做。



学习的途径有哪些。



你觉得什么样的代码是好代码。



团队是怎么分工的。



怎么做需求管理。



期望什么样的团队。



怎么看待大前端方向。



一个新技术如何在团队里推广。



未来的规划是什么，你打算怎么实现。



认为自己的优点是什么，缺点是什么。



为什么离职。



**HR面**



整理：



为什么离职。



介绍一下过往的工作经历。



在上家公司你有什么收获吗。



目前看机会会考虑哪些因素。



你在之前的团队中是怎样一个角色。



有什么兴趣爱好吗。



最有成就感的一件事。



有没有做过什么不可思议的事。



你认为自己的优点是什么。



最近有在看什么书吗，有什么感想。



你一般遇到问题都是怎么解决的。



未来的职业规划是什么。



你对未来的公司有什么期望吗。



目前薪资。



期望薪资。



还有什么想要问我的吗。



**技术要点**



针对上面的问题，我总结了一下面试前需要掌握的一些知识点：



Java基础、Kotlin基础、Android基础（重要）。



App启动流程。



Handler消息机制。



View绘制流程。



事件分发机制。



Jetpack常用组件原理。



Kotlin协程原理。



性能优化。



多线程、并发。



组件化开发。



热修复原理。



常用三方库原理。



常见的设计模式。



数据结构和算法。



建议面前多练练手写算法，最好是拿笔在纸上写。



关于算法，不过是基于数据结构去操作数据的思想而已。



如果说限制了复杂度而想不出来的话，可以先写再看如何优化。



*2*

市场行情



目前并不是招聘旺季，但机会还是有的。



可能有些同学看了上面的面试题觉得卷，正常的。



现在市场越来越成熟稳定，对面试者的要求也更高，加上技术更新又快，从Java到Kotlin、到Flutter、到Compose等等，确实有很多东西要学，很多同学都表示学不动了，我觉得，盲目跟风不如好好沉淀。



另外，再从面试官的角度聊聊。



虽然说大部分面试确实是各种底层实现、底层原理、手写算法什么的，不过作为面试官来说，其实有些也并不是要你都掌握的，问的深，一方面是校验八股文，另一方面主要是技术摸底，看看你的技术边际在哪，所以说，一场面试下来，能答上大部分即是通过了，当然，越多越加分。



只要技术够硬，都是机会。



*3*

如何写好简历



简历是开启面试的第一步，重要性不言而喻，一方面反应你的实力，另一方面也反应跟目标岗位的匹配度，不过很多JD都是复制粘贴，我个人也没有动态改简历。



如何写好简历，一定要简洁且突出重点。我也面过不少人了，看过7-8页的简历，有些项目经历是没必要全都往上写的，面试官也看不过来，最好是保持在3页左右比较合适，项目经历比较丰富的同学，可以挑重点来写。



我个人简历大概模板：



个人信息



技能清单



工作经历/项目经历



开源项目/博客



教育经历



我是MD排版，PDF格式，参考模板

*https://github.com/geekcompany/ResumeSample/blob/master/android.md*



投简历时有一个建议，不要开放简历，要主动投递。开放简历会有各种邀请面试，也不好拒绝，就可能会因为没准备好而错失一些机会。可以先去其他公司找找感觉，再面心仪的公司。



另外，一定要对自己简历上写的东西做到熟练，没用过的，不会的就别写了，万一问了不会，就是在给自己挖坑。



*4*

自我介绍



自我介绍需要好好准备，因为这可能是你整个面试环节中唯一的主动机会，也是引导面试官的第一步，可以介绍最近的项目经历啥的，以及相关技术栈等等，引导面试官往你擅长的领域提问。



挑重点不要啰嗦，时间控制在两分钟左右。



*5*

离职原因



这个其实大家都心知肚明，但是回答的时候还是委婉些的好，不抱怨原则。



不过HR总是有很多种问法，比如：



你在上家公司才做了一年多，为什么选择离职呢？



你在上家公司已经做了四年多，为什么选择离职呢？



回答建议：



想去更好的平台。



薪资与个人付出不成正比。



公司业务方向与个人职业规划出现偏离。



关于公司倒闭，我个人觉得没问题，但如果是干一家倒一家，那HR可能会否你…



*6*

职业规划



很多都会问这个问题，相似问题，你最近在学什么技术，看什么书。



这块很多同学其实会放松警惕，看似无关紧要，实则暗藏玄机，因为在求职过程中，在学在看的，可能是自己薄弱的地方。



比如你说未来想研究一下主流三方库的源码，学习优秀的设计理念，看似好像很努力很上进，其实面试官听到的是，主流三方库我只会用，不知道原理，我就是个API调用师。（尬不尬？）



所以这块的回答一定要有深度或者广度，要有想象空间，但是不能太离谱，需要好好斟酌。



回答建议：



**技术方向**：要么全要么精，全栈或细分领域专家。



**管理方向**：有较强的沟通能力、协作能力，希望能做团队的领头羊。



*7*

关于心态



准备前，可能有些同学看到面试题已经不自信了，感觉自己一半都答不上来，这是正常的，人的记忆是有限的，慢慢复习就好了，放平心态。



面试中，可能有些同学会被问到自闭，其实大可不必，东边不亮西边亮，总有面试官会挖掘出你的亮点。而且面试中除了技术之外，也有很多客观因素，比如面试官的心情、你的状态等等。



面试后，好与坏都坦然接受，及时做好复盘，查漏补缺，才能在下一次面试中有更好的发挥，这也是一个愈战愈勇的过程。



*8*

学习方法



我个人是梳理知识树，不会的就去补充，制定学习计划。



我个人的学习方式：



看官方文档，比如Kotlin文档，第一遍快读，有个大概印象，第二遍精读，关注一些细节。



看书，还是Kotlin，先快读，再重点精读。我觉得比看视频方便，可以划重点记笔记，随时可以停下来进入思考状态，也很方便反复阅读，主要是没有干扰。



看相关开源项目，学习优秀的设计理念、代码风格，三人行必有我师。



看一些针对性的博客。



实践，这个很重要，纸上得来终觉浅，绝知此事要躬行。



*9*

其他注意事项



尽量不要迟到，不管是现场还是视频。



如果是现场面试，记得关注当天的天气，提前查一下路线。



如果要修改面试时间，提前一天跟HR沟通。



如果不去，不要直接放鸽子，跟HR说一声。



手机电量保持充足，面前可以临阵磨枪。



面试登记，字尽量写的好认一些，个人作为面试官时，不好认的扣分，字如其人，代码同理。



不要作假，编造一个谎言往往需要更多的谎言去圆它。



大厂一般面试周期较长，注意时间安排。



保持自信，保持自信，保持自信。



**寄语**



多思考，看问题尽量看透本质。



技术上的问题都能找到解决办法，如何在思维上打通才是需要思考的。



举个例子：



说一下Android系统启动流程。



可能很多同学对这个问题没有头绪，或者看了也记不住。



回想一下Android平台架构，相信大家对下面这张图应该是很熟悉了。



![图片](https://mmbiz.qpic.cn/mmbiz_jpg/MOu2ZNAwZwMbf7W2kKBqdUsWibtKFAarWAiab8H1Rkicsd5bbXkYdkH0kGTZMNxOdanmxrIycj9ApHNjibSYfajYzA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



ok，再次回到问题，简单流程就是从电源键触发唤醒Linux内核，然后虚拟机、Framework，最后System Apps。



先理解大致流程，再去串联细节，比如其中涉及到的Zygote、AMS、Launcher等等。



**最后**



ok，终于啰嗦完了，不过句句发自肺腑，真心希望能帮助到一些同学。



祝大家都能在心仪的公司，拿着不错的薪水，开心的写bug～



------



最后推荐一下我做的网站，玩Android: *wanandroid.com* ，包含详尽的知识体系、好用的工具，还有本公众号文章合集，欢迎体验和收藏！



推荐阅读：

[LiveData奇思妙用的 11 个场景总结~](http://mp.weixin.qq.com/s?__biz=MzAxMTI4MTkwNQ==&mid=2650839175&idx=1&sn=025e4c188cd5fd11e325975a27b381af&chksm=80b74c19b7c0c50f60e82ff8df9fa508743789fff5ef58e3b7f4ceab5603a8e4a14e28fa45a7&scene=21#wechat_redirect)

[Android 中看似高大上的字节码修改，这样学就对了！](http://mp.weixin.qq.com/s?__biz=MzAxMTI4MTkwNQ==&mid=2650839137&idx=1&sn=8fa173e63a0f9bc614b02b1d94bf38e9&chksm=80b74cffb7c0c5e93f7fdd55deb442a96e9065072afbef91229a3e2a79c377fa27b074ed22c9&scene=21#wechat_redirect)

[经过20天的面试终于进了阿里！](http://mp.weixin.qq.com/s?__biz=MzAxMTI4MTkwNQ==&mid=2650839006&idx=1&sn=b717ed791cea3d4a2fbb3085b3f12b74&chksm=80b74340b7c0ca56a7153e17eb4e0041e75adb328db610501b7ee244a792c6ce88003432ce8f&scene=21#wechat_redirect)



![鸿洋](http://mmbiz.qpic.cn/mmbiz_png/MOu2ZNAwZwM1quwCc0dXZZcaUy1fm87qugzUGeKP0NsiajbazT8EicLKQ03qbHBnx8JYyOA5rpPRN7yFgDdW50gg/0?wx_fmt=png)

**鸿洋** 

你好，欢迎关注鸿洋的公众号，每天为您推送高质量文章，让你每天都能涨知识。点击历史消息，查看所有已推送的文章，喜欢可以置顶本公众号。此外，本公众号支持投稿，如果你有原创的文章，希望通过本公众号发布，欢迎投稿。

255篇原创内容



公众号

**点击** 关注我的公众号

如果你想要跟大家分享你的文章，欢迎投稿~



┏(＾0＾)┛明天见！

[阅读原文](https://mp.weixin.qq.com/##)

阅读 4916

赞27在看12

分享此内容的人还喜欢 

为什么现在JAVA初级程序员要求这么高？ 

为什么现在JAVA初级程序员要求这么高？ 

... 

阅读 492 

终端研发部 

不喜欢

不看的原因

确定

- 内容质量低
-  

- 不看此公众号

优秀的项目代码都是怎么分层的 

优秀的项目代码都是怎么分层的 

... 

阅读 2261 

顶级程序员 

不喜欢

不看的原因

确定

- 内容质量低
-  

- 不看此公众号

写下你的留言

**精选留言**

- ![img](http://wx.qlogo.cn/mmopen/Y7ATj127kRwW6YmQINHCSmcXkrY92ibvA1fc0NgxHBLHvj0icghrG0RXqfL4pCfTHBSqJ74Ey0KL4ebWO9dv7jwQe4fvtMEB3g/96)

  Jerry

  33

  

  面试官：五年了为什么你还只会Android

- ![img](http://wx.qlogo.cn/mmopen/GXKLwCaeOia8N9ia8bCMQcicia8XhewywSW26rKnOOTwO5PYTQ41tJWAO5uQoqbsH7PicmD8c7vkCpmYSdhia0lOO3FR66odlZnQ2A/96)

  毛豆先生^ω^

  11

  

  10年的我有不少不熟，证明实际开发中其实多数没用，只有提升到一定层次，这些知识点才会用得上。当然我十年还不会，大概是我能力有限吧，我是记不住那么多东西

- ![img](http://wx.qlogo.cn/mmopen/PiajxSqBRaEInGzn78aKlla44pFbzS1DtNNA8HXxEia58RGA40Vu89nfbO74RJwkeQSdNbhm0dergT9Zx7U0sxgw/96)

  上官瑞杰

  3

  

  大概扫了一眼，大部分都是一知半解或者是看过源码却没有一个系统的体系能表达出来。看来学习之余还是要多总结多回顾

- ![img](http://wx.qlogo.cn/mmopen/PiajxSqBRaEJvheVkicxygricIRFoI1HNpwrFxic8DjAZ5VpvwDjHjiaJw3uF6mgicXR4iceeicANEXsQT9Xb1cwZkO4TQ/96)

  J.C

  3

  

  我是个假的安卓开发…跪了

- ![img](http://wx.qlogo.cn/mmopen/ohaPLGgZo1KKf8n5St55GgK7QvuoVNI5J8YFu0RDo4Z6E5nYvbrib4D4cbzEIQmcvlibHIXzOZF9VzY6aE1Eic3bR8FTKV36PFo/96)

  小肥羊冲冲冲

  2

  

  超哥威武，看了超哥的文章就进阿里了 并且是临桌，xdm还等什么

  ![img](http://wx.qlogo.cn/mmhead/Q3auHgzwzM5h268UOh5ich1icianEYEJSouXL8OakwNpqTKo7AFhuibIaQ/0)

  鸿洋

  (作者)

  1

  

  牛批呀

- ![img](http://wx.qlogo.cn/mmopen/Y7ATj127kRxSq4j2QAxlJarlWVyhfjfYTNjEicmjzxnztBzEcR6KftibUEtdvy9xOIZBWlT1S3ZicicsVtNGwibhweF1ASXDyKmPT/96)

  清茶

  2

  

  六年了，别问我源码，问，就是一把梭，一周给你整出app，安全稳定可靠无bug

  ![img](http://wx.qlogo.cn/mmhead/Q3auHgzwzM5h268UOh5ich1icianEYEJSouXL8OakwNpqTKo7AFhuibIaQ/0)

  鸿洋

  (作者)

  

  哈哈，自信

- ![img](http://wx.qlogo.cn/mmopen/ohaPLGgZo1LNnXMHCj0FUZcvExnfFOdthSZrzSpuXlp80Qluk4Jv9AwenFJcO4uO10Yw9gtMDOaf8qoQg6rcXmM2zJiaUoC22/96)

  小怪受

  2

  

  chao大佬yyds！

- ![img](http://wx.qlogo.cn/mmopen/ohaPLGgZo1LNnXMHCj0FUShibcC1D5HUFYricmEfKZIRbb1iboOdibB1u33DoChnz3jp0iaURiapMujII0z2B9ywoVZV08CuY94yGG/96)

  亢龙有悔

  2

  

  可以称为面试宝典了。

- ![img](http://wx.qlogo.cn/mmopen/GXKLwCaeOia9EfKVasckyVbV2GUv4CPWw9IudaXd4F6s5HRah85jXXHsOo7p4h0WcFsGDibrfAsTUdlgia0IG4Z0YYRzhJjO8Lp/96)

  sorgs

  1

  

  日常打卡

- ![img](http://wx.qlogo.cn/mmopen/GXKLwCaeOia8mptuVib9LdKpzsNfQ5lNwiah3YkTwq1cc1MmhClK2pY7h74KuYSVKf0Pibk8PtXcDJjHYW3hUibgt5JnEmLVf6EVF/96)

  慎之

  1

  

  收藏了。太实用了。

- ![img](http://wx.qlogo.cn/mmopen/ZKmlvB4Wulwe6ibQQvhTa2JQ2SPUcRjwg5VHh1cFxkicibEvuxwOZc18gsibUHzccxazuSAOMicBFl1fBBZt5CrZzKCVVKXpbtkibI/96)

  朱亮

  1

  

  收藏为敬

- ![img](http://wx.qlogo.cn/mmopen/GXKLwCaeOia9XjlvIy2VTSAPSBqHI6pkgcZGyXnMhKhGf0Ty6meh5t1f0o9g7MgUKD1Sy994a5RNnE9yJLqgFNzCwLofSeMM0/96)

  远海

  1

  

  看了一下，太简单了，虽然我是14年工作经验

- ![img](http://wx.qlogo.cn/mmopen/rEBhcKSUEPsfkEtqkib3xAvM3TJAqa9YdO61CoGV92rUp8u2TvtmgBDicUGkjibUGE0breXGsIbWGnrPJEnic95Baddp9h5B5Jm5/96)

  yangzh

  1

  

  很好的面试题大纲，收藏了

- ![img](http://wx.qlogo.cn/mmopen/ohaPLGgZo1KzgTUz0XOR1ia3Kjk5VibnK1ONLuxClv0XbgG4CeOXmq59ufBukKYzefZsnnqbSXoNbEzRoyyEZr809ibL6bGa9kg/96)

  ❌x💪

  1

  

  干到不行的干货，有面试要求直接对着面试题一个个复习就行了，先收藏了

- ![img](http://wx.qlogo.cn/mmopen/PiajxSqBRaELqAzs4pF9lAkznYMWicIjxDiafn0DbveyoXCqqYPK883icIotQWicu2X8enicgE5fczHg8vVLWibOIibiaFA/96)

  贺强

  

  真不错

- ![img](http://wx.qlogo.cn/mmopen/ohaPLGgZo1JWjtqwDItTXcrI7DNfRHzduIcIhicwKiceckRjzGlEsiaSbno41oRUzpoWXIwHZicXqfqc7vOcune5sAKSl8iaXjpOG/96)

  Mr.Mo

  

  想了解系统开发的文章

- ![img](http://wx.qlogo.cn/mmopen/6FqXWGH2kd08mjWibKRFAADHuZqeFK9qFvf4vT00qBWWup1lBfJLicfMR78f8cPHt4lh4PvGIHCE9NxViaYSNYys0tk3qeAibeld/96)

  明国

  

  已含泪收藏

- ![img](http://wx.qlogo.cn/mmopen/Z89ZntJu6ARJVAbpnZYp7uU3VUdxic0twJLk79uk5XcWrHcWsgWZXCgmnpeROMBaxBGVBAN9OrpLDjDg3iaSZOllyKusM91a6ia/96)

  loading

  

  大部分更需要的是 敲门砖！ 

- ![img](http://wx.qlogo.cn/mmopen/6xfFA5kjiaWDXAy41xtIf3RJh7J4ZqicCCZMamxDAge0YBOCKdf1OqxKbO2qV6jTiaZsYVDQhiaXmdibrzSP8RcfD3IzBLjfaLObia/96)

  RegExp

  

  我也想知道协程底层实现

  ![img](http://wx.qlogo.cn/mmhead/Q3auHgzwzM5h268UOh5ich1icianEYEJSouXL8OakwNpqTKo7AFhuibIaQ/0)

  鸿洋

  (作者)

  

  以前就推送过，可以搜一下

- ![img](http://wx.qlogo.cn/mmopen/Y7ATj127kRxQ9DIuaRHMiag36p6DrSYknAyLvohOFAHzpyLzFNPrH1AzLXmft8hBHNXcPjMUiavpI4MLvCJyMicKmlrGTHibHRtl/96)

  Crixalis

  

  太感谢了

- ![img](http://wx.qlogo.cn/mmopen/ohaPLGgZo1LNnXMHCj0FUTwGUGy337trC49styNlB89EvqbZbfTdAlfRLk0rzmBv3vqnafZR8QstDUQCdNjKAI305RYEdYMM/96)

  zzzwhy

  

  棒，又有的看了

- ![img](http://wx.qlogo.cn/mmopen/GXKLwCaeOia9mgPVPiajQiaJjhYU2cv6A85gCpVZkCKWHuFPYSiahGeoP6VqOibfwrOfhQDMKKJicv2JbEZVcVye2eSBLU5lnPVFHB/96)

  YyuTtian

  

  都会了能开多少钱？

- ![img](http://wx.qlogo.cn/mmopen/ajNVdqHZLLDbIIL4dvnST4fsJPcRIx05kR6wWysR4kRoAte5ovmXW5FWGlCWXJBsFTgjXNR1MW10a3rH1GFOAW1Ficjh5RicbrW6euW1BU8Q4/96)

  challenge

  

  很棒！

- ![img](http://wx.qlogo.cn/mmopen/Y7ATj127kRxQ9DIuaRHMiasWmDweImghecmtnQQtR2eRvCajDibibRXzFLrRhRf1beTfXlTicOiaCSichCnnMribRqRXrf7tgkZKEjX/96)

  一曲小情歌

  

  转行啊

- ![img](http://wx.qlogo.cn/mmopen/ajNVdqHZLLCqlNX5PN6E6R9hW3tN7CpMAS9m8zNxAp3icJLgNTIZOObrxxI6mvdkEAuhYG8ysMjo8dBRLT6RtVg/96)

  我就是我

  

  鸿神总是应需而发

- ![img](http://wx.qlogo.cn/mmopen/GXKLwCaeOia9ecZvHpXuicbssZv2eZTkprb2yVInqVt9BxwA3xzI7mtdAicmyQulyRGnUZQetI6rV04e4y3Ix8icVxyQNkOrtqaG/96)

  流星雨

  

  

  普通的上市公司，规模100多人的，应该不会问这么细吧？

- ![img](http://wx.qlogo.cn/mmopen/Y7ATj127kRxe4w0loEYic3MQgZOJGJSMOt7poZJxzmLqonzug2pbicxUiaUibPJ8tiad55PDBH6icxicGunZNoEVicExo8BNxDmlorkic/96)

  csl