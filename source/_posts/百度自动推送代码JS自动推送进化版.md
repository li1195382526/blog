# [百度自动推送代码JS自动推送进化版](https://www.cnblogs.com/chinafine/articles/9359814.html)



百度站长平台提供链接索引的自动提交 JS 代码脚本。用百度自己的话讲：JS链接推送代码以网页为最小对象，服务于全平台多终端，PC站和移动站均可使用。安装代码的页面在任意平台（浏览器、微信、微博）被加载时，页面链接会被第一时间推送给百度，从而提高站点新内容的发现速度。
<!-- more -->
今天分享的这个自动推送 JS 代码 进化版来自百度站长学院

先来看看百度站长默认的自动推送 js 代码是这样的：

```js
<script>
(function(){
    var bp = document.createElement('script');
    var curProtocol = window.location.protocol.split(':')[0];
    if (curProtocol === 'https') {
        bp.src = 'https://zz.bdstatic.com/linksubmit/push.js';        
    }
    else {
        bp.src = 'http://push.zhanzhang.baidu.com/push.js';
    }
    var s = document.getElementsByTagName("script")[0];
    s.parentNode.insertBefore(bp, s);
})();
</script>
```

只要把这段代码放入你的每个页面中，每当用户访问这些页面时，就会通过这段脚本从百度下载一个1x1的gif，同时记录页面此时此刻的URL地址，然后推送给百度。

使用百度默认的代码有两个问题：

第一 这段脚本先后会调用两个百度资源，这造成了冗余，不利于页面加载速度。

第二 该脚本会提交目前URL，但是许多URL会是动态URL，会带各种参数。虽然百度爬虫也有自己的判断方法，但无疑这增加了其负担。

于是，为了解决这两个问题，笔者咨询了好友柴云翔同时是前端开发的大牛。在大牛的帮助下，我们有了下面这个改良版本。

 

```js
<script>
	(function(){
		var canonicalURL, curProtocol;
		//Get the <link> tag
		var x=document.getElementsByTagName("link");
		//Find the last canonical URL
		if(x.length > 0){
			for (i=0;i<x.length;i++){
				if(x[i].rel.toLowerCase() == 'canonical' && x[i].href){
					canonicalURL=x[i].href;
				}
			}
		}
		//Get protocol
	    if (!canonicalURL){
	    	curProtocol = window.location.protocol.split(':')[0];
	    }
	    else{
	    	curProtocol = canonicalURL.split(':')[0];
	    }
	    //Get current URL if the canonical URL does not exist
	    if (!canonicalURL) canonicalURL = window.location.href;
	    //Assign script content. Replace current URL with the canonical URL
    	!function(){var e=/([http|https]:\/\/[a-zA-Z0-9\_\.]+\.baidu\.com)/gi,r=canonicalURL,t=document.referrer;if(!e.test(r)){var n=(String(curProtocol).toLowerCase() === 'https')?"https://sp0.baidu.com/9_Q4simg2RQJ8t7jm9iCKT-xh_/s.gif":"//api.share.baidu.com/s.gif";t?(n+="?r="+encodeURIComponent(document.referrer),r&&(n+="&l="+r)):r&&(n+="?l="+r);var i=new Image;i.src=n}}(window);})();
</script>
```

这个新脚本的作用是多了一步查看页面的canonical URL的步骤。我们知道canonical属性表示该页面纵有千种URL的花样，请搜索引擎只认准href中给出的URL值。这样一来就不会让搜索引擎为了同一个页面（或许已经索引了）多次检查你的推送页面具体内容。

这个新脚本的另一个更改是直接将上述两个js的内容拿了出来。由于这两个js中的代码其实是静态的，每次都去调用并不必要。另一方面，我们需要对r的值进行更改，将它更改为canonical URL的值，因此这样解决了我们上面的第二个问题。

IT粉丝网看到这个版本好处在于推送的链接是 canonical 标签属性里面的链接，对于网站链接有过改版的网站是友好的，不会重复推送链接，上面的代码适用于任何网站！

需要注意的是使用这个改进版，百度默认的推送代码不能变，如果默认的自动推送代码改变，这个也会失效！

**个人认为这个代码适用自适应站更好，因为自适应站手机版和PC版地址相同，通过canonical标签重新定义了标准的链接，那些带参数的，直接就不再进行提交。如果是m.XXX.com这样的，和www.XXX.com这样的网站，一般移动端会canonical会指向PC端链接。按这种方法不会提交手机版，觉得并不恰当。**