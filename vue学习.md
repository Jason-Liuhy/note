# vue学习

## 	1.必备知识

### 	1.ES6基础知识

### 	2.ES6规范 

### 	3.包管理

### 	4.数组

### 	5.axios

### 	6.promise

## 	2.vue基础知识

### 	1.vue中6个默认事件

#### 			1.1 prevent

#### 			1.2 stop

#### 			1.3 once

#### 			1.4 self

#### 			1.5 capture

#### 			1.6 passive

### 	2. vue中键盘事件

#### 			2.1



### 3.vue中的样式绑定

1.class样式

写法： ：class=“xxx” xxx可以是字符串、对象、数组

字符串写法适用于:类名不确定，要动态获取。

对象写法适用于：要绑定多个样式，个数不确定，名字也不确定。

数组写法适用于：要绑定多个样式，个数确定，名字也确定，但不确定用不用。



2.style 样式

：style=“{fontSize:xxx}"	 xxx 是动态值

：style=“[a,b]” a,b 是样式对象。



### 4. v-if v-show

使用频率高用v-show ，v-if会直接删除元素节点,template中只能使用v-if，

v-else-if v-else 只能有v-if才能嵌套，且嵌套的元素中没有被打断。

<template v-if="1===1">
    <h1>
        hello
    </h1>
    <h2>
        world
    </h2>
</template>>

### 5. 数据监测的原理
    归根揭底还是改变了属性的值。引起了set的调用。
    
    模拟：let data={
        name:"jason",
        age:18
    }
    
    function Observer(obj)
    {
        const keys = Object.keys(obj);
        keys.forEach((k)=>{
            Object.defineProperty(this,k,{
                get(){
                    return obj[k];
                }
                set(val){
                    obj[k]=val;
                }
            })
        });
    }
    
    var vm = new Observer(data);
    vm.name="test";//改变了对象的值，调用了set方法。然后更新虚拟dom，虚拟dom和old 虚拟dom对比。看哪些属性改变了。
                    //更新model
    
    数组中监测：data中数组值的改变，vue只支持6个数组改变的操作。push，pop，shife，unshife，splice，sort,reverse。
    
    Vue.set(vm._data.ss.aa ,1,"11");
    vm.$set(vm._data.ss.aa,1,"111");
    
    ### 6.表单 
    收集表单数据：
    				若：<input type="text"/>，则v-model收集的是value值，用户输入的就是value值。
    				若：<input type="radio"/>，则v-model收集的是value值，且要给标签配置value值。
    				若：<input type="checkbox"/>
    						1.没有配置input的value属性，那么收集的就是checked（勾选 or 未勾选，是布尔值）
    						2.配置input的value属性:
    								(1)v-model的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）
    								(2)v-model的初始值是数组，那么收集的的就是value组成的数组
    				备注：v-model的三个修饰符：
    								lazy：失去焦点再收集数据
    								number：输入字符串转为有效的数字
    								trim：输入首尾空格过滤

 ### 7.内置指令
    1.v-text  <div  v-text="替换掉div里的所有内容">默认的都是无效的</div>
    2.v-html  <div v-html="<h3>也是替换div里的内容，但是会识别标签</h3>">
    3.v-cloak  没有值 ，本质是一个特殊属性，vue实例创建完毕并接管容器后，会删掉v-cloak属性，使用css配合v-cloak,可以解决网速慢时候，页面展示{{xxx}}的问题。[v-cloak]{display:none;}
    4.v-once <div v-once @click="n++">{{n}}</div>  这里的n只执行一次，相当于初始化，可以优化一些特殊的情景调用
    5.v-pre <div v-pre>{{不会编译}}</div> v-pre 标识后，vue认为这个标签不需要编译，解析。可以优化编译速度。


 ### 8.生命周期 
        1.beforeCreated:之前进行了vue初始化：生命周期，事件，但数据代理暂未开始。此时无法通过vm访问到data中的数据，methods中的方法。
        2.created：之前初始化数据监测，数据代理，此时可以通过vm访问到data中的数据，methods中的方法。
        3.beforeMounte：页面呈现的是未经vue编译过的dom，此时对dom的操作都无效。
        4.mounted：挂载，vue完成模板的解析，并把真实的dom元素放入页面后调用mounted，页面呈现的是经过vue编译的dom，初始化结束。此时可以做一些常用操作，写定时器，发送ajax请求，消息订阅，绑定自定义事件
        5.beforeUpdate 此时数据是新的，页面是旧的，页面还没有与数据同步。
        6.updated 
        7.beforeDestory
        8.destory