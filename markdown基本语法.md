# MarkDown文档的基本语法 
 
## 一、标题  
在markdown文档中用来显示标题的方法是在标题开始的地方加上#表明其为标题，#与标题用空格隔开，其中markdown文档共有六级标题，需要显示某级标题就在该标题前加上相应数量的#号即可。另外一级标题可以用后一行加上三个等于号（===）表示，二级标题可以用后一行加上三个中杠线（---）表示。
```markdown
# 一级标题
一级标题
===
## 二级标题
二级标题
---
### 三级标题
……
###### 六级标题
```
## 二、段落、强调与水平分割线
- 段落
段落不需要加特殊的符号格式化，但在段落结束时需要空一行或者加两个空格表示段落结束，
否则段落不会结束。  
- 强调
    - 倾斜：markdown文档中对选中文本前后加上一个*号将使选中文本倾斜。
	- 加粗：markdown文档中对选中文本前后加上两个*号将使选中文本加粗。
	- 删除：markdown文档中对选中文本前后加上两个~号将使选中文本加粗。
	- 倾斜加粗：markdown文档中对选中文本前后加上三个*号将使选中文本倾斜加粗。
	- 倾斜删除：markdown文档中对选中文本前后加上*~~号将使选中文本倾斜删除。
	- 加粗删除：markdown文档中对选中文本前后加上**~~号将使选中文本加粗删除。
	- 加粗删除：markdown文档中对选中文本前后加上***~~号将使选中文本倾斜加粗删除。
```markdown
	*倾斜*
	**加粗**
	~~删除~~
	***倾斜加粗***
	*~~倾斜删除~~*
	**~~加粗删除~~**
	***~~倾斜加粗删除~~***
```
- 水平分隔线
可以在单独一行上使用---或___(三个中杠线或三个下划线)表示水平分割线
```markdown
    ---
    ___
```

## 三、<span id="jump">列表</span>
- 无序列表
在markdown文档中可以在列表项前加上-、+或*（空格隔开）使其成为无序列表，同一组列表项前选用相同的符号，如统一用-或*。
```markdown
- item1
- item2
- item3

+ item1
+ item2
+ item3

* item1
* item2
* item3
```
- 有序列表
在markdown文档中可以在列表项前加上数字编号.（空格隔开）使其成为有序列表。
```markdown
1. item1
2. item2
3. item3
```
- 列表嵌套
在markdown文档中使用缩进四个空格的方式实现列表嵌套
```markdown
无序列表嵌套无序列表
- item1
    - item1.1
    - item1.2
    - item1.3
- item2
- item3
- 
有序列表嵌套有序列表
1. list1
    1. item1.1
    2. item1.2
    3. item1.3
2. list2  

有序列表嵌套无序列表
1. list1
    - item1.1
    - item1.2
    - item 1.3
2. list2

无序列表嵌套有序列表
- item1
    1. list1
    2. list2
    3. list3
- item2
- item3
```

## 四、链接、图片与图片链接
在markdown文档中，链接、图片与图片链接有两种表示方式，分别为内嵌式链接和引用式链接。内嵌式链接是指在使用链接、图片或图片链接时将其地址一并写入，引用式链接是指在在使用链接、图片或图片链接时以别名代替，在文档结束时指出其地址，这样做可以使文档比较整洁，减少地址输入。
- 链接
    - 内嵌式链接
        - 外部链接：[百度](http://www.baidu.com)
        - 内部链接1：链接仓库的其它文件：[README](README.md)
        - 内部链接2：链接本文件的其它部分：[列表](#jump)
    - 引用式链接
        - 外部链接：[百度] 或 [百度][baidu]
        - 内部链接1：链接仓库的其它文件：[README]
        - 内部链接2：链接本文件的其它部分：[列表]  
```markdown
- 内嵌式链接
    - 外部链接：[百度](http://www.baidu.com)
    - 内部链接1：链接仓库的其它文件：[README](README.md)
    - 内部链接2：链接本文件的其它部分：[列表](markdown基本语法.md#三、列表)
- 引用式链接
    - 外部链接：[百度] 或 [百度][baidu]
    - 内部链接1：链接仓库的其它文件：[README]
    - 内部链接2：链接本文件的其它部分：[列表]  
```
        
- 图片
    - 图片的内嵌式链接
        - 外部图片 
		  ![hao123](https://gss1.bdstatic.com/5eN1dDebRNRTm2_p8IuM_a/res/img/richanglogo168_24.png "hao123")
        - 仓库内部的图片  
         ![comment](images/Comment.png "发表评论")
    - 图片的引用式链接
        - 外部图片 
         ![hao123][hao123_logo]
        - 仓库内部的图片  
         ![comment][comment_png]
```markdown
- 图片的内嵌式链接
    - 外部图片 
	  ![hao123](https://gss1.bdstatic.com/5eN1dDebRNRTm2_p8IuM_a/res/img/richanglogo168_24.png "hao123")
    - 仓库内部的图片  
     ![comment](images/Comment.png "发表评论")
- 图片的引用式链接
    - 外部图片 
     ![hao123][hao123_logo]
    - 仓库内部的图片  
     ![comment][comment_png]
```
- 图片链接
    - 内嵌式链接
    [![hao123](https://gss1.bdstatic.com/5eN1dDebRNRTm2_p8IuM_a/res/img/richanglogo168_24.png)](http://www.hao123.com)
    - 引用式链接
    [![hao123][hao123_logo]][hao123]

```markdown
 - 内嵌式链接
    [![hao123](https://gss1.bdstatic.com/5eN1dDebRNRTm2_p8IuM_a/res/img/richanglogo168_24.png)](http://www.hao123.com)
    - 引用式链接
    [![hao123][hao123_logo]][hao123]
```
## 五、引文、代码块
- 引文
	1. 单重引用
	>这是一个引文。     
	       
			——出自《出处》
	2. 多重引用
	>>这是多重引文。
- 代码块
在markdown文档中，可以使用``将代码语句包起来的方式引入单句代码，使用四个空格缩进可以引入一段代码，使用``````可以引入一段代码，在```之后加入语言名称以支持语法高亮（在MarkDown支持该语法特性的情况下）

    - 代码块 示例
        - 块式代码  
			```javascript
			var x=10;
			console.log(x);
			```
			    var x=10;
			    console.log(x);
			<div>
			```javascript<br />
			&nbsp;&nbsp;&nbsp;&nbsp;var x=10;<br />
			&nbsp;&nbsp;&nbsp;&nbsp;console.log(x);<br />
			```
			</div>	
        - 行内代码  
上段代码中定义变量的语句是`var x=10;`，将变量输出到控制台调用的是`console.log();`函数。	
- HTML代码
<h3 align="center">在MarkDown文档中仍旧可以使用HTML标记</h3>

## 六、表格
- 完整表格
 
|    这            |    是          |   表头       |
| :-----  		   | :-------:     | ------:      |
| cell11 默认左对齐 | cell12居中对齐 | cell13右对齐  |
| cell21           | cell22        | cell23       |
| cell31           | cell32        | cell33       |

```markdown
|    这            |    是          |   表头       |
| :----- 	   | :-------:      | ------:      |
| cell11 默认左对齐 | cell12居中对齐 | cell13右对齐  |
| cell21           | cell22        | cell23       |
| cell31           | cell32        | cell33       |

```

- 精简表格

这   |     是   |表头
-------|--------|-------
cell11 | cell12 | cell13
cell21 | cell22 | cell23
cell31 | cell32 | cell33

```markdown
这     |     是  |表头
-------|--------|-------
cell11 | cell12 | cell13
cell21 | cell22 | cell23
cell31 | cell32 | cell33
```

## 七、 GFM（Github Flavored Markdown）语法
- 多选框
	- [x] 吃饭
	- [x] 睡觉
	- [ ] 打豆豆

```markdown
    - [x] 吃饭
	- [x] 睡觉
	- [ ] 打豆豆
```
- 表情
markdown支持emoji表情，如 :blush:(`:blush:`)
emoji表情可参考[emoji表情](https://github.com/guodongxiaren/README/blob/master/emoji.md)



<!--下面是本文档中用到的链接 -->
[百度]: http://www.baidu.com 
[baidu]: http://www.baidu.com
[README]: README.md
[列表]: #jump
[hao123_logo]: https://gss1.bdstatic.com/5eN1dDebRNRTm2_p8IuM_a/res/img/richanglogo168_24.png
[hao123]: https://www.hao123.com
[comment_png]: images/Comment.png


