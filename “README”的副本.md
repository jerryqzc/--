# **这是邱志成的培训材料**





## 是什么？

**Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。**

**弹性盒子是 CSS3 的一种新的布局模式。**

**给予容器控制内部元素高度和宽度的能力**

**一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式**

**引入弹性盒布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间**

任何一个容器都可以指定为 Flex 布局

> ```css
> .box{
>   display: flex;
> }
> ```

行内元素也可以使用 Flex 布局。

> ```css
> .box{
>   display: inline-flex;
> }
> ```

Webkit 内核的浏览器，必须加上`-webkit`前缀。

> ```css
> .box{
>   display: -webkit-flex; /* Safari */
>   display: flex;
> }
> ```

**注意，设为 Flex 布局以后，子元素的`float`、`clear`和`vertical-align`属性将失效。**





------

## 咱们先来看一个引入

### 倘若在一个大的div里，我们想水平排列三个小的div，怎么做？



---

## 基本概念

采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。

也就是说弹性盒子的内容包括：弹性容器(Flex container)和弹性子元素(Flex item)。

说了这么多，怎么让一个div被设置成弹性盒子呢？让我们再回去看一次。（即设置 display 属性的值为 flex 或 inline-flex）

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071004.png)

容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做`main start`，结束位置叫做`main end`；交叉轴的开始位置叫做`cross start`，结束位置叫做`cross end`。

项目默认沿主轴排列。单个项目占据的主轴空间叫做`main size`，占据的交叉轴空间叫做`cross size`。

咱们来看一个🌰

打开Hbuilder



---

## 容器的属性

### 首先咱们把属性分为两类

### 一类是设置在容器上的（flex container）

### 另一类是设置在项目上的（flex item）

第一类属性有：

- `flex-direction`
- `flex-wrap`
- `flex-flow`
- `justify-content`
- `align-items`
- `align-content`

第二类属性有：

- `order`
- `flex-grow`
- `flex-shrink`
- `flex-basis`
- `flex`
- `align-self`



### 虽然我也不想，但咱门还是要一一了解这些属性的，对吧？

###第一类：

####1、`flex-direction`

`flex-direction`属性决定主轴的方向（即项目的排列方向）。

> ```css
> .box {
>   flex-direction: row | row-reverse | column | column-reverse;
> }
> ```

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071005.png)

它可能有4个值。

> - `row`（默认值）：主轴为水平方向，起点在左端。
> - `row-reverse`：主轴为水平方向，起点在右端。
> - `column`：主轴为垂直方向，起点在上沿。
> - `column-reverse`：主轴为垂直方向，起点在下沿。

####2、`flex-wrap`

默认情况下，项目都排在一条线（又称"轴线"）上。`flex-wrap`属性定义，如果一条轴线排不下，如何换行。

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071006.png)

> ```css
> .box{
>   flex-wrap: nowrap | wrap | wrap-reverse;
> }
> ```

它可能取三个值。

（1）`nowrap`（默认）：不换行。

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071007.png)

（2）`wrap`：换行，第一行在上方。

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071008.jpg)

（3）`wrap-reverse`：换行，第一行在下方。

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071009.jpg)

####3、`flex-flow`

`flex-flow`属性是`flex-direction`属性和`flex-wrap`属性的简写形式，默认值为`row nowrap`。

> ```css
> .box {
>   flex-flow: <flex-direction> || <flex-wrap>;
> }
> ```

####4、`justify-content`

`justify-content`属性定义了项目在主轴上的对齐方式。

> ```css
> .box {
>   justify-content: flex-start | flex-end | center | space-between | space-around;
> }
> ```

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071010.png)

它可能取5个值，具体对齐方式与轴的方向有关。下面假设主轴为从左到右。

> - `flex-start`（默认值）：左对齐
> - `flex-end`：右对齐
> - `center`： 居中
> - `space-between`：两端对齐，项目之间的间隔都相等。
> - `space-around`：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

####5、`align-items`

`align-items`属性定义项目在交叉轴上如何对齐。

> ```css
> .box {
>   align-items: flex-start | flex-end | center | baseline | stretch;
> }
> ```

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071011.png)

它可能取5个值。具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下。

> - `flex-start`：交叉轴的起点对齐。
> - `flex-end`：交叉轴的终点对齐。
> - `center`：交叉轴的中点对齐。
> - `baseline`: 项目的第一行文字的基线对齐。
> - `stretch`（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

####6、`align-content`

`align-content`属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

> ```css
> .box {
>   align-content: flex-start | flex-end | center | space-between | space-around | stretch;
> }
> ```

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071012.png)

该属性可能取6个值。

> - `flex-start`：与交叉轴的起点对齐。
> - `flex-end`：与交叉轴的终点对齐。
> - `center`：与交叉轴的中点对齐。
> - `space-between`：与交叉轴两端对齐，轴线之间的间隔平均分布。
> - `space-around`：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
> - `stretch`（默认值）：轴线占满整个交叉轴。



###第二类:

####1、`order`

`order`属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

> ```css
> .item {
>   order: <integer>;
> }
> ```

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071013.png)

####2、`flex-grow`

`flex-grow`属性定义项目的放大比例，默认为`0`，即如果存在剩余空间，也不放大。

> ```css
> .item {
>   flex-grow: <number>; /* default 0 */
> }
> ```

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071014.png)

如果所有项目的`flex-grow`属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的`flex-grow`属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

####3、`flex-shrink`

`flex-shrink`属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

> ```css
> .item {
>   flex-shrink: <number>; /* default 1 */
> }
> ```

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071015.jpg)

如果所有项目的`flex-shrink`属性都为1，当空间不足时，都将等比例缩小。如果一个项目的`flex-shrink`属性为0，其他项目都为1，则空间不足时，前者不缩小。

负值对该属性无效。

####4、`flex-basis`

`flex-basis`属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为`auto`，即项目的本来大小。

> ```css
> .item {
>   flex-basis: <length> | auto; /* default auto */
> }
> ```

它可以设为跟`width`或`height`属性一样的值（比如350px），则项目将占据固定空间。

####5、`flex`

`flex`属性是`flex-grow`, `flex-shrink` 和 `flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选。

> ```css
> .item {
>   flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
> }
> ```

该属性有两个快捷值：`auto` (`1 1 auto`) 和 none (`0 0 auto`)。

建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。

####6、`align-self`

`align-self`属性允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`。

> ```css
> .item {
>   align-self: auto | flex-start | flex-end | center | baseline | stretch;
> }
> ```

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071016.png)

该属性可能取6个值，除了auto，其他都与align-items属性完全一致。



### 恭喜，所有属性讲解完毕！！！



### 不过，怎么好像有些头晕？



### 没关系，咱们还有一个表格





---

## 容器属性总结表

![1008386-20160830160542949-371754668](https://images2015.cnblogs.com/blog/1008386/201608/1008386-20160830160542949-371754668.png)

**For more details, please visit**:

- [](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

- [](https://www.cnblogs.com/nuannuan7362/p/5823381.html)

  这里针对上面的例子，我们来给盒子添加一些属性





---

## 优缺点

- **传统布局，基于盒模型，依赖 display属性 、position属性 、float属性。它对于那些特殊布局非常不方便，比如垂直居中。而flex布局用六个字概括？简单、方便、快速。**

+ **浏览器兼容性比较差，只能兼容到IE9及以上**

+ **宽度分配问题**--flex-grow属性用于设置或检索弹性盒的扩展比率，默认为0，不允许为负值。

  最为常见的用法是用flex-grow实现等比例“tab”布局，举例：

  ```
  <div class="box">
      <span class="item">元素</span>
      <span class="item">元素</span>
      <span class="item">元素</span>
      <span class="item">元素</span>
      <div class="item">元素</div>
      <div class="item">元素</div>
  </div>
  ```

  css:

  ```
  .box {
      display: flex;
      align-items: center;
      padding: 40px 20px;
      color: white;
      background-color: black;
  }
  .item {
      flex-grow: 1;
      height: 60px;
      line-height: 60px;
      text-align: center;
      border: 1px solid white;
      background-color: #ff0000;
  }
  ```

  不用害怕浮动，不用考虑子元素是块级元素还是行内元素，显示OK~~,不管外面flex父级宽度如何变化，它们都等比分布：~~

  

  **纠正一下自己错误的理解，flex-grow是分配flex容器除内容外**剩余空间**的比例，并不是整个容器的比例[捂脸]，所以出现下面的现象是完全正常的，虽然解决方案可行，但我依然不懂其中的缘由，再次[捂脸]。。。**

  ![clipboard.png](https://segmentfault.com/img/bVBUg8?w=505&h=141)

  但是，“意外”来了：
  ![clipboard.png](https://segmentfault.com/img/bVBUmN?w=504&h=142)

  ~~好奇怪，怎么不是等比例显示？大家flex-grow都是1，为什么你要占那么宽？~~
  最后找到解决方案，所有flex-grow的子元素加上flex-basis: 0%;就是完全等比分布了，这个属性值会让父级主轴在计算剩余空间时忽略子元素的本身宽度，从而实现等比分配。简单写法就是直接定义flex: 1;不分开定义三个属性。当然如果是那种连串的英文就要设置word-break: break-all;。

  ![clipboard.png](https://segmentfault.com/img/bVBUrp?w=502&h=141)

+ **设置了flex-grow元素的子级宽度问题**

  举个栗子：

  ```
  <div class="box">
      <span class="other">Hi</span>
      <div class="item">
          <div class="text">
               一个flex-grow为1的元素的子级一个flex-grow为1的元素的子级一个flex-grow    为1的元素的子级一个flex-grow为1的元素的子级
          </div>
      </div>
  </div>
  ```

  css:

  ```
  .box {
      display: flex;
      align-items: center;
      padding: 40px 20px;
      color: white;
      background-color: black;
  }
  
  .item {
      flex-grow: 1;
      width: 100%;
      height: 60px;
      line-height: 60px;
      text-align: center;
      background-color: #ff0000;
  }
  
  .text {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
  }
  
  .other {
      flex-shrink: 0;
      display: inline-block;
      width: 150px;
      height: 60px;
      line-height: 60px;
      background-color: orange;
  }
  ```

  大跌眼镜的事就这么发生了，flex-grow元素的子级居然撑破了父级的宽度，超出去了，不知道该怎么解释这种现象：
  ![clipboard.png](https://segmentfault.com/img/bVBU0M?w=510&h=234)
  ![clipboard.png](https://segmentfault.com/img/bVBU0N?w=522&h=139)

  解决方案就是，flex-grow元素设置overflow: hidden;效果：

  ![clipboard.png](https://segmentfault.com/img/bVBU2f?w=505&h=142)

  最后一个小坑，算不上坑，就是父级设置了flex布局后，子元素就算是行内元素很多浏览器可以把它当做inline-block或者block元素来用，可以直接设置它的宽高，但是还是有些浏览器不支持，所以要设置行内元素的宽度，还是手动设置一下它的display为inline-block或者block

+ **其他等待我们发现的各种鬼畜**

---

## 补充材料

### 布局类型

- 静态布局：

  传统布局，屏幕宽高变化时，盒子使用横向或者竖向的滚动条来查看被遮挡部分，也就是不管浏览器窗口的大小怎么变化就按html语义标签排列的布局来布置

- 弹性布局：

  css3引入的，flex布局；优点在于其容易上手，根据flex规则很容易达到某个布局效果，然而缺点是：浏览器兼容性比较差，只能兼容到ie9及以上

- 自适应布局：

  分别为不同的屏幕分辨率定义布局，在每个布局中，页面元素不随窗口大小的调整而发生变化，当窗口大小到达一定分辨率时变化一次

- 流式布局：

  页面元素的宽度按照屏幕进行适配调整，元素的位置不变，大小变化，屏幕太大或者太小导致元素不能正常显示

- 响应式布局：

  <meta name="viewport" content="divice-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no">

  使用meta标签设置，页面元素宽度随窗口调整自动适配。主要属性及其含义如下：name="viewport"：   名称=视图；width=device-width 页面宽度=设备宽度(可以理解为获取你手机的屏幕宽度)；initial-scale - 初始的缩放比例  ；minimum-scale - 允许用户缩放到的最小比例   ；maximum-scale - 允许用户缩放到的最大比例  ；user-scalable - 用户是否可以手动缩放

- 网格(grid)布局：

  二维布局系统，随意的定义每行每列的数目和大小。也非常简单方便，兼容性较差

---

### 推荐学习材料

- [](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html) **阮一峰** **Flex语法**
- [](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html) **阮一峰 Flex实例**
- [](https://www.runoob.com/w3cnote/flex-grammar.html) **菜鸟教程**
- [](https://www.w3cschool.cn/flex/) **W3Cschool**
- **更多精彩，等你来找**





**最后**

**感谢大家的配合，本人才疏学浅，讲解过程中难免有错误，谢谢支持🙏**