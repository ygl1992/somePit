# 在APP的webview中使用微信支付时遇到的问题

### 场景：公司开发了一个APP，这个APP要嵌入几个H5的页面，其中有个页面需要用到微信支付，打开微信APP进行支付

### 过程：

1. 一开始也没有报错，但就是微信支付调不出来，比对文档发现，ip地址需要时用户端的ip地址，引入了一个第三方的库（[http://httpbin.org/ip](http://httpbin.org/ip)），获取ip地址
2. ip地址的问题解决了，在浏览器上可以完成支付了，但是在app中出现如下错误（在Android中有问题，IOS下没问题）
	<img src="../images/001.png" />
![](https://github.com/ygl1992/somePit/blob/master/images/001.png?raw=true)

3. adf