# iOS 解决 4.3a【二进制加固】

<p><span style="color:#000000">​</span></p>

<h3>我们应该知道,面对iOS 上架 遇到4.3a的问题或者制作马甲包.最基础的操作就是混淆代码</h3>

<p>&nbsp;</p>

<p>尤其是我们专业做上架的,需要对各种语言的编译模式,产物,以及ipa构成都需要非常了解, 每种语言开发的App的编译产物不同,针对不同的编译产物做不同的处理方式</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<h2>有一些经验的开发者, 应该了解目前的混淆方式大概分为三种</h2>

<h1><br>
1: 源代码混淆</h1>

<p>顾名思义, 就是通过处理源代码,让代码达到翻新的效果, 比如修改一些静态特征,代码结构</p>

<p>难度: &nbsp;低</p>

<p>优点: 效率高,限制低</p>

<p>缺点:</p>

<p>1: 难以维护最难级别, &nbsp;源代码改动之后,难以辨别, 对维护多个项目造成非常大的工作量</p>

<p>2: 需要针对各种语言分别开发,比如当前开发iOS的app 的语言有iOS , swift, c++, 需要针对各种不同的语言开发不同的混淆工具, 这个工作量太大, 能够开发iOS的app 的语言高达十几种, 制作十几种语言的混淆工具 根本不现实</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<h1>2: 编译器混淆</h1>

<p>这种混淆方式不需要处理源代码, 直接通过xcode在编译时混淆,也就是在xcode将源代码编译成.o的时机接入混淆,替换符号</p>

<p>难度: 中</p>

<p>优点: 不需要改动源代码, 不涉及到维护难度,不区分语言, 可混淆各种语言的代码</p>

<p>缺点:</p>

<p>1: 处理范围小, 只能对一些符号进行替换, 比如你想改变一些代码结构, 这个基本无法实现.<br>
2: 能力有限,比如一些静态库在xcode编译前就已经被编译好, 所有静态库无法替换符号 ,也就是说他只能处理编译列表的文件<br>
<img alt="" data-widget="image" height="274" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/ccd5ab94e0f39d5f56c06e7726c5d463.png" width="531"><br>
&nbsp;</p>

<p>3: 替换符号可能会造成闪退,因为有些访问是通过kvc来完成的,如果符号被替换了, kvc还是使用原来的字符串去访问就会造成闪退或者功能异常</p>

<p>&nbsp;</p>

<h1>3: 直接修改二进制-加固</h1>

<p>你是否听到了熟悉的词语-"加固", 我们这行把直接修改二进制的方法喜欢叫成" 加固", 直接修改二进制,达到混淆的效果,也就是说我们直接最终编译的ipa中的可执行文件</p>

<p>&nbsp;</p>

<p>举个例子, 比如我们正在考试.</p>

<p>1: 修改源代码的方式相当于,你勤勤恳恳的学习,然后提交试卷后,等待老师审查<br>
2: 编译器的方式相当于, 你在考试的提交试卷的时候替换了别人的考卷,等到老师审查</p>

<p>3: iOS加固的方式相当于,&nbsp;直接修改考试分数<br>
&nbsp;</p>

<h1>我们简单的了解加固的概念后,进入正题:</h1>

<p>难度指数:满级</p>

<p>优点:非常多,不需要关注源代码,不需要打开xcode,&nbsp;你只需要给我一个ipa, 我返回给你一个ipa</p>

<p>&nbsp;</p>

<p>我们先简单了解什么是二级制:&nbsp;</p>

<p>我们通过拆解ipa, 你往往会看到一个黑色的小盒子, 这就是一个可执行文件 ,我们简称二进制,当然这个文件不能直接打开或者双击执行</p>

<p><br>
<img alt="" data-widget="image" height="285" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/e5c426bb106e3314421c81b015b4bebc.png" width="417"></p>

<p>&nbsp;</p>

<h1>这个可执行文件的大小, 往往取决于你的代码量, 代码量越大, 这个文件越大,这个里面是什么东西呢?&nbsp;<br>
<br>
<br>
机器码</h1>

<p>没错这个二进制里面全是机器码,我们使用xxd命令查看最原始的内容<br>
<img alt="" data-widget="image" height="462" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/fa46bf1ce28878367550693f148e74d7.png" width="398"></p>

<p>没错这个就是二进制的最原始的内容,但是这种机器码我们根本无法阅读,&nbsp;</p>

<p>&nbsp;</p>

<h1>汇编代码</h1>

<p>&nbsp;</p>

<p>这些原始的机器码（十六进制字节）<strong>正是由汇编代码（Assembly Code）转换（“汇编”）而来的</strong>。这个转换过程由<strong>汇编器（Assembler）</strong>&nbsp;完成。</p>

<p>我们使用otool -tV 命令进行反汇编查看内容</p>

<p><br>
<img alt="" data-widget="image" height="525" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/0deeaf86a0e20a61a64cf09208f051e1.png" width="687"></p>

<p>是不是发现了一些带语义的符号了? &nbsp;但是仍然难以阅读, 我们来翻编译更高级的语言<br>
<br>
&nbsp;</p>

<h1><br>
高级语言</h1>

<p>反编译的目标是将机器码/汇编代码转换回更抽象、可读性更高的<strong>伪代码, 还需要一个解析的过程,不同语言所在二进制的位置不同, &nbsp;解析方式也不同,这里不过多介绍, 我们直接来看解析后的结果</strong></p>

<p>&nbsp;</p>

<p><img alt="" data-widget="image" height="738" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/b861dc2eb2de2e096bb694c03b720192.png" width="902"></p>

<p>&nbsp;</p>

<h1>这个是不是就是你最熟悉的oc代码了?&nbsp;<br>
<br>
它们的层级关系是：</h1>

<h5><br>
<strong>高级语言 (C/C++/Swift) -&gt; 编译器 -&gt; 汇编代码 (Assembly) -&gt; 汇编器 -&gt; 机器码 (Machine Code)</strong></h5>

<p>&nbsp;</p>

<p>我们继续关注二进制里面的结构,看看它内部是怎么划分的, 我们使用size-m 查看二进制的概览情况</p>

<p>&nbsp;</p>

<p><img alt="" data-widget="image" height="657" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/ef1ac566ea3fd9102e6e351ad6e8c317.png" width="595"></p>

<p>&nbsp;</p>

<p>我们发现内容非常多, 非常乱, 不过像我看多了就习惯了, 大致就是分为几个段, 段里面又被分成了各种小的节<br>
&nbsp;</p>

<p>&nbsp;</p>

<h1>三大段</h1>

<p>1:&nbsp;__LINKEDIT (符号表主要存放位置)</p>

<p>2:&nbsp;__TEXT (代码主要存放位置)</p>

<p>3:&nbsp;__DATA (静态变量主要存放位置)</p>

<p>&nbsp;</p>

<p>我们发现text段中的text节 占据了主要的体积 , 没错, 这就是你的源代码主要存放的位置, 我们加固重点就是处理这个text节&nbsp;<br>
<br>
<img alt="" data-widget="image" height="208" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/bbf1229d3baf504ba52a0ebcb6319ec6.png" width="538"></p>

<p>&nbsp;</p>

<h1>我们来直接展示加固成果:&nbsp;</h1>

<h1><br>
<img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/242fb506875b8c8a157b31ae7c5be61b.png" style="max-width: 100%; height: auto; display: block;"></h1>

<p><strong>我们可以选择一个二进制或者多选:</strong></p>

<p>&nbsp;</p>

<p><img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/efd2ebe14b51c070a7e7c74802beda03.png" style="max-width: 100%; height: auto; display: block;"></p>

<p><span style="color:#000000"><strong>​开始加固</strong></span><br>
<img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/efe9ecdc4178261d94a3fa6ef6f0eeb1.png" style="max-width: 100%; height: auto; display: block;"></p>

<h1>我们来检测加固后的ipa和之前的ipa的代码差异:</h1>

<p><img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/c696a3a4413aedd8fff47ef11d3e03cc.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>我们可以看到主二进制和动态库差异非常明显, 变化非常大, 但是这里我们没有处理资源文件.&nbsp;</p>

<p>&nbsp;</p>

<p>我再说一下加固的适用范围:&nbsp;<br>
<br>
1: 如果你的二进制或者动态库使用oc或者swift原生编写的, 加固非常适用, 但是如果代码大部分由c++编写, 加固效果非常差, 因为c++的编译后会优化掉大部分符号, 导致我们找不到能处理的符号</p>

<p>2: 加固后可能会对App功能或者业务造成影响, 较为严重会闪退, 需要全面测试,然后修复, 再测试, 而不是加固之后万事大吉</p>

<p>3: 但是加固的有非常多, 你甚至不需要修改一行源代码,&nbsp; &nbsp;当前也可以处理一些没有源码的三方库. 这是任何一种混淆方案都做不到的</p>

<p>&nbsp;</p>

<p>遇到4.3就找 柏芝科技,全国顶尖<img alt="" height="362" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/565e251b95c92b132e1eaafb63b3f7a1.png" style="max-width: 100%; height: auto; display: block;" width="598"></p>
