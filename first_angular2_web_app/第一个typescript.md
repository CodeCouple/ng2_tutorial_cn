##第一个TypeScript
现在可以创建我们的第一个TypeScript文件了。在同一个文件夹下新建一个文件**app.ts**
	import { bootstrap } from "angular2/platform/browser"; 	import { Component } from "angular2/core";		@Component({  		selector: 'hello-world',  		template: `  		<div>    		Hello world  		</div>		`	})	class HelloWorld { 	}
	bootstrap(HelloWorld);

这段代码起初看起来可能有些吓人，但是不用担心，下面我们来一步步分析。<br/>
import语句引入了我们在写代码时需要用到的模块。在这里，我们引入了两个模块：Component和Bootstrap。<br/>
我们从"angular2/core"中引入了Component，它会告诉我们的程序如何寻找依赖。同样的方法，我们从"angular/platform/browser"中引入bootstrap。<br/>
注意import语法的结构是`import {thing} from wherever`。{thing} 这部分叫做重构（destructuring）。重构（destructuring）是ES6提供的一个特性，我们会在下一章详细讨论。
###构造组件
Angular 2最伟大的思想之一就是组件的思想。

在我们的Angular App中我们通过HTML来实现交互式应用，但是浏览器只认识例如\<select>、\<form>或\<video>这些基础的浏览器自己定义的内建标签，但是如果我们想让浏览器识别新的标签应该怎么办呢？例如我们想有一个\<weather>标签来显示天气？或者用一个\<login>标签来构造一个登录板块？

组件的理念在于：教浏览器识别有新功能的新标签。

让我们来构造第一个组件。当我们写完这个组件后，就可以在我们的HTML文件中这样写了：<br/>
`<hello-world></hello-world>`

那么到底如何定义一个新的组件呢？一个基本的组件要有这两部分：

1. 一个组件注解（whan's this?）
2. 一个组件定义类

如果你写过JavaScript程序，那么下面的这几句代码在你看来可能怪怪的：

    @Component({
        //······
    })

这里是怎么回事呢？如果你有Java开发经验的话可能会对这种语句比较熟悉：这就是注解（annotation）。

可以把注解理解为增加到你代码中的元数据。当我们在HelloWorld类中使用@Component时，我们就是将HelloWorld这个类装饰成一个组件。

现在我们希望能够在标签语言中使用<hello-world>，那么，让我们来配置@Component并将它的选择器指定为hello-world。

    @Component({
        selector: 'hello-world'
    })
   
如果你熟悉CSS选择器、XPath或者JQuery选择器，你就知道设置选择器的方法有很多。Angular为组合选择器（what 's selector mix?）加入了自己的特性，我们稍后将讲到它，目前只需要知道在这种情况下就是**定义一个新的标签**。

selector属性表明这个组件将使用哪个DOM元素。这种情况下，如果我们的模板中有<hello-world></hello-world>这个标签的话，这个标签会被编译器用Component类编译。

###添加一个模板
我们可以通过template选项为@Component增加一个模板：

    @Component({
        selector: 'hello-world',
        template: `
        <div>
            Hello world
        </div>
        `
    })
    
注意，我们在定义template的时候使用的是反引号（\`...\`）。这是ES6的一个新特性（而且非常棒！），它让我们可以写多行的字符串。用反引号来写多行字符串的方式大大的方便我们在代码文件中插入模板。

####启动程序

最后一行代码`bootstrap(HelloWorld);`会启动程序。第一个参数表示这个应用的"main"组件是HelloWorld。

一旦我们的程序被引导启动后，HelloWorld组件会被应用到index.html中所有的<hello-world></hello-world>代码段中。让我们来试试吧！

####加载程序

为了运行程序，还有两件事要做：

1. 我们得告诉HTML文件将app文件引入进来
2. 我们要使用<hello-world>组件

在body中加入以下代码：

    <!doctype html>
    <html>

    <head>
        <title>First App - Hello world</title>
        <!-- Libraries -->
        <script src="node_modules/es6-shim/es6-shim.js"></script>
        <script src="node_modules/angular2/bundles/angular2-polyfills.js"></script>
        <script src="node_modules/systemjs/dist/system.src.js"></script>
        <script src="node_modules/rxjs/bundles/Rx.js"></script>
        <script src="node_modules/angular2/bundles/angular2.dev.js"></script>
        <!-- Stylesheet -->
        <link rel="stylesheet" type="text/css" href="resources/vendor/semantic.min.c\ ss">
        <link rel="stylesheet" type="text/css" href="styles.css"> 
    </head>

    <body>
        <script>
        System.config({
            packages: {
                app: {
                    format: 'register',
                    defaultExtension: 'js'
                }
            }
        });
        System.import('app.js')
            .then(null, console.error.bind(console));
        </script>
        
        <hello-world></hello-world>
        
    </body>

    </html>

在script标签中配置模块加载器，System.js。下面一行代码非常重要：

`System.import('app.js')`

这行代码告诉System.js我们想加载app.js作为程序的入口，但是有一个问题：我们还没有app.js这个文件呢！（app.ts是一个TypeScript文件.）

