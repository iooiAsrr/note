# 差值表达式

![image-20240515103812287](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405151038432.png)

# 响应式特性

![image-20240515104336318](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405151043403.png)



# Vue指令

![image-20240515105505559](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405151055644.png)

```vue
<div v-html>//渲染标签内容及标签类似.innerHTML</div>
<div v-show>//控制元素显示隐藏通过css的display属性</div>
<div v-if>//控制元素显示隐藏通过元素添加和移除</div>
<div v-else>//必须配合v-if使用</div>
<div v-else-if>//配合v-if使用</div>
<div v-on>
    //注册事件=添加监听+提供处理逻辑
    <button v-on:click="sum++">+</button>
    //简写
    <button @:click="sum++">+</button>
    <button @:click="methods">+</button>
    <button @:click="methods(参数)">+</button>
</div>
<div v-bind>
    //动态设置标签属性,v-bind:属性名="表达式"
    <img v-bind:src=""></img>
	//简写
	<img :src="{}"></img>
</div>
<div v-for>//基于数据循环,多次渲染整个元素</div>
<div v-for="(item,index) in xxx ":key="唯一值">//</div>
<div v-model>//视图数据双向绑定</div>
```

![image-20240518130551112](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181305259.png)

![image-20240518131258155](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181312276.png)

# 指令修饰符

![image-20240518135047663](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181350776.png)

![image-20240518140628461](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181406562.png)

![image-20240518141539609](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181415724.png)

# 计算属性

![image-20240518142539195](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181425365.png)

![image-20240518143214282](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181432448.png)

![image-20240518144053090](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181440246.png)

# watch监听器

![image-20240518150626949](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181506081.png)

![image-20240518150722363](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405181507490.png)

# 生命周期

![image-20240524143416290](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241434518.png)

# 钩子函数

![image-20240524143808569](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241438753.png)

# 工程化

![image-20240524153144608](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241531760.png)

![image-20240524155647989](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241556125.png)

![image-20240524160311940](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241603131.png)

# 组件注册

![image-20240524174915665](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241749910.png)

![image-20240524175548450](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241755573.png)

# scoped样式冲突

![image-20240524180952318](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241809373.png)

![image-20240524181036862](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405241810009.png)

# data是一个函数

![image-20240525171922788](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405251719982.png)

# 组件通信

![image-20240525173341124](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405251733228.png)

# Prop

![image-20240525173904934](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405251739143.png)

# Props校验

![image-20240525174525513](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405251745606.png)

![image-20240525174633743](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405251746832.png)

# prop & data

![image-20240525180149794](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405251801981.png)

# 非父子通信-event bus

![image-20240526153206868](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261532089.png)

![image-20240526153621567](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261536732.png)

# v-model原理

![image-20240526154354716](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261543878.png)

# 表单类组件封装

![image-20240526155620935](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261556121.png)

![image-20240526163052182](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261630286.png)

# .sync修饰符

![image-20240526170200370](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261702546.png)

# ref和$refs

![image-20240526171318078](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261713243.png)

![image-20240526172215939](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261722071.png)

# 异步更新和$nextTick

![image-20240526173851660](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261738730.png)

# 自定义指令

![image-20240526174506186](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261745367.png)

 ![image-20240526180002200](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261800297.png)

![image-20240526181617504](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405261816634.png)

# 插槽

![image-20240529103223328](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405291032480.png)

![image-20240529104728971](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405291047051.png)

![image-20240529105027619](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405291050688.png)

# 具名插槽

![image-20240529105447319](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405291054397.png)

![image-20240529110937038](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405291109127.png)

# 路由

![image-20240529111812470](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405291118564.png)

![image-20240529112056400](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405291120480.png)

![image-20240530142750213](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301427348.png)

![image-20240530144244218](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301442287.png)

# 组件分类

![image-20240530144648015](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301446096.png)

![image-20240530150021080](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301500151.png)

# router-link(声明式导航)

![image-20240530150744723](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301507802.png)

![image-20240530151323155](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301513214.png)

![image-20240530151829089](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301518148.png)

# 跳转传参

![image-20240530153906924](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301539987.png)

![image-20240530154633673](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301546750.png)

![image-20240530154949804](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301549919.png)

# 路由重定向

![image-20240530155331652](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301553732.png)

# 路由-404

![image-20240530155456460](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301554563.png)

# 路由模式

![image-20240530160200325](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301602416.png)

# 编程式导航

![image-20240530161628343](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301616438.png)

![image-20240530162839015](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301628097.png)

![image-20240530162910748](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301629850.png)

![image-20240530162925101](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405301629182.png)

# ESLint

![image-20240531165648712](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405311656944.png)

# VueX

![image-20240531171021394](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405311710610.png)

![image-20240531180332227](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405311803418.png)

![image-20240531182905900](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405311829104.png)

# mutations

![image-20240531185557195](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405311855354.png)

# mapmutations

![image-20240531191206186](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202405311912354.png)

# actions

![image-20240601095931791](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406010959048.png)

# mapActions

![image-20240601101252114](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406011012318.png)

# getters

![image-20240601103016033](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406011030245.png)

# vuex-module

![image-20240601144440497](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406011444764.png)

![image-20240601144715960](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406011447138.png)

![image-20240601151232853](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406011512988.png)

![image-20240601154124325](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406011541501.png)

![image-20240601154802342](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406011548534.png)

# 组件

![image-20240601162627370](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406011626452.png)

# 打包优化

![image-20240602215235163](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202406022152416.png)













