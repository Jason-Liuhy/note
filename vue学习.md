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



