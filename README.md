
## video.js文档笔记

### 坑

- 提示跨域问题找后台，nigix可以设置。。。

- 如果video加载后的回调funciton没有起作用，请检查id和function中间的那个{}有没有。。。

- video 标签在没有poster属性的情况下，疯狗般不停的循环发送请求，请在标签里写个poster属性，哪怕为空在后面初始化时在指定poster。。。

### 初始化

- 动态添加video(append...)时,data-setup参数设置可以放到video方法里(必须为合法的json格式)：

```
	videojs("example_video_1", {data-setup...}, function(){
	  //video.js初始化完成后会调用该回调函数
	});
```

###　data-setup参数设置

- video标签的部分属性在<video>中出现即为true，而不是显示的设置 ”属性“=true，而在video.js中设置data-setup中为后者。

- autoplay：
	该属性使video会在页面加载完毕后立即播放，而IOS设备屏蔽了这个属性。

- preload：
	autoplay属性会屏蔽掉preload属性，没有autoplay属性时，
	当preload值为auto时，页面加载时即加载媒体，但是苹果移动设备会忽略该属性以保护带宽
	当preload值为metadata时，只加载一些关于视频的元数据信息，如持续时间，媒体尺寸等等。

- poster:
	视频播放之前的图片

- loop
	循环

- width/height 
	宽高

- Component Options 组件参数化
	（屏蔽静音效果按钮）
	var player = videojs('video-id', {
	  controlBar: {
	    muteToggle: false
	  }
	});

### videojs API

#### 皮肤设置
- 屏蔽video默认皮肤，在videojs加载前设置 window.VIDEOJS_NO_BASE_THEME = true 
- 屏蔽videojs的动态皮肤，在videojs加载前设置window.VIDEOJS_NO_DYNAMIC_STYLE  设置后的尺寸会被置0

## hls.js文档笔记

持续更新中。。。

