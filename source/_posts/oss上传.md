HTML5的[`FileReader`](https://developer.mozilla.org/en/docs/Web/API/FileReader) API可以让客户端浏览器对用户本地文件进行读取，这样就不再需要上传文件由服务器进行读取了，这大大减轻了服务器的负担，也节省了上传文件所需要的时间。不过在实践中我发现用[`FileReader.readAsText()`](https://developer.mozilla.org/en-US/docs/Web/API/FileReader/readAsText)可以轻易地处理一个300k的日志文件，但当日志文件有1G、甚至2G那么大，浏览器就会崩溃。这是因为`readAsText()`会一下子把目标文件加载至内存，导致内存超出上限。所以如果Web应用常常需要处理大文件时，我们应该使用[`FileReader.readAsArrayBuffer()`](https://developer.mozilla.org/en-US/docs/Web/API/FileReader/readAsArrayBuffer)来一块一块读取文件。

```js
 if (fileType === 1) {//fileType:文件类型
	reader.readAsDataURL(file)//一次读取，大文件上传导致内存不足
     } else {
     reader.readAsArrayBuffer(file)//分块读取
     }
```

