# 组件

## Layout 布局组件

::: tip

- 该目录（layout）下的组件为一些基础布局组件
- 组件前缀一般为“L”
  :::

### LGrid

::: tip
九宫格类的组件
:::
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

```html
<l-grid col="3" border="0" :list="girds"></l-grid>
```

**props**
| 参数 | 说明 | 类型 | 默认值 |
| ---- |----| -----|:-----:|
| list | 数据源 | Array | - |
| col | 行数 | String | 3 |
| border |边框记录 | String | 1 |
**数据源例子**

```json
[
  {
    "id": "1",
    "fontIcon": "location",
    "title": "我的申请",
    "link": "/taskApplyList"
  },
  {
    "id": "2",
    "fontIcon": "setting",
    "title": "我的待办",
    "badge": "",
    "link": "/awaitList"
  },
  {
    "id": "3",
    "fontIcon": "fire",
    "title": "我的已办",
    "link": "/taskDoneList"
  }
]
```

fontIcon（vant 的 icon 名称）/icon（svg 图标）/img（图片） 三选一

### LHeader

::: tip
页面头部的组件
:::
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
| ------------- |-------------| -----|:-----:|
| title | 标题 | String | - |
| backBtn | 是否显示返回按钮 | Boolean | true |
| fixed | vant 的 header 组件的布局 | Boolean | true |

**slots**
| 参数 | 说明 |
| -----|---- |
| left |左侧内容 |
| right | 右侧内容 |

### LList
::: tip
列表组件，已经封装了下拉刷新和无限滚动。
:::
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
插槽：list-content，为主要的内容主体。
```html
<l-list ref="list" :load="onLoad" :list="list">
  <tabs-list-item
    slot="list-content"
    v-for="(item,index) in list"
    :key="index"
    :item="item"
  />
</l-list>
```
该组件的使用重点在于 onLoad 方法，方法的参数是分页查询的页码。
```js
export default {
  data() {
    return {
      list: []
    };
  },
  methods: {
    async onLoad(pageIndex) {
      let obj = {
        typeCode: this.columnId,
        pageindex: pageIndex,
        pagesize: 15
      };
      let data = await api.getNewsListByCode(obj);
      if (data.code == "200") {
        if (pageIndex == 1) {
          this.list = data.data;
        } else {
          this.list = this.dox.doArrayConcat(this.list, data.data);
        }
      }
      // 加载状态结束
      this.$refs.list.loading = false;

      // 数据全部加载完成
      if (data.data.length < 15) {
        this.$refs.list.finished = true;
      }
    }
  }
  // ...
};
```
**props**
| 参数 | 说明 | 类型 | 默认值 |
| ---- |----| -----|:-----:|
| load | 获取数据的方法 | Function | - |
| list | 数据源 | Array | - |
**slots**
| 参数 | 说明 |
| -----|---- |
| list-content | 主体内容 |

### LListLink
::: tip
列表导航组件，图标-标题-链接
:::
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
```html
<l-list-link :list="list"></l-list-link>
```
```json
[
  {
    "id": "1",
    "title": "库存信息",
    "item": [
      {
        "id": "2",
        "fontIcon": "setting",
        "title": "我的项目",
        "link": "/baseBuilding"
      }
    ]
  },
  {
    "id": "2",
    "title": "信息",
    "item": [
      {
        "id": "2",
        "fontIcon": "setting",
        "title": "信息中心",
        "link": "/baseBuilding"
      }
    ]
  },
  {
    "id": "3",
    "title": "新闻",
    "item": [
      {
        "id": "1",
        "fontIcon": "setting",
        "title": "新闻资讯",
        "link": "/newsTabs"
      },
      {
        "id": "2",
        "title": "项目档案",
        "fontIcon": "setting",
        "link": "/newsTabs"
      }
    ]
  },
  {
    "id": "4",
    "title": "版本说明",
    "item": [
      {
        "id": "1",
        "fontIcon": "setting",
        "title": "版本说明",
        "link": "/versionDatail"
      },
      {
        "id": "2",
        "fontIcon": "setting",
        "title": "意见反馈",
        "link": "/versionDatail"
      }
    ]
  }
]
```
**props**
| 参数 | 说明 | 类型 | 默认值 |
| ---- |----| -----|:-----:|
| list | 数据源 | Array | - |

### LSlider
::: tip
轮播图组件
:::
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
```html
<do-slider :list="sliderList" :ratio="367/750"></do-slider>
```
**props**
| 参数 | 说明 | 类型 | 默认值 |
| ---- |----| -----|:-----:|
| list | 数据源 | Array | - |
| ratio | 图片的宽高比例 | String | 0.488 |
| showTitle | 标题是否显示 | Boolean | true |
**数据源**
| 参数 | 说明 | 类型 | 默认值 |
| ---- |----| -----|:-----:|
| img | 图片地址 | String | - |
| title | 标题 | String | - |
| link | 跳转链接 | String | - |

### LSplash
::: tip
启动图组件
- 启动图的显示与否，通过环境变量文件控制；
- 若显示启动图，必须自行写设置splash为false的逻辑；
- 该组件一般写在App.vue文件
:::
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
```html
<l-splash v-show="splash == 'yes'"></l-splash>
```
```js
export default {
  data() {
    return {
      splash: this.config.IS_SHOW_SPLASH,
    };
  }
  // ...
};
```
