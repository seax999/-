> BFC(Block Formatting Context)，块级格式化上下文，是一个独立的渲染区域，让处于 BFC 内部的元素与外部的元素相互隔离，使内外元素的定位不会相互影响

要创建一个块级格式化上下文（BFC），可以应用以下方法：

1. 使用`float`属性：将元素的`float`属性设置为除`none`以外的值，可以创建一个BFC。
2. 使用`overflow`属性：将元素的`overflow`属性设置为除`visible`以外的值，例如`auto`或`hidden`，可以创建一个BFC。
3. 使用`display`属性：将元素的`display`属性设置为`inline-block`、`table-cell`、`table-caption`等特定的值，可以创建一个BFC。
4. 使用`position`属性：将元素的`position`属性设置为`absolute`、`fixed`、`relative`或`sticky`，可以创建一个BFC。
5. 使用`contain`属性：将元素的`contain`属性设置为`layout`，可以创建一个BFC（仅适用于部分浏览器）。

> 在`IE`下, `Layout`,可通过`zoom:1` 触发

**BFC布局与普通文档流布局区别 普通文档流布局:**

- 浮动的元素是不会被父级计算高度
- 非浮动元素会覆盖浮动元素的位置
- `margin`会传递给父级元素
- 两个相邻元素上下的`margin`会重叠

**BFC布局规则:**

- 浮动的元素会被父级计算高度(父级元素触发了`BFC`)
- 非浮动元素不会覆盖浮动元素的位置(非浮动元素触发了`BFC`)
- `margin`不会传递给父级(父级触发`BFC`)
- 属于同一个`BFC`的两个相邻元素上下`margin`会重叠

**开发中的应用**

- 阻止`margin`重叠
- 可以包含浮动元素 —— 清除内部浮动(清除浮动的原理是两个 `div`都位于同一个 `BFC` 区域之中)
- 自适应两栏布局
- 可以阻止元素被浮动元素覆盖





> 触发 hasLayout 是