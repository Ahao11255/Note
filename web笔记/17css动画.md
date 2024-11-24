  动画

​    css3里面的动画有三个属性能实现  transition transform animetion

​    前两个属于动画一种，需要配合鼠标事件才能触发

​    后者动画不需要鼠标事件就能直接完成



  1.定义动画

  \- 在css样式表

  \- @keyframes 动画名字{

​    0%{}起始

​    100%{}结束

  }



  2.调用动画

  \- 在css样式表中

  \- 那个元素需要动画就给那个元素添加animetion





  暂停动画: animation-play-state: paused;





  常用的单一的动画属性

  animetion-name========================动画名字

  animetion-duration====================动画执行时间

  animetion-timing-function=============动画速度类型

  animetion-delay=======================延迟时间

  animetion-interation-count============动画执行次数

  animetion-direction===================动画执行方向

![02](.\图片\02.png)

```css

        @keyframes boxmove{
            0%{top: 0px;left: 0px;}
            25%{top: 0px;left: 350px;}
            50%{top: 350px;left: 350px;}
            75%{top: 350px;left: 0px;}
            100%{top: 0px;left: 0px;}
        }
	       .box{
            width: 150px;
            height: 150px;
            background: green;
            position: absolute;
            animation: boxmove 2s infinite;
        }
```

