# iOS   审核  4.3a 最新解读2026

<p>近几年来, 我一直为客户处理iOS 上架4.3a问题 , 几乎已经合作的企业达到了1000家,&nbsp; 大部分企业的4.3a问题解决起来是比较快速顺利的,我们一次性解决4.3a的客户成功率 高达90%以上,&nbsp; 那么也有二轮处理三轮处理的, 几乎100%的客户4.3a问题最后都能被解决 , 只不过是时间长短的问题</p>

<p>&nbsp;</p>

<p>我在钻研iOS 4.3a审核问题, 已经到了白热化阶段, 似乎每一个案例, 每一条线索, 我都会深入研究.&nbsp; 有些解决过程中不太顺利的APP, 也会让我深深陷入思考, 不会盲目的提审</p>

<p>&nbsp;</p>

<p>网上有大量的关于我的 4.3a的文章,&nbsp; 都是我手动一个个字打出来的, 并非参考或者借鉴任何其他人的想法或者是建议, 因为我在这个领域已深耕多年, 以 ipa 相似度对比技术 , 二进制加固技术 为主要核心工具, 帮助客户解决4.3a问题</p>

<p><img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/f5893d5222ecce50cf961d6a48a845e4.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>不断地探索&nbsp; 不断地验证, 不断地优化, 最终得以商业化使用</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>IPA相似度对比工具是我在给客户解决4.3a问题的一个重磅工具,&nbsp; 为什么要使用到这个脚本,&nbsp; 要归根于你的IPA 上传到AppStore后经历了一个怎样的历程&nbsp; , 也就是说, 你必须弄清楚,苹果到底是如何审核的,你才能更好的精准的解决这个问题</p>

<p>&nbsp;</p>

<h1>1: IPA上传到AppStore经历了什么?&nbsp;</h1>

<p>&nbsp;</p>

<p>这个问题也会帮助你了解等待审核和正在审核, 请仔细阅读,&nbsp; IPA提交之后我们都知道, APP进入"等待审核状态",&nbsp; 这个状态苹果做了什么?&nbsp;<br>
<br>
我可以告诉你 这个状态就是ipa 进入机审队列,&nbsp; 而不是正在审核状态才进入机审.&nbsp; IPA提交之后并不是立马进入机审, 而且排队,&nbsp; 也就是说机审是一个长长的队伍, 你进入后要排队.</p>

<p>&nbsp;</p>

<p>也就是说在"等待审核状态"的这个过程中, 你的IPA 可能随时进入机审, 那么机审整个过程不会太久, 这个机审的时间取决于, 苹果全球的AppStore 数量,&nbsp; 当然包括&nbsp; 已经上架的,&nbsp; 下架的, 被封的,&nbsp; 提交过被拒4.3的,&nbsp; 也就是说苹果的对比量非常大,&nbsp; 我们来看一组数据<br>
<img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/14c66eaf208ad0a6ebb5708e20b25aa2.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>&nbsp;</p>

<p>一年的提交量几乎达到了千万级别, 比如对比一个app 的时间为1s ,&nbsp; 算一下</p>

<p>1000 万秒 ≈ 115.7 天 ≈ 3.9 个月（约 2778 小时）</p>

<p>也就是说, 你的ipa 机审 要在3.9月才能完成, 那么这显然是不现实的&nbsp; ,&nbsp; 1秒时间可能太长 , 苹果应该有一个快速对比的方式,&nbsp; 以及并发的一些算法优化, 可以把机审维持在小时级别, 或者是分钟级 ,我们只需要他要进行全量对比</p>

<p>&nbsp;</p>

<p>那么对比后就代表机审结束了 , 那么你会不会直接进入"正在审核"?&nbsp; &nbsp; 并不会, 机审对比完之后, 属于一种准备的状态, 你仍在下一阶段的队列中,&nbsp; 什么时候人工审核空余了, 那么你的app 进入到人工审核阶段, 这个时候你的App状态就会变更为"正在审核" .</p>

<p>&nbsp;</p>

<p>那么类似于银行办业务,&nbsp; 人工一直在窗口, 什么时候到你了, 叫号, 你在过去, 就属于正在办理</p>

<p>&nbsp;</p>

<p><img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/aeb130cc6e83f5279c6444190f8bae43.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>&nbsp;</p>

<p>人工审核的时候, 必然会直接拿着机审报告, 作为审核依据,&nbsp; 比如机审报告结果显示你的App 和众多APP代码重复极高,&nbsp; 那么你不一定被拒4.3a, 他首先要看是否是同一种类型, 功能是否雷同, 以及UI 体验是否毫无差别,&nbsp; 如果代码重复较高, 但是类型差距很大,&nbsp; 你并不会命中4.3a,&nbsp; 那么返回来, 代码重复很高, 类型也相同, 功能大差不差,&nbsp; 你无疑就是一个4.3a打回.&nbsp;&nbsp;</p>

<p>&nbsp;</p>

<p>当然目前APP提审量极大, 机审报告中如果太多的代码重复, 人工甚至可能不会打开你的App仔细查阅, 而是反手一个秒拒. 这就是你的4.3a 为什么会秒拒的情景再现</p>

<p>&nbsp;</p>

<p>那么这也是为什么ab 包在代码重复的情况下, 为什么更容易过审, 因为ab包的a面 往往制作的比较冷门, 和查出来的重复app类型差距较大</p>

<p>&nbsp;</p>

<h1>这就是你的App由提审到被拒的全过程, 接下来我们讲一下专业知识:二进制</h1>

<p>&nbsp;</p>

<p><img alt="" height="372" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/40ab461cb06be1ed86b9c4161a66f0ce.png" style="max-width: 100%; height: auto; display: block;" width="565"></p>

<h3>要记住, 二进制永远是你解决代码重复的核心目标, 如果你的代码改的天翻地覆, 但是二级制变化不大,&nbsp; 你的修改就属于无效修改,&nbsp; 无用功</h3>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>当然能够开发iOS的语言或者说是框架众多, 比如flutter , uniapp , oc, swift , rn , cocos, unity, laya , 虽然苹果不限制开发者使用什么样的语言开发,&nbsp; 但是他们的检测标准都是相同的,&nbsp; 不会因为用什么语言而采取不同的查重机制</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>二级制里面到底有什么, 我们来逆向解析一下</p>

<p><img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/c75e116bb98a7efd2cd3daebefbb776c.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>&nbsp;</p>

<p>我们来看一个常规的二进制有三大段, _TEXT, _DATA,__LINKEDIT,段中还有一些节,&nbsp; 比如__objc_classname,__objc_methname, 看到这两个节,开发者应该比较熟悉, 因为你的很多符号都会被编译到这个节中,&nbsp; &nbsp;而_text存放的是机器码,&nbsp; 他们分工明确,&nbsp; 存储分明,&nbsp;它们不是互相“调用”，而是：代码在&nbsp;<code>__text</code>&nbsp;里跑，查类/发消息时去引用另外两个节里的字符串。</p>

<p>&nbsp;</p>

<p>我们不必研究二进制的运行原理, 只需要简单了解一下构造, 你在做代码混淆的时候必须让__objc_classname和__objc_methname发生变化,&nbsp; 否则都是无效改动<br>
<br>
<br>
这就解释了为什么uniapp 开发的APP 4.3后, 如论怎么修改vue代码都无效?&nbsp; 为什么cocos开发的应用 4.3后, 无论怎么修改ts或者js 都解决不了?&nbsp; &nbsp;因为他根本没有让符号节 发生变化<br>
&nbsp;</p>

<p><span style="color:#e74c3c;">当然还有一个重要的节__cstring ,&nbsp; </span>这个我们本期不予介绍, 这个节的内容也是主要查重对象, 因为里面有大量的开发者自定义符号</p>

<h1>&nbsp;</h1>

<h1>我们来看一个特殊的二进制<img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/e31bfc2915fc8808d096901120761043.png" style="max-width: 100%; height: auto; display: block;"></h1>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>这个二进制中含有一些其他二进制没有的节__rodata,__gopclntab以及__rodata,&nbsp; 而且存储的数据很大, 真实达到十几兆, 同样也会触发苹果的4.3a条例,&nbsp; &nbsp;这个线索说明了一个问题,&nbsp; 苹果不是对某一个固定的节, 进行检测,&nbsp; &nbsp;很有可能扫描所有节, 或者所有含有内容的节</p>

<p>那么这是一个vpn 的主流使用的go框架, 导致了这个二进制包含了很多go开头的节,如果你的节中含有和其他app 重复的内容, 那么就会触发了4.3a</p>

<p>&nbsp;</p>

<p>也就是说, 你必须知道的代码被编译到哪里 , 这是一个非常重要的问题</p>

<p>&nbsp;</p>

<h1>说了这么多如何解决?</h1>

<p><br>
不要一门的着急如何解决,&nbsp; 你首先要找到问题产生的原因, 你才能更好的思考如何解决</p>

<p>&nbsp;</p>

<p>遇到4.3a就找柏芝科技https://www.appstore.love</p>

<p>&nbsp;</p>
