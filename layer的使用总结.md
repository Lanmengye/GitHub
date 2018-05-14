layer是一款近年来备受青睐的web弹层组件，可以独立使用，也可以通过Layui模块化使用。独立版本[下载地址](http://layer.layui.com)

### 独立版本使用方法
获得 layer 文件包后，解压并将 layer 整个文件夹（不要拆分结构） 存放到你项目的任意目录，使用时，只需引入 layer.js 即可

### layer基础参数说明

- type: 弹窗类型（Number）
  
  * 0 信息框（默认）
  * 1 页面层
  * 2 iframe层
  * 3 加载层
  * 4 tips层

- title: 标题（String/Array/Boolean)
  * String 标题文本 例：'我是标题'
  * Array 标题文本、CSS样式 例：['文本', 'font-size:18px;']
  * Boolean 是否显示标题栏，例：title: false

- content: 内容（String/DOM/Array）
  * String 普通html内容
  * DOM DOM对象
  * Array 参数数组
  例

```js

	//如果是页面层
	layer.open({
	  type: 1, 
	  content: '传入任意的文本或html' //这里content是一个普通的String
	});
	
	
	layer.open({
	  type: 1,
	  content: $('#id') //这里content是一个DOM，注意：最好该元素要存放在body最外层，否则可能被其它的相对元素所影响
	});
	
	
	//Ajax获取
	$.post('url', {}, function(str){
	  layer.open({
	    type: 1,
	    content: str //注意，如果str是object，那么需要字符拼接。
	  });
	});
	
	
	
	//如果是iframe层
	layer.open({
	  type: 2, 
	  content: 'http://sentsin.com' //这里content是一个URL，如果你不想让iframe出现滚动条，你还可以content: ['http://sentsin.com', 'no']
	}); 
	
	
	//如果是用layer.open执行tips层
	layer.open({
	  type: 4,
	  content: ['内容', '#id'] //数组第二项即吸附元素选择器或者DOM
	});

```

