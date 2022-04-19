#动画
##1.过渡
- 通过过渡可以指定一个属性发生变化的切换方式
- 通过过渡可以创建一些非常好的效果,提升用户的体验
- 大部分属性都支持过渡效果(比如值可以计算的)
- 使用过渡时必须是从一个有效值向另外一个有效值进行过渡

transition-property 指定要执行过渡的属性
```eg: transition-property: all```

transition-duration 指定过渡效果持续的时间

transition-timing-fuction  过渡的时序函数 - 指定过渡执行的方式
        
        可选值:
        ease 默认值,慢速开始,先加速后减速
        linear 匀速运动
        ease-in 加速运动
        ease-out 减速运动
        ease-in-out 先加速后减速
        cubic-bezier() 来指定时序函数
        https://cubic-bezier.com 
        eg:cubic-bezier(0,0,1,1)表匀速运动
        steps() 分布执行过渡效果
            可以设置第二个值: end/start 在时间开始/结束执行过渡

transition-delay 过渡效果的延迟

transition 可以同时设置所有属性 如要写延迟 两个时间中第一个必须是持续时间

##2.动画
- 和过渡类似 都可以实现过渡效果
- 而过渡需要某个属性发生变化才触发 动画可以自动触发
- 设置动画效果,必须要设置一个关键帧,关键帧设置了动画执行每一个步骤
```
@keyframes test
{

    /* 表示动画的开始 也可以使用0%*/
    from{
        margin-left: 0;
    }

    /* 表示动画的结束位置 也可以使用100%*/
    to{
        margin-left: 700px;
    }
}
```
- 在CSS中设置执行动画效果
```
/* 设置动画 */
/* 设置当前元素生效的关键帧的名字 */
animation-name: test;

/* 设置动画的执行时间 */
animation-duration: 2s;

/* 设置动画的延迟 */
animation-delay: 2s;

/* animation-timing-function: linear; */

/* animation-iteration-count: 2; 动画执行的次数 */

/* animation-direction: reverse; 指定动画执行的方向*/

/* 
animation-fill-mode 动画的填充模式
    可选值: 
    none 默认值 执行结束元素回到原来位置
    forwards 执行结束元素停在结束位置
    backwards 动画延迟等待时,元素将处于动画开始位置
    both 结合了上述两种特点
*/

/* 
    设置动画的执行状态
        可选值: 
        running 默认值 动画执行
        paused 动画暂停
*/
animation-play-state: running;

/* animation可以设置所有值 */
```

##3.变形
- 变形指通过CSS改变元素的形状或位置
- 变形不会影响到页面的布局
- transform 设置元素的变形效果

        平移属性: 
        translateX()
        translateY()
        translateZ()
        平移元素 百分比是相对于自身计算的

        旋转属性:
        通过旋转可以使元素沿着x,y,z轴旋转指定角度
        rotateX()
        rotateY()
        rotateZ()

        缩放属性:
        scaleX()
        scaleY()
        scaleZ()(极少使用)

        变形的原点 默认值 center
        transform-origin: 

- z轴平移 调整元素在z轴的位置 正常情况下就是调整元素和人眼之间的距离
- 元素在网页中使用的是相对坐标系,坐标系会跟着元素方向改变

        距离越大 元素离人越近
        默认情况下浏览器不支持透视,不能看见z轴平移的效果
        所以必须设置网页的视距

        position: absolute
        top: 0
        left: 0
        bottom: 0
        right: 0
        margin: auto
        这种居中方式只适用于元素的大小确定情况下

        可以使用如下方式实现垂直居中效果
        left: 50%;
        top: 50%;
        transform: translateX(-50%) translateY(-50%);
