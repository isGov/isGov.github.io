---
abbrlink: Redux常用方法
title: Redux常用方法
date:  2024-03-12 15:31:57
type: "react"
tags: react
categories: react
keywords: react
description: Redux常用方法有哪些？
cover: /img/91.jpg
copyright_author: gov
top_group_index: 7
---
# Redux常用方法

## Redux Store

> 所有 Redux 应用的中心都是 store。 “store” 是保存应用程序的全局state 的容器
>
> store 是一个JavaScript 对象。具有一些特殊的功能和能力。使其与普通的全局对象不同：
>
> - 切勿直接修改(modify) 或 更改(change) 保存在Redux 存储中的状态
> - 相反，导致状态更新的唯一方法是创建一个描述 “应用程序中发生的某些事情”的普通action对象，然后将该action dispatch 到 store 以告诉它发生了什么
> - 当一个action 被dispatch 后，store 会调用根 reducer 方法，让其根据action 和旧 state 计算出 state
> - 最后，store 会通知 **订阅者(subscribers)** 状态已更新，以便可以使用新数据更新UI

## Redux 数据流

> - actions 会在用户交互时被dispacth(action就是对行为的描述，例如我要干嘛，洗车)
> - store 通过执行reducer 方法计算出一个新的state(此时reducer就会去洗车(执行))
> - UI 读取最新的 state 来展示最新的值

