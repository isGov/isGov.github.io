---
abbrlink: context是如何响应的
title: context是如何响应的
date:  2024-03-12 15:13:57
type: "react"
tags: react
categories: react
keywords: react
description: context是如何响应的，从底层出发
cover: /img/97.jpg
copyright_author: gov
top_group_index: 5
---
# context是如何响应的

> 通过发布订阅者模式，给每一位订阅的消费者发布更新数据

```js
// 1.定义context
const ThemContext = React.createContext();
// 子级
function ToolBar() {
  return <div>
    <ToolButton ></ToolButton>
  </div>
}
// 孙级
class ToolButton extends React.Component {
  // 这种响应变化能力是谁提供的？
  // 到底是因为setState导致的render ？ 还是消费者响应生产的变化（发布订阅者模式）？
  // 通过 让ToolBar 不执行render(在class 中使用shouldComponentUpdate returnfalse 实现) 发现是使用后者
  // 结论：组件只要定义了contextType 就是消费者，消费者可以订阅生产者
  render() {
    return <div>{this.context}</div>
  }
}
// 父级
class App extends React.Component {
  constructor(){
    super();
    this.state={
      count:0
    }
  }
  handleClick = () =>{
    this.setState({
      count:this.state.count+1
    })
  }
  render() {
    return (
       <ThemContext.Provider value={this.state.count}>
        <button onClick={this.handleClick}>点击改变</button>
        <ToolBar />
       </ThemContext.Provider>
    )
  }
}
ToolButton.contextType = ThemContext;
```

