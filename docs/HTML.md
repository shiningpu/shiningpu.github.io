# HTML

字体大小:
如果你不指定一个字体的大小，默认大小和普通文本段落一样，是16像素（16px=1em）
可以通过下面这个公式将像素转换为em：**px/16=em**

```css
h1 {font-size:2.5em;} /* 40px/16=2.5em */
h2 {font-size:1.875em;} /* 30px/16=1.875em */
p {font-size:0.875em;} /* 14px/16=0.875em */
```
在所有浏览器的解决方案中，设置 <body>元素的默认字体大小的是百分比

```css
body {font-size:100%;}
h1 {font-size:2.5em;}
h2 {font-size:1.875em;}
p {font-size:0.875em;}
```

