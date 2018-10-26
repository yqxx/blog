---
layout: post
title: react-redux
date: 2018-6-1
categories: react
tags: [react-redux]
description: 边学边记录。
---
[http://www.ruanyifeng.com/blog/2016/09/redux_tutorial_part_three_react-redux.html](http://www.ruanyifeng.com/blog/2016/09/redux_tutorial_part_three_react-redux.html)
### 两个核心方法1

- Provider

普通组件，可以作为顶层app的分发点，它只需要store属性就可以了。它会将state分发给所有被connect的组件，不管它在哪里，被嵌套多少层

- connect

它是一个科里化函数，意思是先接受两个参数（数据绑定mapStateToProps和事件绑定mapDispatchToProps），再接受一个参数（将要绑定的组件本身）

引用自[https://www.zhihu.com/question/41312576?sort=created](https://www.zhihu.com/question/41312576?sort=created)

`mapStateToProps`

第一个参数总是state对象，还可以使用第二个参数，代表容器组件的props对象

构建好Redux系统的时候，它会被自动初始化，但是你的React组件并不知道它的存在，因此你需要分拣出你需要的Redux状态，所以你需要绑定一个函数，它的参数是state，简单返回你关心的几个值

这个函数来指定如何把当前 Redux store state 映射到展示组件的 props 中

`mapDispatchToProps`

声明好的action作为回调，也可以被注入到组件里，就是通过这个函数，它的参数是dispatch，通过redux的辅助方法bindActionCreator绑定所有action以及参数的dispatch，就可以作为属性在组件里面作为函数简单使用了，不需要手动dispatch

连接Redux和React
React和Redux没有直接联系, 也就是说, Redux中dispatch触发store中state变化, 并不会导致React重新渲染
要在React的项目中使用Redux，比较好的方式是借助react-redux这个库来做连接，更舒服地在React的代码中使用Redux


使用 connect() 前，需要先定义 mapStateToProps 这个函数来指定如何把当前 Redux store state 映射到展示组件的 props 中。例如，VisibleTodoList 需要计算传到 TodoList 中的 todos，所以定义了根据 state.visibilityFilter 来过滤 state.todos 的方法，并在 mapStateToProps 中使用

我们希望 VisibleTodoList 向 TodoList 组件中注入一个叫 onTodoClick 的 props ，还希望 onTodoClick 能分发 TOGGLE_TODO 这个 action：

{% highlight Perl %}
import { connect } from 'react-redux'
import { toggleTodo } from '../actions'
import TodoList from '../components/TodoList'

const getVisibleTodos = (todos, filter) => {
  switch (filter) {
    case 'SHOW_COMPLETED':
      return todos.filter(t => t.completed)
    case 'SHOW_ACTIVE':
      return todos.filter(t => !t.completed)
    case 'SHOW_ALL':
    default:
      return todos
  }
}

const mapStateToProps = state => {
  return {
    todos: getVisibleTodos(state.todos, state.visibilityFilter)
  }
}

const mapDispatchToProps = dispatch => {
  return {
    onTodoClick: id => {
      dispatch(toggleTodo(id))
    }
  }
}

const VisibleTodoList = connect(
  mapStateToProps,
  mapDispatchToProps
)(TodoList)

export default VisibleTodoList
{% endhighlight %}

children是react自带的，比如
```
<Root>
    <Inner>
        <div></div>
    </Inner>
</Root>
```
<Inner />是<Root />的children, <div />是<Inner />的children，不向子组件明确传递也能取到
```
Link.propTypes = {
  active: PropTypes.bool.isRequired,
  children: PropTypes.node.isRequired,
  onClick: PropTypes.func.isRequired
}
```
这东西只是react的类型校验，有没有不影响代码的正常运行，这里校验了父组件的children, 如果父组件没有children，会报一个没有children的错，便于定位问题。