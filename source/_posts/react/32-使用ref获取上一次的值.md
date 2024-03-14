---
abbrlink: 使用ref获取state中上一次的值
title: 使用ref获取state中上一次的值
date:  2024-03-12 15:26:57
type: "react"
tags: react
categories: react
keywords: react
description: 使用ref获取state中上一次的值
cover: /img/98.jpg
copyright_author: gov
top_group_index: 6
---
# 使用ref获取state中上一次的值

```react
function App(){
  const inputRef = useRef();
  const [count ,setCount] = useState(0)
  const handleClick = ()=>{
    setCount(count+1)
  }
  useEffect(()=>{
    console.log("useEffect count");
    inputRef.current = count; // 更新ref的值
  })
  console.log("beforCount count");
  const beforCount = inputRef.current;
  return(
    <>
      <div>
      <div  >now:{count} befor:{beforCount}</div>
      <button onClick={handleClick}>更新</button>
      </div>
    </>
  )
}
```

