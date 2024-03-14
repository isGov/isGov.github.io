---
abbrlink: 在函数式组件中使用context响应
title: 在函数式组件中使用context响应
date:  2024-03-12 15:13:57
type: "react"
tags: react
categories: react
keywords: react
description: 如何在函数式组件中使用context响应
cover: /img/98.jpg
copyright_author: gov
top_group_index: 5
---
# 在函数式组件中使用context响应

> 通过<ThemContext.Consumer> 通过这个api可以让函数式组件也拥有响应式context 

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
{/* <ThemContext.Consumer> 通过这个api可以让函数式组件也拥有响应式context */}
function ToolButton(){
  return (
    <ThemContext.Consumer>
      {value => <div>{value}</div>}
    </ThemContext.Consumer>
  )
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
```

> **如果使用context引用一个对象，而只修改这个对象的属性不修改引用地址的时候，这个context是不会执行发布模式的**