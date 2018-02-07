
## video.js文档笔记(videojs)

### 坑

- 二话不说先把版本弄到最新的，有时候解决问题就是这么简单...

- 提示跨域问题找后台，nigix可以设置。。。[stackOverFlow](http://stackoverflow.com/questions/10636611/how-does-access-control-allow-origin-header-work)

- 如果video加载后的回调funciton没有起作用，请检查id和function中间的那个{}有没有。。。

- video 标签在没有poster属性的情况下，不知道为何疯狗般不停的循环发送请求，在标签里写个poster属性就他么好了，哪怕为空在后面初始化时在指定poster。。。

- [html5兼容插件](https://github.com/etianen/html5media)

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
- window.HELP_IMPROVE_VIDEOJS = false; 禁止默认的GA统计

- 屏蔽在全屏播放

```javascript
<video playsinline x5-playsinline webkit-playsinline  x5-video-player-type="h5" x5-video-player-fullscreen="true" x5-video-orientation/>
```

### 皮肤设置
- 屏蔽video默认皮肤，在videojs加载前设置 window.VIDEOJS_NO_BASE_THEME = true 
- 屏蔽videojs的动态皮肤，在videojs加载前设置window.VIDEOJS_NO_DYNAMIC_STYLE  设置后的尺寸会被置0
- class中添加vjs-big-play-centered使出现居中的暂停播放按钮，前提是你的controls事开启的，否则无法播放

## 插件机制
1. 声明插件函数 function Fun(option){}
2. 注册为一个插件 videojs.plugin('Fun',Fun)
3. 使用插件:
	动态创建的video在初始化videojs时调用插件，即videojs('id',{plugins:{Fun:option}})
	非动态创建的video初始化了的videojs对象可以直接调用，即videojs.Fun(option)

具体插件(广告插件)的使用参考videoHls_ad.html

### 插入广告流程(videoHls_ad.html)
- 参考videoHls_ad.html，可以将exampleAds提取出单独的插件文件
- 在videoHls_ad.html中有较为详细的注意事项以及部分注释
- 请在试验中将视频及广告的url换为自己的url，并确认服务端的跨域问题
