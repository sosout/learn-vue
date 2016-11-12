# vue-demos
重温Vue.js，并将二次学习成果整理成demo分享给大家(v2.0.5)
##收集了Vue开发中遇到的各种坑、注意事项以及相对解决方案
知识点一、Vue实例只有这些被代理的属性是响应的。如果在实例创建之后添加新的属性到实例上，它不会触发视图更新。详细请参考[响应系统](http://cn.vuejs.org/v2/guide/reactivity.html)。

知识点二、不要在实例属性或者回调函数中（如 vm.$watch('a', newVal => this.myMethod())）使用箭头函数。因为箭头函数绑定父上下文，所以 this 不会像预想的一样是 Vue 实例，而是 this.myMethod 未被定义。

##二次学习整理成的demo
### Demo01: 该示例主要对Vue.js做一个大致的介绍，大致展示了以下几个功能：
[demo01](https://github.com/sosout/vue-demos/blob/master/demos/demo01.html) 

* 知识点一、将数据和DOM已经被绑定在一起({{  }})。
* 知识点二、将元素节点的title属性和Vue实例的message属性绑定到一起(v-bind)。
* 知识点三、使用v-if指令进行绑定DOM结构到数据(v-if)。
* 知识点四、使用v-for循环指令进行绑定数据到数据来渲染列表(v-for)。
* 知识点五、使用v-on指令进行绑定监听事件(v-on)。
* 知识点六、使用v-model指令进行双向数据绑定(v-model)
* 知识点七、用组件构建(应用)

### Demo02: 该示例主要对Vue.js实例做一个大致的介绍，大致展示了以下几个功能：
[demo02](https://github.com/sosout/vue-demos/blob/master/demos/demo02.html) 
* 知识点一、构造器

```js
// 1、通过构造函数Vue创建一个Vue的根实例
var vm = new Vue({
	// 选项
})

// 2、扩展Vue构造器，从而用预定义选项创建可复用的组件构造器
var MyComponent = Vue.extend({
  // 扩展选项
})

// 所有的`MyComponent`实例都将以预定义的扩展选项被创建
var myComponentInstance = new MyComponent()
```

* 知识点二、属性与方法

```js
// 1、每个Vue实例都会代理其data对象里所有的属性：
var data = { a: 1 }
var vm = new Vue({
  data: data
})
vm.a === data.a // -> true
// 设置属性也会影响到原始数据
vm.a = 2
data.a // -> 2
// ... 反之亦然
data.a = 3
vm.a // -> 3

// 2、除了data属性， Vue实例暴露了一些有用的实例属性与方法
var data = { a: 1 }
var vm = new Vue({
  el: '#example',
  data: data
})
vm.$data === data // -> true
vm.$el === document.getElementById('example') // -> true
// $watch 是一个实例方法
vm.$watch('a', function (newVal, oldVal) {
  // 这个回调将在`vm.a`改变后调用
})
```

* 知识点三、实例生命周期
