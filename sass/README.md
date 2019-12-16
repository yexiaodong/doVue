# 样式

## 变量
::: tip
- 文件名称：variable.scss 
- 作用：全局样式变量
:::
```sass
//基础颜色
$color-red:#ff6263;
$color-green:#07c160;
$color-blue:#1989fa;

//常用颜色
$color-primary:$color-blue;//网站主题颜色
$color-border:#f2f2f2; //边框
$color-background:#f2f2f2; //边框
$color-text-desc: #7d7e80; //次要文字
$color-btn:$color-primary; //按钮

//其他颜色

//头部高度
$l-header-height:46px;
  ```


## mixin
::: tip
- 文件名称：mixin.scss 
- 作用：封装常用样式
:::
### 阴影
@include box-shadow-default()
```sass
@mixin box-shadow($x1, $x2, $x3, $x4) {
  box-shadow: $x1 $x2 $x3 $x4;
  -webkit-box-shadow: $x1 $x2 $x3 $x4;
  -moz-box-shadow: $x1 $x2 $x3 $x4;
  -ms-box-shadow: $x1 $x2 $x3 $x4;
  -o-box-shadow: $x1 $x2 $x3 $x4;
}
@mixin box-shadow-default() {
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
  -webkit-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
  -moz-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
  -ms-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
  -o-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
```
### 文字行数控制
@include show-line(2);
```sass
@mixin show-line($x1) {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: $x1;
  -webkit-box-orient: vertical;
}
```
### inline-block
@include inline-block-align-top;
```sass
@mixin inline-block-align-top{
  display: inline-block;
  *zoom:1;
  *display:inline;
  vertical-align:top
}
```

## vant
::: tip
- 文件名称：vant.scss 
- 作用：重置vant UI的样式
:::

```sass
body{
    .van-tabs__line{
        background-color:$color-primary;
    }
}
```