---
abbrlink: PureComponent
title: PureComponent
date:  2024-03-12 15:22:57
type: "react"
tags: react
categories: react
keywords: react
description: PureComponent
cover: /img/98.jpg
copyright_author: gov
top_group_index: 6
---
# PureComponent

> 如果父组件需要传入很多属性，子组件要根据这些属性来判断要不要进行更新时，如果一个一个进行判断的话，会很麻烦，而react 有一个api：PureComponent就可以自己来判断属性是否变化，从而决定子组件是否重新渲染
>
> **使用**：class Button extends React.PureComponent{} 直接继承即可
>
> **原理**：把props所有的属性拿出来遍历，把state所有的属性拿出来遍历，只要有属性的引用不一样(===)，就更新组件，否则不更新