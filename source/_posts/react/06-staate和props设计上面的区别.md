---
abbrlink: state和props设计层面上的区别
title: state和props设计层面上的区别
date:  2024-03-12 15:06:57
type: "react"
tags: react
categories: react
keywords: react
description: state和props设计层面上的区别是什么呢？
cover: /img/97.jpg
copyright_author: gov
top_group_index: 1
---
# state和props设计层面上的区别

> 举个例子：一台车，它的同一个款式，发动机可以是一样的，大灯可以是一样的，齿轮可以是一样的，配色可能是不一样的，那么我们可以将她归一下类：
>
> - 不常变化的：大灯，发动机，齿轮
> - 常变化的：配色

```react
import React from "react";
import ReactDOM from "react-dom";

class Car extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      fadongji: "8v4t",
      right: "LED 2",
      chilun: "固齿"
    }
  }
  render() {
    return <>
      卡卡汽车
    </>
  }
}
ReactDOM.render(<Car  color="green"/>, document.getElementById("root"));
```

> 可以看出，外在的配色通过props进行传值，这样可以有几个优点：
>
> - **在组建内部可以形成闭环的状态，不管是静态还是动态，使用state**
> - **组件外部的状态，常常需要发生变化，或者定制化的内容，可以考虑使用props**