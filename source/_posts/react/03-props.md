---
abbrlink: Props
title: Props
date:  2024-03-12 15:04:57
type: "react"
tags: react
categories: react
keywords: react
description: 本文将介绍什么Props
cover: /img/94.jpg
copyright_author: gov
top_group_index: 1
---
# Props

> 如果说state是组件的内部状态，那么props就是外部状态；
>
> 无状态组件就是没有内部状态的

```react
import React from "react";
import ReactDOM from "react-dom";

class App extends React.Component {
  render(){
    const {name} = this.props
    return <h1>{name}</h1>
  }
}

ReactDOM.render(<App name="我是props" />, document.getElementById("root"));
```

> **在无状态组件中props是通过参数的形式传递的**

```react
import React from "react";
import ReactDOM from "react-dom";

function Count (props){
  return <h1>{props.count}</h1>
}
class App extends React.Component {
  render(){
    return <Count count="2"/>
  }
}

ReactDOM.render(<App name="我是props" />, document.getElementById("root"));
```

