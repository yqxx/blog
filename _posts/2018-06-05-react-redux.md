---
layout: post
title: react-redux
date: 2018-6-1
categories: react
tags: [react-redux]
description: 边学边记录。
---

### 两个核心方法

- Provider
普通组件，可以作为顶层app的分发点，它只需要store属性就可以了。它会将state分发给所有被connect的组件，不管它在哪里，被嵌套多少层

- connect
它是一个科里化函数，意思是先接受两个参数（数据绑定mapStateToProps和事件绑定mapDispatchToProps），再接受一个参数（将要绑定的组件本身）

- mapStateToProps
构建好Redux系统的时候，它会被自动初始化，但是你的React组件并不知道它的存在，因此你需要分拣出你需要的Redux状态，所以你需要绑定一个函数，它的参数是state，简单返回你关心的几个值

- mapDispatchToProps
声明好的action作为回调，也可以被注入到组件里，就是通过这个函数，它的参数是dispatch，通过redux的辅助方法bindActionCreator绑定所有action以及参数的dispatch，就可以作为属性在组件里面作为函数简单使用了，不需要手动dispatch

作者：Wang Namelos
链接：https://www.zhihu.com/question/41312576/answer/90782136
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

连接Redux和React
React和Redux没有直接联系, 也就是说, Redux中dispatch触发store中state变化, 并不会导致React重新渲染
要在React的项目中使用Redux，比较好的方式是借助react-redux这个库来做连接，更舒服地在React的代码中使用Redux