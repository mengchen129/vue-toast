# vue-toast

A Toast Component by Vue.js

## 实例

http://182.92.167.237/pages/vue-toast/

## 功能
- 在固定底部未知弹出toast信息
- 一次只展示一个toast, 后执行的toast会覆盖前一个

## 用法

在根组件注册:
```html
<toast v-ref:toast></toast>  <!-- vue 1.0 -->
<toast ref="toast"></toast>  <!-- vue 2.0 -->
```

在js中注册:
```javascript
import Toast from './Toast.vue';
Vue.component(Toast.name, Toast);
```

在实例中调用:
```javascript
this.$refs.toast.show('message');     // 弹出toast (默认3秒)
this.$refs.toast.show('message', 1000);     // 弹出toast 1秒后消失
```

外部调用:

```javascript
import Utils from './Utils';
Utils.invoke('toast', 'message', 2000);
```
采用类似Event Bus的模式, Toast组件在ready/mounted时在公共模块Utils中注册show方法, 可供其他组件或外部JS文件进行调用.

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
