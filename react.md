# react
用于构建用户界面的 JavaScript 库
## create-react-app
react脚手架，创建简易的react模板

## react-app-rewired
CRA(create-react-app)的配置工具，将所有配置都写于config-overrides

## react-router
在React router中有三种类型的组件，一是路由组件第二种是路径匹配组件第三种是导航组件。
- 路由组件: BrowserRouter 和 HashRouter
- 路径匹配的组件: Route 和 Switch 
- 导航组件: Link

react-router-dom
> yarn add react-router-dom

```js
import React from 'react'
import { HashRouter, Route, Switch } from 'react-router-dom'
import Login from '@/views/Login'
const Router = () => {
	return (
		<HashRouter>
			<Switch>
				<Route component={Login} exact path="/login" />
			</Switch>
		</HashRouter>
	)
}

export default Router
```

```js
import { withRouter } from 'react-router-dom' 
export default withRouter(xxxx)

// dom
import { Link } from 'react-router-dom'
<Link to={route.path}></Link>
// js
props.history.push('/dashboard')
```


## react-dom
```js
import ReactDom from 'react-dom'
ReactDom.render(<App />, document.getElementById('root'));
```

## redux,react-redux
store.js
```js
import { createStore,/* applyMiddleware, compose*/ } from 'redux'
import reducers from './reducers/index'
const store = createStore(
	reducers
)
export default store
```
app.js
```js
import React from 'react'
import { Provider } from 'react-redux'
import Router from './router/index'
import store from '@/redux/store'
class App extends React.Component {
	render() {
		return (
			<Provider store={store}>
				<Router />
			</Provider>
		);
	}
}
export default App;
```
### connect()
```js
import { connect } from 'react-redux'

class Login extends Component {
  constructor(props) {
		super(props)
	}
  login() {
    ...
    this.props.setUserInfo()
  }
}
const mapStateToProps = state => state
const mapDispatchToProps = dispatch => ({
	setUserInfo: data => {
		dispatch(setUserInfo(data))
	}
})
export default connect(
	mapStateToProps,
	mapDispatchToProps
)(Login)
```

## react hooks
react 16.8版本推出
function component 跟 class component的区别
> function component
```js
function FC(props){
  return <div>{props.message}</div>
}
```
> class component
```js
class CC extends React.Component{
  constructor(props) {
    super(props)
  }
  render(){
    return <div>{this.props.message}</div>
  }
}
```

### 生命周期
```js
import React, { useEffect } from 'react'
```
### state
```js
import React, { useState } from 'react'
```
```js
function Count() {
  const [data, setData] = useState({
    count: 0,
    name: 'cc',
    age: 18,
  })
  const handleClick = () => {
    const { count } = data
    // 这里必须将完整的state对象传进去
    setData({
      ...data,
      count: count + 1,
    })
  }
  return (<button onClick={handleClick}></button>)
}
```

### antd
UI组件
