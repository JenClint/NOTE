## 一、 [Vue.js](https://cn.vuejs.org/)简介 
### 1. Vue.js是什么
  **Vue.js**也称为Vue，读音/vju:/，类似view，错误读音v-u-e
  版本：v1.0 v2.0

  + 是一个构建用户界面的框架
  + 是一个轻量级MVVM（Model-View-ViewModel）框架，和angular、react类似，其实就是所谓的数据双向绑定
  + 数据驱动+组件化的前端开发（核心思想）
  + 通过简单的API实现**响应式的数据绑定**和**组合的视图组件**
  + 更容易上手、小巧

### 2.vue和angular的区别

#### 2.1 angular
  + 上手较难
  + 指令以ng-xxx开头
  + 所有属性和方法都存储在$scope中
  + 由google维护

#### 2.2 vue
  + 简单、易学、更轻量
  + 指令以v-xxx开头
  + HTML代码+JSON数据，再创建一个vue实例
  + 由个人维护

 共同点：`都不兼容低版本IE`
 对比：GitHub上vue的stars数量大约是angular的两倍


## 二、起步

### 1. 下载核心库vue.js
	bower info vue
	npm init --yes
	cnpm install vue --save
	
	vue2.0和1.0相比，最大的变化就是引入了Virtual DOM（虚拟DOM）,页面更新效率更高，速度更快

### 2. Hello World（对比angular）
	
#### 2.1 angular实现
	js:
		let app=angular.module('myApp',[]);
		app.controller('MyController',['$scope',function($scope){
			$scope.msg='Hello World';
		}]);
	html:	
		<html ng-app="myApp">
			<div ng-controller="MyController">
				{{msg}}
			</div>
		</html>

#### 2.2 vue实现
	js:
		new Vue({
			el:'#itany', //指定关联的选择器
			data:{ //存储数据
				msg:'Hello World',
				name:'tom'
			}
		});
	html:
		<div id="itany">
			{{msg}}
		</div>

### 3. 安装vue-devtools插件，便于在chrome中调试vue
	直接将vue-devtools解压缩，然后将文件夹中的chrome拖放到扩展程序中
    
    //配置是否允许vue-devtools检查代码，方便调试，生产环境中需要设置为false
        Vue.config.devtools=false;
        Vue.config.productionTip=false; //阻止vue启动时生成生产消息


## 三、 常用指令

### 1. 什么是指令
    用来扩展html标签的功能
    angular中常用的指令：
        ng-model
        ng-repeat
        ng-click
        ng-show/ng-hide
        ng-if

### 2. vue中常用的指令
  + v-model
    双向数据绑定，一般用于表单元素

  + v-for
    对数组或对象进行循环操作，使用的是v-for，不是v-repeat
    注：在vue1.0中提供了隐式变量，如$index、$key
        在vue2.0中去除了隐式变量，已被废除

  + v-on 
    用来绑定事件，用法：v-on:事件="函数"

  + v-show/v-if   
    用来显示或隐藏元素，v-show是通过display实现，v-if是每次删除后再重新创建，与angular中类似 

## 四、 事件和属性

### 1. 事件

#### 1.1 事件简写
    v-on:click=""    
    简写方式 @click=""

#### 1.2 事件对象$event    
    包含事件相关信息，如事件源、事件类型、偏移量
    target、type、offsetx

#### 1.3 事件冒泡
    阻止事件冒泡：
        a)原生js方式，依赖于事件对象
        b)vue方式，不依赖于事件对象
            @click.stop

#### 1.4 事件默认行为 
    阻止默认行为：
        a)原生js方式，依赖于事件对象

#### 1.5 键盘事件
    回车：@keydown.13 或@keydown.enter
    上：@keydown.38 或@keydown.up

    默认没有@keydown.a/b/c...事件，可以自定义键盘事件，也称为自定义键码或自定义键位别名

#### 1.6 事件修饰符    
    .stop - 调用 event.stopPropagation()。
    .prevent - 调用 event.preventDefault()。
    .{keyCode | keyAlias} - 只当事件是从特定键触发时才触发回调。
    .native - 监听组件根元素的原生事件。
    .once - 只触发一次回调。

### 2. 属性
    
#### 2.1 属性绑定和属性的简写
    v-bind 用于属性绑定， v-bind:属性=""

    属性的简写：
        v-bind:src="" 简写为 :src=""

#### 2.2 class和style属性
    绑定class和style属性时语法比较复杂：

    <!-- class属性 -->
    <!-- <p class="aa">南京网博</p> -->  <!-- 可以访问，普通css方式 -->

    <!-- <p :class="aa">南京网博</p> --> <!-- 不可以，Vue的属性绑定时不能直接css样式 -->

    <!-- 方式1:变量形式 -->
    <!-- <p :class="bb">南京网博</p> -->

    <!-- 方式2：数组形式，同时引用多个 -->
    <!-- <p :class="[bb,dd]">南京网博</p> -->

    <!-- 方式3：json形式，常用！！！ -->
    <!-- <p :class="{aa:true,cc:flag}">南京网博</p> -->
    <!-- <p :class="{aa:num>0}">南京网博</p> -->

    <!-- 方式4：变量引用json形式 -->
    <!-- <p :class="hello">南京网博</p> -->
    
    <!-- style属性 -->
    <p :style="[xx,yy]">itany</p>


## 五、 模板

### 1. 简介
    Vue.js使用基于HTML的模板语法，可以将DOM绑定到Vue实例中的数据
    模板就是{{}}，用来进行数据绑定，显示在页面中
    也称为Mustache语法

### 2. 数据绑定的方式
    a.双向绑定
        v-model
    b.单向绑定    
        方式1：使用两对大括号{{}}，可能会出现闪烁的问题，可以使用v-cloak解决
        方式2：使用v-text、v-html

### 3. 其他指令
    v-once 数据只绑定一次
    v-pre 不编译，直接原样显示


## 六、 过滤器

### 1. 简介
    用来过滤模型数据，在显示之前进行数据处理和筛选
    语法：{{ data | filter1(参数) | filter2(参数)}}

### 2. 关于内置过滤器
    vue1.0中内置许多过滤器，如：
        currency、uppercase、lowercase
        limitBy
        orderBy
        filterBy
    vue2.0中已经删除了所有内置过滤器，全部被废除
    如何解决：
        a.使用第三方工具库，如lodash、date-fns日期格式化、accounting.js货币格式化等
        b.使用自定义过滤器

### 3. 自定义过滤器
    分类：全局过滤器、局部过滤器

#### 3.l 自定义全局过滤器
    使用全局方法Vue.filter(过滤器ID,过滤器函数)

    Vue.filter('addZero',function(data){
			// console.log(data);
			return data<10?'0'+data:data;
		});
		/*Vue.filter('number',(data,n) => {
			// console.log(data,n);
			return data.toFixed(n);
		});*/
		Vue.filter('date',data => {
			let d=new Date(data);
			return d.getFullYear()+'-'+(d.getMonth()+1)+'-'+d.getDate()+' '+d.getHours()+':'+d.getMinutes()+':'+d.getSeconds();
		});
    
    let vm=new Vue({
				el:'#itany',
				data:{
					currentTime:Date.now()
				},
				filters:{ //局部过滤器
					number:(data,n) => {
						return data.toFixed(n);
					}
				}
			});


## 七、 发送AJAX请求

### 1. 简介
    vue本身不支持发送AJAX请求，需要使用vue-resource、axios等插件实现
    axios是一个基于Promise的HTTP请求客户端，用来发送请求，也是vue2.0官方推荐的，同时不再对vue-resource进行更新和维护
    
    参考：GitHub上搜索axios，查看API文档

### 2. 使用axios发送AJAX请求

#### 2.1 安装axios并引入
    npm install axios -S
    也可直接下载axios.min.js文件

#### 2.2 基本用法  
    axios([options])  
    axios.get(url[,options]);
        传参方式：
            1.通过url传参
            2.通过params选项传参
    axios.post(url,data,[options]);
        axios默认发送数据时，数据格式是Request Payload，并非我们常用的Form Data格式，
        所以参数必须要以键值对形式传递，不能以json形式传参
        传参方式：
            1.自己拼接为键值对
            2.使用transformRequest，在请求发送前将请求数据进行转换
            3.如果使用模块化开发，可以使用qs模块进行转换
    
    axios本身并不支持发送跨域的请求，没有提供相应的API，作者也暂没计划在axios添加支持发送跨域请求，所以只能使用第三方库

### 3. 使用vue-resource发送跨域请求

#### 3.1 安装vue-resource并引入    
    cnpm install vue-resource -S

#### 3.2 基本用法
    使用this.$http发送请求  
        this.$http.get(url, [options])
        this.$http.head(url, [options])
        this.$http.delete(url, [options])
        this.$http.jsonp(url, [options])
        this.$http.post(url, [body], [options])
        this.$http.put(url, [body], [options])
        this.$http.patch(url, [body], [options])  


## 八、Vue生命周期
    vue实例从创建到销毁的过程，称为生命周期，共有八个阶段
  <img src="https://github.com/JenClint/NOTE/blob/master/img/lifecycle.png" width = "50%" />
  

## 九、计算属性

### 1. 基本用法
    计算属性也是用来存储数据，但具有以下几个特点：
        a.数据可以进行逻辑处理操作
        b.对计算属性中的数据进行监视

### 2.计算属性 vs 方法
    将计算属性的get函数定义为一个方法也可以实现类似的功能
    区别：
        a.计算属性是基于它的依赖进行更新的，只有在相关依赖发生改变时才能更新变化
        b.计算属性是缓存的，只要相关依赖没有改变，多次访问计算属性得到的值是之前缓存的计算结果，不会多次执行

### 3. get和set
    计算属性由两部分组成：get和set，分别用来获取计算属性和设置计算属性
    默认只有get，如果需要set，要自己添加
    num2:{
        get:function(){
            console.log('num2：'+new Date());
            return this.num1-1;
        },
        set:function(val){
            // console.log('修改num2值');
            // this.num2=val;
            this.num1=111;
        }
    }


## 十、 vue实例的属性和方法

### 1. 属性
    vm.$el
    vm.$data
    vm.$options
    vm.$refs

### 2. 方法
    vm.$mount()
    vm.$destroy()
    vm.$nextTick(callback)

    vm.$set(object,key,value)
    vm.$delete(object,key)
    vm.$watch(data,callback[,options])


## 十一、自定义指令
    分类：全局指令、局部指令

### 1. 自定义全局指令
    使用全局方法Vue.directive(指令ID,定义对象)
    注：使用指令时必须在指名名称前加前缀v-，即v-指令名称
    bind(){ //常用！！
				alert('指令第一次绑定到元素上时调用，只调用一次，可执行初始化操作');
			},
    inserted(){
        alert('被绑定元素插入到DOM中时调用');
    },
    update(){
        alert('被绑定元素所在模板更新时调用');
    },
    componentUpdated(){
        alert('被绑定元素所在模板完成一次更新周期时调用');
    },
    unbind(){
        alert('指令与元素解绑时调用，只调用一次');
    }

    //钩子函数的参数
    Vue.directive('world',{
        bind(el,binding){
            // console.log(el); //指令所绑定的元素，DOM对象
            // el.style.color='red';

            console.log(binding); //name
        }
    });

### 3. 练习
    拖动页面中的元素
    onmouseover onmouseout 
    onmousedown onmousemove  onmouseup

    Vue.directive('drag',function(el){
        el.onmousedown=function(e){
            //获取鼠标点击处分别与div左边和上边的距离：鼠标位置-div位置
            var disX=e.clientX-el.offsetLeft;
            var disY=e.clientY-el.offsetTop;
            console.log(disX,disY);

            //包含在onmousedown里面，表示点击后才移动，为防止鼠标移出div，使用document.onmousemove
            document.onmousemove=function(e){
                //获取移动后div的位置：鼠标位置-disX/disY
                console.log(111);
                var l=e.clientX-disX;
                var t=e.clientY-disY;
                el.style.left=l+'px';
                el.style.top=t+'px';
            }

            //停止移动
            document.onmouseup=function(e){
                document.onmousemove=null;
                document.onmouseup=null;
            }

        }
    });


## 十二、过渡(动画)

### 1. 简介
    Vue 在插入、更新或者移除 DOM 时，提供多种不同方式的应用过渡效果
    本质上还是使用CSS3动画：transition、animation

### 2. 基本用法
    使用transition组件，将要执行动画的元素包含在该组件内
        <transition>
            运动的元素
        </transition>       
    过滤的CSS类名：6个
            @before-enter="beforeEnter"
			@enter="enter"
			@after-enter="afterEnter"
			@before-leave="beforeLeave"
			@leave="leave"
			@after-leave="afterLeave"

### 3. 结合第三方动画库animate..css一起使用
    <transition enter-active-class="animated fadeInLeft" leave-active-class="animated fadeOutRight">
        <p v-show="flag">网博</p>
    </transition>    

### 4. 多元素动画
    <transition-group>

    <transition-group enter-active-class="animated bounceInLeft" leave-active-class="animated bounceOutRight">
        <p v-show="flag" :key="1">itany</p>
        <p v-show="flag" :key="2">网博</p>
    </transition-group>
 
  




















































