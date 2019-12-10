# 目录说明

## Layout 布局组件

::: tip

- 该目录（layout）下的组件为一些基础布局组件
- 组件前缀一般为“L”
  :::

### LGrid
**导入**
```js
import LGrid from "@/components/layout/LGrid.vue";
export default {
  components: {
    LGrid
  }
  // ...
};
```
**基本使用**
**插槽使用**
**props**
**slots**

### LHeader

**导入**
```js
import LHeader from "@/components/layout/LHeader.vue";
export default {
  components: {
    LHeader
  }
  // ...
};
```

**基本使用**

```html
<l-header title="详情"></l-header>
```

**插槽使用**

```html
<l-header title="">
  <span slot="left">美丽奋斗者</span>
  <span slot="right">
    <router-link to="/">
      <van-icon name="search" />
    </router-link>
  </span>
</l-header>
```

**props**
| 参数 | 说明 | 类型 | 默认值 |
| ------------- |-------------| -----|-----|
| title | 标题 | String | - |
| backBtn | 是否显示返回按钮 | Boolean | true |
| fixed | vant 的 header 组件的布局 | Boolean | true |

**slots**
| 参数 | 说明 |
| -----|---- |
| left  |左侧内容 |
| right | 右侧内容 |



### LList
**导入**
```js
import LList from "@/components/layout/LList.vue";
export default {
  components: {
    LList
  }
  // ...
};
```
**基本使用**
**插槽使用**
**props**
**slots**


### LListLink
**导入**
```js
import LListLink from "@/components/layout/LListLink.vue";
export default {
  components: {
    LListLink
  }
  // ...
};
```
**基本使用**
**插槽使用**
**props**
**slots**


### LListLink
**导入**
```js
import LListLink from "@/components/layout/LListLink.vue";
export default {
  components: {
    LListLink
  }
  // ...
};
```
**基本使用**
**插槽使用**
**props**
**slots**


### LSlider
**导入**
```js
import LSlider from "@/components/layout/LListLink.vue";
export default {
  components: {
    LSlider
  }
  // ...
};
```
**基本使用**
**插槽使用**
**props**
**slots**

### LSplash
**导入**
```js
import LSplash from "@/components/layout/LSplash.vue";
export default {
  components: {
    LSplash
  }
  // ...
};
```
**基本使用**
**插槽使用**
**props**
**slots**

