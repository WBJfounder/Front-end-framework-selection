# 前端框架（vue angular react之间的选择与优劣）

## angularJs
- angularJs是一款优秀的前端JS框架，被作用于很多产品当中，维护者颇多。
- angularJs的特性如下：
1. MVC
2. 双向数据绑定
3. 指令(Directive)
4. HTML模板
5. 依赖注入
- 优点：
1. 模板强大的angular指令
2. 简易的双向数据流进行数据绑定
3. 比jq更加灵活地自定义指令(Directive)
4. 依赖注入使测试简单轻松降低代码逻辑复杂度
- 缺点
1. angularJs的重！这就是一些新手和培训的学生还有一些未接触过的人说的重中之重，其实他的原因很简单，也就是因为他的功能强大，框架设计之初都是为了开发者的开发效率，封装了大量的功能性代码，优点中的指令啊还有动画路由什么的，虽然在1.2版本之后抽离了动画还有路由什么的，但本身集成的功能还是造成人们所述的框架过重，所以说人无完人框架也是一样，所以选择的优劣自己斟酌。

2. 性能上，angular依赖对数据的脏检查。那么脏检查又是什么？对于看过我github中专门写angular文章的应该知道，不知道的我简单说下（脏检查其实就是，将原有的对象复制一份，在特定时间，比较于备份的值，这样就要求了俩份数据的遍历所以会造成性能上的浪费。)
* 多说一嘴（关于脏检查机制）
1. 只有当对象被绑定到HTML之后才会添加为检查对象（watcher）
2. 只有当属性被绑定后，这个属性才会被列为检查属性    
> 注意：先知道下浏览器渲染DOM的过程    
1.  浏览器的事件回路一直等待着事件的触发，事件包括用户的交互操作、定时事件或者网络事件（如服务器的响应等）；
2.  一旦有事件触发，就会进入到Javascript的context中，一般通过回调函数来修改DOM；
3.  等到回调函数执行完毕之后，浏览器又根据新的DOM来渲染新的页面。
> 注意: angular的渲染机制    
>  AngularJS修改了一般的Javascript工作流，并且提供了它自己的事件处理机制。这样就把Javascript的context分隔成两部分，一部分是原生的Javascript的context，另一部分是AngularJS的context。只有处在AngularJS的context中的操作才能享受到Angular的data-binding、exception handling、property watching等服务，但是对于外来者（如原生的Javascript操作、自定义的事件回调、第三方的库等）Angular也不是一概不接见，可以使用AngularJS提供的$apply()函数将这些外来者包进AngularJS的context中，让Angular感知到他们产生的变化。
1.  首先，浏览器会一直处于监听状态，一旦有事件被触发，就会被加到一个event queue中，event queue中的事件会一个一个的执行。
2.  event queue中的事件如果是被$apply()包起来的话，就会进入到AngularJS的context中，这里的fn()是我们希望在AngularJS的context中执行的函数。
3.  AngularJS将执行fn()函数，通常情况下，这个函数会改变应用的某些状态。
4.  然后AngularJS会进入到由两个小循环组成的$digest循环中，一个循环是用来处理$evalAsync队列（用来schedule一些需要在渲染视图之前处理的操作，通常通过setTimeout(0)实现，速度会比较慢，可能会出现视图抖动的问题）的，一个循环是处理$watch列表（是一些表达式的集合，一旦有改变发生，那么$watch函数就会被调用）的。$digest循环会一直迭代知道$evalAsync队列为空并且$watch列表也为空的时候，即model不再有任何变化。
5.  一旦AngularJS的$digest循环结束，整个执行就会离开AngularJS和Javascript的context，紧接着浏览器就会把数据改变后的视图重新渲染出来。
> 不懂联系我：18610760206 王博钧 还能讲的细一点，代码实现啥的太费时间就不写了
- 适应场景解释
> 不适合类型开发：
1. 内容网站，需要SEO的。(SEO目前也有了prerender解决方案) https//prerender.io

2. 交互频繁的，如游戏之类交互体验网站。

3. 太过于简单的页面。

>适合类型开发
1. 管理系统的开发

## Vue.js 
- vue是一个MVVM的框架（库）,比angular更加轻巧，学习成本低
- vue是一个构建用户界面的渐进式框架,也就是自底向上增量式开发
- vue的API简单实现数据绑定和组合的视图组件
- vue的特征如下：
1. 轻量级的框架
2. 双向数据绑定
3. 指令
4. 组件化
- 优点：
1. 官方文档清晰,上手简单
2.  