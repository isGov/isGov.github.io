---
abbrlink: Effect
title: Effect
date:  2024-03-12 15:20:57
type: "react"
tags: react
categories: react
keywords: react
description: 什么是Effect Hook？有什么作用？
cover: /img/95.jpg
copyright_author: gov
top_group_index: 6
---
# Effect Hook

> **在组件中执行过数据获取、订阅或者手动修改过DOM，我们统一把这些数据称为“副作用”，或者简称为“作用”**
>
> useEffect 是一个Effect Hook ，给函数组件增加了操作副作用的能力，**它跟class组件中的componentDidMount、componentDidUpdate和componentWillUnmount 具有相同的用途，只不过被合并成了一个API**

```react
function Num (){
  const [num,setNum] = useState(0);
  useEffect(()=>{
    console.log('useEffect');
  })
  return <div>
    <p>num:{num}</p>
    <button onClick={()=>setNum(num+1)}>+1</button>
  </div>
}

class App extends React.Component {
  render() {
    return <div>
      <Num></Num>
    </div>;
  }
}
```

>  18版本后，effect仅在开发模式(development)下，且使用了严格模式(Strict Mode)下会触发两次，生产环境不会
>
> 之所以执行两次，是为了模拟立即卸载组件和重新挂载组件，为了帮助开发者提前发现重复挂载造成的Bug的代码
>
> **18版本加入了分片更新 fiber架构，组件可能执行多次，目的就是我们在开发的时候，useEefect执行多次不会影响组件状态**

# 使用规则

> 1. **只能在函数最外层调用hook，不要再循环、条件判断或者子函数中调用**
> 2. **只能在React的函数组件中调用hook，不要再其他Javascript函数中调用**

