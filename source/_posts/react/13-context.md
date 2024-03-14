---
abbrlink: Context
title: Context
date:  2024-03-12 15:12:57
type: "react"
tags: react
categories: react
keywords: react
description: Context
cover: /img/95.jpg
copyright_author: gov
top_group_index: 5
---
# Context

> Context 提供了一个无需为每层组件手动添加props，就能在组件树件进行数据传递的方法
>
> Context 提供了一种在组件之间共享此类值的方式，而不必显示地通过组件树的逐层传递props

# 传统传值-逐层传递

> 在ToolButton中使用爷爷传过来的them需要逐层传递才能到达自身

```js
// 子级
function ToolBar (props){
  return <div>
    <ToolButton them={props.them}></ToolButton>
  </div>
}
// 孙级
class ToolButton extends React.Component {
  render(){
    return <div>{this.props.them}</div>
  }
}
// 父级
class App extends React.Component {
  render() {
    return (<div>
     <ToolBar them = "dark"></ToolBar>
    </div>)
  }
}
```

# 如何使用

> 1.先定义context  ： const ThemContext = React.createContext();
>
> 2.父级直接使用Porvider组件包裹： ThemContext.Provider value="right"  ，value为要传过去的值
>
> 3.要使用到的组件直接使用：static contextType = ThemContext; 通过this.context使用值

```js
// 1.定义context
const ThemContext = React.createContext();
// 子级
function ToolBar() {
  return <div>
    <ToolButton></ToolButton>
  </div>
}
// 孙级
class ToolButton extends React.Component {
  static contextType = ThemContext;
  render() {
    return <div>{this.context}</div>
  }
}
// 父级
class App extends React.Component {
  render() {
    return (
      <ThemContext.Provider value="right">
        <ToolBar></ToolBar>
      </ThemContext.Provider>
    )
  }
}
```

# 使用之前考虑

> Context 主要应用在于很多不同层级的组件需要访问同样一些数据
>
> **与props对比**：
>
> - props：复用性最强，组件嵌套深了，传值不方便
> - context：复用性不强，组件嵌套深了，传值方便（复用需要新的父组件重新定义context，还需要使用provider进行传值）

> 想要避免层层传递一些属性，组件组合（component composition）可能会比context更加合适