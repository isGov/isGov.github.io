---
abbrlink: 二级路由
title: 二级路由
date:  2024-03-12 15:29:57
type: "react"
tags: react
categories: react
keywords: react
description: 二级路由
cover: /img/97.jpg
copyright_author: gov
top_group_index: 6
---
# 二级路由

> 需要在父级路由中使用 outlet(子路由子级占位符)，并且使用时需要传入 组件 <child/>

```react
function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Wrap />}>
          <Route index element={<Home />}></Route>
        </Route>
      </Routes>
    </BrowserRouter>
  );
}
```

## v6优化

> 会先渲染明确了的组件，动态组件优先级会比明确名字组件优先级低，之前是按顺序进行确定优先级