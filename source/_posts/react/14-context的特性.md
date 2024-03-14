---
abbrlink: Context的特性
title: Context的特性
date:  2024-03-12 15:12:57
type: "react"
tags: react
categories: react
keywords: react
description: Context的特性有哪些？
cover: /img/96.jpg
copyright_author: gov
top_group_index: 5
---
# API

## React.createContext

```js
const MyContext = React.createContext(defaulValue)
```

> 创建一个Context对象。当React渲染一个订阅了这个Context对象的组件，这个组件会从组件树中离自身最近的那个匹配的Provider中读取到当前的context值

> 当所有组件所处的树都没有匹配到Provider时，其defaultValue参数才会生效，此默认值有助于在不使用Provider包装组件的情况下对组件进行测试。注意：将undefined传递给Provider 的 value时，消费组件的defaultValue不会生效

## Context.Provider

```js
<Context.Provider  value={/*某个值*/}/> 
```

> 每个Context 对象都会返回一个Provider React 组件，它允许**消费组件**订阅context 的变化

> Provider 接收一个value属性，传递给消费组件，一个Provider可以和多个消费组件有对应关系，多个Porvider 也可以嵌套使用，里层的会覆盖外层的数据

> 当**Provider 的value值发生变化时，它内部的所有消费组件都会重新渲染**。从Provider 到其内部consumer组件（包括 contextType和useContext） 的传播不受限于shouldComponentUpdate 函数，因此当consumer组件在其祖先组件跳过更新的情况下也能更新

> 通过新旧值检测来确定变化，使用了与Object.is相同的算法（和===类似）

## contextType

```js
App.contextType =  ThemContext;
```

> 挂载在class上的contextType 属性可以赋值为由 React.createContext() 创建的Context 对象。从属性可以让你使用 this.context 来获取Context 上的值，你可以在任何生命周期中访问到他，包括render函数