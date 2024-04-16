### flex 布局-弹性盒子



> 基本概念

采用 flex 布局的盒子，称之为弹性盒子，弹性盒子的子元素自动作为其容器成员，弹性盒子可以自由设置其对其主轴。

容器默认有两个主轴：水平轴和垂直轴



> 基本属性

- flex-direction
  - row：默认值，默认排列方向水平，方向从左往右
  - row-reverse：主轴为水平轴，方向从右向左
  - column：主轴为垂直轴，方向从上往下
  - column-reverse：主轴为垂直轴，方向从下往上
- flex-wrap
  - 描述：默认情况下，弹性盒子按照排列主轴方向排列，flex-wrap 属性定义如果一条轴线排列不下时，如何换行
  - nowrap：不换行
  - wrap：换行，第一行在上方
  - wrap-reverse：换行，第一行在下方
- flex-flow
  - 描述：属性为 flex-direction 和 flex-wrap 的缩写
- justify-content
  - 描述：定义水平主轴的对齐方式
  - flex-start：左对齐
  - flex-end：右对齐
  - center：居中
  - space-between：两端对齐，子项目之间的间隔相等
  - space-around：环绕
- align-items
  - 描述：定义垂直主轴的对齐方向
  - flex-start：垂直轴的起点对齐
  - flex-end：垂直轴的终点对齐
  - center：垂直轴的居中对齐
  - baseline：项目的第一行文字的基线对齐
  - stretch：默认值，未设置高度或是auto，则占满整个高度
- align-content
  - 描述：属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用



> 子项属性

- order：排列顺序，数值越小越靠前
- flex-grow：定义项目的放大比例，这里指的是剩余可支配的空间的比例放大，默认是0，即如果存在剩余空间也不放大
- flex-shrink：定义子项目的收缩规则，只有当元素的默认宽度（不包括flex-grow的剩余支配空间）之和大于容器的时候才会发生收缩
- flex-basis：定义在分配多余空间之前占据的主轴空间
  - auto：默认，即项目的本来的大小
  - <length>：具体的宽度
- flex：flex-grow flex-shrink flex-basis 的缩写，后两者可选
- align-self
  - 描述：该属性允许单个项目可以有与其他项目不一样的对其方式
  - auto | flex-start | flex-end | center | baseline | stretch