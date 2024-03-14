---
abbrlink: redux
title: redux
date:  2024-03-12 15:30:57
type: "react"
tags: react
categories: react
keywords: react
description: 什么是redux？他有什么作用？
cover: /img/99.jpg
copyright_author: gov
top_group_index: 7
---
# 为什么要用redux

> redux 提供的模式和工具使你更容易理解应用程序中的状态何时、何地、为什么以及如何更新，以及当这些更改发生时，你应用程序逻辑将如何表现

# 什么是redux

> redux 是一个使用叫作 “actions” 的事件去管理和更新应用状态的模式和工具库。它以集中式Store 的方式对整个应用中使用的状态进行集中管理，其规则确保状态只能以可预测的方式更新

# 什么时候用

> - 在应用的大量地方，存在大量的状态
> - 应用状态会随着时间的推移而频繁更新
> - 更新该状态的逻辑可能很复杂
> - 中型和大型代码量的应用，很多人协同开发

# Redux 库和工具

## React.Redux

> redux可以结合任何UI框架 一起使用，最常与react一起使用，他让react组件和redux有了交互，可以从store读取一些state ，可以通过dispatch actions 来更新store

## Redux Toolkit

> Redux Toolkit 使我们推荐的编写Redux 逻辑的方法，它包含我们认为对于构建redux应用程序必不可少的包和函数，redux toolkit 构建在我们建议的最佳实践中，简化了大多数的redux任务，防止了常见错误，并使得编写redux 应用程序变得更加容易

## Redux DevTools拓展

> Redux DevTools拓展 可以显示redux 存储中状态随时间变化的历史记录，这允许你有效地调试应用程序，包括使用强大的技术，如 “时间旅行调试”