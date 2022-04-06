# Vue基础知识

## 1.需要掌握的知识

### 	1.ES6语法规范

### 	2.ES6模块化

### 	3.包管理

### 	4.原型，原型链

### 	5.promise

### 	6.axios

### 	7.数组常用方法

## 2.vue中6个默认事件

### 		1.prevent 阻止默认事件 a链接

### 		2.stop 阻止事件冒泡

### 		3.once 事件只执行一次

### 		4.capture 使用事件的捕获模式

### 		5.self  只有event.target是当前操作的元素才触发事件

### 		6.passive 事件的默认行为立即执行，无需等待事件回调执行完毕。

@click.stop.prevent="func()";//阻止冒泡，阻止默认 

## 3.vue中常用的按键别名

## @keyup，@keydown

### 		1.enter	

### 		2.up

### 		3.down

### 		4.left

### 		5.right

### 		6.esc

### 		7.tab

### 		8.delete

### 		9.space

## vue没有提供别名的按键，可以使用按键原始的键名绑定，需要注意转为kebab-case（短线命名）

### 系统修饰键（用法特殊）ctrl，alt，shift，meta

配合keyup使用，按下修饰键的同时，再按下其他键，随后释放其他键，事件才被执行

配合keydown使用，正常触发事件

## vue中自定义键名

Vue.config.KeyCodes.huiche=13;  @keyup.huiche="func"



# 事件传参  @click=“func($event,parms)” 



## vue中插值语法中调用函数{{func（）}} data中的数据发生变化，func会重新执行一次。



