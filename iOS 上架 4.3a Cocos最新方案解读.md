# iOS 上架 4.3a Cocos最新方案解读

<h2>很多开发者都会在iOS 上架遇到4.3(a) ,&nbsp; &nbsp;当然开发者可能使用不同的语言开发自己的App.&nbsp;</h2>

<p>&nbsp;</p>

<p><strong>比如 uniapp, flutter,&nbsp; oc, swift ,&nbsp; unity&nbsp; , laya , rn 等等层出不穷</strong></p>

<p>&nbsp;</p>

<p>这是因为苹果没有限制开发者使用什么语言 去开发他的app, 但是苹果审核的标准却是相同的,&nbsp; &nbsp;也就是说他不会因为你是什么语言开发的App, 给与不同的审核标准.&nbsp; &nbsp;</p>

<p>&nbsp;</p>

<p>在我们专业处理4.3a的过程中, 我们会发现哪些语言触发4.3a的概率比较高, 从而更精准的预测苹果是如何审核的.</p>

<p>&nbsp;</p>

<h3>那么请注意,&nbsp; 这将是你过往, 现在, 以及未来几年看到的关于cocos 上架4.3a问题的<span style="color:#e74c3c;">一篇极具价值的文章. 这是你在任何AI模型中都找不到的答案</span></h3>

<p>&nbsp;</p>

<p>我们将从问题的产生,&nbsp; 问题如何解决 , 来一一讲解</p>

<h1>&nbsp;</h1>

<h1><span style="color:#e74c3c;">问题1:&nbsp;为什么cocos触发4.3a的概率最高 ?</span></h1>

<h1>&nbsp;</h1>

<p>我凭什么说cocos触发4.3a的概率最高? 这正是因为我是专业处理4.3a的, 在客户的大量4.3a案例中, 我们能几乎给出一种语言触发的4.3a 粗略的概率<br>
&nbsp;</p>

<h3>我简单做一个常用语种的排序<br>
<br>
最高:&nbsp; cocos&nbsp; uniapp&nbsp;</h3>

<p>较高 : unity ,flutter</p>

<p>较低: oc , swift&nbsp; .</p>

<p>当然还有一些其他的语言使用的较少, 我们暂时不做排序</p>

<h1>&nbsp;</h1>

<h3>为什么最高的是cocos 和uniapp&nbsp; ?&nbsp;</h3>

<p>两个核心原因</p>

<p>1: 你会发现这两种使用&nbsp; ts&nbsp; 和 vue (这是一个框架, 开发者本身使用js) 开发他们的app . 这两种语言有什么共性?&nbsp;<br>
<br>
解释型语言 ,不会产生符号<br>
&nbsp;</p>

<p>2: 引擎 ,&nbsp; cocos 开发的App 都会集成cocos 默认的引擎, 可能是cocos2d , 或者cocos3 , 引擎本身由C++ 开发,&nbsp; 一个特点, 引擎非常大,&nbsp; &nbsp;cocos2的基础引擎编译后的二进制可以达到15M,&nbsp; &nbsp;cocos3 的基础引擎默认能达到可怕的23M,&nbsp; &nbsp;3比 2&nbsp; 更大</p>

<p><img alt="" height="222" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/eb0d9b229a2e1ae7d570034f21bfe910.png" style="max-width: 100%; height: auto; display: block;" width="350"></p>

<p>&nbsp;</p>

<p><img alt="" height="230" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/51b1b6abae18042c7fe59adb8adbfca2.png" style="max-width: 100%; height: auto; display: block;" width="347"></p>

<p>那么正因为连点结合起来,&nbsp; ts代码不产生符号,&nbsp; 加默认引擎造就了cocos 4.3a概率稳居所有语言第一 (uniapp本篇不讲述)</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<h1><span style="color:#e74c3c;">问题2: 那岂不是所有cocos都不能上架?</span></h1>

<p>并不是所有cocos 都会被拒4.3a, 这个时候你的App类型 起到了很大的作用.&nbsp; &nbsp;因为你要知道, 苹果判定4.3a的标准不只是代码一个维度, 受App类型,质量, 精美度多重影响,&nbsp;</p>

<p>&nbsp;</p>

<p>情况一:&nbsp; 如果你的App类型是一个研发火箭的,&nbsp; 和另一个棋牌类App 具有非常高的代码重复,&nbsp; 因为类型差距非常大,&nbsp; 或者类型非常冷门, 市面上你这种类型几乎没有 ,那么你有可能不受代码重复影响</p>

<p>&nbsp;</p>

<p>情况二:&nbsp; 如果你的App类型非常普遍, 比如是一个棋牌类的cocosApp,&nbsp; 并且和其他棋牌App具有非常高的代码重复,&nbsp; 但是如果你的App制作极其精美, 玩法非常新颖, 那么苹果可能直接忽略你的代码重复 , 因为苹果的4.3a条例的本身就是为了控制App数量和质量, 如果你的App质量过关, 你可以无视代码重复</p>

<p>&nbsp;</p>

<p>情况三: 如果你的App 即是 大众棋牌类型,&nbsp; 又没什么新颖玩法,&nbsp; 又这么高的代码重复 . 那么你无疑是一个4.3a打回 , 这就是为什么&nbsp; 往往ab面的马甲包 过审更容易的原因.&nbsp;</p>

<p>&nbsp;</p>

<p><span style="color:#e74c3c;">很多开发者不明白问题的根本原因, 一直执着的修改ts代码,&nbsp; 甚至把ts代码全部翻新依然没有任何效果, 最后账号无情被封.&nbsp;&nbsp;</span></p>

<h1><br>
<span style="color:#e74c3c;">问题三: 那么如何解决?&nbsp;</span></h1>

<p>&nbsp;</p>

<p>我们既然找到了是引擎的问题, 我们还是要从引擎出发 ,&nbsp; 看到了这里, 你是否学到了一些?&nbsp; 我考你一个问题</p>

<p><span style="color:#e74c3c;">unity 也是默认嵌入一个引擎, 而且更大, 为什么要比cocos 触发4.3a的概率低很多?&nbsp; 不懂的可以加我 v: xsooop 哦&nbsp;</span></p>

<p><br>
下面我们来说如何解决: 我们既然找到了是引擎的问题, 我们还是要从引擎出发</p>

<h1><br>
Cocos的引擎是c++开发的. 我们是否能混淆引擎?&nbsp;</h1>

<p>&nbsp;</p>

<p>理论上可以,但不推荐. 而且效果差,&nbsp; 了解过c++的, 你应该知道c++全是结构体. 编译后的二进制符号被优化很多 .&nbsp;&nbsp;</p>

<p>也就是说即便是你混淆了整个引擎,&nbsp; 你的符号整体变化不明显,效果非常差 , 而且c++的代码构建的引擎 又和 js 端 搞了一大堆契约, 非常容易把引擎搞坏</p>

<p>&nbsp;</p>

<h1>&nbsp;</h1>

<h1>我们是否能把引擎重构?&nbsp;</h1>

<p>可以, 但这几乎超出了所有开发者的能力, 以及所有AI模型的能力,&nbsp; 这不是你自己或者简单借助AI就能做到的 ,而且这不是你应该做的事,&nbsp; 这是我需要做的</p>

<p>&nbsp;</p>

<p>来看看我重构的cocos2d 引擎, 从15m 精简至6M&nbsp;</p>

<p><img alt="" height="258" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/ae97b431de36401598b4cd348bf4f95d.png" style="max-width: 100%; height: auto; display: block;" width="546"></p>

<p>&nbsp;</p>

<p>这是精简的cocos3引擎, 从23m 精简至 15M<br>
<br>
<img alt="" height="326" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/eb0d9b229a2e1ae7d570034f21bfe910.png" style="max-width: 100%; height: auto; display: block;" width="515"></p>

<p>这是我的重构的引擎生成简洁的xcode目录, 非常干净整洁,<br>
<img alt="" loading="eager" src="https://baizhi-1318151832.cos.ap-shanghai.myqcloud.com/images/cfb902e985d4b9f89c924e48908f4af5.png" style="max-width: 100%; height: auto; display: block;"></p>

<p>cocos上架遇到4.3a就找柏芝 www.appstore.love</p>
