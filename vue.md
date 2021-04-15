## 第10章、计算属性(computed)

### 10.1、什么是计算属性?

​	计算属性也是用来存储数据

### 10.2、计算属性的特点

```
a.数据可以进行逻辑处理操作
b.对计算属性中的数据进行监视
```

### 10.3、计算属性 vs 方法

```
将计算属性的get函数定义为一个方法也可以实现类似的功能
区别：
    a.计算属性是基于它的依赖进行更新的，只有在相关依赖发生改变时才能更新变化
    b.计算属性是缓存的，只要相关依赖没有改变，多次访问计算属性得到的值是之前缓存的计算结果，不会多次执行
```

### 10.4、计算属性的get和set

```
计算属性由两部分组成：get和set，分别用来获取计算属性和设置计算属性
默认只有get，如果需要set，要自己添加
```



## 第11章、组件(component)

### 11.1、什么是组件？

- 组件（Component）是 Vue.js 最强大的功能之一。组件可以扩展 HTML 元素，封装可重用的代码
- 组件是自定义元素（对象）

### 11.2、定义组件的方式

- 方式1：先创建组件构造器(Vue.extend)，然后由组件构造器创建组件
- 方式2：直接创建组件

### 11.3、组件的分类

-  分类：全局组件、局部组件

### 11.4、引用模板

- 将组件内容放到模板<template>中并引用

### 11.5、动态组件

1. <component :is="">组件========>多个组件使用同一个挂载点，这是个占位符,:is来指定要展示的组件名称
2. <keep-alive>作用:缓存非活动组件,可以保留状态,避免重新渲染,默认每次都会销毁非活动组件并重新创建

### 11.6、组件间数据传递

1.  父子组件

   - 在一个组件内部定义另一个组件，称为父子组件
   - 子组件只能在父组件内部使用
   - 默认情况下，子组件无法访问父组件中的数据，每个组件实例的作用域是独立的

2. 组件间数据传递(通信)

   - 子组件访问父组件的数据

     - a)在调用子组件时，绑定想要获取的父组件中的数据
     - b)在子组件内部，使用props选项声明获取的数据，即接收来自父组件的数据
          总结：父组件通过props向下传递数据给子组件
          注：组件中的数据共有三种形式：data、props、computed

   - 父组件访问子组件的数据

     - a)在子组件中使用vm.$emit(事件名,数据)触发一个自定义事件，事件名自定义
     - b)父组件在使用子组件的地方监听子组件触发的事件，并在父组件中定义方法，用来获取数据
           总结：子组件通过events给父组件发送消息，实际上就是子组件把自己的数据发送到父组件

   - 单向数据流

     - props是单向绑定的，当父组件的属性变化时，将传导给子组件，但是不会反过来
     - 而且不允许子组件直接修改父组件中的数据，报错
     - 解决方式：
       - 方式1：如果子组件想把它作为局部数据来使用，可以将数据存入另一个变量中再操作，不影响父组件中的数据
       - 方式2：如果子组件想修改数据并且同步更新到父组件，两个方法：
         - a.使用.sync（1.0版本中支持，2.0版本中不支持，2.3版本又开始支持） 需要显式地触发一个更新事件
         - b.可以将父组件中的数据包装成对象，然后在子组件中修改对象的属性(因为对象是引用类型，指向同一个内存空间)，推荐  

   - 非父子组件间的通信

     -  非父子组件间的通信，可以通过一个空的Vue实例作为中央事件总线（事件中心），用它来触发事件和监听事件

       ```javascript
       var Event=new Vue();
       Event.$emit(事件名,数据);
       Event.$on(事件名,data => {});
       ```

### 11.7、slot内容分发

-   本意：位置、槽





















## 第12章、路由(router)

### 12.1、简介

- 使用Vue.js开发SPA（Single Page Application）单页面应用

- 根据不同url地址,显示不同的内容,但显示在同一个页面中,称为单页面应用

  参考网站:https://router.vuejs.org/zh-cn

  

### 12.2、路由的使用

- 安装路由指令(vuecli):

```
cnpm install vue-router -S
```

- 使用案例

```html
-----------------------HTML---------------------------->
<script src="https://unpkg.com/vue/dist/vue.js"></script>
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>

<div id="app">
  <h1>Hello App!</h1>
  <p>
    <!-- 使用 router-link 组件来导航. -->
    <!-- 通过传入 `to` 属性指定链接. -->
    <!-- <router-link> 默认会被渲染成一个 `<a>` 标签 -->
    <router-link to="/foo">Go to Foo</router-link>
    <router-link to="/bar">Go to Bar</router-link>
  </p>
  <!-- 路由出口 -->
  <!-- 路由匹配到的组件将渲染在这里 -->
  <router-view></router-view>
</div>
```

```js
JavaScript----------->
// 0. 如果使用模块化机制编程，导入Vue和VueRouter，要调用 Vue.use(VueRouter)
// 1. 定义 (路由) 组件。
// 可以从其他文件 import 进来
const Foo = { template: '<div>foo</div>' }
const Bar = { template: '<div>bar</div>' }

// 2. 定义路由
// 每个路由应该映射一个组件。 其中"component" 可以是
// 通过 Vue.extend() 创建的组件构造器，
// 或者，只是一个组件配置对象。
// 我们晚点再讨论嵌套路由。
const routes = [
  { path: '/foo', component: Foo },
  { path: '/bar', component: Bar }
]

// 3. 创建 router 实例，然后传 `routes` 配置
// 你还可以传别的配置参数, 不过先这么简单着吧。
const router = new VueRouter({
  routes // (缩写) 相当于 routes: routes
})

// 4. 创建和挂载根实例。
// 记得要通过 router 配置参数注入路由，
// 从而让整个应用都有路由功能
const app = new Vue({
  router
}).$mount('#app')

// 现在，应用已经启动了！
```

- vuecli中使用route
  - 通过注入路由器,我们可以在任何组件内通过 `this.$router` 访问路由器,也可以通过 `this.$route` 访问当前路由
  - 通常使用 `router` 实例。留意一下 `this.$router` 和 `router` 使用起来完全一样。
  - 我们使用 `this.$router` 的原因是我们并不想在每个独立需要封装路由的组件中都导入路由。

```javascript
// Home.vue
export default {
  computed: {
    username() {
      // 我们很快就会看到 `params` 是什么
      return this.$route.params.username
    }
  },
  methods: {
    goBack() {
      window.history.length > 1 ? this.$router.go(-1) : this.$router.push('/')
    }
  }
}
```



### 12.3、路由嵌套和参数传递 

- 传参的两种形式：
       a.查询字符串:login?name=tom&pwd=123     ========> {{$route.query}}
       b.rest风格url:regist/alice/456    ========> {{$route.params}}

### 12.4、路由实例的方法 

- router.push() 添加路由，功能上与<route-link>相同
- router.replace() 替换路由，不产生历史记录 

