# React面试题 

目录
面试中常提的重要概念
React生命周期
Redux
Router
重要的方法
面试中常提的重要概念
1 什么是模块化

是从代码的角度进行分析的。把一些可复用的代码抽成一个单独的模块，便于项目维护和开发

2 什么是组件化

是从ui的角度进行分析的 把一些可复用的ui元素抽成一个单独的组件便于项目的维护和开发

3 组件化的好处

随着项目的规模增大 手里的组件越来越多 很方便就能把现有的组件拼接成一个完整的页面

4 DOM和虚拟DOM

DOM的本质 ：浏览器中用js对象表示页面上的元素 并提供操作DOM的API

虚拟DOM的本质：这是框架中的概念 是程序员用js对象来模拟页面上的DOM和DOM的嵌套 为的是实现DOM的高效更新

虚拟DOM是如何工作的？

虚拟DOM只不过是真实的DOM的javascript对象表示。与更新真实的DOM相比，更新javascript对象更容易，更快捷。

React将整个DOM副本保存为虚拟DOM。每次更新时，它都会维护两个虚拟DOM，比较之前的状态和当前的状态，并确定哪些对象已被更改。并将这些变化更新到实际的DOM上

5 React如何提高性能

5.1 适当地使用shouldComponentUpdate生命周期方法。 它避免了子组件的不必要的渲染。 如果树中有100个组件，则不重新渲染整个组件树来提高应用程序性能。

5.2 使用create-react-app来构建项目，这会创建整个项目结构，并进行大量优化。

5.3 不可变性是提高性能的关键。不要对数据进行修改，而是始终在现有集合的基础上创建新的集合，以保持尽可能少的复制，从而提高性能。

5.4 在显示列表或表格时始终使用 Keys，这会让 React 的更新速度更快

5.5 多使用无状态组件(Function)

5.6 代码分离是将代码插入到单独的文件中，只加载模块或部分所需的文件的技术。

6 React如何在重新加载页面时保留数据

单页面应用程序首先在DOM中加载index.html，然后在用户浏览页面时加载内容，或者从同一index.html中后端API中获取任何数据。如果我们通过点击浏览器中的重新加载按钮 重新加载页面index.html，整个React应用程序将重新加载，我们将丢失应用程序的状态。

如何保留应用状态？

每当重新加载应用程序时，我们使用浏览器localstorage来保存应用程序的状态。我们将整个存储数据保存在localstorage中，每当有页面刷新或重新加载时，我们从localstorage加载状态。


7 如何在React中应用样式

1 外部样式表

通过import导入外部样式表，然后应用className 注意不是class

2 内敛样式

给style内接收的是一个对象形式的css，注意css中的'-'自动去掉 并且下一个单词首字母大写

style={{backgroundColor:'red'}}
3 定义样式对象并应用

const footerStyle = {
                width: '100%',
                backgroundColor: 'red',
                padding: '20px',
                font: '20px',
                color: 'white',
                fontWeight: 'bold'
            }
<div style={footerStyle}></div>
8 state

8.1 一句话解释state和props的区别

state是组件内部维护的一组用于反映组件ui变化的状态集合 是可变的

props一般存在于子组件 通过父组件的state变化传递给子组件作业propss来更新视图

8.2 state使用细节

1 state必须是一个对象

2 this.setState方法一般情况是异步的 注意<一般情况下>特殊 在一些异步函数中 (定时器，ajax,Promise)中setState是同步的

8.3 什么时候可以定义一个state或者说是一个变量可否可以作为一个state

state不能定义过多，因为如果使用了state就会给这个变量增加一些响应式挂载

1 如果这个变量是通过props从父组件获取 他就不是一个状态

2 如果这个变量可以通过其他状态state或是属性props 通过数据处理得到 那么他不是一个状态

3 如果变量在render中没有使用到 那么他就不是一个状态

4 如果变量在整个生命周期中都保持不变 那么他不是一个状态

9 什么是jsx

JSX 是JavaScript XML 的简写。是 javascript的语法扩展，它利用 JavaScript 的表现力和类似 HTML 的模板语法，来生成React元素，并将这些元素在DOM中呈现

下面是JSX的一个例子：

render(){
    return(        
        <div>
            <h1>{{name}}</h1>
        </div>
    );
}
浏览器无法识别jsx 需要babel（jsx转化器）将jsx转化为js对象

10 什么是props

Props 是 React 中属性的简写。它们是只读组件，必须保持纯，即不可变。

它们总是在整个应用中从父组件传递到子组件。

子组件永远不能将 prop 送回父组件。这有助于维护单向数据流，通常用于呈现动态生成的数据。

11 什么是React

React是一个简单的javascript UI库，用于构建高效、快速的用户页面。它是一个轻量级库，因此很受欢迎。它遵循组件设计模式、声明式编程范式和函数式编程概念，以使前端应用程序更高效。它使用虚拟dom来优秀地操作dom。它遵循从高阶组件到低阶组件的单项数据流

12 React 中 keys 的作用是什么？

在开发过程中，我们需要保证某个元素的 key 在其同级元素中具有唯一性。在 React Diff 算法中 React 会借助元素的 Key 值来判断该元素是新近创建的还是被移动而来的元素，从而减少不必要的元素重渲染。此外，React 还需要借助 Key 值来判断元素与本地状态的关联关系，因此我们绝不可忽视转换函数中 Key 的重要性。

13纯函数

纯函数是始终接受一个或多个参数并计算参数然后返回数据或是函数的函数。

14高阶函数

高阶函数就是将 函数作为参数 或 返回函数 的函数 或者都有

这些高阶函数可以操纵其他函数

15什么是函数式编程

函数式编程是声明式编程的一部分（声明式编程（注重过程）命令式编程（注重结果））

函数式编程的几个部分：1 不可变性 2纯函数 3数据转换 4高阶函数 5递归 6组合

在react中，我们将功能划分为小型可重用的纯函数，我们必须将这些可重用的函数放在一起，最终使其成为产品。

将所有较小的函数组合成更大的函数，最终得到一个应用程序，这称为组合。

16 diff算法

三次对比

1 tree diff 新旧dom树逐层对比

2 component diff 每一层进行组件级别的对比 只是对比组件类别

3 element diff 组件相同时 进行元素级别的对比

17 组件

组件的类别分为

17.1 函数/无状态组件/展示组件

函数或是无状态组件是一个纯函数，他可接收参数并返回react元素，并且没有任何副作用。但这些组件没有生命周期函数，所以也叫展示组件

export const Header = () => {
    return(
        <div style={{backgroundColor:'red'}}>
            <h1>Hello World</h1>
        </div>
    )
}
17.2 类/有状态组件

这就是我们在编写react中最经常创建的组件类同 通过class xx extends React.Component这类组件可以通过setState()来改变组件的状态，并且可以使用生命周期函数

17.3 容器组件

容器组件用来包含展示其它组件或其它容器组件，但里面从来都没有html。

17.4 高阶组件

其实和高阶函数的意思差不多。意思是将组件作为参数并生成另一个组件的组件。

17.5 受控和非受控组件

例如input option radio 他们的状态是不受react控制的 而是控件本身具有的 我们把这样的组件称为非受控组件

非受控->受控组件的转化

首先把状态绑定到非受控组件的value、checked上

然后监听该组件的onChange事件 用e.target 获取input上面的数据 然后通过setState设置数据给state内的数据

18 更新组件的正确方式和错误方式

//错误方式
this.state.name = '马东什么'
//正确方式
this.setState({name:'马东什么'})

//错误方式
this.setState({
    title: this.state.name + this.props.type
})
//正确方式
this.setState((state, props) => {
    title: state.name + props.type
});
19超越继承的组合compose

在react中，我们总是使用组合而不是继承，组件中的组合 直接上例子

import { UserForm } from './userForm';
import { CompanyForm } from './companyForm';

export class FormList extends React.Component {

render() {
    render() {
        return (
          <div className="dashboard"> 
              <UserForm />
              <CompanyForm />
          </div>
        );
    }
}
20 什么是 Fragments

react中我们需要有一个父元素去包裹其他react元素

return (
    <div>
      <div>一步 01</div>,
      <div>一步 02</div>,
      <div>一步 03</div>
    </div>
)
解决这个问题第一种方法是数组的方式

 return [
        <div>一步 01</div>,
        <div>一步 02</div>,
        <div>一步 03</div>
    ];
第二种方式就是 Fragments

return (
    <React.Fragment>
         <div>一步 01</div>,
         <div>一步 02</div>,
         <div>一步 03</div>
    </React.Fragment>
)
并且它可以简写<>

return (
    <>
         <div>一步 01</div>,
         <div>一步 02</div>,
         <div>一步 03</div>
    </>
)
21类型检查

随着时间推移应用程序变得越来越大,因此类型检查非常重要。ProTypes为组件提供类型检查

import PropTypes from 'prop-types';

具体实现通过上下文的示例

22 什么是上下文

在react中，我们会遇见这么一个情况，如果爷爷想传东西给孙子，那么需要这么做

爷爷->孙子->儿子

如果层级特别深 那么如果通过props层层传递是明显不合理的。这时我们就需要用到context上下文 通过设置上下文 任意一个后代元素都可以直接取到上下文的内容 不需要层层传递

//首先在父组件定义上下文 并且需要先标明上下文的类型通过  21的内容
//定义类型
static childContextTypes={
    color:PropTypes.string
}
//定义上下文属性
getChildContext(){
 //这里返回什么  上下文的内容就是什么
  return {
            color:this.state.color
  }

//先定义出这个属性
 constructor(props){
    super(props);
    this.state={
        color:"red"
    }
}
然后是后代元素  可以使子元素也可以是孙子元素 等等等
//后代必须验证  不验证就没有 上下文
static contextTypes={
    color:PropTypes.string
}

然后就可以直接通过this.context.color来取出上下文的这个属性

return (
    <div>
        <h1 style={{color:this.context.color}}>孙子</h1>
    </div>
)


React生命周期
初始化阶段

default 是默认 预设的意思 init是初始化 这两个单词含义不同

getDefaultProps() 设计初始的props getInitialState() 可以定义this.state 并且此时可以访问this.props

其实都可以在里construstor设置 这两个钩子函数很少用

componentWillMount 此时可以修改status 但是千万不要在这里拿数据 render()

componentDidMount 很重要的钩子函数

此时已经讲组件渲染出来了 推荐在这里拿数据并更新（这里可以具体查下为什么在这个阶段去请求数据）

其实上面这个阶段可以分为 inti阶段和Mounting阶段

更新阶段

componentWillReceiveProps(nextProps) 接收新的props时用

!!shouldComponentUpdata(nextProps,nextState)

react性能优化非常重要的额一环。组件接收新的state或props时 调用 ，我们可以设置在此时对比前后两个props和state是否相同，如果相同 则返回false阻止更新 因为相同的属性状态一定会产生相同的dom树，这样就不用创造新的dom树和旧的dom树进行diff算法对比。节省大量的性能优化 尤其是在dom结构复杂的时候

案例

再用redux进行状态管理时 很重要的一个优化就是判断状态是否改变

当点击商品分类时 点击不同的分配组件的数据都会更新 但是如果点击的是和现在展示的相同的分类 这时让组件再更新一遍就很浪费性能

就可以使用这个钩子函数 判断 状态是否改变 只有改变时 才会出发更新

componentWillUpdata(nextProps,nextState)

此时可以修改state

render()

componentDidupdata()

更新完成 此时可以获取DOM节点

卸载

componentWillUnmount()

组件要卸载时调用，一些监听和定时器需要在此时清除



Redux
Redux是React的一个状态管理仓库，为了解决React组件通信和组件间状态共享

为何要使用Redux

React 是单向数据流，也就是 props 只能从父组件一层一层向子组件传递

而当数据流动复杂时 也就时子组件的状态改变会影响父组件的改变 而父组件改变又会引起其他子组件改变

这时由于 props 的单向传递

就需要父组件将需要改变的状态 和能够改变这个状态的函数 用props 一层一层传递下去 然后子组件一改变 一直逐层调用回调函数 完成各个组件的更新

在这种情况下 就需要使用redux

redux 只能使用dispatch来完成组件的更新

当子组件状态改变时 dispatch监控 然后传到reducer reducer判断是哪钟状态改变

然后直接去改变store(状态库)里的数据 然后store直接将数据分发到需要改变的组件中

省去了反复回调的麻烦

图片解释

图片出处：justjavac：4 张动图解释为什么（什么时候）使用 Redux

项目第一天

动图封面
项目第五天

动图封面
项目第20天

动图封面
使用redux

动图封面
介绍redux

官方的解释是 redux 是javascript的状态容器

我的理解是 redux是为了解决react组件间的通信和组件间的状态共享而提出的一种解决方案 它包括 store+action+reducer

1 store 用来存储react状态机 （state）的对象 跟组件connect后 store 的改变就会驱动 组件的更新

2 action 用于接收state的改变命令 是改变state的唯一途径和入口

3 reducer 是action的处理器 1监控是action的哪种type变化 用于修改store中的state值 返回一个新的state

组件间的通信

1 由于connect后 各个connect组件共享store

所以各个组件可以通过store来进行数据通信

规则 view由dispatch引起改变 然后 去触发reducer改变 store 然后引起组件的更新

2通过对象驱动组件进入生命周期

对于一个react组件来说 只能对自己的state改变驱动自己的生命周期

或是通过外部传入props进行驱动

而通过redux可以通过store来改变state 来驱动组件更新

3方便进行数据管理和切片

redux通过对store的管理和控制，可以很方便的实现页面状态的管理和切片

redux 三大原则

1单一数据源

2状态是只读的

3状态得修改均有纯函数完成





Router
种类

1.react-router是浏览器和原生应用的通用部分。

2.react-router-dom是用于浏览器的。

3.react-router-native是用于原生应用的。

这里只说react-router-dom

react-router-dom是应用程序中路由的库。React库中没有路由功能，需要单独安装react-router-dom



1.它提供两个路由器 BrowserRouter和HashRouter

BrowserRouter，这是对Router接口的实现。使得页面和浏览器的history保持一致。等于：window.location。

HashRouter，和上面的一样，只是使用的是url的hash部分，等于：window.location.hash

前者：http://127.0.0.1:3000/user/type

后者：http://127.0.0.1:3000/#/user/type不一定是这样，但#是少不了的）

如果你使用的是一个非静态的站点、要处理各种不同的url那么你就需要使用BrowserRouter。

相反的如果你的server只处理静态的url，那么就使用HashRouter。

2.react-router-dom组件

BrowserRouter和HashRouter是路由器

Route用于路由匹配

Link组件用于在应用程序中创建链接。它讲在HTML中渲染为锚标记

NavLink是突出显示当前活动链接的特殊链接。

Switch 不是必需的，但在组合路由时很有用。

Redirect 用于强制路由重定向

//示例
// normal link
<Link to="/gotoA">Home</Link>

// link which highlights currentlu active route with the given class name
<NavLink to="/gotoB" activeClassName="active">
  React
</NavLink>

// you can redirect to this url
<Redirect to="/gotoC" />

//示例
import React from 'react'
// import react router DOM elements
import { Switch, Route, Redirect } from 'react-router-dom'
import ComponentA from '../common/compa'
import ComponentB from '../common/compb'
import ComponentC from '../common/compc'
import ComponentD from '../common/compd'
import ComponentE from '../common/compe'


const Layout = ({ match }) => {
    return(
        <div className="">
            <Switch>
                <Route exact path={`${match.path}/gotoA`} component={ComponentA} />
                <Route path={`${match.path}/gotoB`} component={ComponentB} />
                <Route path={`${match.path}/gotoC`} component={ComponentC} />
                <Route path={`${match.path}/gotoD`} component={ComponentD} />
                <Route path={`${match.path}/gotoE`} component={ComponentE} />
            </Switch>
        </div>
    )}

export default Layout
Link、Redirect

<Link to{{
    pathname: '/me',
    search: '?sort=asc',
    hash: '#hash',
    state: { fromHome: true }
}} />

<Redirect to {{
    pathname: '/register',
    search: '?utm=something',
    state: { referrer: someplage.com }
}}>




重要的方法
1 combineReducers from 'redux'

随着应用变得复杂，需要对reducer函数进行拆分,拆分后每一块独立负责管理state的一部分

combineReducers 辅助函数的作用是，把一个由多个不同reducer函数作为value的object，

合并成一个最终的reducer函数，然后就可以对这个reducer函数调用createStore



2 applyMiddleware from 'redux'

添加中间件

中间件：redux提供了通过利用中间件来扩展自身功能以满足用户需求

因为在整个数据操作过程中 reducer是纯函数 不能做额外的处理

在view视图层显然也不行

所以只能在dispatch过程中做额外的处理 比如保存日志等等操作

而这些额外的处理就叫做中间件 middlew

而

applyMiddleware(...middlewares) 可以在其中传入多个中间件 在action过程中添加更多处理过程

并且每个中间件都有自己的'熔断'处理，当他认为这个action不需要后面的中间件进行处理时，后面的中间件也就不能对这个action进行处理

而为什么不同的中间件可以组合使用 因为redux要求所有的中间件必须提供统一的接口



3 redux-thunk中间件

thunkMiddleware等同于react-thunk 都是为了实现action的异步

将同步的action转化成异步的action 适合用于api请求场景



4 applyMiddleware(thunkMiddleware)(createStore)(reducers) 这种写法什么意思

正常写法：const store = createStore(reducer,applyMiddleware(thunk));

applyMiddleware函数参数是中间件，会返回一个函数，那个函数会接受一个store然后在返回一个函数，而这个函数还会返回一个函数，参数是reducer



5 withRouter from 'react-router-dom'

将组件和withRouter组件绑定 可以获取到history对象

withRouter 会在render时把更新后的match,location,history传递给包裹组件



6 bindActionCreators from redux

他将单个或多个ActionCreator转化为dispatch(action)的函数集合形式。

开发者不用再手动dispatch(actionCreator(type))，而是可以直接调用方法。

好处

1 将dispath触发规则单独抽离出去 便于维护

2 多个组件可重复调用
