---
abbrlink: router
title: router
date:  2024-03-12 15:28:57
type: "react"
tags: react
categories: react
keywords: react
description: 实现一个router
cover: /img/94.jpg
copyright_author: gov
top_group_index: 6
---
# 实现一个router

## 思路

> **BrowserRouter 的职责：**
>
> 将react的生命周期和history结合起来
>
> 再将path和route进行关联
>
> 对path进行管理
>
> **route的职责：**
>
> 什么路径对应什么组件，组件和路径一一对应

```react
//react中的路由使用
<BrowserRouter>
    <>
    	<Route path="/" componnet={Home}>
    		
        </Route>
    </>
</BrowserRouter>
```

## 封装router

```react
import React, { useEffect, useState } from "react";

const RouterContext = React.createContext();
// 将react的生命周期和history结合起来
// 再将path和route进行关联
// 对path进行管理
function BrowserRouter(props) {
  const [path, setPath] = useState(() => {
    const { pathname } = window.location;
    return pathname || "/";
  });
  const goPath = function (path) {
    setPath(path);
    window.history.pushState({ path }, "", path);
  };
  const RouterData = {
    path,
    goPath,
  };
  function handlePopState(){
    const {pathname} = window.location
    setPath(pathname)
  }
//   监听浏览器回退
 useEffect(()=>{
    window.addEventListener("popstate",handlePopState)
    console.log("pops");
    return function(){
        window.removeEventListener("popstate",handlePopState)
    }
 },[])
  return (
    <RouterContext.Provider value={RouterData}>
      {props.children}
    </RouterContext.Provider>
  );
}
// 什么路径对应什么组件，组件和路径一一对应
function Route(props) {
  const { path, component: Component } = props;
  return (
    <RouterContext.Consumer>
      {(router) => {
        return path === router.path ? <Component /> : null;
      }}
    </RouterContext.Consumer>
  );
}
export { BrowserRouter, Route,RouterContext };

```

> 使用 context 的好处是可以隔组件传值，而且context不受shouldcomponentupdate影响

## 使用

```react
function ButtonView(){
  return (
  <BrowserRouter>
  <RouterContext.Consumer>
    {(router)=>(
        <>
          <button onClick={()=>router.goPath('/')}>首页</button>
          <button onClick={()=>router.goPath('/about')}>关于</button>
          <button onClick={()=>router.goPath('/user')}>用户</button>

          <Route path="/" component={Home} />
       <Route path="/about" component={About} />
       <Route path="/user" component={User} />
        </>
    )}
  </RouterContext.Consumer>
  </BrowserRouter>
  )
}
```

