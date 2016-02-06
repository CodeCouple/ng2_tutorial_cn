##Angular 2是用TypeScript开发的
Angular 2是用类Javascript语言——TypeScript写的。你可能会对Angular使用这种新语言而产生质疑，但实际上，我们使用TypeScript而不是JavaScrpt是有很多原因的。

TypeScript不是一种完完全全的新语言，它是ES6的超集。如果我们写的是ES6代码，那它也完美使用于TypeScript代码。下面的图展示了几种语言之间的关系：

![](http://ww1.sinaimg.cn/mw1024/006nuRA9gw1f0jw5bngfxj30bv0ay0t2.jpg)

>什么是ES5？什么是ES6？ES5是ECMAScript5的缩写，也就是是我们熟悉且热爱的标准JavaScript。它或多或少可以在每一种浏览器上运行。ES6是下一代JavaScript，使我们将会重点讲的。

直到本书出版之时，只有少数浏览器可以在现有框架外运行极少部分TypeScript.为了解决这个问题我们用到了转换编译器(tanspiler,有时也叫transcompiler)。TypeScript转换编译器把TypeScript代码作为输入，输出几乎所有浏览器都能理解的ES5代码。

>对于从TypeScript到ES5的转换，只有TypeScript核心团队开发的一个转换编译器。但是如果想把ES6代码转换成ES5代码，就有两种主流的ES6-to-ES5编译器：由谷歌开发的traceur和由JavaScipt社区开发的babel。我们在本书中不会使用它们，但它们都是值得我们了解的伟大的项目。

>我们在上一张安装了Typescript，但万一你是从本章开始学习的，可以使用下面的命令安装：
    
>    npm install -g typescript

TypeScript是由微软和谷歌合作开发的，这事儿简直太棒了，因为有这两家技术牛逼的公司做依靠，相信TypeScript能得到长期的支持和维护。这两家公司都为Web的发展做出了贡献，而我们这群开发者都受益于它们。

转换编译器的一个很重要的贡献在于它使得一些小团队可以对开发语言做出改进，而不需要要求互联网上的每个用户更新自己的浏览器。

需要指出一点：并不是必须使用TypeScript来开发Angular2应用。你当然也可以使用ES5（"标准JavaScript"）开发。Angular 2为其所有的功能提供了一套ES5 API。那我们为什么用TypeScript？因为TypeScript有很多很酷炫的特性，可以让开发更便捷。
