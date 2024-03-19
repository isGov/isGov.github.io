---
abbrlink: redux执行顺序
title: redux执行顺序
date:  2024-03-19 10:31:57
type: "react"
tags: react
categories: react
keywords: react
description: redux执行顺序
cover: /img/94.jpg
copyright_author: gov
top_group_index: 8
---
# redux执行顺序

> - createStore,然后执行reducer，action的类型为@@redux.x.x.x,就对store进行初始化，不会去执行store.subsribe中的订阅
> - 通过按钮点击 dispatch 发起一个action
> - 进入reducer，去修改store的状态
> - 去执行 subscribe 中订阅的函数