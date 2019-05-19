# react

<a name="rebusm"></a>
# [](#rebusm)初级
<a name="wbt4sz"></a>
### [](#wbt4sz)第三方资源
[React 入门实例教程-阮一峰](http://www.ruanyifeng.com/blog/2015/03/react.html)<br /> 
<a name="iki1fq"></a>
### [](#iki1fq)特别提示
<a name="cmyces"></a>
#### [](#cmyces)关于this
React.createClass有一个内置功能，自动绑定所有方法this。React的类模型无此功能。当使用ES6的class语法来创建组件，react本身取消了这种自动绑定this的功能，要使得this正确指向生成的组件实例，要使用bind或者箭头函数。<br />this.handleClick = this.handleClick.bind(this); <br /><div onClick={() => this.handleClick()}> ；
<a name="00bmdc"></a>
#### [](#00bmdc)**网络请求**
React官网上提到，可以在componentDidMount中发送网络请求，这也是一般情况下的最佳实践。
<a name="vsarhd"></a>
### [](#vsarhd)**数据**
每个React组件都有自己的 state，其与 props 的区别在于 state只存在组件的内部，props 在所有实例中共享。
<a name="67fbui1490614868218"></a>
#### [](#67fbui1490614868218)p**rops**
1. props是一种父级向子级传递数据的方式，切是单向的，只会从父组件传到子组件；<br />2. props是只读的。<br />3. props是组件唯一的数据源，上层组件的prop改变会递归地向下遍历整棵组件树，重渲染用此属性的组件。
<a name="84wzjp1488453678789"></a>
#### [](#84wzjp1488453678789)**state**
react把每一个组件都看成是一个状态机，组件内部通过state来维护组件状态的变化，这也是state唯一的作用。<br />**每次修改 state，都会重新渲染组件**，实例化后通过 state 更新组件。<br />调用this.setState （并不是一次setState会触发一次render，React可能会合并操作，再一次性进行render）。
<a name="yl3pwe"></a>
### [](#yl3pwe)**属性**
<a name="70ebkx"></a>
#### [](#70ebkx)**refs属性**
  ReactDOM.findDOMNode（this.refs.xxx）来找到实际的节点 
<a name="68gtzd1492428445944"></a>
#### [](#68gtzd1492428445944)**ref属性**
	`ref`可挂组件上也可dom元素上；

- 挂到组件(`class`声明的组件)上的ref表示对组件实例的引用。不能在函数式组件上使用 ref 属性，因为它们没有实例：

- 挂载到dom元素上时表示具体的dom元素节点。


ref 属性可接受一个回调函数，在组件被加载或卸载时会立即执行。

1. 当给 HTML 元素添加 ref 属性时，ref 回调接收了底层的 DOM 元素作为参数。

2. 当给组件添加 ref 属性时，ref 回调接收当前组件实例作为参数。

3. 当组件卸载的时候，会传入null

4. ref 回调会在componentDidMount 或 componentDidUpdate 这些生命周期回调之前执行。 

<a name="m0d98510-e133-a1e9-e58e-4d263529b89b"></a>
#### [](#m0d98510-e133-a1e9-e58e-4d263529b89b)**key属性**
可以为组件或元素设置key属性，key用来标识这个组件或元素。key不需要全局唯一，只需要在兄弟组件或兄弟元素间保证唯一性就可以。key常用到集合（List）元素中。不要使用元素在集合中的索引值作为key。
<a name="49fpfi1500376834716"></a>
# [](#49fpfi1500376834716)**Api**
<a name="h38wzb"></a>
### [](#h38wzb)api变动
React 官方正式发布了 v16.3 版本。在这次的更新中，除了前段时间被热烈讨论的新 `Context API` 之外，新引入的两个生命周期函数 `getDerivedStateFromProps`，`getSnapshotBeforeUpdate` 以及在未来 v17.0 版本中即将被移除的三个生命周期函数 `componentWillMount`，`componentWillReceiveProps`，`componentWillUpdate` .<br />
<a name="h1ffgo"></a>
### [](#h1ffgo)**dom**
组件并不是真实的 DOM 节点，而是存在于内存之中的一种数据结构，叫做虚拟 DOM （virtual DOM）。只有当它插入文档以后，才会变成真实的 DOM 。<br />ReactDOM.findDOMNode(component)<br />getDOMNode: this.refs.mainC.getDOMNode()<br />  -- jquery对象<br />**var _$this _**= _$_(**ReactDOM**.**findDOMNode**(**this**));<br />**var _$this _**= _$_(_e_.target);<br />_$_(**this**.refs.regSch)
<a name="gpbggz"></a>
### [](#gpbggz)**延展操作符**
延展操作符用于属性的批量赋值上。在JSX中，可以使用…运算符，表示将一个对象的键值对与ReactElement的props属性合并。<br />**var _props _**= {};<br />**_props_**.**foo **= **x**;<br />**_props_**.**bar **= _y_;<br />**var _component _**= <**Component **{...**_props_**} />;<br />_//等价于_<br />**var _component _**= <**Component foo=**{**x**} **bar=**{_y_} />;<br /> <br />它也可以和普通的XML属性混合使用，需要同名属性，后者将覆盖前者：<br /> **var _props _**= { **foo**: **'default' **};<br />**var _component _**= <**Component **{...**_props_**} **foo=**{**'override'**} />;<br />**console**.log(**_component_**.props.foo); _// 'override'_
<a name="l10ieg"></a>
##### [](#l10ieg)**forceUpdate**
强制更新
<a name="6xh7nc"></a>
##### [](#6xh7nc)**propTypes**
**static propTypes **= {<br />  **name**: PropTypes.string<br />}
<a name="nwpses"></a>
##### [](#nwpses)**context**
某个组件只要往自己的 context 里面放了某些状态，这个组件之下的所有子组件都直接访问这个状态而不需要通过中间组件的传递。一个组件的 context 只有它的子组件能够访问，它的父组件是不能访问到的，你可以理解每个组件的 context 就是瀑布的源头，只能往下流不能往上飞。<br />教程：<br />[http://huziketang.com/books/react/lesson29](http://huziketang.com/books/react/lesson29)<br /> 
<a name="ooizwq"></a>
### [](#ooizwq)**React.Children**
 <br />React.Children 是顶层API之一，为处理 this.props.children 这个封闭的数据结构提供了有用的工具。<br />this.props 对象的属性与组件的属性一一对应，但是 this.props.children 属性表示组件的所有子节点。<br />this.props.children 的值有三种可能：<br />如果当前组件没有子节点，它就是 undefined ;<br />如果有一个子节点，数据类型是 object ；<br />如果有多个子节点，数据类型就是 array 。<br />可以用 React.Children.map 来遍历子节点，而不用担心 this.props.children 的数据类型是 undefined 还是 object。<br />**React.Children.forEach**类似于 React.Children.map()，但是不返回对象。<br /> 
<a name="4d51lx"></a>
# [](#4d51lx)**生命周期**
  ![](https://cdn.nlark.com/yuque/0/2018/png/87490/1536926234104-f516b0cd-b4f3-4a2f-b802-4ef36456c387.png#width=807)

![](https://cdn.nlark.com/yuque/0/2018/png/87490/1539504268061-4ee3ea91-e15b-4db1-9a25-b32b41077ad2.png#width=740)<br /> <br />![](https://cdn.nlark.com/yuque/0/2018/png/87490/1539504963134-b021b472-69a1-4257-9387-36830efce931.png#width=826)
<a name="grggfh"></a>
#### [](#grggfh)**触发条件**
**组件运行中生命周期函数被触发的条件：**<br />**● 当父组件修改子组件的属性props时；**<br />**● 当组件自身修改状态state时。**
<a name="pt4gdn"></a>
#### [](#pt4gdn)**阶段**
**静态初始化**getDefaultProps（只会调用一次）<br />**首次实例化**getInitialState/constructor**》**componentWillMount**》**render**》**componentDidMount<br />**存在期**componentWillReceiveProps**》**shouldComponentUpdate**》**componentWillUpdate**》**render**》**componentDidUpdate<br />**销毁期**componentWillUnmount
<a name="3lvxve"></a>
#### [](#3lvxve)**API**
<a name="0htqvv"></a>
##### [](#0htqvv)**1.getDefaultProps**
作用于组件类，只调用一次，返回对象用于设置默认的props，对于引用值，会在实例中共享。
<a name="145qvo"></a>
##### [](#145qvo)**2.getInitialState/constructor**
作用于组件的实例，在实例创建时调用一次，用于初始化每个实例的state，此时可以访问this.props。getInitialState 和 getDefaultPops 的调用是有区别的，getDefaultPops 是对于组件类来说只调用一次，后续该类的应用都不会被调用，而 getInitialState 是对于每个组件实例来讲都会调用，并且只调一次。
<a name="59nilw"></a>
##### [](#59nilw)-**3.componentWillMount**
在完成首次渲染之前调用，该方法在首次渲染之前调用，也是再 render 方法调用之前修改 state 的最后一次机会。一些组件启动的动作，包括像 Ajax 数据的拉取操作、一些定时器的启动等
<a name="dgp5rw"></a>
##### [](#dgp5rw)**4.render**
必选的方法，创建虚拟DOM，在每次调用setState方法时，React会自动执行render方法来更新虚拟DOM，如果组件已经被渲染，那么还会更新到DOM中去。<br />**1. 只能通过this.props或this.state访问数据**<br />**2. 只能出现一个顶级组件（不能返回数组）**<br />**3. 可以返回null、false或任何React组件**<br />**4. 不能对props、state或DOM进行修改**
<a name="l816kg"></a>
##### [](#l816kg)**5.componentDidMount**
真实的DOM被渲染出来后调用，在服务端中，该方法不会被调用。 该方法被调用时，已经渲染出真实的 DOM，可以再该方法中通过 this.getDOMNode() 访问到真实的 DOM(推荐使用 ReactDOM.findDOMNode())。此时已可以使用其他类库来操作这个DOM。
<a name="xq8tez"></a>
##### [](#xq8tez)-**6.componentWillReceiveProps（nextProps）**
当挂载的组件收到新的props时，调用此函数，在初始化渲染的时候，该方法不会调用。对外部传入的数据进行一些预处理，该方法用于比较this.props和nextProps，当两者不同的时候，使用this.setState()来改变state。<br />猜测：<br />当组件的属性可能发生变化时，这个方法会被调用。这里说可能，是因为父组件render方法每次被调用时，子组件的这个方法都会被调用（子组件第一次初始化时除外）
<a name="34sttl"></a>
##### [](#34sttl)**7.shouldComponentUpdate(nextProps,nextState)**
当挂载的组件收到新的props、state时时，调用此函数，做出是否更新dom的决定，返回false表示跳过后续的生命周期方法。通常不需要使用以避免出现bug。在出现应用的瓶颈时，可通过该方法进行适当的优化。<br />在首次渲染期间或者调用了forceUpdate方法后，该方法不会被调用。<br />React提供了一个React.PureComponent组件，这个组件重写了shouldComponentUpdate，会对前后两次的state和props进行浅比较，如果不一致，才会返回true，触发后续的render方法。这里的浅比较指，只会对state和props的第一级属性进行比较（使用!==），这满足一般的使用场景。
<a name="xprkfg"></a>
##### [](#xprkfg)-**8.componentWillUpdate(nextProps,nextState)**
接收到新的props或者state后，在组件重新渲染之前执行，在渲染之前最后的props和state都发生了改变，这个函数使用很少，一般用在日志和记录的打印。 不可以在这个方法中修改props或state，如果要修改，应当在componentWillReceiveProps()中修改。
<a name="37o9rx"></a>
##### [](#37o9rx)**9.componentDidUpdate(prevProps, prevState)**
完成渲染新的props或者state后调用，此时可以访问到新的DOM元素。当组件重新渲染完毕后调用，即完成渲染新的props或者state后调用，此时可以访问到新的DOM元素。
<a name="r3y0fu"></a>
##### [](#r3y0fu)**10.componentWillUnmount**
组件被移除之前被调用，可以用于做一些清理工作，在componentDidMount方法中添加的所有任务都需要在该方法中撤销，比如创建的定时器或添加的事件监听器。因此可以在这个方法中销毁非React组件注册的事件、插入的节点，或者一些定时器之类。这个过程要小心处理，如果处理不当可能导致内存泄漏，比如实例化了某个第三方插件却没销毁。这个函数很少用到，因为浏览器本身具有垃圾回收机制<br /> <br />举列子<br />// Correct<br />this.setState(function(prevState, props) {<br />  return {<br />    counter: prevState.counter + props.increment<br />  };<br />});
<a name="diosgy"></a>
### [](#diosgy)**Dom操作**
--------------dom操作--------------<br />  -- jquery对象<br />**var _$this _**= _$_(**ReactDOM**.findDOMNode(**this**)); **this=this.refs.componentName**<br />**var _$this _**= _$_(_e_.target);<br />_$_(**this**.refs.regSch)

--------------作为属性使用--------------<br />  dangerouslySetInnerHTML={{**__html**: **reminder**}}<br /> 
<a name="b3dooh"></a>
## [](#b3dooh)**路由**
**Link**<br />1. url?**hosId**=225<br />  实际效果: <**a href='url?hosId=225'**>deptName </**a**><br />组件获取传参:this.props.location.query;<br />2.<Link **to**={{pathname:url,query:{**hosId**:1332}}}> {**deptName**} </**Link**><br />实际效果: <**a href='url?hosId=225'**>deptName </**a**><br />组件获取传参:this.props.location.query;<br /> <br /> <br />https://open.weixin.qq.com/connect/oauth2/authorize?appid=wx71af21a4dcabb07b&redirect_uri=http%3A%2F%2Fm.hsyuntai.com%2Fcloud%2F310000%2FonlineConsult%2FchooseDoctor&response_type=code&scope=snsapi_base&state=weixinAuthorize#wechat_redirect<br />histroy 属性<br />Router组件的history属性，用来监听浏览器地址栏的变化，并将URL解析成一个地址对象，供 React Router 匹配。<br />history属性，一共可以设置三种值。<br />● browserHistory<br />● hashHistory<br />● createMemoryHistory<br />如果设为hashHistory，路由将通过URL的hash部分（#）切换，URL的形式类似example.com/#/some/path。<br /> <br />如果设为browserHistory，浏览器的路由就不再通过Hash完成了，而显示正常的路径example.com/some/path，背后调用的是浏览器的History API。<br /> <br />createMemoryHistory主要用于服务器渲染。它创建一个内存中的history对象，不与浏览器URL互动。
<a name="lmviok"></a>
## [](#lmviok)八 实践

[最佳实践](https://segmentfault.com/a/1190000005013207)
<a name="tflfsb"></a>
## [](#tflfsb)**九 资料**
<a name="5i3kgl"></a>
#### [](#5i3kgl)**书籍**
<a name="y0n2lv"></a>
##### [](#y0n2lv)**《React.js 小书》 **
**http://huziketang.com/books/react/**




