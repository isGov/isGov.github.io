---
abbrlink: history对象
title: history对象
date:  2024-03-12 15:27:57
type: "react"
tags: react
categories: react
keywords: react
description: 什么是history对象，它有什么属性？
cover: /img/92.jpg
copyright_author: gov
top_group_index: 6
---
# history对象

> history 对象提供了对浏览器回话历史的访问，总共5个api

> 1. pushState：创建一个新的url，并跳转至该url
>
>    pushState() 需要三个参数：
>
>    - ​	一个状态对象
>    - 一个标题(目前可忽略)
>    - 一个url(可选)
>
> - **状态对象：**状态对象state 是一个javascript 对象，通过pushState() 创建新的历史记录条目，无论什么时候用户导航到新的状态，popState 事件都会被触发，且该事件的 state 属性包含该历史记录条目状态对象的副本。状态对象可以是被序列化的任何东西，原因是在Firefox 将状态对象保存在用户的磁盘上，以便在用户重启浏览器时使用，我们规定了状态对象在序列化表示后有640k 的大小限制。如果你给 pushState() 方法传了一个序列化后大于640k的状态对象，该方法会抛出异常，如果你需要更大的空间，建议使用sessionStorage 以及locaStorage
> - **标题：**Firebox 目前忽略这个参数，但未来可能会用到，在此处传一个空字符串应该可以安全的防范未来这个方法的更改，或者，你可以为跳转的 state 传递一个短标题
> - **URL：**该参数定义了新的历史URL记录，注意，调用 pushState() 后浏览器并不会立即加载这个URL，但可能会在稍后某些情况下加载这个URL，比如在用户重新打开浏览器时，新URL不必须为绝对路径，如果新URL 是相对路径，那么它将被作为相对于当前URL 处理，新URL 必须与当前URL 同源，否则 pushState() 会抛出一个异常，该参数时可选的，缺省为当前URL

> 2.popState
>
> 调用 history.pushState() 或者 history.replaceState() 不会触发popState 事件 ,popstate 事件只会在浏览器某些行为下触发，比如点击**后退 前进**按钮(或者在JavaScript中调用 history.back()、history.forward()、history.go()方法)，此外，a标签的锚点也会触发该事件
>
> ```react
> var stateObj = {foo:"bar"}
> history.pushState(stateObj,"page 2","bar.html")
> ```
>
> 这将使浏览器地址栏显示为 http://mozila,org/bar.html，但并不会导致浏览器加载 bar.html ，甚至不会检查bar.html 是否存在
>
> 假设现在用户又访问了 http://google.com，然后点击了返回按钮，此时，地址栏将显示 http:imozilia.org/bar.html，同时页面会触发 popstate 事件，事件对象state中包含了 stateObj的一份拷贝。页面本身与 foo.html 一样，尽管其在 popstate 事件中可能会修改自身的内容

> 3.replaceState:修改当前url
>
> history,replacestate()的使用与 history.pushstate()非常相似，**区别在于replacestate()是修改了当前的历史记录项而不是新建一个**。注意这并不会阻止其在全局浏览器历史记录中创建一个新的历史记录项
> replacestate()的使用场景在于为了响应用户操作，你想要更新状态对象 slale 或者当前历史记录的 URL

> 4.back:返回后一个url
>
> 在history中向后跳转
>
> ```js
> window.history.back()
> ```

> 5.forward:返回前一个url
>
> 这和用户点击浏览器回退按钮的效果相同
>
> ```js
> window.history.forward()
> ```

> 6.go:跳转到指定页面的url
>
> 当前页面为0
>
> ```js
> window.history.go(-1)
> ```

