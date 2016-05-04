
## video.js文档笔记

#### 初始化

－　动态添加video(append...)时,data-setup参数设置可以放到video方法里：

```
	videojs("example_video_1", {}, function(){
	  //video.js初始化完成后会调用该回调函数
	});
```

####　参数设置

－　video标签的部分属性在<video>中出现即为true，而不是显示的设置 ”属性“=true，而在video.js中设置data-setup中为后者。

－　autoplay：
	该属性使video会在页面加载完毕后立即播放，而IOS设备屏蔽了这个属性。

－　preload：
	autoplay属性会屏蔽掉preload属性，没有autoplay属性时，
	当preload值为auto时，页面加载时即加载媒体，但是苹果移动设备会忽略该属性以保护带宽
	当preload值为metadata时，只加载一些关于视频的元数据信息，如持续时间，媒体尺寸等等。

## hls.js文档笔记

持续更新中。。。

