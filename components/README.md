# 目录说明

## Layout 布局组件

::: tip

- 该目录（layout）下的组件为一些基础布局组件
- 组件前缀一般为“L”
  :::


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
| 参数        | 说明           | 类型  | 默认值  |
| ------------- |-------------| -----|-----|
| title      | 标题              | String |  -  |
| backBtn      | 是否显示返回按钮      |   Boolean |  true  |
| fixed | vant 的header组件的布局      |    Boolean |  true  |


### LGrid