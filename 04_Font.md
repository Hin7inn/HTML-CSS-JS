#字体和背景
##1.字体
- font-face可以将服务器中的字体直接提供给用户取使用 
- 问题:加载速度和版权

```
@font-face{
    /* 指定字体的名字(自己起) */
    font-family: 'WDNMD';
    /* 服务器中字体的路径 */
    src: url();
}
```
###字体的相关样式
1. color 用来设置字体颜色
2. font-size 字体的大小
相关单位: 

        em  相当于当前元素的一个font-size
        rem 相当于根元素的一个font-size

3. font-family 字体族(字体格式)
可选值之三:

        serif 衬线字体
        sans-serif 非衬线字体
        monospace 等宽字体
    
- 指定字体的类别,浏览器会自动使用该类别下的字体
- 可以同时指定多个字体,多个字体间使用,隔开
    字体生效优先使用第一个,第一个无法使用就用第二个 以此类推
```
font-family: 'Courier New', Courier, monospace;
```

##2.图标字体(Iconfont)
- 在网页中经常需要使用一些图表,可以通过图片来引入图标
但是图片大小本身比较大,并且非常的不灵活
- 所以在使用图标时,我们可以将图标直接设置为字体
然后通过font-face的形式对字体进行引入
- 这样我们就可以使用字体的形式来使用图标
- 通过实体来使用图标字体:
语法: &#x图标的编码
- 通过伪元素来设置图标字体
1.找到要设置图标的元素通过before和after选中
2.在content中设置字体的编码
3.设置字体的样式
```
content: '\f1b0';
font-family: 'Font Awesome 6 Free';
font-weight: 900;
```
- 使用Alicon或fontawesome来引入图标字体
以fontawesome为例:

        ①将all.css引入到网页中
        ②使用图标字体
        ③直接通过类名来使用图标字体
        ④class="fas fa-bell"
- Alicon则需要使用上述第三种方法引入

##3.字体样式
- 行高指的是文字占有的实际高度
- 可以使用line-height设置行高
- 可以直接指定一个大小(px em)
也可以直接设置一个整数 则行高会是字体所指定的倍数
- 行高经常还用来设置文字的行间距 = 行高 - 字体大小
- **字体框**就是字体存在的格子,设置font-size实际上就是在设置字体框的高度
- 行高会在字体框的上下平均分配
**所以将行高设置成和高度一样 则单行文字可以在一个元素中垂直居中**

- font 可以设置字体相关的所有属性
    语法: font: 风格 字重 字体大小/行高 字体族
    风格 字重 行高 可以省略不写 默认使用默认值

- font-weight:bold 字体加粗效果
可选值:

        normal 默认值
        bold 加粗
        100-900 九个级别(效果不大)
- font-style 字体风格
可选值:

        normal 正常的
        italic 斜体

##4.文本样式
- text-decoration 设置文本修饰
可选值:

        none
        underline 下划线
        line-through 删除线
        overline 上划线
- white-space 设置网页如何处理空白
可选值:

        normal 正常
        nowrap 不换行
        pre 保留空白

- text-align 文本的水平对齐
可选值:

        left 左侧对齐
        right 右侧对齐
        center 居中对齐
        justity 两端对齐

##5.背景
- backgroung-image 设置背景图片 
- 可以同时设置背景图片和背景色
- 如果背景图片小于元素,则背景图片会自动在元素内将元素铺满
- 如果背景图片大于元素,将会一部分背景无法完全显示
```background-image: url(../Exercise/163.webp);```


- background-repeat 设置背景的重复方式
可选值:

        repeat 默认值,背景会沿着x,y轴双方向重复
        repeat-x 沿着x轴重复
        repeat-y 沿着y轴方向重复
        no-repeat 背景图片不重复

- backgroung-position 用来设置背景图片的位置
设置方式:

        通过top left right bottom center 设置
        默认方位词必须同时指定两个值,如果只有一个值则第二个默认是center

        通过偏移量指定背景图片位置:
            水平方向的偏移量 垂直方向偏移量
    ```background-position: center;```

- background-clip 设置背景的范围
可选值:

        border-box 默认值,背景会出现在边框的下边
        padding-box 背景不会出现在边框,只出现在内容区和内边距
        content-box 背景只会出现在内容区
    ```background-clip: content-box;```
- background-origin 背景图片的偏移量计算的原点

        border-box  背景图片变量从边框处计算
        padding-box
        content-box
    ```background-origin: border-box;```
- background-size 设置背景图片的大小

        第一个值表示宽度
        第二个值表示高度
            只写一个 另一个默认为auto

        cover 图片的比例不变,将元素铺满
        contain 图片比例不变,将图片在元素中完整显示
```background-size: contain;```
- background-attchment 背景图片是否跟随元素移动
可选值:

        scroll 默认值 背景图片会跟随元素i东
        fixed 背景会固定在页面中,不会随元素移动
- background 背景相关的简写属性,所有背景相关的样式都可以通过该样式进行设置
```background:url() #bfa center center/contain no-repeat```
==_**注意:无顺序要求 但size必须写在position后面
origin必须在clip前面**_==

##6.渐变
- 通过渐变可以设置一些复杂的背景颜色
- 可以实现从一个颜色向其他颜色过渡的效果

- 线性渐变,颜色沿着一条直线发生变化
linear-gradient()
- 线性渐变的开头可以指定一个渐变的方向

        to left/right/bottom/top
        xxx deg deg表示度数 通过角度调整
        xxx turn 表示圈

- 渐变可以同时指定多个颜色,多个颜色默认情况下平均分配
- 也可以手动指定渐变的分布情况

repeating-linear-gradient()可以平铺的线性渐变

radial-gradient() 径向渐变(放射性效果)

- 默认情况下径向渐变圆心的形状根据元素的形状来计算的

        正方形--->圆形
        长方形--->椭圆形
- 也可以手动指定径向渐变的大小
```circle/elipse/100px 100px```
- 也可以指定渐变的位置
语法: radial-gradient(大小 at 位置,颜色 位置,颜色 位置...)
大小:circle/ellipse/closest-side/farthest-side...
    ```radial-gradient(100px 100px at center,orange,red)```
