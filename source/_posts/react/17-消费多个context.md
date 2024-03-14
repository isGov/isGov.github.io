---
abbrlink: 消费多个Context
title: 消费多个Context
date:  2024-03-12 15:13:57
type: "react"
tags: react
categories: react
keywords: react
description: 如何消费多个Context
cover: /img/91.jpg
copyright_author: gov
top_group_index: 5
---
# 消费多个Context

```react
// 子级
function ToolBar() {
  return <div>
    <ToolButton ></ToolButton>
  </div>
}
// 孙级
function ToolButton() {
  return (
    <ThemContext.Consumer >
        {(value) => (
          <ColorCotenxt.Consumer>
            {(value_item) => (
              <button>{`${value} ${value_item}`}</button>
            )}
          </ColorCotenxt.Consumer>
        )}
      </ThemContext.Consumer>
  )
}
// 父级
class App extends React.Component {
  constructor() {
    super();
    this.state = {
      count: 0
    }
  }
  handleClick = () => {
    this.setState({
      count: this.state.count + 1
    })
  }
  render() {
    return (
      <ThemContext.Provider value={this.state.count}>
          <ColorCotenxt.Provider value="blue">
              <button onClick={this.handleClick}>点击</button>
              <ToolBar></ToolBar>
          </ColorCotenxt.Provider>
      </ThemContext.Provider>
    )
  }
}
```

# 注意

> **context会根据引用标识来决定何时进行渲染（本质啥事value属性值的浅比较），所以这里可能存在一些陷阱，当provider的父组件进行重渲染时，可能会在consusmers组件中触发意外的渲染，所以尽量将value的状态定义在父节点的state中**