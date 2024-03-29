---
layout: post
title:  三石 · 道——聊聊Java
date:   2014-11-01 01:15							
category: "Java"			
---

> 本文转载来自：[三石 · 道个人博客](http://www.molotang.com)
转载请注明出处：[http://www.molotang.com/articles/51.html](http://www.molotang.com/articles/51.html)

<br />
### 聊聊Java（零）
---

俗话说，“*三句话不离本行*”，貌似是出自《官场现形记》原意搞不清楚了，现在通常说的是人的行为总离不开所处的职业范围。这是我的第三篇日志，觉得很有必要聊聊技术。做Java这么久，多少有点想说的，想起啥说啥吧，算是一个总结。

**本文主要是对Java开发语言以及Java体系结构学习的一个总结，Java的历史背景和发展，以及和大家分享一些个人学习经历和（我认为的）经典书目。**

从开发语言上来看，Java无疑是目前业界的中流砥柱。TIOBE有一个认可度很高的编程语言热门度排行榜，如下是最新(2013)的展示。

![](http://www.molotang.com/wp-content/uploads/2013/06/%E6%8D%95%E8%8E%B7.png)

从中可以看出，长久以来，C和Java始终保持在第一阵营，可见热门度超高。C++则结合了C的优点和面向对象的思想，成为很多对偏底层或性能上要求较高的首选开发语言。Objective-C在近期一飞冲天，乔布斯( Steve Jobs )功不可没，苹果应用的开发几乎独占了这门语言。PHP就不说了，Zencart、Wordpress等优秀的开源项目都很受青睐，本站就是基于这个的。C#、VB用的少，基本上属于MS阵营，就不多说了。Perl也了解不多。Python是一门抽象度更高，使用更灵活的语言，记得有种说法叫“胶水语言”，她立于此列中。随着Ajax技术的广泛认可，跑在浏览器端的js代码似乎更受到重视，但Javascript绝不仅仅局限在BS系统的前端，MongoDB也是它出没的场所，最近服务端考虑用到的Node.js更是展现了Javascript无穷的生机。

扯远了……

**先回过历史简要看下Java诞生的年代背景吧。**通常认为Java诞生于1995年，但事实上在此之前Java的雏形已经酝酿了好久，最初是因为C/C++的一些弱点使用起来让人头疼，安全性是一个考量，于是打算在家用电器等智能物件的通信等方面尝试采用新的语言，但貌似并不算成功，这个当时叫Oak。后来随着互联网的发展（不知道这个要不要感谢一下雅虎和杨致远），Java真正意义上迎来了新的起点，在浏览器上大做文章。

但其实这跟Java如今的应用场景也大为不同，记得大学时一本国人写的《Java程序设计》教材中还提到过applet这个东西（很多老版本的Java开发还会提一些）。没错，早期的Java其实是通过用这个和浏览器一起，搞出一些互动的应用来，但后来……大家都清楚，如今做Java工程师的写applet貌似不多了。

Java诞生于Sun。大家知道Sun（Stanford University Network）这个公司曾经是很风光的，主要做工作站和小型机，在微软要成为霸主的时候，Sun都是大家心目中的挑战者，而Java也是在这个时候产生的，要做跨平台、面向网络，其实也是在动摇微软的垄断。但很不荣幸的是，Sun并没有像众人期待的那样拿下微软，而最终只留下了短暂的春秋（吴军《浪潮之巅》）。然而不幸中的万幸就是，Java如今仍然屹立不倒，受到最大规模程序人员的喜爱，本人也十分喜爱Java。

至于Java为何叫Java，和咖啡又为何有如此情缘，以至于徽标是咖啡杯，class开头要0xCAFEBABE，这些个大家可以去网上广泛收集资料了……

写到这，发现要说的还有好多，先在标题上加个“（零）”，后事且听下文分解。

<br />
### 聊聊Java（一）
---
上文大致说明了Java的概况和早期形成，要想进一步了解Java的发展历史，我们有必要知道Java体系结构和Java平台。

![](http://www.molotang.com/wp-content/uploads/2013/06/jdkimg.png)

其实，单纯讲Java这个词，她可能有很多含义。她可以指Java语言，也可以指Java技术体系或平台等。

总的来讲，通常Java（体系结构）分为四个非常主要的部分：**Java语言、Java虚拟机、Java API 和 Java的类文件格式(.class)**。Java语言就不用说了；Java虚拟机是实现“Write Once, Run Anywhere”的最强力支持部分，她屏蔽了底层环境的不同，而且实现了垃圾回收和安全等方面的重要机制；API即对应用开发者向上提供的编程接口，可以直接用这些暴露出来的接口进行开发，这个概念落到实际上，就可以理解为你看JavaDoc的时候，包和、类、方法的定义说明；class类文件结构，则是定义了一套完整的类文件规范，能够在不同的虚拟机实现上做到统一，这个class的结构也被Groovy等基于JVM的一些开发技术作为中介广泛使用。

其中，Java虚拟机和API一般被统称为Java平台。而JDK和JRE这类词貌似和这些没有太直接的对应关系，JRE就是Java应用运行的一套环境，而JDK是在此之上增加了开发、调试、监控等工具，这必然又包括JVM。当然也有人把Java语言和平台统一到一起，认为这就是JDK的实际意义。

说道Java平台，就不得不沿着JDK的发展历史再详细说说。可以先说说我知道的一些。

JDK1.0，1996，主要是提供了虚拟机和Applet等技术（上文提过随着互联网兴起的发展背景，这些都和浏览器有关），那时的虚拟机实现主要是纯解释型的。

JDK1.1，1997，像Jar、JDBC、RMI和Reflection这个时候都有了，相信做Java的基本都离不开这些。

JDK1.2，代号PlayGround，1999。这个得好好说说，有个大变化。Java平台被细化为三个大的发展方向，为桌面基本应用、为企业级站点、为移动手持设备分别服务，即为StandardEdition、EnterpriseEdition和MicroEdition，通常说的JavaSE、JavaEE和JavaME，因为是在这个2.0的时候，所以也有称呼方式为J2SE等。对于开发者来说，至少API不同了。这个时候有了JSP，而且我们现在还在用的Hotspot实现(JIT融入)，这时候已经出来了，集合类大家用的也很多吧。

JDK1.3，代号Kestrel，2000。实时、CLDC、MIDP、CDC规范发布。

JDK1.4，代号Merlin，2002 。这个使Java走向成熟。NIO等主要的东西就是在这个时候出现的，WebService也大行其道。

JavaSE5，Project Tiger，2004 。主要是语言易用性的改进，如foreach相关的和@annotation等，还有就是JUC(java.util.concurrent)，这个包里的东西你会看到since 1.5 。

2006年的JavaSE6，更需要关注的是，开源了，还有就是不叫J2xE了，改成JavaxE了。

2011，Java7，此时Java已经进入Oracle的时代了，G1回收机制是一个新点，而且Hotspot和JRockit必然走向统一。

当然更详细的，具体到年的，可以参看[Java Timeline](http://oracle.com.edgesuite.net/timeline/java/)


### 聊聊Java（二）
---

> 厄尔尼诺分割了大气流，从大洋彼岸掠过，温暖、潮湿的空气弥漫在整个得克萨斯。他与冷锋气流发生遭遇，在南面的压力下形成了漩涡，并当场锁定了冷空气。暖湿气流冲入冷气团中，相互交汇，产生一个完美的风暴。

这是对Bruce A.Tate在他的《[Beyond Java](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CFcRfH0GoT805sipKkHXaAvr3k4oHlI%2F1qu01Ji86xrVgEOvu%2FFWl4K7%2FOH3EsWduiQNqdC1IgiNPeY9E%2Byqe7j%2FA%3D%3D)》书中一段描述的翻译。任何风暴都不是偶然，它需要很多因素聚结在一起，而Java就如同这股完美风暴，席卷了世界。

![](http://www.molotang.com/wp-content/uploads/2013/06/wave.jpg)

自1995年Java正式向世界发布，到如今已经影响了世界近20年，从技术创新到企业的发展合作模式，也不断地改变着人们的生活。Java成为了第一大开发平台，有着约9百万的开发者，平均每年有10亿下载量，有30亿的设备在运行着Java，占领者97%的企业桌面份额。可以说Java是很成功的，这点从Java语言在TIOBE榜上的情况也可以看得出来。Java的成功是由多方面因素共同造就的，我们就来看看。

#### **一  我们回顾下Java体系结构特点。**
---
通常，在介绍Java的时候都要提到的几个基本特点就是，平台无关性、安全性、网络移动性。其中前面的两者是支持后者的基础和前提。Java的JVM是平台无关性的最根本技术支持，屏蔽了底层环境的不相同。安全性则体现在Java体系结构的各个层面上，class文件格式的规范性和校验机制，JVM类加载器动态加载类时的信任代理机制，Java API中安全管理器的概念和栈中权限检测的机制，还有就是Java语言中对指针的抽象、数组越界异常机制等安全的控制。网络移动性，则与互联网的发展，计算方式的改变等有着密切的关系，可以说是顺应形势。下面的两节会更详细地结合情况说明这些。

####**二   下面，我们详细看下Java在技术上诞生和发展方面的因素。**
---
**（1）计算方式的改变和互联网的兴起。**在PC流行以前，多终端的大型机系统还是主要的计算模式，计算相关的很多资源都是共享的，当需求发展到一定程度，计算资源就到达了一个瓶颈。在PC刚刚开始流行的时候，互联还并不方便，因此各个计算机就如孤岛一般，但不久这个限制最终被互联网打破。自此，Client/Server的计算形式便开始广泛得到了运用。但这还有另外一个问题，就是和如今做C/S所需要注意的问题一样，就是客户端程序不易于管理，可能会存在多版本，服务端必需兼容处理个版本的客户端程序才能保证全局是稳定的。

不知道读者中有多少了解移动互联网或者说无线应用开发的，对于大中型公司的应用，很多有一种需求，叫做插件化——就是说，客户端初始安装只是一个框架，在这个框架体系下，客户端可以通过用户定制来进行可插拔的软件安装和更新，软件本身也成为一个网络传输的内容，而不仅仅是单纯的数据。但据本人了解，目前iOS平台还无法真正意义上地实现这些，我推测原因可能有安全性方面的考虑等。其实除了安全，在各种硬件和操作系统环境中能够实现同样的效果等也不容易，但这些正是Java崭露头角的机会（前文重复过几次，平台无关性、安全性以及网络移动性的特征）。Java在出世的时候，就是以Applet，HotJava等打破了这个僵局，后续的Serialization、RMI、Reflection等对此提供更强有力的支持。

**（2）C++和Java。**相信大家都看到我的文章“聊聊Java（零）”中TIOBE中，第一阵营中除了Java，还有一个C。C语言是一门很古老的语言，是汇编语言基础层面之上最重要的一门语言，和汇编比起来具有很好的可读性，和VB比起来又很有执行效率，是开发操作系统层面最重要的一门语言，直到如今亦如此。但任何事物都有不完善的方面，比如在当时很受人欢迎的面向对象概念，C就不怎么具备。面向对象可以对应用做更好的设计，并重用代码，这种对事物已有资源的积累，是任何事物向更高更广发展的前提。C++诞生了，在C的基础上融进了OO的理念。C++也算是一门很重要的语言，但很遗憾，她也有着非常脆弱的特点。先不说C先天的缺陷，C++就算是面向对象，也不纯粹，没有做到everything is object，她不指定唯一根（不像Java的java.lang.Object），而且多重继承。这些一方面使得语法更为复杂，出现了虚基类等概念，学习成本更高，而且在类结构上层次容易带来很多困惑，不利于更清晰的设计。回头再看C和C++的一些通病，就是对底层环境依赖强，基本谈不上什么可移植性，对内存操作直接（也有好的一面），野指针可以满天飞，而且没有Java中的垃圾内存回收机制，内存泄露也许是经常发生的事儿。据说在Win下还有一个“DLL问题”，本人用C++在Win下做应用开发的少不太了解，这个就不细说了。

如此种种，使C++的开发者很困惑不爽，早就期待着有Java这样声称有各类有点的语言和平台，而Java确实做到了这些，使众人眼前一亮。

**（3）面向对象。**前文说C++也提到了一些OO，这里少说点,说点其它的。面向对象的三个基本特征是封装、继承、多态。用OO直接的好处就是可重用性设计，其实OO不仅仅是这些，她使得应用程序的设计更接近自然更为人的思维所接受，也就更利于设计出更好的应用，推动软件开发的发展。早期的OO语言有Simula、SmallTalk等（貌似《设计模式》一书中很多例子都基于SmallTalk）。其中SmallTalk是非常成功的面向对象语言启蒙者，也是单继承，但由于其他因素局限于特定的领域内。可以说，如今的Java、ObjectiveC都从SmallTalk中学到了很多。

**（4）再说JVM和API。**其实对于Java平台，这两者也提到了很多次。不得不说JVM对于Java的成功非常关键，平台无关性和安全性在这里都做了很多。JVM其实不是一个特定的实现，她有一套完整的规范，允许个厂商合作推出适合特定系统和场景的实现，这是一个很好的合作机制。虽然Sun给出了HotJava和HotSpot，但JRockit等也都是不错的实现。JVM规范给出了class的结构、并粗略地规划了类加载和内存管理以及执行相关的条款，但具体到堆了栈了这种实施，是没有任何硬性要求的，甚至可以使非软件实现而用硬件。JVM相当于给了下面实现者很大的空间，又对用Java语言的开发者一个统一的开发平台。规范设计的相当好，据我所知，Java对于JVM规范的制定改动一直很少，只有几个版本：第一版、第二版和Oracle时代的7。规范相关详细的内容可见http://docs.oracle.com/javase/specs/jvms/se7/html 。对于JVM成功的另一个佐证就是，Groovy、Scala这些后来语言对JVM的应用了。对于API，在第二版之后对各个方向的分工是非常有利于Java的发展的，任何领域发展到一定程度，都会细化分工，明确各自的方向。

#### **三   还有一些是技术本身之外的东西。**
---
作为码农/开发者/程序员/工程师，技术很重要。但技术不意味着整个世界，不是所有事情都仅靠技术就能解决。这个观点很重要。

**（1）微软和Java同盟。**微软大家都了解，在PC的发展过程中，有一个称谓叫Wintel，就是Intel加Win的OS。微软在软件界可以说是霸主地位，说他是霸主不仅仅因为他干得很大，更重要的是，谁是他的竞争对手，几乎都会很惨……比如网景、Lotus等，当时Win还在图形界面上抄袭了乔帮主的Macintosh，让苹果在PC一度被动。1997年，Sun和MS终于迎来的第一仗，Sun起诉MS在Win下歧视Java（貌似是微软对Win下Java平台相关的东西有改动致使Win下Java程序能用而其他环境的不行）垄断并胜诉。后续的斗争更为激烈，比方说MS抄袭Java搞出了自己的.NET和C#（虽然目前的市场占有应该远不及Java）等。

另一方面，Java的跨平台优势吸引了众多底层的操作系统提供方和企业。早在1996年，10家主要的操作系统提供商就声明引入Java技术，其中微软的各个竞争对手（IBM、Apple等），每年一度的JavaOne大会也开始进行。之前微软以OS垄断使其Windows大举扩张，而目前Java这个跨操作系统的平台似乎弱化了这一点，在MS竞争对手的支持下，Java正不断向前发展。此外，Java声称的安全性对微软Win中被抱怨的种种缺陷也是一大明显优势。

**（2）企业支持业界标准。**随着Java企业用户的发展和技术上的不断革新，Java从客户端的applet不断走向服务端，1997年有了servlet这个东西（可以理解为server applet），98年又搞出了个EJB1.0 。这促使了IBM这种大企业将Java和企业内部的数据库、消息系统等整合起来，而且在这个过程中Java再一次展现了她在服务器程序开发和整合上的优势，也积累了很多不错的产品。

Java吸引了大批优秀企业用户。像IBM，拥有非常大量的工程师应用Java做各种开发，这些大企业促使了一些基于Java的业界标准，就像秦始皇统一货币度量衡一样，这对Java的进一步统一发展是有着很大的促进作用的。

**（3）开源和社区。**Java的成功，开源功不可没。正因为开源，更多企业和个人才能更容易的接受和使用Java程序。其实Sun最初是对开源有抵制情绪的，因为微软已经通过垄断赚取了大量利润。开源，这是发展的必然，开源给大家带来的非常丰富的选择，开源也提高了收费的门槛，促使软件提高质量和价值，开源也促进了Java的推广。这里举个可能不很恰当的例子，开源就好比电商领域的淘宝。在淘宝出现以前，传统的百货公司把持着市场，只有有一定资本的人才能在百货大楼中有一席之地，而像北京西单中友百货这种，一件普通的衣服要卖到好几千，这中间的利润到底耗费在了什么环节，进了谁的腰包我们并不清楚。但我们应该清楚的是，这个价格应该在一定程度上讲是虚高的，超出了一件衣服应有的价值。马云貌似说过这样一句话“不是淘宝太便宜，是传统商场太贵”。从经济学的角度上讲，商品的价格应该与价值相关联，一件商品到底有多贵，不是谁来要多少就是多少，而应该探其本身的价值，价值是什么，无差别的社会劳动。

放到开源意义上讲也是一样，微软垄断了操作系统，不开源，而这样的软件或者企业必定会受到开源社区的影响，甚至威胁。就像越来越多的人会使用淘宝而不是去百货大楼买贵的衣服一样。在开源社区，开源的应用会显现其应有的价值，并随着需求不断发展进步，最终得到广大用户的认可，这是开源软件的价值所在。

就算大家可能没有看过Tomcat、Spring等优秀产品的源码，但一定用过并且知道他们的源码是可读的。开源社区创造了这样一个环境，她不但催生出从Jetty这类服务器，netty这类网络通信框架，而且也会产出像Lucene这种搜索引擎和Hadoop分布式计算框架等。另外，这一切的一切，回过头来又进一步促进了Java的发展。

其实，Java的发展成功因素也许不仅这些，但历经近二十年，Java依然是开发平台中的中流砥柱。

### 聊聊Java（三）
---

前面“聊聊Java”已经聊了三篇了，争取用这篇对这个系列做个小结。

![](http://www.molotang.com/wp-content/uploads/2013/06/javacup.jpg)

这篇主要对Java的展望、个人经验的简要小结和一些值得推荐的资源。

说到对Java发展的展望，就不得不提到JCP。

Sun在1995年公开了Java这样一个技术，在三年后也就是1998年，Sun又创建了一个开放的社区组织JCP（Java Community Process，翻译过来大概是Java社区进程），让关心Java的人都可以来参与Java特征和新版本规范的制定，而非让Java只有Sun一家把控。与JCP相关的一个概念JSR，Java Specification Request，是一个以特定格式详细描述需求的规范文档。JSR可以由一个JCP成员发起，经过多个状态。JCP最后产出三个东西——规范Specification、参考实现Reference Implemention、技术兼容包Technology Compatibility Kit。

2010年，Oracle收购了Sun，加大了其对Java的影响。在展望Java未来前，我们再来回顾下Oracle时代的Java7。

2011年，Java 7发布。在Java7中主要做了以下几件事情：提供了异步IO，提供了新的文件系统API，增强了对非Java语言的支持，用了G1垃圾收集，还有就是Java语言语法易用性上的改进。

有关Java7更详细的说明请参见：http://www.oracle.com/technetwork/java/javase/jdk7-relnotes-418459.html

下面对Java的未来做一些展望 。时代在不断的变迁，需求也不断的更新，人们对Java的期待实在太多，Sun被收购，Java7的发布拖后，JCP的效率低下也被人所诟病。未来的Java需要解决的问题很多，说说主要的几个。

服务模块化，OSGi则一直是工程师的首选，对于未来Java来说模块化是很重要的需求。Jigsaw在路上。
对于高级开发语言来讲，闭包是很有价值的部分，因此Lambda也是大家对Java的一个期待。
Java语言的易用性和Java的高性能一直都是Java人所追求的，这点在未来的Java中也一样会受到关注。
很多非Java语言和技术的使用以及他们和Java的结合应该受到关注，Groovy、Scala、Jruby。Javascript也在各种应用场景也在发挥着新的作用，将这些和Java整合也是Java很重要的发展点。
此外，如今已是云计算时代和大数据时代，如何适应这个变化发展的背景环境，也是Java发展所需要考虑的。
接下来，Java8会发布，对Java8感兴趣的，可以看下这个。

http://www.jcp.org/en/jsr/detail?id=337

对Java，本人也还在学习和认知理解的阶段，可以算得上是菜鸟一个，在应用实践中略有一些感想，小结一下。一来有助于自己回头复习的时候有个参照，二来也希望真的对同在学习Java的人有那么一点点帮助。

作为一个接触Java0-3年的人，对Java语言的学习运用依然是很重要，这是接触Java的第一个阶段。Java到目前已经发展了18年，为了满足各个方面的需求，不断增加新的东西，这对于学习Java的人还是有一些成本的。其中涉及面向对象概念的理解，这需要一个过程，最初是对规则比较死和硬的认知和记忆，而后逐步过度到理解和融入自己的思维方式，去实践去设计。面向对象这块，主要的语法体现，就是继承、封装、多态，具体到Java就是extends/implements，public/protected/default/private和overload和override。除此之外的语法涉及面也比较广，主要包括容器、泛型、IO和多线程并发相关的内容等，细节就不一一说明了。在这块《[Thinking in Java](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CITy7klxxrJ35Nnc0lgjJuxv%2BefLb%2FWP8SzTL1Qsdev3b6x%2ByXVbD0SKLWv6mWC%2ByUbJT1fGlrNqaJzZOy8spAIQw%3D%3D)》是非常经典的学习资料，本书的作者也是《[Thinking in C++](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CITy7klxxrJ35Nnc0lgjJuxvSH%2BnLgVNlBun%2FBCcGM7QpCEg75yb0AN2f5idzJuBoa6HZYcjtWsr1HycVAwM1IxRQ%3D%3D)》的作者，Bruce Eckel，至少本人觉得值得反复读反复学习，从中学到的不只是语法使用上的东西。

在此基础上，还要对Java的体系结构和IDE有认知了解。IDE不用多说，Eclipse是非常好的开发环境，用起来非常舒服，插件化支持非常好，有必要熟练掌握其使用。Java体系结构的话，API实际上和上面所说的是相关联的，要能熟悉JavaDoc中所描述的才好。必要的时候去查文档，文档要看官方的，http://docs.oracle.com/javase/7/docs/api/ ，除非有把握或者真的值得相信，论坛的东西是不会比官方文档更靠谱的。除了Java language和API，了解class文件的大致结构是有必要的，比如至少知道0xCAFEBABE这是个什么东西。其实，说起对Java体系结构有了解，JVM是这其中最需要了解，也值得深入挖掘的东西。前文说过，JCP制定的只是一个规范，虚拟机也是一样，她允许不同的实现。对于规范，可参见这里http://docs.oracle.com/javase/specs/jvms/se7/html/ 。还有一本书个人觉得也不错，《[Inside the Java Virtual Machine]()》,不过这本书年代比较久远，有些东西可以说是过时了，而且这本书估计是买不到了，可以参看这里http://www.artima.com/insidejvm/blurb.html 。提JVM规范可能扯得有点远，作为工程师，其实能对JVM的配置和调优有所掌握是有必要的，运行程序要知道自己运行在什么情况的环境下，在这点上，周志明的《[深入理解Java虚拟机](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CFcRfH0GoT805sipKkHXaAvpXnvt0ComTjwkjckGy3EUP2zg%2FUOUZNXDD3AhKnzY3rUR6yumbVafvSwxx0ZsRlY2A%3D%3D)》还算不错，可以读一读。这里说了好多JVM，我觉得学习JVM，至少需要了解她是如何进行类加载的、如果进行垃圾对象回收的，比如Hotspot就分了新生代和老生代，在不同区域用不同的算法进行回收。了解JVM怎么保证安全其实也有必要，这里就不多说了。想更多了解JVM的规范和实现的，可以看这里，昨天刚刚看到前淘宝网同事莫枢的分享，非常不错：http://book.douban.com/doulist/2545443/ 。

到这里，其实已经有了前面两者的基础，就可以做很多事情了。前面的文章里我提过，不是所有问题都是仅靠技术就能解决的。作为工程师，除了掌握这些技术基础外，更多的是去实践，在具体的业务场景下解决具体的问题。目前来看，很多情况我们应用Java解决问题，需要了解Servlet这个东西。我最初是在学校里的一门课程了解到，当时的教材叫《[J2EE程序设计]()》，不是很推荐。后来倒是看过一本叫《[Head First Servlets and JSP](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CFcRfH0GoT805sipKkHXaAvollSbudjKDpmZ3xEQe10bScQjGNKrkS9BjEN1cylpFqyYViz%2BnnwJ%2BNhL4rmEloW)》,评论这本书，我觉得可以说“很生动”，呵呵。和Servlet相关的，至少要知道Tomcat是什么东西，Jetty和Tomcat又是啥关系，可以看看《[Tomcat:The Definitive Guide](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CITy7klxxrJ35Nnc0lgjJuxuxyuJJWOAj661PCIOVeQeE2Ur3SXeCKwfGvzLDXn%2F6RA85lTdGrAK6%2FSbpRS28Ot3w%3D%3D)》，OReilly出品。

之后，随着业务需求复杂化了，应用的工具和框架了，可能就不止这些，Ant、Maven、Spring、Struts、Hibernate、Ibatis、Freemarker/Velocity。对于这些，更多的是了解文档，会配置会应用。当然，我觉得对于优秀的开源产品，源码是一个很好的学习资源。当然这需要时间和精力，具备一定理论基础和搭建好一个合适的调试环境在这个过程中都很重要。本人粗略读过SpringIOC部分和Tomcat的部分源码，了解Tomcat可以看早期版本相关的一本书《[How Tomcat Works](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CFcRfH0GoT805sipKkHXaAvo2ZHc05jvm2pfYUAAG6UUnYlSAFYeQj55NNOzbsiSmP4jjaR8ZYSg8jAgmg4Ba52ew%3D%3D)》，但Tomcat的源码有些复杂，可能去看Jetty是更好的选择。读源码的目的一方面是作为基础语法和实践不足的补充，另一方面可以看看一个好的开源的产品是怎么设计架构的。

对于企业级的开发，其实还有一些几乎是必须要学习的。分布式应用的开发离不开高性能的网络通信，基于服务的架构（SOA）几乎是必然用到的。这就有必要知道Java的RMI和序列化的作用，BIO和NIO的不同，netty是啥东东，传统的基于XML的WebService还有一些如Hessian的技术也都是有必要熟悉下的，也要知道ActiveMQ是干嘛的怎么用。 这方面有本书可以看下，淘宝网的林昊《[分布式Java应用：基础与实践](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CITy7klxxrJ35Nnc0lgjJuxuUf3jQWuwCEnLtPSNv8Mr6FtsZ6hNszAsPmtT%2BVdtsi2xN%2BJ0nXeIAKebL45vPYV)》，虽然书中直接具体讲分布式的内容比例并不算大，但读读还是有收获的。

上面说来说去都是紧密和Java相关的，其实在很多场景下，Java不是万能的，相关的技术也要有所学习有所了解才能更好的和Java结合起来解决问题。比如Mysql是很好的数据库，提供了丰富的存储引擎，采用何种更合适。Java是一个平台，那平台之下的OS如何和JVM交互并支持着JVM等。还有就是JVM如何去调优，是否有可能对JVM了解后做一些适合特定业务场景的改进。扯远了……

除了上面提到的，还有很多不错的书目值得推荐，比如《[Core Java](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CITy7klxxrJ35Nnc0lgjJuxuUf3jQWuwCEnLtPSNv8Mr6FtsZ6hNszAsPmtT%2BVdtsi2xN%2BJ0nXeIAKebL45vPYV)》（分卷一、卷二）等，更多的还请大家多多探索和沟通。

此外，我还想说一句的是，这个世界上很少有什么东西能更无限长久地生存下去，技术也是一样。Java已经走过了近20年的风风雨雨，这是十分难得的。早在Java诞生后的第十个年头，2005，Bruce A.Tate就著有《[Beyond Java](http://s.click.taobao.com/t?e=zGU34CA7K%2BPkqB07S4%2FK0CFcRfH0GoT805sipKkHXaAvoZfenKzcodoQUcRg9yhgj7iJMYIgKImrbSOZ59PmeAkDdomNxdOVcVj8btNExesR3g%3D%3D)》, 里面分析了Java从诞生到发展的过程，也指出了Java的危机和将来有可能会超越Java甚至替代Java地位的语言或技术。虽然里面的提到很多危机并没有影响到Java的实际发展，或者被Java解决掉了，或者不是什么危机。但随着Java的成长，我们在看到其成功的优势背后还仍然存在很多问题。我们有必要关注Java的发展动向，有必要关注新技术的成长。

到这，这篇文章写的已经不短了，“聊聊Java”就聊到此为止吧。这些内容都是本人想到哪写到哪，多而杂，有描述不对的地方，还希望指出，共同讨论共同进步，谢谢！

> [聊聊Java（零）](http://www.molotang.com/?p=51)
[聊聊Java（一）](http://www.molotang.com/?p=65)
[聊聊Java（二）](http://www.molotang.com/?p=106)
[聊聊Java（三）](http://www.molotang.com/?p=119)
