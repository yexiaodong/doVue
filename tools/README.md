# 工具

## JS变量
::: tip
- 文件名称：config.js
- 作用：全局js变量
:::
```js
export default{
    BASE_API:process.env.VUE_APP_BASE_API,
    VERSION:process.env.BUILD_DATE,
    IS_SHOW_SPLASH:process.env.VUE_APP_IS_SHOW_SPLASH,
    IMG_IP:process.env.VUE_APP_IMG_IP,

    TIPS_NO_DATA:'查无数据！',
    TIPS_SCROLL_BOTTOM:'已到达底部！'
}
```
### 环境变量
1. BASE_API，接口域名
2. VERSION，版本
3. IS_SHOW_SPLASH，是否使用启动图
4. IMG_IP，图片域名
### 常量
1. TIPS_NO_DATA，无数据的描述
2. TIPS_SCROLL_BOTTOM，底部描述

## 公共方法
::: tip
- 文件名称：do.js
- 作用：全局js方法
:::
**引入（main.js）**
```js
import do_ from '@/tools/do.js';
Vue.prototype.dox = do_;
```
**使用**
```js
this.dox.doIsNull(xxx)
```
**方法列表**
| 方法名 | 说明 | 使用场景 |
| ---- |----| -----|:-----:|
| doIsNull | 空判断 | - | Boolen |
| doRichTextChange | 富文本内容处理 | 富文本需要重置视频/图片路径 |
| doArrayConcat | 数组拼接 | - |
| doGetUpdateTime | 时间描述 | 距离当前时间的描述，如：“1周前”、“3分钟前”等描述 |
| doUrlGetParam | 获取url参数 | - |


## 路由守卫
::: tip
- 文件名称：guard.js
- 作用：vue的路由守卫
:::

## 异步请求
::: tip
- 文件名称：http.js
- 作用：全局js变量
:::

## 加密
::: tip
- 文件名称：jsencrypt.js
- 作用：全局js变量
:::

## link封装
::: tip
- 文件名称：moblie.js
- 作用：全局js变量
:::

## H5缓存
::: tip
- 文件名称：storage.js
- 作用：全局js变量
:::

## 表单验证
::: tip
- 文件名称：veeValidate.js
- 作用：全局js变量
:::