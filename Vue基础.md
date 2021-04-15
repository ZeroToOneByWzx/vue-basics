

## 一、 Vue.js简介

### 1. Vue.js是什么
  **Vue.js**也称为Vue，读音/vju:/，类似view，错误读音v-u-e
>  版本：v1.0 v2.0

- 是一个构建用户界面的框架
- 是一个轻量级MVVM（Model-View-ViewModel）框架，和angular、react类似，其实就是所谓的数据双向绑定
- 数据驱动+组件化的前端开发（核心思想）
- 通过简单的API实现**响应式的数据绑定**和**组合的视图组件**
- 更容易上手、小巧

参考：[官网](https://cn.vuejs.org/)

**<kbd>不兼容低版本IE</kbd>**


## 二、起步

### 1. 下载核心库vue.js
	bower info vue
	npm init --yes
	cnpm install vue --save
	版本 v2.3.4 目前最新版本(2017.6.29)
	
	vue2.0和1.0相比，最大的变化就是引入了Virtual DOM（虚拟DOM）,页面更新效率更高，速度更快

  


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


## 四、 练习：用户管理 
    使用BootStrap+Vue.js   


## 五、 事件和属性

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


## 六、 模板

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


## 七、 过滤器

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

#### 3.l 自定义局部过滤器    




## 一、 发送AJAX请求

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

### 4. 练习
    百度搜索列表
    课后作业：
        1.只显示4条
        2.回车后在新页面中显示搜索结果


## 二、Vue生命周期
    vue实例从创建到销毁的过程，称为生命周期，共有八个阶段






## 四、 vue实例的属性和方法

### 1. 属性
```vue
vm.$el
vm.$data
vm.$options
vm.$refs
```

### 2. 方法
    vm.$mount()
    vm.$destroy()
    vm.$nextTick(callback)
    
    vm.$set(object,key,value)
    vm.$delete(object,key)
    vm.$watch(data,callback[,options])


## 五、自定义指令
    分类：全局指令、局部指令

### 1. 自定义全局指令
    使用全局方法Vue.directive(指令ID,定义对象)    

### 2. 自定义局部指令

### 3. 练习
    拖动页面中的元素
    onmouseover onmouseout 
    onmousedown onmousemove  onmouseup


## 六、过渡(动画)

### 1. 简介
    Vue 在插入、更新或者移除 DOM 时，提供多种不同方式的应用过渡效果
    本质上还是使用CSS3动画：transition、animation

### 2. 基本用法
    使用transition组件，将要执行动画的元素包含在该组件内
        <transition>
            运动的元素
        </transition>       
    过滤的CSS类名：6个

### 3. 钩子函数
    8个

### 4. 结合第三方动画库animate..css一起使用
    <transition enter-active-class="animated fadeInLeft" leave-active-class="animated fadeOutRight">
        <p v-show="flag">网博</p>
    </transition>    

### 5. 多元素动画
    <transition-group>    

### 6. 练习
    多元素动画    


## 五、 单文件组件

### 1. .vue文件
    .vue文件，称为单文件组件，是Vue.js自定义的一种文件格式，一个.vue文件就是一个单独的组件，在文件内封装了组件相关的代码：html、css、js
    
    .vue文件由三部分组成：<template>、<style>、<script>
        <template>
            html
        </template>
    
        <style>
            css
        </style>
    
        <script>
            js
        </script>

### 2. vue-loader  
    浏览器本身并不认为.vue文件，所以必须对.vue文件进行加载解析，此时需要vue-loader
    类似的loader还有许多，如：html-loader、css-loader、style-loader、babel-loader等
    需要注意的是vue-loader是基于webpack的     

### 3. webpack
    webpack是一个前端资源模板化加载器和打包工具，它能够把各种资源都作为模块来使用和处理
    实际上，webpack是通过不同的loader将这些资源加载后打包，然后输出打包后文件 
    简单来说，webpack就是一个模块加载器，所有资源都可以作为模块来加载，最后打包输出
    
    [官网](http://webpack.github.io/)     
    
    webpack版本：v1.x v2.x
    
    webpack有一个核心配置文件：webpack.config.js，必须放在项目根目录下

### 4. 示例，步骤：

#### 4.1 创建项目，目录结构 如下：
webpack-demo
    |-index.html
    |-main.js   入口文件       
    |-App.vue   vue文件
    |-package.json  工程文件（npm init --yes）
    |-webpack.config.js  webpack配置文件
    |-.babelrc   Babel配置文件

### 4.2 编写App.vue
	<template> </template>
	
	<script> </script>
	
	<style> </style>
### 4.3 安装相关模板    
    cnpm install vue -S
    
    cnpm install webpack -D
    cnpm install webpack-dev-server -D
    
    cnpm install vue-loader -D
    cnpm install vue-html-loader -D
    cnpm install css-loader -D
    cnpm install vue-style-loader -D
    cnpm install file-loader -D
    
    cnpm install babel-loader -D
    cnpm install babel-core -D
    cnpm install babel-preset-env -D  //根据配置的运行环境自动启用需要的babel插件
    cnpm install vue-template-compiler -D //预编译模板
    
    合并：cnpm install -D webpack webpack-dev-server vue-loader vue-html-loader css-loader vue-style-loader file-loader babel-loader babel-core babel-preset-env  vue-template-compiler

### 4.4 编写main.js    

### 4.5 编写webpack.config.js

### 4.6 编写.babelrc    

### 4.7 编写package.json

### 4.8 运行测试
    npm run dev    


## 六、 vue-cli脚手架 

### 1. 简介
    vue-cli是一个vue脚手架，可以快速构造项目结构
    vue-cli本身集成了多种项目模板：
        simple  很少简单
        webpack 包含ESLint代码规范检查和unit单元测试等
        webpack-simple 没有代码规范检查和单元测试
        browserify 使用的也比较多
        browserify-simple

### 2. 示例，步骤：

#### 2.1 安装vue-cli，配置vue命令环境 
    cnpm install vue-cli -g
    vue --version
    vue list

#### 2.2 初始化项目，生成项目模板
    语法：vue init 模板名  项目名

#### 2.3 进入生成的项目目录，安装模块包
    cd vue-cli-demo
    cnpm install

#### 2.4 运行
    npm run dev  //启动测试服务
    npm run build //将项目打包输出dist目录，项目上线的话要将dist目录拷贝到服务器上

### 3. 使用webpack模板
    vue init webpack vue-cli-demo2
    
    ESLint是用来统一代码规范和风格的工具，如缩进、空格、符号等，要求比较严格
[官网](http://eslint.org)    

    问题Bug：如果版本升级到node 8.0 和 npm 5.0，控制台会报错：
        GET http://localhost:8080/__webpack_hmr net::ERR_INCOMPLETE_CHUNKED_ENCODING
    解决方法：
        a)降低Node版本到7.9或以下
        b)修改build/dev-server.js文件，如下：
            var hotMiddleware = require('webpack-hot-middleware')(compiler, {
              log: () => {},
              heartbeat:2000 //添加此行
            })
        参考：https://github.com/vuejs-templates/webpack/issues/731    






## 一、模块化开发

### 1. vue-router模块化
    cnpm install vue-router -S

#### 1.1 编辑main.js

#### 1.2 编辑App.vue

#### 1.3 编辑router.config.js

### 2. axios模块化
    cnpm install axios -S
    
    使用axios的两种方式：
        方式1：在每个组件中引入axios
        方式2：在main.js中全局引入axios并添加到Vue原型中

### 3. 为自定义组件添加事件        




## 三、 自定义全局组件（插件）

    全局组件（插件）：就是指可以在main.js中使用Vue.use()进行全局引入，然后在其他组件中就都可以使用了，如vue-router
        import VueRouter from 'vue-router'
        Vue.use(VueRouter);
    
    普通组件（插件）：每次使用时都要引入，如axios
        import axios from 'axios'


## 四、 Vuex

### 1. 简介
    Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。
    简单来说，用来集中管理数据，类似于React中的Redux，都是基于Flux的前端状态管理框架           

### 2. 基本用法

#### 2.1 安装vuex
    cnpm install vuex -S

#### 2.2 创建store.js文件，在main.js中导入并配置store.选项

#### 2.3 编辑store.js文件
    Vuex的核心是Store(仓库)，相当于是一个容器，一个store实例中包含以下属性的方法：
        state       定义属性（状态、数据）
        getters     用来获取属性
        actions     定义方法（动作）
        commit      提交变化，修改数据的唯一方式就是显式的提交mutations
        mutations   定义变化
        注：不能直接修改数据，必须显式提交变化，目的是为了追踪到状态的变化 

#### 2.4 编辑App.vue        
    在子组件中访问store对象的两种方式：
        方式1：通过this.$store访问
        方式2：通过mapState、mapGetters、mapActions访问，vuex提供了两个方法：
            mapState    获取state
            mapGetters  获取getters
            mapActions  获取actions

### 3. 分模块组织Vuex          

    |-src
        |-store
            |-index.js
            |-getters.js
            |-actions.js
            |-mutations.js
            |-modules  //分为多个模块，每个模块都可以拥有自己的state、getters、actions、mutations
                |-user.js
                |-cart.js
                |-goods.js
                |....










































