---
abbrlink: Fragments
title: Fragments
date:  2024-03-12 15:18:57
type: "react"
tags: react
categories: react
keywords: react
description: Fragments
cover: /img/93.jpg
copyright_author: gov
top_group_index: 5
---
# Fragments

> Fragment 允许你将子列表分组，而无需向DOM 添加额外的节点

```react
class App extends React.Component {
  
 render(){
  return (
    <React.Fragment>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </React.Fragment>
  )
 }
}
```

> 也可以使用 <> </>