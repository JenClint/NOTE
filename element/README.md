# [element](https://element.eleme.cn/#/zh-CN/component/installation)

### 引用
#### npm 安装
 推荐使用 npm 的方式安装，它能更好地和 webpack 打包工具配合使用。
    
    npm i element-ui -S

#### CDN
 目前可以通过 unpkg.com/element-ui 获取到最新版本的资源，在页面上引入 js 和 css 文件即可开始使用。

    <!-- 引入样式 -->
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
    <!-- 引入组件库 -->
    <script src="https://unpkg.com/element-ui/lib/index.js"></script>

#### hello world

#### vue-cli
    vue create my-app
    cd my-app
    vue add element

#### 使用 Starter Kit
 通用的项目[模板](https://github.com/ElementUI/element-starter)
 Laravel[模板](https://github.com/ElementUI/element-in-laravel-starter)

#### 引入 Element
 引入整个 Element，在main.js中写入以下内容：

    import Vue from 'vue';
    import ElementUI from 'element-ui';
    import 'element-ui/lib/theme-chalk/index.css';
    import App from './App.vue';
    
    Vue.use(ElementUI);

    new Vue({
    el: '#app',
    render: h => h(App)
    });

 也可只引入需要的组件，以达到减小项目体积的目的

