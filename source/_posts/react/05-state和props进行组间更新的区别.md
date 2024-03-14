---
abbrlink: state和props进行组件更新的区别
title: state和props进行组件更新的区别
date:  2024-03-12 15:05:57
type: "react"
tags: react
categories: react
keywords: react
description: state和props进行组件更新的区别是什么呢？
cover: /img/96.jpg
copyright_author: gov
top_group_index: 1
---
# state和props进行组件更新的区别

```react
import React from "react";
import ReactDOM from "react-dom";

function Count(props) {
  let count = 0
  setInterval(()=>{
    console.log("Count count",count);
    count=++count
  },1000)
  return <h1>{count}</h1>
}
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    }
    setInterval(() => {
      this.setState({
        count: this.state.count + 1 // 这里会触发render方法
      })
    }, 1000);
  }
  render() {
    const { count } = this.state;
    //每次执行setStat 都会执行一次render
    console.log("render coung",count);
    return <Count  />
  }
}

ReactDOM.render(<App name="我是props" />, document.getElementById("root"));
```

> 通过上述代码可以知道，每次执行setState都会执行一次render，那么这个驱动数据更新是不是setState引起的呢？？目前知道的是
>
> 1. 只要setState 就会执行当前组件的render方法，其实不完全准确（生命周期函数）
> 2. 无状态组件是怎么更新的？  Count组件的更新，是render引起的吗？
>
> **但是通过上面代码显示，Count中的count并不会随着render的调用而刷新页面，那么无状态组件数据的更新是通过props来实现的**
>
> **结论**：**props的组件，状态变化是通过props的变化引起的，只要props不发生变化，组件就不会进行更新**

> 将上述代码稍作修改即可验证这一点

```react
import React from "react";
import ReactDOM from "react-dom";

function Count(props) {
  return <h1>{props.count}</h1>
}
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    }
    setInterval(() => {
      this.setState({
        count: this.state.count + 1 // 这里会触发render方法
      })
    }, 1000);
  }
  render() {
    const { count } = this.state;
    //每次执行setStat 都会执行一次render
    console.log("render coung",count);
    return <Count count ={count} />
  }
}

ReactDOM.render(<App name="我是props" />, document.getElementById("root"));
```

# 总结

> 1. **setState会引起有状态class组件，render方法的执行**
> 2. **render方法的执行，不一定可以影响无状态组件的更新**
> 3. **无状态组件只看自己的props有没有发生变化**