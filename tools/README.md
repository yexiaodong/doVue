# 工具
::: tip
工具类的js路径：src/tools
:::
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
- 作用：声明路由守卫的方法
- 该方法js只负责声明守卫方法
- [官网：路由守卫](https://router.vuejs.org/zh/guide/advanced/navigation-guards.html#全局前置守卫)
:::
**声明**
```js
function currentTrain(to, form, next){
    let obj = store.getters['train/getCurrentTrain'];
    console.log('路由守卫，currentTrain：',obj);
    if(obj.planId == ''){
        next(false);
        //Toast('用户没有进行中的培训');
        store.dispatch("train/asyncCurrentTrain");
    }
    else{
        next();
    }
}
...
export default {
    currentTrain,
    ...
}
```
**使用（全局）**
```js
//全局路由守卫
import guard from './tools/guard';
router.beforeEach(guard.backButton)
router.beforeEach(guard.switchSolatiumByType)
router.beforeEach(guard.menuClickLog)
```
**使用（独享）**
```js
{
    path: '/feedbackFormLogistic/:id',
    name: 'feedbackFormLogistic',
    component: () => import('./views/feedback/FormLogistic.vue'),
    beforeEnter: guard.currentTrain
},
```

## 异步请求
::: tip
- 文件名称：http.js
- 作用：封装的异步请求（可根据项目实际需求修改）
- 注意：如果在头部添加请求参数（如：token等）会导致请求发送两次，这是浏览器机制问题，无法避免。
:::
**使用**
```js
//GET
getListForCreater(obj){
    return http({
        url:'App_Interface/Repast.ashx',
        method: 'get',
        params:{
            ...obj,
        }
    })
},

//POST
postLogin(obj) {
    return http({
        url: '/api/sys/user/login',
        method: 'post',
        data: obj
    })
},

//POST form-data方式
postLogin(obj) {
    obj = qs.stringify(obj);
    return http({
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
        },
        url: '/api/sys/user/login',
        method: 'post',
        data: obj
    })
},

//POST 站群的form-data  
//args: {"PageNo":1,"PageSize":52,"ClassifyID":"15a47d1e-ed02-4dba-adf5-f514f955978b"}
getColumnInfo(obj){
    obj = {
        args:JSON.stringify(obj)
    }
    return http({
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
        },
        url:'/Ashx/PostHandler.ashx?action=PotralColumn-GetColumnInfo',
        method:'post',
        data:qs.stringify(obj)
    })
},
```

## 加密
::: tip
- 文件名称：jsencrypt.js
- 作用：登陆接口参数加密
:::
**使用**
```js
//导入
import jsencrypt from '@/tools/jsencrypt.js'
//使用
jsencrypt.getData(this.user.username)
```

## link封装
::: tip
- 文件名称：moblie.js
- 作用：针对港城警务APP的特殊封装
:::
**使用（main.js）**
```js
//个人信息
import { mobile } from '@/tools/mobile.js';
mobile.init();
```
## H5缓存
::: tip
- 文件名称：storage.js
- 作用：localStorage缓存封装
:::
**使用**
```js
//导入
import { storage } from '@/tools/storage.js'
...
//使用
storage.remove('user');
```

## 表单验证
::: tip
- 文件名称：veeValidate.js
- 作用：表单验证
:::
具体使用可以参考霞山随手拍项目
**导入 (main.js)**
```js
//表单验证
import '@/tools/veeValidate'
```
**使用**
```html
<ValidationObserver ref="form" v-slot="{validate}">
    <van-cell-group>
        <ValidationProvider rules="required" name="用户名" v-slot="{ errors }">
            <van-field placeholder="请输入用户名" left-icon="contact" v-model="user.username" :error-message="errors[0]" />
        </ValidationProvider>
    </van-cell-group>
    <van-cell-group>
        <ValidationProvider rules="required" name="密码" v-slot="{ errors }">
            <van-field placeholder="请输入密码" type="password" left-icon="closed-eye" v-model="user.password" :error-message="errors[0]" />
        </ValidationProvider>
    </van-cell-group>
</ValidationObserver>
<van-button type="primary" @click="submit()">登陆</van-button>
```