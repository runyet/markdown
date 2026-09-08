# iOS 上架/审核 4.3a全面解读-最新

<p>&nbsp;</p>

<p>目前审核随AI 编写代码成熟, 大量外行人涌入开发App.&nbsp; 苹果审核量暴增.据说苹果每周大约有<span style="color:#e74c3c;">20万</span>个 App提交, 并且借助AI来帮助审核</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>由于挤压的太多, 无论是谁来审核, 这么大的工作量, 根本保证不了审核质量, 有些App侥幸过审,&nbsp; 有些实打实开发的App反而大量被拒5.6 , 看来是AI环节进行了风控, 但是误伤了很多无辜开发者<img alt="" height="213" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/1ca47bf6640cacd14e32e0e34e88b75e.png" style="max-width: 100%; height: auto; display: block;" width="243"></p>

<p>&nbsp;</p>

<p><img alt="" height="171" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/7860f39745373c2c23bd35ec343f2bb9.png" style="max-width: 100%; height: auto; display: block;" width="241"></p>

<p>我们这篇文章先不去介绍如何解决5.6问题,&nbsp; 我们先还是只关注4.3a问题, 之前我写了大量的关于4.3a的文章,大部分含有"柏芝科技"的公司名 其实都是我手动写的文章 , 也帮助了不少开发者提供思路和方向.</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<h1>进入正题&nbsp; Guideline 4.3(a) - Design - Spam</h1>

<p>&nbsp;</p>

<p>我们之前提到过, 不同语言开发的App 遇到的4.3 原因不同, 要找到根本原因, 你才能一次性解决4.3a问题, 否则你都是在瞎猫碰死耗子, 乱改一通, 这个版本过了, 下个版本又4.3a , 或者这个App奏效, 下一个App失效的情况</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>目前以我的了解 大概有8种主流语言能开发iOS App.&nbsp; 如果你恰好使用这种语言开发的, 你要仔细看, 几年来我个人给公司解决4.3a 案例高达1000例, 一次性解决4.3a 成功率95%.&nbsp; 这是真实数据, 没有夸张的成分</p>

<p>&nbsp;</p>

<p>目前主流的语言有(包含框架)&nbsp; oc, swift , uniapp , flutter,&nbsp; rn,&nbsp; unity, laya, cocos. 也差不多就这几种了.&nbsp;</p>

<p>&nbsp;</p>

<p>无论是你oc 开发的, 或者swift ,或是uniapp , 一定要搞清楚一个前提, 你的语言是一种什么类型的语言,&nbsp; 是解释型, 还是编译型?&nbsp; 什么是编译型?&nbsp; 这俩有什么本质区别, 你要记住,我们分析的是iOS上架, 一定要分析编译产物, 而不是编译过程</p>

<p>&nbsp;</p>

<p>我可以直接给出答案, 编译型的语言会产生符号, 二符号就是苹果判定4.3a的重要指标之一</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>1: 你写的oc代码&nbsp; &nbsp;basemodel * model = [basemodel alloc]init&nbsp; &nbsp;编译后到底是什么? 编译到哪里去了?&nbsp;</p>

<p>2: 你写的js 代码编译后 到哪去了? 进入二进制了? 还是被整合成一个文件类型?&nbsp;</p>

<p>3: 你的dart代码翻新了一个遍?&nbsp; 最后影响了谁?&nbsp;&nbsp;</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p>这也许是你重构或者翻新后的App, 你自认为你的代码变化极大,&nbsp; 但是检测后,相似度极高,当然这要一步步分析, 任何一个原工程, 或者App, 不可能只通过一个混淆工具混淆一下子 就完事了, 纯属是自欺欺人, 卖混淆工具的自己都没上架过几个App, 你成了他们的测试客户</p>

<p><img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/7cd9fe5d46882fe6d14a37d69381295f.png" style="max-width: 100%; height: auto; display: block;"></p>

<h1>1: oc &amp;swift&nbsp;</h1>

<p>&nbsp;</p>

<p>因为oc和swift 都是编译型语言, 我们统一放到一起讲解.&nbsp; 有过一定经验的开发者,一定会有一种感觉,&nbsp; 使用原生开发的App遇到4.3的概率会更低,&nbsp; &nbsp;这是因为oc和swift 编译后产生大量原创符号, 以至于你在苹果机审提取App特征对比的时候, 不会和其他App的特征重复 .</p>

<p>&nbsp;</p>

<p>但是也有缺点, 原生开发的App做马甲包的难度较大,&nbsp; 正是因为产生了大量符号, 你需要将所有的符号变更</p>

<p>也就是说&nbsp; &nbsp;aaaa 变更成bbbb , 那么无论是你混淆原工程的角度, 还是直接通过修改二进制(加固)的角度, 都稍显复杂,&nbsp; 混淆必然会产生编译报错, <span style="color:#e74c3c;">加固遇到更多的问题就是闪退, 我们的加固技术是非常成熟的,有时间我单独出一个加固原理讲解</span></p>

<p>&nbsp;</p>

<h1>2: uniapp&nbsp;</h1>

<p>&nbsp;</p>

<p>我在对接企业的时候, uniapp是所有语言中触发4.3a概率最高的,&nbsp; 那么你要思考一个问题:&nbsp;<br>
<br>
为什么各个企业都写自己的代码 , 都是自己开发的,&nbsp; 为什么会这么大量的报4.3a?&nbsp;<br>
<br>
我这里直接给出答案, 因为你写的vue代码不会产生符号, <span style="color:#e74c3c;">苹果从你的代码中提取不到符号</span></p>

<p>&nbsp;</p>

<h1>提取不到符号, 为什么会报4.3a?&nbsp; 别忘了 uniapp框架却是用原生开发的,&nbsp; 你是否已经猜到答案了?&nbsp;<br>
<br>
没错, uniapp 的4.3a问题就是框架导致</h1>

<p>&nbsp;</p>

<p>我们来看一组数据库对比:&nbsp;</p>

<p><img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/fd439ef299aa6719f098aa50463654df.png" style="max-width: 100%; height: auto; display: block;"><br>
<img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/7cb453c3d37818d107772c0765186499.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>这无疑是大量的重复, 重复代码几乎高达80%左右,主要框架重复是<b>DCUniBase ,DCloudUTSExtAPI ,DCloudUTSFoundation, 当然还有uniapp-x, 重复会不一样</b></p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<h1>那么如何解决?&nbsp;</h1>

<p>这里我需要说明一下, 并不是所有uniapp 都会被拒,&nbsp; 审核会根据App类型以及精美度综合判定, 也就是说前两个达标了, 你仍然可以在代码高重复下过审,&nbsp; 这就是为什么有的uniapp可以过, 有的报4.3a的根本原因, 但是被拒4.3a仍占多数</p>

<p>&nbsp;</p>

<p>如何解决? 你要知道uniapp框架是没有源码的, 怎么办?&nbsp; 这里我不得不又提到一个词语"加固",&nbsp; 目前解决uniapp 4.3a最好的方式还是加固, 直接处理二进制, 因为本身没有源码.</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<h1>3: cocos</h1>

<p>&nbsp;</p>

<p>cocos 触发4.3的概率几乎和uniapp持平, 但是解决起来比uniapp难度大很多, 几乎是地域级别难度.&nbsp;</p>

<p>&nbsp;</p>

<h1>为什么这么说?&nbsp;</h1>

<p>&nbsp;</p>

<p>我们首先还是需要找到为什么cocos 也会大量的触发4.3a, 明明也是开发者手动一点点敲出来的代码</p>

<p>&nbsp;</p>

<p>因为cocos 项目是用 ts编写,&nbsp; 最后转成js ,&nbsp; js 属于解释型语言, 不会产生符号, 你懂了么?&nbsp; &nbsp;</p>

<p>重点来了,&nbsp; cocos 有一个非常大的引擎被编译到二进制中, 这个引擎是c++写的,这就是重复的原因,&nbsp; c++这种语言和oc以及siwft又有较大不同, 编译后符号都被优化了.</p>

<p>我们来看一下引擎大小:<br>
<br>
cocos3<br>
<br>
一个cocos3 引擎最小也有23m左右 , 这个示例几乎是最小引擎大小<br>
<img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/22ca7f4ab4ee8104e3402f580ddff136.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>&nbsp;</p>

<p>cocos2:<br>
<br>
<img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/671d8a07640a0ff987aabe612be0bd99.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>虽然比cocos3小了很多, 但是15m的引擎仍然一个非常高的重复</p>

<p>&nbsp;</p>

<p>能不能用像uniapp直接使用加固 来处理, 我来告诉你:不能&nbsp;</p>

<p>&nbsp;</p>

<h1>为什么?</h1>

<p>遇到4.3a就找柏芝科技&nbsp; www.appstore.love</p>
