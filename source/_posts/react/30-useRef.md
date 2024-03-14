---
abbrlink: useeRef
title: useeRef
date:  2024-03-12 15:24:57
type: "react"
tags: react
categories: react
keywords: react
description: useeRef
cover: /img/91.jpg
copyright_author: gov
top_group_index: 6
---
# useeRef

> 可以直接获取dom ，返回一个可变的ref对象

```react
function App(){
  const inputRef = useRef();
  const handleClick = ()=>{
    inputRef.current.focus()
  }
  return(
    <>
      <div>
      <input ref={inputRef} type="text "></input>
      <button onClick={handleClick}>聚焦</button>
      </div>
     
    </>
  )
}
```

