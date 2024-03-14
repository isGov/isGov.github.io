---
abbrlink: useState
title: useState
date:  2024-03-12 15:19:57
type: "react"
tags: react
categories: react
keywords: react
description: 什么是useState？有什么作用？
cover: /img/94.jpg
copyright_author: gov
top_group_index: 6
---
# useState

```react
function Num (){
  // 声明一个 变量
  // useState就是一个hook
  // num是在渲染中需要的数据
  // setNum 是提供修改数据的方法
  // useState的返回值就是一个数组
  const [num,setNum] = useState(0);
  return <div>
    <button onClick={()=>setNum(num+1)}>+1</button>
    {num}
  </div>
}

class App extends React.Component {
  render() {
    return <div>
      <Num></Num>
    </div>;
  }
}
```

