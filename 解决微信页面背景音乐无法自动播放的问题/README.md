# 解决微信页面背景音乐无法自动播放的问题
### 最近做项目是有个需求，就是加背景音乐，需要自动播放，当然也可以点击一下暂停播放，本地在浏览器里测试都是没问题的，但是一上线，在微信里打开音乐就不自动播放了，需要点一次，然后再点一次才能播放音乐。网上搜了各种办法，解决方案如下：

	<audio src="bg.mp3" id="Jaudio" class="media-audio" autoplay preload loop="loop"></audio>

###
	
	function audioAutoPlay(id){
		var audio = document.getElementById(id);  
		audio.play();
		document.addEventListener("WeixinJSBridgeReady", function () {  
		    audio.play();  
		}, false);   
	}
	audioAutoPlay('Jaudio');
    
#### 在微信里面监听WeixinJSBridgeReady加载完，再去播放音乐就可以了