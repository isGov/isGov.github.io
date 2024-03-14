---
abbrlink: hook
title: hook
date:  2024-03-12 15:19:57
type: "react"
tags: react
categories: react
keywords: react
description: 什么是hook？有什么作用？
cover: /img/92.jpg
copyright_author: gov
top_group_index: 6
---
# 动机

> HOOK 解决了我们五年来编写和维护成千上万的组件时遇到的各种看起来不相关的问题

# 1.在组件之间复用状态逻辑很难

> React 没有提供将可复用性行为 “附加” 到组件的途径(例如 把组件连接到store)，如果你使用过Reaact一段时间，你会熟悉一些解决此类问题的方法，比如render props 和高阶组件(redux)
>
> 你会发现这类方法需要重新组织你的组件架构，使代码更加难以理解也会形成“嵌套地狱”
>
> 这说明一个更深层次的问题：**React 需要为共享状态逻辑提供更好的原生途径(HOOKS)**
>
> **可以使用HOOK 从组件中提取状态逻辑，使得这些逻辑可以单独测试并复用，Hook 使你在无需修改组件结构的情况下复用状态逻辑，这使得在组件间或社区内共享hook变得更加便捷**

# 2.复杂组件变得难以理解



# 3.难以理解的class

# 什么是hooks

> hook就是可以让你在一些函数组件里“钩入” React state及生命周期等特性的函数，**HOOK不能在class组件中使用**