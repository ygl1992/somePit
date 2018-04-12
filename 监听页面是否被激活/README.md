# 监听页面是否被激活

### 使用情景


- 网站有图片轮播效果，只有在用户观看轮播的时候，才会自动展示下一张幻灯片。

- 显示信息仪表盘的应用程序不希望在页面不可见时轮询服务器进行更新。

- 页面想要检测是否正在渲染，以便可以准确的计算网页浏览量

- 当设备进入待机模式时，网站想要关闭设备声音（用户按下电源键关闭屏幕）


### 例子
	
	// 设置隐藏属性和改变可见属性的事件的名称
	var hidden, visibilityChange; 
	if (typeof document.hidden !== "undefined") { // Opera 12.10 and Firefox 18 and later support 
	  	hidden = "hidden";
	  	visibilityChange = "visibilitychange";
	} else if (typeof document.msHidden !== "undefined") {
	  	hidden = "msHidden";
	  	visibilityChange = "msvisibilitychange";
	} else if (typeof document.webkitHidden !== "undefined") {
	  	hidden = "webkitHidden";
	  	visibilityChange = "webkitvisibilitychange";
	}
	
	document.addEventListener(visibilityChange, function(){
        if( document[hidden] ){
            document.title = 'hide';
        }else{
            document.title = 'show';
        }
    }, false)