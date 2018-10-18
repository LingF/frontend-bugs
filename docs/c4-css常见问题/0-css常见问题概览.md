#### css常见问题概览
1. 禁止用户选中文字：-webkit-user-select:none；  
1. 去掉按钮touch时有蓝色的边框 : -webkit-tap-highlight-color:rgba(0,0,0,0)；  
1. 去除webkit的滚动条: ::-webkit-scrollbar{ display: none; }；  
1. 禁止保存或者拷贝图像(仅ios有效) : img { -webkit-touch-callout: none; }  
1. 禁止选中内容 htm: { -webkit-user-select: none;}  

1. 修改表单元素中placeholder 的样式： ::-webkit-input-placeholder{  }；
1. 去除表单元素的默认样式:  -webkit-appearance:none；  如select、input;
1. 表单元素 的placeholder属性会使文本位置偏上  
   line-height: （和input框的高度一样高）---pc端解决方法
   line-height：normal ---移动端解决方法
1. input type=number之后，pc端出现上下箭头  
    ```
    input::-webkit-outer-spin-button, input::-webkit-inner-spin-button {
        -webkit-appearance: none !important;
        margin: 0;
    }
    ```

1. table > td用col设置了宽度后超出部分隐藏: table加属性table-layout:fixed（固定宽度布局）；  
1. table > td 圆角表格： 设置border-collapse： collapse属性后，单元格td的圆角属性失效  
1. table > td 定义了border-collapse:collapse属性，border-spacing属性不起做用  
1. table > col和colgroup 能发挥作用还能保证兼容的应用就只有俩： width和background  

1. display:table-cell, 子元素不从顶部开始显示： vertical-align:top。table-cell默认居中。
1. 表单元素和display:-webkit-box的问题：表单元素使用display:-webkit-box，文字无法居中。使用-webkit-flex-align:center, -webkit-flex-pack: center, text-align: center,都无效。可将-webkit-box改成display: block等。

1. body设置100%高度后被底部的导航栏挡住: document.documentElement.style.height = window.innerHeight + 'px'；  
1. body设置100%、overflow，仍有X方向滚动条: body没有设置postion:relative，且有absolute元素宽度超过屏幕宽度。

1. 元素上下border不包含在元素高度height中；元素左右border、padding包含在元素的宽度width中，可用box-sizing:border-box改变。
1. border-radius百分比失效：部分Android不识别百分比单位，可设置一个较大值的px、em、rem单位；部分手机下，width值过大，border-radius无效；  Android 4.2.x 不支持border-radius缩写。
1. Samsung S4圆角Bug  
  Samsung S4手机在 Android Browser4.4.2 上（其他版本未测），如果你使用了 border-radius，并且使用了 -webkit-transform 属性，当使用了 translatez 或者 translate3d 值，圆角会出现问题，可以直接使用 -webkit-transform: translate(0, 0) 来避免这个问题。
1. android 4.x bug  
    三星 Galaxy S4中自带浏览器不支持border-radius缩写  
    同时设置border-radius和背景色的时候，背景色会溢出到圆角以外部分  
    部分手机(如三星)，a链接支持鼠标:visited事件，也就是说链接访问后文字变为紫色  
    android无法同时播放多音频audio

1. 背景图片CSS书写兼容问题： background:url() no-repeat top top/80% auto。部分手机不支持"/"后加参数的写法。需另外写background-size；  
1. 背景渐变颜色兼容问题：
```
{  //部分手机不支持background-image属性写渐变颜色。如酷派、联想s810t；
  background-image:-webkit-radial-gradient(center center, circle cover, #0087fb 0%, #0087fb 35%,transparent 35%);
}
```

1. a标签伪类顺序：
```
{
  :link{};
  :visited{};
  :hover{};
  :active{}
  //按L-V-H-A的顺序设置超链接样式即可，可速记为LoVe（喜欢）HAte（讨厌）；
}
```

1. CSS动画页面闪白,动画卡顿  
    1.尽可能地使用合成属性transform和opacity来设计CSS3动画，不使用position的left和top来定位  
    2.开启硬件加速  
    ```
    -webkit-transform: translate3d(0, 0, 0);
    -moz-transform: translate3d(0, 0, 0);
    -ms-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    ```

1. IE无法设置滚动条的颜色：将原来设置在body上的滚动条颜色样式定义到html标签选择符上即可；

1. 当文字超出范围时自动补...省略号： 
  ```
  {  //单行
    white-space: nowrap;
    overflow: hidden;
    text-overflow:ellipsis;
  }

  {  //多行
    overflow: hidden;
    text-overflow: ellipsis;
    display:-moz-box;
    display:-webkit-box;
    display:box;
    -moz-line-clamp: 3;
    -webkit-line-clamp: 3;
    line-clamp: 3;
    -moz-box-orient: vertical;
    -webkit-box-orient: vertical;
    box-orient: vertical;
  }
  ```

1. 快速回弹滚动 (iOS上拥有像Native 的滚动效果): 

```
{
  overflow: auto;
  -webkit-overflow-scrolling:touch;
}
```
