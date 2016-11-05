# 在document下与client相关的宽高
### 1. document.body.clientWidth.
### 2. document.body.clientHeight.
- [ ] **改属性指的是元素的可视部分宽度和高度，即`padding + content`,如果没有出现滚动条，即为元素设定的高度和宽度，如果出现滚动条，滚动条会遮住元素的宽高，那么该属性就是其本来宽高减去滚动条的宽高。**

```
body {
			border: 20px solid #ccc;
			margin: 10px;
			padding: 40px;
			background: #eee;
			height: 350px;
			width: 500px;
			overflow: scroll;
		}
		console.log(document.body.clientHeight); //350+80 = 430
		console.log(document.body.clientWidth);  //500 + 80 = 580
```

### 3. document.body.clientLeft.
### 4. document.body.clientTop.
- [ ] **这两个返回的是`元素周围边框的厚度`，如果不指定一个边框或者不定位该元素，它的值就是0.**

```
console.log(document.body.clientLeft); //20
console.log(document.body.clientTop);  //20
```
# 在document下与offset相关的宽高
### 1. document.body.offsetWidth.
### 2. document.body.offsetHeight.
- [ ] **这一对属性指的是元素的`border+padding+content的宽度和高度`，该属性和其内容是否超出元素大小无关，只和本来设定的border以及width和height有关**

```
		console.log(document.body.offsetWidth); //40 + 80 + 500 = 620
		console.log(document.body.offsetHeight);//40 + 80 + 350 = 470
```
### 3. document.body.offsetLeft.
### 4. document.body.offsetTop.

`这两个属性有点坑，小心翻车`
#### offsetParent
- [ ] 如果当前元素的父级元素`没有`进行CSS定位(position为absolute或relative),offsetParent为body.
> 在IE8/9/10以及chrome中,offsetLeft = (offsetParent的margin-left)+(offsetParent的border宽度)+(offsetParent的padding-left)+(当前元素的margin-left).

> 在firefox中,offsetLeft = (offsetParent的margin-left)+(当前元素的margin-left)+(offsetParent的padding-left).

- [ ] 如果当前元素的父级元素`有`进行CSS定位(position为absolute或relative),offsetParent取最近的那个父级元素

```
		body {
			border: 20px solid #ccc;
			margin: 10px;
			padding: 40px;
			height: 350px;
			width: 500px;
		}
		
		#mdiv {
			width: 400px;
			height: 200px;
			padding: 20px;
			margin: 10px;
			background: #F60;
			border: 20px solid #888;
		}
		var mdiv = document.getElementById("mdiv");
			//在IE8/9/10以及chrome中
		console.log(mdiv.offsetLeft);//80
		console.log(mdiv.offsetTop); //80
			//在Firefox
		console.log(mdiv.offsetLeft);//60
		console.log(mdiv.offsetTop); //60
```

# 与scroll相关的宽高
### 1.scrollWidth和scrollHeight
- [ ] `document.body`的scrollWidth和scrollHeight与`div`的scrollWidth和scrollHeight是有点区别的。(`document.body`在chrome与FF表现不一致，但`div`在chrome和FF表现是一致的)
> 给定宽高小于浏览器窗口的时候scrollWidth和scrollHeight通常是浏览器窗口的高度

- [ ] 给定宽高大于浏览器窗口，且`内容小于`给定宽高**scrollWidth:**给定的宽度 + 其所有的padding、margin 和 border,**scrollHeight:**给定的高度+其所有的padding、margin 和border.
- [ ] 给定宽高大于浏览器窗口，且`内容大于`给定宽高**scrollWidth:**内容宽度+其所有的padding、margin和border，**scrollWidth:**内容高度+其所有的padding、margin 和border.

# 坐标
### 1.clientX和clientY
- [ ] 相对于浏览器（可视区左上角0,0）的坐标。
### 2.screenX和screenY
- [ ] 相对于设备屏幕左上角(0,0)的坐标。
### 3.offsetX和offsetY
- [ ] 相对于事件源左上角(0,0)的坐标
### 4.pageX和pageY
- [ ] 相对于整个网页左上角(0,0)的坐标
### 5.x和y
- [ ] 相对于用css动态定位的最内层包容元素（chrome下不管有没有设置position都与1相等）












