---
abbrlink: forwardRef
title: forwardRef
date:  2024-03-12 15:16:57
type: "react"
tags: react
categories: react
keywords: react
description: forwardRef
cover: /img/96.jpg
copyright_author: gov
top_group_index: 5
---
# forwardRef

```react
// ForwardButton 返回一个组件
const ForwardButton =React.forwardRef((props,ref)=>{
  <button ref={ref} >
    {props.children}
  </button>
})
class App extends React.Component {
  constructor(){
    super();
    this.forwardRef_ref = React.createRef();
    console.log(" this.forwardRef_ref", this.forwardRef_ref);
  }
  componentDidMount(){
    console.log(" this.forwardRef_ref", this.forwardRef_ref);
   
  }
 render(){
  return(
    <ForwardButton ref={this.forwardRef_ref}>
      <h1>hello word</h1>
    </ForwardButton>
  )
 }
}
```

