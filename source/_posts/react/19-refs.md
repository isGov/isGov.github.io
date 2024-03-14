---
abbrlink: Refs
title: Refs
date:  2024-03-12 15:15:57
type: "react"
tags: react
categories: react
keywords: react
description: Refs and the DOM
cover: /img/93.jpg
copyright_author: gov
top_group_index: 5
---
# Refs and the DOM

> Refs 提供了一种方式，**允许我们访问DOM节点，或在render方法中创建的React元素(class组件)**

> 在典型的react数据流中，props是父组件与子组件交互的唯一方式，要修改一个子组件，你需要使用新的props来重新渲染它。但是，**在某种情况下，你需要在典型数据流之外强制修改子组件，被修改的子组件可能是一个React组件的示例，也可能是**

# 何时使用？

> - 管理焦点，文本选择或媒体播放
> - 触发强制动画
> - 集成第三方DOM库
>
> 避免使用ref来做任何可以通过声明式实现来完成的事情
>
> 例如：避免在DIalog 组件中暴露open()和close()方法，最好传递isOpen属性

```react
class App extends React.Component {
  constructor() {
    super();
    this.dom_refs = React.createRef();
  }
  componentDidMount(){
    console.log(this.dom_refs);

  }
  render() {
    return <div ref={this.dom_refs}>
      hello react
    </div>
  }
}
```

> **ref获取到的dom 和 document获取到的dom是一样的**

# 函数式组件使用ref

> 一般来说 函数式组件没有实例不支持ref，一般使用forwardRef

# ref的回调函数

> 通过ref的回调函数获取 dom

```react
// 子组件
class Child extends React.Component{
  render(){
    return <input ref={this.props.InputRef} />
  }
}
class App extends React.Component {
  componentDidMount(){
    console.log(this.InputRef);
  }
 render(){
  return(
    <Child InputRef={(el)=>this.InputRef=el}></Child>
  )
 }
}
```

