# vue3-doc-learning
vue3文档学习

## Migration from Vue2 to Vue3
### 1. New Features
* Composition API
* Teleport
* Fragments
* Emits Component Option
* `createRenderer` API from `@vue/runtime-core` to create custom renderers
* `<script setup>` 实验性
* `<style vars>` 实验性
* `<style scoped>` 现在可以包含全局规则或只针对插槽内容的规则


### 2. Breakings 非兼容变更
#### 全局API 非兼容
* 全局Vue API已更改为使用应用程序实例(-- 需要详细看文档 --)
* 全局和内部API被重构为可tree-shakable(-- 需要详细看文档 --)
  
#### 模板指令
* 组件上v-model用法更改
* `<template v-for>`和非-`<v-for>`节点上`key用法更改`
* 在同一元素上使用的`v-if`和`v-for`的优先级更改
* `v-bind="object"`现在排序敏感
* `v-for`中的`ref`不再注册ref数组

#### 组件
* 只能使用普通函数创建功能组件
* `functional`属性在SFC `<template>`和`functional`组件选项被抛弃
* 异步左键现在需要`defineAsyncComponent`方法来创建

#### 渲染函数
* 渲染函数API改变
* `scopedSlots` property已删除，所有插槽都通过`$slots`作为函数暴露
* 自定义API指令API已更改为与组件生命周期一致
* 一些转换class被重命名:
  * v-enter -> v-enter-from
  * v-leave -> v-leave-from
* 组件watch选项和实例方法`$watch`不再支持分隔字符串路径，请改用计算函数作为参数
* 在Vue2.x中，应用根容器的`outerHTML`将替换为根组件模板(如果根组件没有模板/渲染选项，则最终编译为模板)，Vue3.x现在使用应用程序容器的`innerHTML`

#### 其他小改变
* `destroyed` -> `unmounted`
* `beforeDestroy` -> `beforeUnmounted`
* prop `default`工厂函数不再有权访问`this`是上下文
* 自定义指令API更改为与组件生命周期一致
* `data`应始终声明为函数
* 来自mixin的`data`选项现在可简单地合并
* attribute强制策略已更改
* 一些过渡class被重命名
* 组件watch选项和实例方法`$watch`不再支持分隔字符串路径，请改用计算函数作为参数
* `<template>`没有特殊指令的标记(v-if/else-if/else、v-for、v-slot)现在被视为普通元素，并将生成原生的`<template>`元素，而不是渲染其全部内容
* 在Vue2.x中，应用根容器的`outerHTML`将替换为根组件模板(如果根组件没有模板/渲染选项，则最终编译为模板)，Vue3.x现在使用应用程序容器的`innerHTML`，这意味着容器本身不再视为模板的一部分

#### 移除API
* `keyCode`支持作为`v-on`的修饰符
* `$on,$off和$once`实例方法
* 过滤
* 内联模板attribute
* `$destroy`实例方法，用户不应再手动管理单个Vue组件的生命周期