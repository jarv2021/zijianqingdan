#HTML

##1.从规范的角度理解HTML，从分类和语义的角度使用标签
参考资料：https://www.jianshu.com/p/1ee96def153c

##2.常用页面标签的默认样式、自带属性、不同浏览器的差异、处理浏览器兼容问题的方式

###常用页面标签的默认样式
参考资料：
https://www.cnblogs.com/madman-dong/p/5866286.html
https://www.cnblogs.com/chosen-man/p/6684674.html

###常用页面标签的自带属性
参考资料：
https://www.cnblogs.com/bahcelor/p/6510393.html

###不同浏览器的差异、处理浏览器兼容问题的方式
参考资料：
https://blog.csdn.net/weixin_38536027/article/details/79375411

##3.元信息类标签(head、title、meta)的使用目的和配置方法
参考资料：https://segmentfault.com/a/1190000019128577

##4.HTML5离线缓存原理
参考资料：http://www.ituring.com.cn/article/213932


#CSS

##1.CSS盒模型，在不同浏览器的差异
参考资料：https://blog.csdn.net/qq_37016928/article/details/79489293

##2.CSS所有选择器及其优先级、使用场景，哪些可以继承，如何运用at规则

###CSS所有选择器及其优先级
参考资料：https://www.cnblogs.com/czy960731/p/8527339.html

###CSS所有选择器的使用场景
参考资料：https://www.jianshu.com/p/c17e78a02f7a

###CSS选择器哪些可以继承

####CSS继承：继承就是子标签继承了上级标签的CSS样式的属性

css继承特性主要是指文本方面的继承，盒模型相关的属性基本没有继承特性。 

CSS哪些属性可以继承？ 

不可继承的： 
display、margin、border、padding、background、height、min-height、max-height、width、min-width、max-width、overflow、position、top、bottom、left、right、z-index、float、clear、 table-layout、vertical-align、page-break-after、page-bread-before和unicode-bidi。 
所有元素可继承的： 
visibility和cursor 
终极块级元素可继承的： 
text-indent和text-align 
内联元素可继承的： 
letter-spacing、word-spacing、white-space、line-height、color、font、font-family、font-size、font-style、font-variant、font-weight、text-decoration、text-transform、direction 
列表元素可继承的： 
list-style、list-style-type、list-style-position、list-style-image

注意：<a>标签有自己的颜色和样式，不会继承自父元素

####控制继承

CSS为处理继承提供了四种特殊的通用属性值：

inherit： 该值将应用到选定元素的属性值设置为与其父元素一样。
initial ：该值将应用到选定元素的属性值设置为与浏览器默认样式表中该元素设置的值一样。如果浏览器默认样式表中没有设置值，并且该属性是自然继承的，那么该属性值就被设置为 inherit。
unset：该值将属性重置为其自然值，即如果属性是自然继承的，那么它就表现得像 inherit，否则就是表现得像 initial。
revert：如果当前的节点没有应用任何样式，则将该属性恢复到它所拥有的值。换句话说，属性值被设置成自定义样式所定义的属性（如果被设置）， 否则属性值被设置成用户代理的默认样式。
注意: initial 和 unset 不被IE支持。

initial 是将属性的初始值( initial value)赋给元素 . initial 适用于所有的css 属性(属性的initial值可在属性表中查到)，包括css 简写属性(全局属性)all.

inherit 值是最有趣的——它允许我们显式地让一个元素从其父类继承一个属性值。

###CSS如何运用at规则

参考资料：https://www.cnblogs.com/theWayToAce/p/5291734.html

##3.CSS伪类和伪元素有哪些，它们的区别和实际应用

###伪类包含两种：状态伪类和结构性伪类。

状态伪类是基于元素当前状态进行选择的。在与用户的交互过程中元素的状态是动态变化的，因此该元素会根据其状态呈现不同的样式。当元素处于某状态时会呈现该样式，而进入另一状态后，该样式也会失去。常见的状态伪类主要包括：

:link 应用于未被访问过的链接；

:hover 应用于鼠标悬停到的元素；

:active 应用于被激活的元素；

:visited 应用于被访问过的链接，与:link互斥。

:focus 应用于拥有键盘输入焦点的元素。

结构性伪类是css3新增选择器，利用dom树进行元素过滤，通过文档结构的互相关系来匹配元素，能够减少class和id属性的定义，使文档结构更简洁。常见的包括：

:first-child 选择某个元素的第一个子元素；

:last-child 选择某个元素的最后一个子元素；

:nth-child() 选择某个元素的一个或多个特定的子元素；

:nth-last-child() 选择某个元素的一个或多个特定的子元素，从这个元素的最后一个子元素开始算；

:nth-of-type() 选择指定的元素；

:nth-last-of-type() 选择指定的元素，从元素的最后一个开始计算；

:first-of-type 选择一个上级元素下的第一个同类子元素；

:last-of-type 选择一个上级元素的最后一个同类子元素；

:only-child 选择的元素是它的父元素的唯一一个子元素；

:only-of-type 选择一个元素是它的上级元素的唯一一个相同类型的子元素；

:empty 选择的元素里面没有任何内容。

###伪元素

伪元素是对元素中的特定内容进行操作，而不是描述状态。它的操作层次比伪类更深一层，因此动态性比伪类低很多。
实际上，伪元素就是选取某些元素前面或后面这种普通选择器无法完成的工作。控制的内容和元素是相同的，
但它本身是基于元素的抽象，并不存在于文档结构中！常见的伪元素选择器包括：

:first-letter 选择元素文本的第一个字（母）。

:first-line 选择元素文本的第一行。

:before 在元素内容的最前面添加新内容。

:after 在元素内容的最后面添加新内容。

###注意事项

有时你会发现伪类元素使用了两个冒号 (::) 而不是一个冒号 (:)，这是 CSS3 规范中的一部分要求，目的是为了区分伪类和伪元素，
大多数浏览器都支持这两种表示方式。单冒号(:)用于 CSS3 伪类，双冒号(::)用于 CSS3 伪元素。对于 CSS2 中已经有的伪元素，
例如 :before，单冒号和双冒号的写法 ::before 作用是一样的。

所以，如果你的网站只需要兼容 webkit、firefox、opera 等浏览器，
建议对于伪元素采用双冒号的写法，如果不得不兼容 IE 浏览器，还是用 CSS2 的单冒号写法比较安全。

###CSS伪类和伪元素的实际应用

(1) 清除浮动
(2) 画分割线
(3) 计数器
(4) 增大点击热区

伪元素的本质是在不增加dom结构的基础上添加的一个元素，在用法上跟真正的dom无本质区别。普通元素能实现的效果，伪元素都可以。有些用伪元素效果更好，代码更精简。

##4.HTML文档流的排版规则，CSS几种定位的规则、定位参照物、对文档流的影响，如何选择最好的定位方式，雪碧图实现原理

###HTML文档流的排版规则
参考资料：https://segmentfault.com/a/1190000012425858

###CSS几种定位的规则、定位参照物、对文档流的影响，如何选择最好的定位方式
参考资料：https://www.cnblogs.com/iamhenanese/p/6965261.html

###雪碧图实现原理
参考资料：https://www.jianshu.com/p/84944af9ccca

##5.水平垂直居中的方案、可以实现6种以上并对比它们的优缺点
参考资料：https://www.cnblogs.com/kevin9103/p/5053575.html

##6.BFC实现原理，可以解决的问题，如何创建BFC
参考资料：https://www.cnblogs.com/lhb25/p/inside-block-formatting-ontext.html

##7.可使用CSS函数复用代码，实现特殊效果
参考css3新属性

##8.PostCSS、Sass、Less的异同，以及使用配置，至少掌握一种
PostCss：https://www.cnblogs.com/dll-ft/p/5811639.html
Sass：http://sass.bootcss.com/docs/sass-reference/
Less：http://lesscss.cn/

##9.CSS模块化方案、如何配置按需加载、如何防止CSS阻塞渲染
CSS模块化方案：https://www.cnblogs.com/samwu/p/5465115.html
如何配置按需加载：https://www.cnblogs.com/skylor/p/7008756.html
如何防止CSS阻塞渲染:https://www.cnblogs.com/goloving/p/9286521.html

##10.熟练使用CSS实现常见动画，如渐变、移动、旋转、缩放等等
参考资料：https://daneden.github.io/animate.css/

##11.CSS浏览器兼容性写法，了解不同API在不同浏览器下的兼容性情况
参考资料：https://www.cnblogs.com/Jener/p/5878729.html
进阶：见8.PostCSS、Sass、Less的异同，以及使用配置，至少掌握一种

##12.掌握一套完整的响应式布局方案
参考资料：https://www.cnblogs.com/zdz8207/p/bootsrtap-HybridApp-ReactNative.html


