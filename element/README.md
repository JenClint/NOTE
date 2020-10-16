# [element](https://element.eleme.cn/#/zh-CN/component/installation)

### ����
#### npm ��װ
 �Ƽ�ʹ�� npm �ķ�ʽ��װ�����ܸ��õغ� webpack ����������ʹ�á�
    
    npm i element-ui -S

#### CDN
 Ŀǰ����ͨ�� unpkg.com/element-ui ��ȡ�����°汾����Դ����ҳ�������� js �� css �ļ����ɿ�ʼʹ�á�

    <!-- ������ʽ -->
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
    <!-- ��������� -->
    <script src="https://unpkg.com/element-ui/lib/index.js"></script>

#### hello world

#### vue-cli
    vue create my-app
    cd my-app
    vue add element

#### ʹ�� Starter Kit
 ͨ�õ���Ŀ[ģ��](https://github.com/ElementUI/element-starter)
 Laravel[ģ��](https://github.com/ElementUI/element-in-laravel-starter)

#### ���� Element
 �������� Element����main.js��д���������ݣ�

    import Vue from 'vue';
    import ElementUI from 'element-ui';
    import 'element-ui/lib/theme-chalk/index.css';
    import App from './App.vue';
    
    Vue.use(ElementUI);

    new Vue({
    el: '#app',
    render: h => h(App)
    });

 Ҳ��ֻ������Ҫ��������Դﵽ��С��Ŀ�����Ŀ��

