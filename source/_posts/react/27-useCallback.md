---
abbrlink: useCallback
title: useCallback
date:  2024-03-12 15:21:57
type: "react"
tags: react
categories: react
keywords: react
description: 什么是useCallback？有什么作用？
cover: /img/91.jpg
copyright_author: gov
top_group_index: 6
---
# useCallback

> 下面这段代码，每次点击按钮 所有按钮都会重新渲染一遍，这样是不现实的，如果页面内容多了，每次渲染多次会对用户体验不好

```react
function App(){
  const [count1,setCount1] = useState(0);
  const [count2,setCount2] = useState(0);
  const [count3,setCount3] = useState(0);
  const handleClickButton1 =()=>{
    setCount1(count1 + 1);
  }
  const handleClickButton2 =useCallback(()=>{
    setCount2(count2 + 1);
  },[count2])
  console.log("App更新");
  return(
    <>
      <div>
        <Button onClickButton={handleClickButton1}>Button1</Button>
      </div>
      <div>
        <Button onClickButton={handleClickButton2}>Button2</Button>
      </div>
      <div>
        <Button onClickButton={()=>{setCount3(count3 + 1)}}>Button2</Button>
      </div>
    </>
  )
}
```

> **可以使用shouldComponentUpdate 来判断函数是否相等来决定是否要更新**，但此时会有一个问题，因为每次重新渲染的时候，箭头函数跟按钮里面的函数都会重新生成一次，导致点击按钮2的时候 1 3 跟着一起变(一起更新)
>
> **useCallback可以缓存函数，每次都是原来的函数，只要依赖不变，他就不会发生改变**