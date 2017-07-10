# CSS 样式书写规范

## 编码设置

采用 `UTF-8` 编码，在 CSS 代码头部使用：

```CSS
@charset "utf-8";
```

> 注意，必须要定义在 CSS 文件**所有字符的前面**（包括编码注释），`@charset` 才会生效。

例如，下面的例子都会使得 `@charset` 失效：

```CSS
/* 字符编码 */
@charset "utf-8";
```
```CSS
html,
body {
  height: 100%;
}

@charset "utf-8";
```

## 命名空间规范

+ 布局：以 g 为命名空间，例如：.g-wrap 、.g-header、.g-content。
+ 状态：以 s 为命名空间，表示动态的、具有交互性质的状态，例如：.s-current、s-selected。
+ 工具：以 u 为命名空间，表示不耦合业务逻辑的、可复用的的工具，例如：u-clearfix、u-ellipsis。
+ 组件：以 m 为命名空间，表示可复用、移植的组件模块，例如：m-slider、m-dropMenu。
+ 钩子：以 j 为命名空间，表示特定给 JavaScript 调用的类名，例如：j-request、j-open。

#### 命名空间思想

没有选择 `BEM` 这种命名过于严苛及样式名过长过丑的规则，采取了一种比较折中的方案。

## 选择器


当一个规则包含多个选择器时，每个选择器独占一行。

>、+、~、> 选择器的两边各保留一个空格。

```CSS
.g-header > .g-header-des,
.g-content ~ .g-footer {
    
}
```

## 规则声明块

+ 当规则声明块中有多个样式声明时，每条样式独占一行。
+ 在规则声明块的左大括号 { 前加一个空格。
+ 在样式属性的冒号 : 后面加上一个空格，前面不加空格。
+ 在每条样式后面都以分号 ; 结尾。
+ 规则声明块的右大括号 } 独占一行。
+ 每个规则声明间用空行分隔。
+ 所有最外层引号使用单引号 ' 。
+ 当一个属性有多个属性值时，以逗号 , 分隔属性值，每个逗号后添加一个空格。

##  数值与单位

+ 当属性值或颜色参数为 0 - 1 之间的数时，省略小数点前的 0 。
```CSS
{
    color: rgba(255, 255, 255, .5);
}
```
+ 当长度值为 0 时省略单位。
```CSS
{
    margin: 0 auto;
}
```
+ 十六进制的颜色属性值使用小写和尽量简写。
```CSS
{
    color: #fc0;
}
```

## 样式属性顺序

+ 同一 rule set 下的属性在书写时，应按功能进行分组，并以 Positioning Model > Box Model > Typographic > Visual 的顺序书写，以提高代码的可读性。
+ Positioning Model 布局方式、位置；相关属性包括：position / top / right / bottom / left / z-index / display / float / ...
+ Box Model 盒模型；相关属性包括：width / height / padding / margin / border / overflow / ...
+ Typographic 文本排版；相关属性包括：font / line-height / text-align / word-wrap / ...
+ Visual 视觉外观；相关属性包括：color / background / list-style / transform / animation / transition / ...
+ 如果包含 content 属性，应放在最前面；

Positioning 处在第一位，因为他可以使一个元素脱离正常文本流，并且覆盖盒模型相关的样式。盒模型紧跟其后，因为他决定了一个组件的大小和位置。其他属性只在组件内部起作用或者不会对前面两种情况的结果产生影响，所以他们排在后面。


## 嵌套层级规定

建议嵌套层级不超过3层

## 代码注释

### 单行注释

星号与内容之间必须保留一个空格。

```CSS
/* 表格隔行变色 */
```

### 多行注释

星号要一列对齐，星号与内容之间必须保留一个空格。

```CSS
/**
 * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
 */
```

### 规则声明块内注释

使用 // 注释，// 后面加上一个空格，注释独立一行。

```CSS
.foo{
    border: 0;
    // ....
}
```

### 文件注释

文件顶部必须包含文件注释，用 @name 标识文件说明。星号要一列对齐，星号与内容之间必须保留一个空格，标识符冒号与内容之间必须保留一个空格。
```
/**
 * @name: 文件名或模块名
 * @description: 文件或模块描述
 * @author: author-name(mail-name@domain.com)
 *          author-name2(mail-name2@domain.com)
 * @update: 2015-04-29 00:02
 */
```
+ @description为文件或模块描述。
+ @update为可选项，建议每次改动都更新一下。

当该业务项目主要由固定的一个或多个人负责时，需要添加@author标识，一方面是尊重劳动成果，另一方面方便在需要时快速定位责任人。
