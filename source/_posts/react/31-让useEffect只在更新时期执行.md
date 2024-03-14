---
abbrlink: 让useEffect在更新时执行
title: 让useEffect在更新时执行
date:  2024-03-12 15:24:57
type: "react"
tags: react
categories: react
keywords: react
description: 让useEffect在更新时执行
cover: /img/97.jpg
copyright_author: gov
top_group_index: 6
---
# 让useEffect在更新时执行

> 正常情况下useEffect 在每次render 的时候都会执行一次，现在想让他只有在state中的count 发生变化了再执行，刷新时不执行

```react
function App(){
  const inputRef = useRef();
  const [count ,setCount] = useState(0)
  const handleClick = ()=>{
    setCount(count+1)
  }
  useEffect(()=>{
   if(!inputRef.current.flag){
    inputRef.current.flag = true;
   }else{
    console.log("useEffect更新");
   }
  })
  return(
    <>
      <div>
      <div ref={inputRef} >{count}</div>
      <button onClick={handleClick}>更新</button>
      </div>
    </>
  )
}
```

