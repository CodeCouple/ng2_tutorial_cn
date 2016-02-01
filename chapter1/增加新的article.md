##增加新的Article
现在我们来改写addArticle函数让它能真正的在按钮点击的时候添加文章：

	addArticle(title: HTMLInputElement, link: HTMLInputElement): void {
		console.log(`Adding article title: ${title.value} and link: ${link.value}`);
		this.articles.push(new Article(title.value, link.value, 0));
		title.value = '';
		link.value = '';
	}
	
这将会：
 
 1. 用用户提交的标题和URL创建一个Ariticle实例 
 2. 将它添加到Article的数组中
 3. 清空input域内的值

>如何清空input的值呢？我们回想一下，title和link都是HTMLInputElement对象。这意味着我们可以设置它们的属性。当我们改变value属性时，页面中的input标签也会相应的被改变了。

现在，如果你增加一篇新的文章，然后点击Submit就会看到文章真的被添加到页面了！  