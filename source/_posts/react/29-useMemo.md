---
abbrlink: useMemo
title: useMemo
date:  2024-03-12 15:23:57
type: "react"
tags: react
categories: react
keywords: react
description: useMemo？
cover: /img/92.jpg
copyright_author: gov
top_group_index: 6
---
# useMemo(函数式组件使用 相当于class组件的pureComponent)

```react
cosnt memoizedValue = useMemo(()=>computeExpensiveValue(a,b),[a,b])
```

> 返回一个 memozied值
>
> 把 “ 创建” 函数和依赖项数组作为参数传入 useMemo，它仅仅会在某个依赖项发生改变时才会重新计算 memoized值，这种优化有助于避免在每次渲染时都进行高开销的计算
>
> 传入 useMemo 的函数会在渲染期间执行，请不要再这个函数内部执行与渲染无关的操作，诸如副作用这类的操作属于 useEffect 的使用范畴，而不是useMemo
>
> 如果没有提供依赖项数组，useMemo 会在每次渲染时重新计算新的值
>
> 你可以把 useMemo作为优化性能的手段，但不要把他当成语义上的保证