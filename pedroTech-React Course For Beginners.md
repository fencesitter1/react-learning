```toc
```


# 介绍
# React 基础
## 安装初始化
1. 安装 npm,node.js
2. `npx create-react-app .`
3. `npm init`
4. `npm start`
# JSX, 组件, 属性(props)
## jsx
### 概念
在 React 中，JSX 是一种 JavaScript 的语法扩展，它被用来描述 React 元素的结构。JSX 看起来类似于 XML 或 HTML，但实际上它更接近于 JavaScript。它提供了一种声明式的方式来描述用户界面的结构，使得 React 组件的编写更加简洁和直观。
### 写法对比
- 普通写法
```jsx
function App() {
  const name = 'wuwei';
  return (
    <div className="App">
      <h1>{name}</h1>
      <h1>{name}</h1>
      <h1>{name}</h1>
    </div>
  );
}
```
- JSX 写法
```jsx
function App() {
  const name = <h1>wuwei</h1>;
  return (
    <div className="App">
      {name}
      {name}
      {name}
    </div>
  );
}
```
## 组件 components
在 React 中，组件是构建用户界面的基本单元。组件可以看作是独立、可复用的代码单元，它封装了特定的功能或 UI 元素。React 中的组件可以是函数组件或类组件，两者都可以接收输入（称为 props）并返回 React 元素作为输出。
**最大特点**:返回一个元素
### 函数组件：
函数组件是一种定义 React 组件的简单方式。它是一个 JavaScript 函数，接收一个 `props` 对象作为参数，然后返回一个 React 元素。以下是一个简单的函数组件的例子：
```jsx
function MyComponent(props) {
  return <div>Hello, {props.name}!</div>;
}
```
在上述例子中，`MyComponent` 是一个函数组件，它接收一个 `props` 对象，其中包含一个名为 `name` 的属性。组件返回一个 `div` 元素，显示一个问候信息。

### 类组件：
类组件是通过继承 `React.Component` 类创建的。它有一个 `render` 方法，该方法返回要渲染的 React 元素。以下是一个简单的类组件的例子：

```jsx
class MyComponent extends React.Component {
  render() {
    return <div>Hello, {this.props.name}!</div>;
  }
}
```
在这个例子中，`MyComponent` 是一个类组件，它有一个 `render` 方法，返回包含问候信息的 `div` 元素。

### 组件与 jsx 对比
- jsx
```jsx
function App() {
  const name = <h1>wuwei</h1>;
  const age = <h2>21</h2>;
  const email = <h2>chensuo0529@gmail.com</h2>;
  const user = (
    <div>
      {name}
      {age}
      {email}
    </div>
  );
  return (
    <div className="App">
      {user}
      {user}
      {user}
    </div>
  );
}
```
- 组件
使用组件的主要优势之一是它们的可复用性。你可以在应用程序的不同部分使用相同的组件，从而减少代码重复，并使代码更易于维护。
### react 组件 VS JS 函数
```jsx
  const GetName = () => {
    return 'chensuo';
  };

  const GetNameComponent = () => {
    return <h1>chensuo</h1>;
  };
}
```

> [!NOTE] react 组件特点
> 首字母大写
> 返回元素
## props (传参)
定义 User 组件,传入 props 属性,在 App 中调用时,传入参数
```jsx
function App() {
  return (
    <div className="App">
      <User
        name="chensuo"
        age="24"
        email="123414@qq.com"
      />
    </div>
  );
}
const User = (props) => {
  return (
    <div>
      <h1>{props.name}</h1>
      <h1>{props.age}</h1>
      <h1>{props.email}</h1>
    </div>
  );
};
```

# 三元运算符, 列表, CSS
## 三元运算符
三元运算符主要有两个 
	{condition ? expression_if_true : expression_if_false;}
	{condition && expression_if_true}
	**注意格式问题**
## css color
`<h1 style= {{color:isGreen?'green':'red' }} >`
注意双大括号
```jsx
function App() {

  const age = 17;
  const isGreen = true;
  return (
    <div className="App">
      <div className="User">
        <User
          name="chensuo"
          age="24"
          email="123414@qq.com"
        />
      </div>
      <div>{age > 18 ? <h2>over age</h2> : <h2>under age</h2>}</div>
      <div>
        <h1 style={{color:isGreen?'green':'red' }}>
        This has color
        </h1> 
        {isGreen && <button>This is a button</button>}
      </div>
    </div>
  );
}
```
# list
## 循环输出 list 内容
- array
```jsx
const names = ['sdfa', 'dasfa', 'fghhg', 'fhtryhtey'];
return(
<div classname="App">
      <div>
        {names.map((name, key) => {
          return <h3 key={key}>{name}</h3>;
        })}
      </div>
</div>
)
```
- list
```jsx
function App() {
  const User1 = (props) => {
    return (
      <div>
        {props.name} {props.age}
      </div>
    );
  };
  const users = [
    { name: 'Pedro', age: 21 },
    { name: 'yuyt', age: 25 },
    { name: 'jhlgj', age: 40 },
  ];

  return (
    <div className="App">
      {users.map((user, key) => {
        return (
          <User1
            name={user.name}
            age={user.age}
            key={key}
          />
        );
      })}
    </div>
  );
}
```
# React 状态, useState Hook
## State
- 概念
	组件需要 "记住 "一些东西：当前输入值、当前图片、购物车。在 React 中，这种特定于组件的内存被称为状态。
## useState hook
### hook 钩子
- 概念
	**钩子**:钩子是仅在 React 渲染时可用的特殊功能（我们将在下一页详细介绍）。它们可以让您 "挂钩 "不同的 React 功能。
### ex1:按钮 onClick

```jsx
import './App.css';
import { useState } from 'react';
function App() {
  const [age, setAge] = useState(0);
  const increaseAge = () => {
    setAge(age + 1);
  };
  return (
    <div className="App">
      <div>
        {age}
        <button onClick={increaseAge}>Increase Age</button>
      </div>
    </div>
  );
}
```
### ex2: 输入框+onChange

```jsx
function App() {
  const [inputValue, setInputValue] = useState(0);
  const handleInputChange = (event) => {
    setInputValue(event.target.value);
  };
  return (
    <div className="App">
      <div>
        <input
          type="text"
          onChange={handleInputChange}
        />
        {inputValue}
      </div>
    </div>
  );
}
```
- 实现效果:
	![动画.gif|500](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2023%2F12%2F28%2F%E5%8A%A8%E7%94%BB_21-08-58.gif)
- 获取输入框的内容
	依靠 event.target.value
### 按钮实现 show/hide

```jsx
function App() {
  const [showText, setshowText] = useState(false);
  const handleInputChange = () => {
    setshowText(!showText);
  };
  return (
    <div className="App">
      <div>
        <button 
        onClick={handleInputChange}>Show/hide</button>
        {showText && <h1>My name is chensuo .</h1>}
      </div>
    </div>
  );
}
```
- 实现效果
	![show button.gif|500](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2023%2F12%2F28%2Fshow%20button_21-37-48.gif)
### 按钮实现字体颜色变化
- 代码实现
```jsx
function App() {
  const [showColor, setshowColor] = useState('black');
  const handleInputChange = () => {
    setshowColor(showColor === 'black' ? 'red' : 'black');
  };
  return (
    <div className="App">
      <div>
        <button onClick={handleInputChange}>Show/hide</button>
        <h1 style={{ color: showColor }}>My name is wuwei .</h1>
      </div>
    </div>
  );
}
```
- 实现效果
	![buttonchangecolor.gif|500](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2023%2F12%2F28%2Fbuttonchangecolor_21-44-43.gif)

# React 中的 CRUD, ToDo 列表
## input 框的 css 设置
```css
input {
  border: 2px solid #1c7ed6;
  border-radius: 50px;
  outline: none; /* 去除点击时的默认外边框 */
}
 /* 悬浮时的样式 */
 /* 点击时的样式 */
input:hover,input:focus{
  border-color: #a5d8ff;
  box-shadow: 0 0 10px #d0ebff; /* 添加点击时的阴影效果 */
}
```
- 实现效果
	![inputcss.gif|500](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2023%2F12%2F28%2Finputcss_22-43-16.gif)

## input 内容的获取和清空
```jsx
  let [todoList, setTodoList] = useState([]);
  let [newInput, setNewInput] = useState('');
  const handleText = (event) => {
    setNewInput(event.target.value); 
    //把输入框的内容赋值给 newInput
  };
<input
  onChange={handleText}
  value={newInput}
/>
```
## 添加按钮
```jsx
const addNewList = () => {
    //添加id
    const task = {
      id: 
      todoList.length === 0? 1:todoList[todoList.length - 1].id + 1,//这里值得学习
      taskName: newInput,
      completed: false,
    };
    setTodoList([...todoList, task]); //合并数组
    setNewInput('');
  };
```
### 添加 id
```jsx
id: 
todoList.length === 0?1:todoList[todoList.length - 1].id + 1
```
### 内容添加到 list 中去
```jsx
[...todoList, task]
```
## list 内容显示
App.js 中
```jsx
<div className="list">
{todoList.map((task) => {
  return (
	<Task
	  id={task.id}
	  taskName={task.taskName}
	  deleteTask={deleteTask}
	  completedTask={completedTask}
	  completed={task.completed}
	/>
  );
})}
</div>
```
## 删除按钮+唯一 id
```jsx
  const deleteTask = (id) => {
    //解决内容重复删除
    setTodoList(todoList.filter((task) => task.id !== id));
  };
```
## 组件化(props)
$ App.js
```jsx
import { Task } from './task';
<Task
	  id={task.id}
	  taskName={task.taskName}
	  deleteTask={deleteTask}
	  completedTask={completedTask}
	  completed={task.completed}
	/>
```
$ Task.js
```jsx

export const Task = (props) => {
  return (
    <div className="container">
      <h1
        key={props.id}
        style={{ color: props.completed && 'green' }}
      >
        {props.taskName}
      </h1>
    <button 
    onClick={
    () => props.completedTask(props.id)}
    >Complete</button>
    <button 
    onClick={
    () => props.deleteTask(props.id)}
    >X</button>
    </div>
  );
};
```

^c97c94

**注意**:子组件中 export 别忘了
## 完成按钮加颜色
```jsx
  const completedTask = (id) => {
    setTodoList(
      todoList.map((task) => {
        //修改函数属性值
        return task.id === id ? { ...task, completed: true } : task;
      })
    );
  };
```
### 修改函数属性值
```jsx
todoList.map((task) => {
	//修改函数属性值
	return task.id === id ? (task.completed = true) : task;
      })
```
## .map 注意点
> [!bug] .map 的返回需要是新的元素
>这样的写法**错误**的
问题在于你在 `.map()` 的回调函数中使用了赋值语句 `(task.completed = true)`，这会导致 `task.completed` 被赋值为 `true`，然后整个表达式的值为 `true`。由于 `.map()` 期望回调函数返回新的元素而不是修改原始元素，这就导致了问题。
应该返回一个新的对象，而不是修改原始对象。修正的方式是使用对象的展开运算符 (`...`) 来创建新的对象. 

## onClick 注意点

> [!NOTE] `onClick`
> `onClick={addNewList(list)}` 这样的写法是**错误**的。
>在 `onClick` 事件中，你应该传递一个函数而不是直接调用函数。如果你写成 `onClick={addNewList(list)}`，它会在渲染时立即调用 `addNewList(list)`，而不是等到点击事件发生时再调用。
**正确的写法**是将一个函数作为 `onClick` 的处理函数，而不是直接调用它。
例如：`onClick={() => addNewList(list)}`
或者，如果 `addNewList` 不需要参数，你可以直接传递函数引用：
`onClick={addNewList}`
## 实现效果
![todolistshow.gif|500](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2023%2F12%2F29%2Ftodolistshow_14-36-35.gif)

# 组件生命周期, useEffect Hook
## 组件生命周期
挂载阶段（Mounting）：
更新阶段（Updating）：
卸载阶段（Unmounting）：
错误处理阶段（Error Handling）：
## useEffect Hook 介绍

1. **`useEffect` 是一个“逃脱通道”：**
   - `useEffect` 提供了一种在 React 范式之外执行操作的机制，即处理副作用的一种手段。
2. **与外部系统同步：**
   - 它使你能够同步组件与外部系统（如非 React 部分、网络请求、浏览器 DOM 等）的状态。
3. **避免不必要的 `useEffect`：**
   - 如果组件内部操作只涉及 React 内部的状态管理，没有与外部系统的交互，那么可能不需要使用 `useEffect`。
4. **简化代码、提高性能：**
   - 移除不必要的 `useEffect` 有助于简化代码，提高代码的可读性，减少潜在的错误，同时也可能提高运行性能。
总的来说，使用 `useEffect` 应该是有目的的，当组件需要进行副作用操作或者需要同步外部系统状态时才使用。在没有这样的需求时，避免不必要的 `useEffect` 可以保持代码的简洁性和可维护性。
## 按钮实现文本框输入的显示+组件化
```jsx
import React, { useState } from 'react';
import './App.css';
// import { Text } from './Text';
function App() {
  const [showText, setshowText] = useState(false);

  const handleShowText = () => {
    setshowText(!showText);
  };
  const Text = () => {
    const [text, setText] = useState('');
    const handleText = (event) => {
      setText(event.target.value);
    };
    return (
      <div>
        <input onChange={handleText} />
        <h1>{text}</h1>
      </div>
    );
  };
  return (
    <div className="App">
      <div className="app-container">
        <button onClick={handleShowText}>show/hide Text</button>
        {showText && <Text />}
      </div>
    </div>
  );
}

export default App;

```

> [!warning] 组件的状态需要在组件内部管理
>`const [text, setText] = useState('');`
> `const handleText = (event) => {setText(event.target.value);};`
> 都需要定义在 Text 组件的内部,要不然会出现输入框只能输入一个字符就会重新渲染的情况.
> 在 Text 内管理 text 状态，就避免了输入只能接受一个字母的问题。


## 使用编写 useEffect
```jsx
import { useEffect } from 'react';

function MyComponent() {
  useEffect(() => {
    // 每次渲染后都会执行此处的代码
  });
  return <div />;
}
```
每当你的组件渲染时，React 将更新屏幕，然后运行 useEffect 中的代码。换句话说，useEffect 会把这段代码放到屏幕更新渲染之后执行。
在严格模式下,当组件挂载时，`useEffect` 会被调用两次.
![image.png|350](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2023%2F12%2F29%2F20231229165740_16-57-41.png)

## 指定依赖项,跳过执行 Effect
```jsx
useEffect(() => {
  // 这里的代码会在每次渲染后运行，包括首次渲染和每次更新
});

useEffect(() => {
  // 这里的代码只会在组件挂载和卸载后执行 第一阶段+第三阶段
}, []);//不会检测更新

useEffect(() => {
  //这里的代码只会在每次渲染后，并且 a 或 b 的值与上次渲染不一致时执行
}, [a, b]);
```
## Unmounting 阶段
```jsx
  useEffect(() => {
    console.log('component mounted');
    return () => {
      console.log('component unmounted');
    };
  }, []);
```
这段代码包括第一阶段和第三阶段
# 从 API 获取数据
## fetch 
```jsx
 fetch('https://catfact.ninja/fact')
    .then((res) => res.json())
    .then((data) => {
      console.log(data);
    });
```
## axois
1. 导入 axios
```jsx
import Axios from 'axios';
```

```jsx
const [catFact, setcatFact] = useState('');
  const fetchCatFact = () => {
    Axios.get('https://catfact.ninja/fact').then((res) => {
      setcatFact(res.data.fact);
    });
  };
  useEffect(() => {
    // fetchCatFact();
  }, []);
```
## 只获取一次数据(useEffect)

## ex2:输入名字查询 api 信息
```jsx
import React, { useState, useEffect } from 'react';
import './App.css';
import Axios from 'axios';

function App() {

  const [info, setInfo] = useState({});
  const [nameInput, setnameInput] = useState('');
  const handlenameInput = (event) => {
    setnameInput(event.target.value);
  };
  const fetchdata = () => {
    Axios.get(`https://api.agify.io/?name=${nameInput}`).then((res) => {
      setInfo(res.data);
    });
  };

  return (
    <div className="App">
      <div className="app-container">
        <input
          placeholder="ex.pedro..."
          onChange={handlenameInput}
        />
        <button
          className="advanced-button"
          onClick={fetchdata()}
        >
          Predict Info
        </button>
        <p>name:{info?.name}</p>
        <p>predict age:{info?.age}</p>
        <p>Count:{info?.count}</p>
      </div>
    </div>
  );
}
export default App;
```
值得学习的地方:
1. `const [info, setInfo] = useState({});`
	`setInfo(res.data);` 直接状态管理为对象
2. 可选链`info?.name`
	适用于对象属性可能为空,或者对象为空的情况
## return 的作用
在 `useEffect` 中，你可以选择返回一个函数。这个函数被称为清理函数，它的作用是在副作用函数下一次运行之前或组件卸载时执行一些清理操作。

这对于需要清理的副作用（例如取消网络请求、清理定时器或取消订阅）非常有用。当你的副作用函数运行时，它可能会创建一些需要在下一次运行之前或组件卸载时清理的资源。

例如，你可能会在副作用函数中订阅一些事件或启动一个定时器。当组件卸载时，你需要取消订阅或清理定时器，以防止内存泄漏或尝试更新已卸载的组件。

下面是一个使用清理函数的 `useEffect` 示例：

```typescript
useEffect(() => {
  const timerId = setInterval(() => {
    console.log('This will run every second');
  }, 1000);

  // Here we return a cleanup function
  return () => {
    clearInterval(timerId); // This will clear the timer when the component unmounts or before the effect runs again
  };
}, []); // Empty dependency array means this effect runs once on mount and cleanup on unmount
```

在这个例子中，我们在副作用函数中启动了一个定时器，并在清理函数中清理了这个定时器。这样，当组件卸载时，定时器将被清理，防止了尝试更新已卸载的组件的错误。
# React Router DOM
## 嵌套路由+link
```jsx
import { BrowserRouter as Router, Routes, Route, Link, NavLink } from 'react-router-dom';
return (
    <div className="App">
      <Router>
        <Navbar />
        <Routes>
          <Route
            path="/"
            element={<Home />}
          />

          <Route
            path="/menu"
            element={<Menu />}
          />
          <Route
            path="/contact"
            element={<Contact />}
          />
          <Route
            path="*"
            element={<h1>404 Not Found</h1>}
          />
        </Routes>
      </Router>
    </div>
  );
}
```
Navbar.js
```js
import { BrowserRouter as Router, Routes, Route, Link, NavLink } from 'react-router-dom';

export const Navbar = () => {
  return (
    <nav>
      <NavLink to="/"> Home</NavLink>
      <NavLink to="/menu"> Menu</NavLink>
      <NavLink to="/contact"> Contact</NavLink>
    </nav>
  );
};

```

> [!warning] 路由组件名称大写
> 
路由组件一定需要大写
## 设定 Navlink 高亮样式
1. app.css 中设定 activeclassname ,默认为.avtive,可以自己设置
```jsx
<CustomNavLink to="/" activeClassName=" ">Home</CustomNavLink>
```
app.css
```css
nav {
  background-color: #333;
  overflow: hidden;
  display: flex;
  justify-content: space-around;
}

nav a {
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

nav a:hover {
  background-color: #ddd;
  color: black;
}

nav a.active(这里为定义的activeClassName) {
  background-color: #1c7f20;
  color: white;
}
```
2. 通过 activeStyle 属性进行直接设置
	```jsx
	<NavLink
  to="/faq"
  activeStyle={{
    fontWeight: "bold",
    color: "red"
  }}
>
  FAQs
</NavLink>
	```
## 封装 NavLink 样式
```jsx
import { NavLink } from 'react-router-dom';

const CustomNavLink = ({ to, children, ...props }) => {
  const defaultStyle = {
    color: 'blue',
    textDecoration: 'none'
  };

  const activeStyle = {
    color: 'red',
    fontWeight: 'bold'
  };

  return (
    <NavLink to={to} style={defaultStyle} activeStyle={activeStyle} {...props}>
      {children}
    </NavLink>
  );
};

export default CustomNavLink;
```

```jsx
import CustomNavLink from './CustomNavLink';
// ...
<CustomNavLink to="/">Home</CustomNavLink>
<CustomNavLink to="/menu">Menu</CustomNavLink>
<CustomNavLink to="/contact">Contact</CustomNavLink>
<CustomNavLink to="/useContext">useContext</CustomNavLink>
```
### children
在你的 CustomNavLink 组件中，children 是链接的文本内容：
```jsx
<CustomNavLink to="/">Home</CustomNavLink>
```
在这个例子中，CustomNavLink 的 children prop 就是字符串 "Home"。
# 状态管理, useContext Hook
## 官方文档
[hook-useContext](https://zh-hans.react.dev/reference/react/useContext)
## porp drilling 
```jsx
import React, { useState } from 'react';
export const UseContext = () => {
  const Topcomponent = () => {
    const [state, setState] = useState('Hello World');
    return (
      <div>
        <Middlecomponent state={state} />
      </div>
    );
  };
  const Middlecomponent = ({ props }) => {
    return (
      <div>
        <Bottomcomponent state=props.state />
      </div>
    );
  };
  const Bottomcomponent = (props) => {
    return <div>{props.state}</div>;
  };
  return (
    <div className="UseContext">
      <Topcomponent />
    </div>
  );
};//最终输出 hello world
```
总体来说，这个 React 组件层次结构演示了状态 ('Hello World') 从 Topcomponent 流向 Middlecomponent，然后再流向 Bottomcomponent 的过程。每个组件负责渲染一部分内容，并且状态通过组件层次结构作为 props 传递。
### prop drilling  缺点
## useContext
不需要一层层通过 props 传参,直接定义一个全局的变量
**app.js**
```jsx
import React, { useState, createContext } from 'react';
export const AppContext = createContext();//**
function App() {
  const [username, setUsername] = useState('WuWei');
  return (
    <div className="App">
      <AppContext.Provider value={{ username, setUsername }}>
        <Router>
          <Navbar />
          <Routes>
            <Route
              path="/"
              element={<Home />}
            />

            <Route
              path="/menu"
              element={<Menu />}
            />
            <Route
              path="/contact"
              element={<Contact />}
            />
            <Route
              path="*"
              element={<h1>404 Not Found</h1>}
            />
            <Route
              path="/useContext"
              element={<UseContext />}
            />
            <Route
              path="/profile"
              element={
                <Profile
                // username={username}
                // setUsername={setUsername}
                />
              }
            />
          </Routes>
        </Router>
      </AppContext.Provider>
    </div>
  );
}
```
Home.js
```jsx
import { useContext } from 'react';
import { AppContext } from '../App';
export const Home = () => {
  const { username } = useContext(AppContext);
  return <h1>This is home page and user is {username}.</h1>;
};
```
# React Query 
### 介绍   
React Query 是一个强大的数据获取库，它可以帮助你在 React 应用中获取、缓存和同步服务器状态。它提供了许多有用的特性，包括：
- 数据获取：React Query 提供了 `useQuery` 钩子，你可以用它来获取数据。这个钩子会返回一个对象，包含数据、错误、加载状态等信息。
- 数据突变：React Query 提供了 `useMutation` 钩子，你可以用它来执行创建、更新或删除操作。这个钩子会返回一个突变函数和突变状态。
- 自动重试：如果数据获取或突变失败，React Query 会自动重试。
- 背景更新：当你重新聚焦到应用或者网络重新连接时，React Query 会在后台更新数据。
- 分页和无限加载：React Query 提供了 `usePaginatedQuery` 和 `useInfiniteQuery` 钩子，你可以用它们来实现分页和无限加载。
- 依赖查询：你可以让一个查询依赖于另一个查询的结果。
- 开箱即用的 Devtools：React Query 提供了一个开发者工具，你可以用它来查看和管理你的查询和突变。
这只是 React Query 的一部分特性。如果你想了解更多，可以查看 [React Query 的文档](https://react-query.tanstack.com/)。
- 遇到的问题: 组件名一定得首字母大写
[掘金-React Query 入门教程！](https://juejin.cn/post/7195540736908394556)
## 安装
```
npm i react-query
```
## 使用
- app.js 中
定义 client  和 QueryClientProvider 组件
```jsx
import { QueryClient, QueryClientProvider } from 'react-query';
function App() {
  const client = new QueryClient({
    defaultOptions: {
      queries: {
        refetchOnWindowFocus: false, //不要在窗口聚焦时重新获取数据
      },
    },
  });
  return (
    <div className="App">
      <QueryClientProvider client={client}>
       <Router>
        <Navbar />
        <Routes>
            <Route
            path="/reactQuery"
            element={<ReactQuery />}
              />
        </Routes>
       </Router>
      </QueryClientProvider>
    </div>
  )
  }
```
- Home.js
```jsx
import Axios from 'axios';
import { useQuery } from 'react-query';

export const Home = () => {
  const {
    data: catData,
    isLoading,//是否正在加载
    isError,//是否错误
    refetch,//重新获取数据
  } = useQuery(['cat'], () => {
    return Axios.get('https://catfact.ninja/fact').then((res) => res.data); //发起请求,获取API的值
  });
  if (isError) {
    return <h1>error...</h1>;
  }
  if (isLoading) {
    return <h1>loading...</h1>;
  }
  return (
    <h1>
      This is home page,
      <p>{catData?.fact}</p> 
      <button onClick={() => refetch()}>Update data</button>
    </h1>
  );
};
```
**注意**:可选运算符的使用,{catData?.fact}避免 catData 属性为空或者本身为空的报错
# React 中的表单 form
```jsx
npm install react-hook-form yup
```
## 为什么使用 react-hook-form ?
[如何在 React 中优雅地处理表单？React Hook Form 的使用指南](https://juejin.cn/post/7208440329652650043)
在 React 中，通常使用受控组件来处理表单。受控组件表单元素的值由 React 组件来管理，当表单数据发生变化时，React 会自动更新组件状态，并重新渲染组件。这种方式可以使得表单处理更加可靠和方便，也可以使得表单数据和应用状态之间保持一致。
但在实际的开发中，表单往往是最复杂的场景，有的表单有数十个字段，如果使用受控组件去构建表单，那么我们就需要维护大量 state，且 React 又不像 Vue 可以通过双向绑定直接修改 state 的值，每一个表单字段还需要定义一下 onChange 方法。因此在维护复杂表单时，使用受控组件会有很大的额外代码量。

为了解决受控组件带来的问题，我们可以使用非受控组件来构建表单。受控组件主要有以下三个优点:
1. 可以减少组件的代码量和复杂度，因为非受控组件不需要在组件状态中保存表单数据。
2. 可以更好地处理大量表单数据，因为非受控组件可以让您直接操作 DOM 元素，而不需要将所有表单数据存储在组件状态中。
3. 可以更容易地与第三方 JavaScript 库和表单处理代码集成，因为非受控组件使您能够使用 DOM API 或 ref 直接访问表单元素，而不是在 React 中重新实现所有的表单处理逻辑。
## useform
`useForm` 是 React Hook Form 库中的一个自定义 Hook，它用于处理表单的状态。React Hook Form 是一个用于处理表单输入和验证的库，它使用 React Hooks API。

当你在组件中调用 `useForm` 时，它会返回一个对象，这个对象包含了一些用于处理表单的方法和属性。

以下是 `useForm` 的基本使用方法：

```jsx
import { useForm } from 'react-hook-form';

function Form() {
  const { register, handleSubmit, errors } = useForm();

  const onSubmit = data => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input name="example" defaultValue="test" {...register('example', { required: true })} />
      <input type="submit" />
    </form>
  );
}
```

在这个例子中，`useForm` 返回了三个方法：

- `register`: 你可以使用这个函数来注册输入元素，这样 React Hook Form 就可以跟踪它们的值和验证状态。
- `handleSubmit`: 这个函数用于处理表单的提交事件。它会自动调用 `event.preventDefault()` 来阻止表单的默认提交行为，然后调用你提供的回调函数，并将表单的数据作为参数传递给这个回调函数。
- `errors`: 这个对象包含了表单中所有输入元素的验证错误。你可以使用它来显示错误消息。

请注意，`useForm` 还有很多其他的方法和属性，你可以根据需要使用它们。
##   Validation with Yup
```tsx
  // 使用 yup 库定义表单验证规则
  const schema = yup.object().shape({
    username: yup.string().required('用户名不能为空'), // 用户名必须是字符串且不能为空
    email: yup.string().email().required(), // 邮箱必须是有效的邮箱格式且不能为空
    age: yup.number().positive().integer().required(), // 年龄必须是正整数且不能为空
    password: yup.string().min(4).max(15).required(), // 密码必须是字符串，长度在4到15之间且不能为空
    password_confirm: yup
      .string()
      .oneOf([yup.ref('password'), null], '两次密码不一致') // 确认密码必须与密码相同且不能为空
      .required(),
  });
```
##  Resolvers
`resolver: yupResolver(schema)` 是在使用 `react-hook-form` 库时，用于集成 Yup 验证库的代码。

在这里，`yupResolver` 是一个函数，它接收一个 Yup 验证模式（`schema`）作为参数，并返回一个解析器（resolver）。这个解析器可以将 Yup 的验证功能集成到 `react-hook-form` 中。

`react-hook-form` 的 `useForm` Hook 接收一个配置对象，其中的 `resolver` 属性用于指定一个解析器。当表单提交时，`react-hook-form` 会使用这个解析器来验证表单数据。

所以，`resolver: yupResolver(schema)` 的作用就是让 `react-hook-form` 使用 Yup 来验证表单数据。

这是一个使用 Yup 和 `react-hook-form` 的例子：

```typescript
import { useForm } from 'react-hook-form';
import { yupResolver } from '@hookform/resolvers/yup';
import * as yup from 'yup';

const schema = yup.object().shape({
  name: yup.string().required(),
  age: yup.number().positive().integer().required(),
});

function Form() {
  const { register, handleSubmit, errors } = useForm({
    resolver: yupResolver(schema)
  });

  // ...
}
```

在这个例子中，`schema` 是一个 Yup 验证模式，它要求 `name` 是一个必填的字符串，`age` 是一个必填的正整数。`useForm` 使用 `yupResolver(schema)` 来验证这些规则。
##  Error Messages
- schema 设置错误信息提示
- 调用 useform 中的 `formState: {errors}` 
- html 显示:`<p>{errors.username?.message}</p>`
## useform+yup 库验证
这段代码是一个使用 `react-hook-form` 和 `yup` 库创建的表单组件。下面是对代码的注释解释：

```javascript
// 定义一个名为 Formpage 的 React 组件
export const Formpage = () => {
  // 定义表单提交时的处理函数，这里只是简单地将表单数据打印到控制台
  const onSubmit = (data) => console.log(data);

  // 使用 yup 库定义表单验证规则
  const schema = yup.object().shape({
    username: yup.string().required('用户名不能为空'), // 用户名必须是字符串且不能为空
    email: yup.string().email().required(), // 邮箱必须是有效的邮箱格式且不能为空
    age: yup.number().positive().integer().required(), // 年龄必须是正整数且不能为空
    password: yup.string().min(4).max(15).required(), // 密码必须是字符串，长度在4到15之间且不能为空
    password_confirm: yup
      .string()
      .oneOf([yup.ref('password'), null], '两次密码不一致') // 确认密码必须与密码相同且不能为空
      .required(),
  });

  // 使用 react-hook-form 的 useForm 钩子初始化表单
  const {
    register, // 用于注册输入字段
    handleSubmit, // 用于处理表单提交
    watch, // 用于观察输入字段的变化
    formState: { errors }, // 包含表单验证错误的对象
  } = useForm({
    resolver: yupResolver(schema), // 使用 yupResolver 将 yup 验证规则与 react-hook-form 集成
  });

  // 返回表单的 JSX
  return (
    <div className="form">
      <form onSubmit={handleSubmit(onSubmit)}>
        {/* 下面是各个输入字段，使用 register 函数注册，并在需要的地方显示验证错误 */}
        <input
          type="text"
          id="username"
          placeholder="Enter username"
          {...register('username', { required: true })}
        />
        <p>{errors.username?.message}</p>
        {/* 省略其他输入字段... */}
        <button type="submit">Submit</button>
      </form>
    </div>
  );
};
```

这个组件会渲染一个包含用户名、邮箱、年龄、密码和确认密码输入字段的表单。表单提交时，会进行 yup 定义的验证，如果验证通过，会调用 `onSubmit` 函数处理表单数据。
# 自定义 Hooks
## useToggle
在 React 中，你可以创建一个名为 `useToggle` 的自定义 Hook，用于切换一个布尔值。这个 Hook 可以用于控制按钮的显示和隐藏。以下是如何实现这个自定义 Hook：

```javascript
import { useState } from 'react';

// 自定义 Hook，用于切换布尔值
function useToggle(initialValue = false) {
  // 使用 useState Hook 存储布尔值
  const [value, setValue] = useState(initialValue);

  // 定义切换函数
  const toggleValue = () => setValue(!value);

  // 返回当前值和切换函数
  return [value, toggleValue];
}
```

然后你可以在组件中使用这个自定义 Hook 来控制按钮的显示和隐藏：

```javascript
import useToggle from './useToggle'; // 假设 useToggle 在这个路径下

function App() {
  const [isButtonVisible, toggleButtonVisibility] = useToggle(true);

  return (
    <div className="App">
      {isButtonVisible && <button>Click me</button>}
      <button onClick={toggleButtonVisibility}>
        {isButtonVisible ? 'Hide' : 'Show'} button
      </button>
    </div>
  );
}

export default App;
```

在这个例子中，`useToggle` Hook 用于控制 `isButtonVisible` 状态。点击 "Hide button" 按钮会隐藏 "Click me" 按钮，点击 "Show button" 按钮会显示 "Click me" 按钮。
## Hooks to abstract logic
## 计数器 hook
useCount.js
```jsx
import { useState } from 'react';

// 自定义 Hook，用于实现计数器功能
export const useCount = (initialValue = 0) => {
  // 使用 useState Hook 存储计数值
  const [count, setCount] = useState(initialValue);

  // 定义增加、减少和重置计数值的函数
  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);
  const reset = () => setCount(initialValue);

  // 返回当前计数值和操作函数
  return { count, increment, decrement, reset };
};
export default useCount;
```
App.js
```jsx
import './App.css';
import useCount from './hooks/useCount'; // 假设 useCount 在这个路径下

function App() {
  const { count, increment, decrement, reset } = useCount(0);

  return (
    <div className="App">
      <h1>Count: {count}</h1>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
      <button onClick={reset}>Reset</button>
    </div>
  );
}

export default App;

```
# TypeScript, 类型安全
00:00 | Intro
01:10 |  What is Type Safety?
04:23 |  Prop Types in React
04:29 |  Installing Prop Types Package
08 :26 |  TypeScript in React
## 08 :53 |  Creating a TypeScript React App
```shell
npx create-react-app . --template typescript
```
09:53 |  TypeScript File Structure
12:21 |  Using TypeScript instead of Prop Types
19:11 |  Defining States with Types in TypeScript
21:59 |  enums in TypeScript
# Redux Toolkit
## 00 :00 | Intro
### 官网链接
[Redux 中文官网](https://cn.redux.js.org/introduction/getting-started/)
### 什么是 redux
Redux 是 JavaScript 应用的状态容器，提供可预测的状态管理。

可以帮助你开发出行为稳定可预测的、运行于不同的环境（客户端、服务器、原生应用）、易于测试的应用程序。不仅于此，它还提供超爽的开发体验，比如有一个与时间旅行调试器相结合的实时代码编辑。

可以将 Redux 与 React 或其他视图库一起使用。它体小精悍（只有2kB，包括依赖），却有很强大的插件扩展生态。
### 什么是 redux Toolkit
Redux Toolkit 是我们官方推荐的编写 Redux 逻辑的方法。它围绕 Redux 核心，并包含我们认为对于构建 Redux 应用必不可少的软件包和功能。Redux Toolkit 建立在我们建议的最佳实践中，简化了大多数 Redux 任务，防止了常见错误，并使编写 Redux 应用程序更加容易。
## Project Introduction
##  Package Installation
### 一键安装
```js
# Redux + 普通 JS 模版
npx create-react-app my-app --template redux

# Redux + TypeScript 模版
npx create-react-app my-app --template redux-typescript
```
### 只安装 react-redux
```jsx
npm install @reduxjs/toolkit react-redux
```
## What is a Store?
在 React 中，"Store"是与状态管理库（如 Redux 或 MobX）相关的概念，而不是 React 本身的术语。Store 是一个对象，用于存储应用程序的状态，并根据分发给它的操作来管理和更新状态。

在 Redux 中，通常只有一个 Store 来保存整个应用程序的状态，这个状态只能通过向 Store 分发操作来更新，然后使用 reducers 生成新的状态。

在 MobX 中，Store 通常是一个可观察的对象或一组可观察的对象，可以直接通过操作来更新。

需要注意的是，虽然 Redux 和 MobX 是 React 应用程序中常用的状态管理选择，但它们并不是 React 本身的一部分，React 具有自己的内置状态管理系统，如 useState 和 useReducer 钩子，以及 Context API 用于更复杂的状态管理。
## Store Configuration
1. 创建 `src/store.js` 或者自带 `app/store.js`
```js
import { configureStore } from '@reduxjs/toolkit';

export const store = configureStore({
  reducer: {},
});
```
### reducer
在编程中，Reducer 是一种特殊类型的函数，它接收两个参数：当前的状态和一个动作，然后基于这两个参数返回一个新的状态。
Reducer 函数是纯函数，也就是说，对于相同的输入，它总是返回相同的输出，而且它不会改变原始状态或动作。
在 Redux 中，Reducer 是用来更新存储在 Store 中的状态的关键机制。当一个动作被分发到 Store 时，这个动作会被传递给 Reducer 函数，Reducer 函数会根据动作的类型来决定如何更新状态，然后返回一个新的状态。

##  Provider in Redux
`Provider` 是 `react-redux` 库中的一个组件，它的作用是使 Redux store 能够在 React 组件树中的所有地方都可用。

当你在应用的最顶层包裹 `Provider` 组件，并将 Redux store 作为 `Provider` 的 `store` 属性传递时，`Provider` 会将 Redux store 放入 context 中，这样 React 组件就可以通过 context 访问到 store。

然后你就可以在任何子组件中使用 `react-redux` 的 `useSelector` 钩子来读取 Redux store 中的状态，或者使用 `useDispatch` 钩子来分发 action。

这样做的好处是，你不需要显式地将 store 作为 prop 传递给每一个需要访问 store 的组件，而是可以在任何地方直接访问到。

以下是一个基本的使用示例：
```jsx
import React from 'react';
import { Provider } from 'react-redux';
import { createStore } from 'redux';
import rootReducer from './reducers';
import MyComponent from './MyComponent';

const store = createStore(rootReducer);

function App() {
  return (
    <Provider store={store}>
      <MyComponent />
    </Provider>
  );
}

export default App;
```
在这个示例中，`MyComponent` 组件和它的所有子组件都可以访问到 Redux store。
### 没有 provider 报错
- 报错
	could not find react-redux context value; please ensure the component is wrapped in a at useReduxContext2 ( http://localhost:3000/static/js/bundle.js:65666:13 ) at useStore2
##  Creating Reducers for the Store
##   What is a Slice? && Creating the Slice
在 Redux Toolkit 中，"slice" 是指应用状态的一部分，它通常对应于特定的功能或领域。每个 slice 都有一个对应的 reducer 和一组 action creators。

Redux Toolkit 提供了一个名为 `createSlice` 的函数，它接收一个初始状态、一个对象，该对象的每个键都是一个 reducer 函数，以及一个 slice 名称。`createSlice` 会自动生成 action creators 和 action types，这些都是基于你提供的 reducer 函数和 slice 名称。

以下是一个使用 `createSlice` 的例子：

```javascript
import { createSlice } from '@reduxjs/toolkit'

const counterSlice = createSlice({
  name: 'counter',
  initialState: 0,
  reducers: {
    increment: state => state + 1,
    decrement: state => state - 1
  }
})

export const { increment, decrement } = counterSlice.actions

export default counterSlice.reducer
```

在这个例子中，我们创建了一个名为 "counter" 的 slice，它有一个初始状态 `0`，以及两个 reducer 函数 `increment` 和 `decrement`。`createSlice` 返回一个对象，该对象包含生成的 action creators 和 reducer。
## login logout slice
这段代码是使用 Redux Toolkit 创建一个 Redux store 和一个名为 "user" 的 slice 的示例。下面是带有注释的代码：
```javascript
// 从 Redux Toolkit 导入 configureStore 和 createSlice 函数
import { configureStore, createSlice } from '@reduxjs/toolkit';

// 使用 createSlice 创建一个名为 "user" 的 slice
const userSlice = createSlice({
  name: 'user', // slice 的名称
  initialState: { // slice 的初始状态
    value: { username: '' },
  },
  reducers: { // 定义了两个 reducer 函数
    // login reducer 接收当前的 state 和一个 action，然后将 state.value 设置为 action.payload
    login(state, action) {
      state.value = action.payload;
    },
    // logout reducer 接收当前的 state，然后将 state.value 设置为一个空的 username 对象
    logout(state) {
      state.value = { username: '' };
    },
  },
});

//导出 userSlice 的 action creators,这样我们就可以在其他地方使用这些函数来分发 actions
export const { login, logout } = userSlice.actions;

// 使用 configureStore 创建一个 Redux store，并将 userSlice.reducer 作为 reducer 传入
// 这样，我们就可以在 store 中使用 userSlice 来管理 user 相关的状态
export const store = configureStore({
  reducer: {
    user: userSlice.reducer,
  },
});
```

这段代码的**主要作用**是创建一个 Redux store，并定义了一个名为 "user" 的 slice，用于管理用户相关的状态。通过调用 `login` 和 `logout` 函数，我们可以分别更新用户的登录状态和注销状态。
### redux store 结构
上面代码定义了一个 Redux store，其结构如下：

```javascript
{
  user: {
    value: {
      username: ''
    }
  }
}
```

这个结构是由 `createSlice` 和 `configureStore` 函数确定的：

- `createSlice` 函数创建了一个名为 `user` 的 slice。这个 slice 的初始状态是 `{ value: { username: '' } }`，并且它有两个 reducer：`login` 和 `logout`。

- `configureStore` 函数创建了 Redux store，并设置了其 reducer。在这个例子中，store 只有一个 reducer，即 `user` slice 的 reducer。这意味着 `user` slice 的状态将被保存在 `state.user` 中。

因此，整个 Redux store 的结构是 `{ user: { value: { username: '' } } }`。你可以通过 `state.user.value.username` 来访问 `username`。
### active.payload
在 Redux 中，一个 action 是一个包含 `type` 属性的普通 JavaScript 对象，用于描述发生了什么。除 `type` 属性外，action 对象可以包含其他属性来携带额外的信息，这些额外的信息通常放在 `payload` 属性中。

在你的代码中，`action.payload` 是一个 action 对象的 `payload` 属性。当你调用 `login` action creator 并传入一个参数时，这个参数就会成为生成的 action 的 `payload`。例如，如果你这样调用 `login`：

```javascript
login({ username: 'John Doe' });
```

那么，生成的 action 就会是：

```javascript
{
  type: 'user/login',
  payload: { username: 'John Doe' }
}
```

在 `login` reducer 中，`state.value` 被设置为 `action.payload`，也就是说，`state.value` 将被设置为你传给 `login` 的参数。
##   Configuring the Login Page
这是你的代码，我已经添加了注释来解释每一部分的功能：

```javascript
import React, { useState } from 'react';
import { login, logout } from '../store'; // 导入 action creators
import { useDispatch, useSelector } from 'react-redux'; // 导入 Redux hooks

export const Login = () => {
  const [newUsername, setnewUsername] = useState(''); // 创建一个状态来保存用户输入的新用户名
  const dispatch = useDispatch(); // 获取 dispatch 函数

  const handleLogin = () => {
    dispatch(login({ username: newUsername })); // 当用户点击 "Submit Login" 按钮时，分发 login action
  };

  const username = useSelector((state) => state.user.value.username); // 从 Redux store 中获取当前的用户名

  return (
    <div className="app-container">
      <h1>{username}</h1> {/* 显示当前的用户名 */}
      <input
        type="text"
        onChange={(e) => {
          setnewUsername(e.target.value); // 当用户在输入框中输入时，更新 newUsername 状态
        }}
      />

      <button
        type="submit"
        onClick={handleLogin} // 当用户点击 "Submit Login" 按钮时，调用 handleLogin 函数
      >
        Submit Login
      </button>
      <button type="submit">Logout</button> {/* 这个按钮目前没有功能 */}
    </div>
  );
};
```

这个组件的工作流程如下：

1. 当组件首次渲染时，它会从 Redux store 中获取当前的用户名，并将其显示在 `<h1>` 元素中。

2. 用户可以在 `<input>` 元素中输入新的用户名。当 `<input>` 元素的值改变时，`setnewUsername` 函数会被调用，将新的用户名保存到 `newUsername` 状态中。

3. 用户可以点击 "Submit Login" 按钮来提交新的用户名。当按钮被点击时，`handleLogin` 函数会被调用。这个函数会分发 `login` action，并将新的用户名作为 action 的 payload。

4. 当 `login` action 被分发时，对应的 reducer 会被调用，这个 reducer 会根据 action 的 payload 来更新 Redux store 中的用户名。

5. 当 Redux store 更新时，`useSelector` Hook 会重新运行，从更新后的 store 中获取新的用户名。然后，React 会重新渲染组件，显示新的用户名。
### 在其他页面使用参数username
如果你需要在其他组件中使用 `username`，你可以使用 `useSelector` Hook 来从 Redux store 中获取它。这是因为 Redux store 是全局的，所以你可以在任何组件中访问它。

例如，如果你有一个 `Profile` 组件，你可以像这样获取 `username`：

```javascript
import React from 'react';
import { useSelector } from 'react-redux';

export const Profile = () => {
  const username = useSelector((state) => state.user.value.username); // 从store中获取username

  return (
    <div>
      <h1>Profile Page</h1>
      <p>Username: {username}</p>
    </div>
  );
};
```

在这个例子中，我们使用 `useSelector` Hook 来从 Redux store 中获取 `username`，然后在 `<p>` 元素中显示它。

请注意，这个代码假设你的 Redux store 的结构是 `{ user: { value: { username: '...' } } }`。如果你的 store 的结构不同，你需要相应地修改 `useSelector` 的参数。
##  Typescript In Redux
# Firebase 项目 (第 1 部分)
## Intro
## Project Initialization
1. 创建 react 项目
```shell
npx create-react-app . --template typescript
```
**注意**:文件名不可以有大写
2. 删除部分文件,保留
![image.png|500](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2024%2F01%2F11%2F20240111142132_14-21-32.png)

## Installing packages
```shell index.tsx
npm install react-router-dom
```
## Creating Routes for the App
1.app.js 中导入
```tsx
import { BrowserRouter as Router,Route,Routes } from 'react-router-dom';

```
2.创建 pages 文件夹
```shell
cd src
mkdir pages
```
3.创建 pages/Home.tsx
```tsx
export const Home = () => {
  return <div>Home Page</div>
}
```
4.app.tsx 中导入并链接
```tsx
import React from 'react';
import { BrowserRouter as Router,Route,Routes } from 'react-router-dom';//here
import './App.css';
import { Home } from './pages/Home';
function App() {
  return (
    <div className="App">
      <Router>
        <Routes>
          <Route path="/" element={<Home/>}></Route>{/* here */}
        </Routes>
      </Router>

    </div>
  );
}
export default App;
```
## Navbar Component
- 步骤
1.创建 src/components 文件夹
2.创建 navbar.tsx 文件并编辑
```tsx
import { Link } from 'react-router-dom';

export const Navbar = () => {
  return (
    <div>
      <Link to="/">Home</Link>
      <Link to="/login">Login</Link>
    </div>
  );
};
```
3.在 app.tsx 中插入
```tsx
import { Navbar } from './components/navbar';

function App() {
  return (
    <div className="App">
      <Router>
      <Navbar/>
        <Routes>
          <Route path="/" element={<Home />}></Route>
          <Route path="/login" element={<Login />}></Route>
        </Routes>
      </Router>
      
    </div>
  );
}
```
### 注意: navbar 的位置问题
在 React Router v6 中，所有的路由相关的组件（如 `<Route>`）必须是 `<Routes>` 组件的直接子组件。这意味着你不能在 `<Routes>` 和 `<Route>` 之间插入其他的组件，如 `<Navbar>`。

在你的代码中，`<Navbar/>` 是 `<Router>` 的直接子组件，而不是 `<Routes>` 的子组件，所以它可以正常工作。如果你尝试将 `<Navbar/>` 放在其他位置，例如 `<Routes>` 和 `<Route>` 之间，你将会收到一个错误，因为这违反了 React Router 的规则。

如果你希望 `<Navbar/>` 出现在所有页面上，你应该将它放在 `<Router>` 内部，但是在 `<Routes>` 外部，就像你现在的代码一样。这样，无论当前的路由是什么，`<Navbar/>` 都会被渲染。

简单来说,navbar 是 Router 的直接子组件,而不是 Routes 的直接子组件

## Setting up Firebase
- 步骤
1. [Firebase官网](https://firebase.google.com/)注册并按步创建项目
2. 选择网页项目
3. 添加 SDK 设置和配置
	首先,安装 firebase
	```shell
	npm install firebase
	```
	其次,创建 src/config 文件夹
	然后.创建 config/firebase.ts
	最后,在 firebase.ts 中导入以下内容

	```tsx
	// Import the functions you need from the SDKs you need
	import { initializeApp } from "firebase/app";
	// TODO: Add SDKs for Firebase products that you want to use
	// https://firebase.google.com/docs/web/setup#available-libraries
	
	// Your web app's Firebase configuration
	const firebaseConfig = {
	apiKey: "AIzaSyBlVKXm1LjmmAUo39h0sumWZ-68jNZDahw",
	authDomain: "react-course-perdro.firebaseapp.com",
	projectId: "react-course-perdro",
	storageBucket: "react-course-perdro.appspot.com",
	messagingSenderId: "333562392481",
	appId: "1:333562392481:web:e0286453d6b991698065e0"
	};
	
	// Initialize Firebase
	const app = initializeApp(firebaseConfig);
	```

## Authentication using Firebase
- 步骤
1. 进入主页,身份验证和管理功能
2. 选择谷歌登录
3. 右上角启用,设置邮箱,保存
4. firebase.ts 中添加 hooks,获取 auth 和 provider 参数
5. 在 login.tsx 中导入参数和 signInWithPopup(使用弹出窗口登录)
6. 创建 signInWithGoogle 变量 && button onclick [弹出窗口登录-signInWithPopup](#弹出窗口登录-signInWithPopup)
7. 
8. 登录后链接到主页 [路由重定向-useNavigate](#路由重定向-useNavigate)
9. 导航栏的所有页面都显示用户名
###  getAuth,GoogleAuthProvider
- 概念
`getAuth` 是 Firebase 提供的一个函数，用于获取 Firebase Authentication 服务的实例。这个实例可以用于调用各种身份验证方法，例如 `signInWithPopup`。

`GoogleAuthProvider` 是 Firebase 提供的一个类，用于创建 Google 登录的提供者对象。这个对象可以用于 `signInWithPopup` 或 `signInWithRedirect` 方法，以启动 Google 登录流程。

在 `signInWithPopup(auth,googleAuthProvider)` 这行代码中，`auth` 和 `googleAuthProvider` 被用于启动一个 Google 登录的弹出窗口。用户可以在这个窗口中通过 Google 账号进行登录，登录结果会被 `await` 捕获并存储在 `result` 中。

-  `../config/firebase` 文件

```typescript
import { initializeApp } from "firebase/app";
import { getAuth, GoogleAuthProvider } from "firebase/auth";

// TODO: Replace the following with your app's Firebase project configuration
const firebaseConfig = {
  //...
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);

export const auth = getAuth(app);
export const googleAuthProvider = new GoogleAuthProvider();
```

在这个文件中，我们首先初始化 Firebase 应用，然后使用 `getAuth` 函数获取 `auth` 对象，并创建 `googleAuthProvider` 对象。这两个对象都被导出，所以它们可以在其他文件中使用。

### 弹出窗口登录-signInWithPopup
- 异步实行 async+await
```tsx
import {auth, googleAuthProvider} from '../config/firebase';
import { signInWithPopup } from 'firebase/auth';
import { useNavigate } from 'react-router-dom';
export const Login = () => {
  const navigate = useNavigate();
  const signInWithGoogle = async () => {
    
    const result = await signInWithPopup(auth, googleAuthProvider);
    console.log(result);
    navigate('/');
  };
  return <div>
    <p>Sign In With Google To Continue</p>
    <button onClick={signInWithGoogle}>Sign In With Google</button>
    </div>;
}
```
这里的异步操作是通过 `async/await` 关键字实现的。

`async` 关键字用于声明一个函数是异步的，这意味着函数的执行不会阻塞后续代码的执行。异步函数总是返回一个 Promise，这个 Promise 在异步操作完成时解析。

`await` 关键字用于等待一个 Promise 解析或拒绝。它只能在 `async` 函数内部使用。`await` 会暂停代码的执行，直到 Promise 解析，然后返回解析的值。
- 代码实现流程

	在你的代码中，`signInWithGoogle` 函数是异步的，因为它使用了 `async` 关键字。在这个函数内部，`signInWithPopup` 函数被调用，它返回一个 Promise。这个 Promise 在用户成功登录或登录失败时解析。
	
	`await` 关键字用于等待 `signInWithPopup` 的 Promise 解析。这意味着，直到用户完成登录（或登录失败），`console.log(result)` 之后的代码才会执行。
	
	这样做的好处是，你可以以同步的方式编写异步代码，使得代码更易读和理解。同时，由于 `await` 会暂停代码的执行，你可以在 Promise 解析后立即处理结果，而不需要使用 `.then()` 或 `.catch()` 方法。
- 异步实现: .then+.catch
```tsx
import {auth, googleAuthProvider} from '../config/firebase';
import { signInWithPopup } from 'firebase/auth';

export const Login = () => {
  const signInWithGoogle = () => {
    signInWithPopup(auth, googleAuthProvider)
      .then(result => {
        console.log(result);
      })
      .catch(error => {
        console.error(error);
      });
  };
};
```
- signInWithGoogle

signInWithGoogle 函数是异步的，这意味着它会立即返回一个 Promise，而不会阻塞其他代码的执行。当用户完成 Google 登录流程时，这个 Promise 将被解析，你可以在那时处理登录结果。
### Promise
- 概念
Promise 是 JavaScript 中用于处理异步操作的一种对象。异步操作是指可能不会立即完成的操作，例如网络请求或定时器。
Promise 是一个包含了异步操作结果的对象。你可以在 Promise 上注册回调函数来处理这个结果，无论它是成功还是失败。
- Promise的三种状态
1. Pending（待定）：初始状态，既不是成功，也不是失败状态。
2. Fulfilled（已实现）：表示操作成功完成。
3. Rejected（已拒绝）：表示操作失败。


- 类比的例子
你可以把 Promise 想象成一个餐厅的服务员。当你（代码）向服务员（Promise）下单（开始一个异步操作）时，服务员会去厨房（后台）准备你的食物（异步操作的结果）。在这个过程中，你可以继续做其他事情（执行其他代码），而不需要等待食物准备完成。当食物准备好了（异步操作完成），服务员会把食物带给你（解析 Promise）。如果厨房出了问题不能完成你的订单（异步操作失败），服务员也会通知你（拒绝 Promise）。

这就是 Promise 的基本概念。它允许你在异步操作完成时或失败时执行特定的代码，而不需要立即等待这个操作的完成。
### 路由重定向-useNavigate
useNavigate 返回一个函数，你可以调用这个函数来导航到不同的路由。你可以传递一个路径字符串给这个函数，也可以传递一个描述目标位置的对象。
- 登录完成之后返回主页
```tsx
import { useNavigate } from 'react-router-dom';
export const Login = () => {
  const navigate = useNavigate();
  const signInWithGoogle = async () => {
    
    const result = await signInWithPopup(auth, googleAuthProvider);
    console.log(result);
    navigate('/');
  };
```
### 导航栏显示用户名
在 Firebase 中，你可以通过 `auth.currentUser` 获取当前登录的用户。这是一个 User 对象，包含了用户的各种信息，包括用户名。
```tsx
import { Link } from 'react-router-dom';
import { auth } from "../config/firebase";

export const Navbar = () => {
  return (
    <div>
      <Link to="/">Home</Link>
      <Link to="/login">Login</Link>
      <p>{auth.currentUser?.displayName}</p>
    </div>
  );
};
```
#### 问题:用户名显示不了
在你的代码中,Navbar 组件在渲染时会立即尝试访问 auth.currentUser.displayName。然而，如果在这个时候用户还没有登录，那么 auth.currentUser 将是 null，并且 displayName 也将是 undefined。

即使用户在之后登录了，Navbar 组件也不会知道这个变化，除非它被重新渲染。这是因为 auth.currentUser 不是 Navbar 组件的状态或属性，React 不会知道它何时发生变化。
## 登录后显示用户信息(react-firebase-hooks)
- 流程
	- npm install react-firebase-hooks
	- 使用 useAuthState 
- 完整代码
```tsx
import { Link } from "react-router-dom";
import { auth } from "../config/firebase";
import { useAuthState } from "react-firebase-hooks/auth";

export const Navbar = () => {
  const [user] = useAuthState(auth);

  const signUserOut = async () => {
    await signOut(auth);
  };
  return (
    <div className="navbar">
      <div className="links">
        <Link to="/"> Home </Link>
        <Link to="/login"> Login </Link>
      </div>
      <div className="user">
        {user && (
          <>
            <p> {user?.displayName} </p>
            <img src={user?.photoURL || ""} width="20" height="20" />
            <button onClick={signUserOut}> Log Out</button>
          </>
        )}
      </div>
    </div>
  );
};
```
## 注销账号 Sign Out 
- 完整代码
```tsx
import { Link } from "react-router-dom";
import { auth } from "../config/firebase";
import { useAuthState } from "react-firebase-hooks/auth";
import { signOut } from "firebase/auth";

export const Navbar = () => {
  const [user] = useAuthState(auth);

  const signUserOut = async () => {
    await signOut(auth);
  };
  return (
    <div className="navbar">
      <div className="links">
        <Link to="/"> Home </Link>
        <Link to="/login"> Login </Link>
      </div>
      <div className="user">
        {user && (
          <>
            <p> {user?.displayName} </p>
            <img src={user?.photoURL || ""} width="20" height="20" />
            <button onClick={signUserOut}> Log Out</button>
          </>
        )}
      </div>
    </div>
  );
};
```
# Firebase 项目 (第 2 部分)
## Firestore Database Configuration
- 选择 firestore database
![image.png|350](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2024%2F01%2F13%2F20240113141736_14-17-38.png)
- 设置名称和位置
- 以生产模式开始

## Creating a collection
- Start collection
- 设置集合 ID:post,随机文档 ID
- 添加字段
	![image.png|500](https://cdn.jsdelivr.net/gh/fencesitter1/pictures/img/2024%2F01%2F13%2F20240113142658_14-26-59.png)

## CreatePost Component
- 创建 createpost 子路由
- 创建 crateform.tsx
## Package Installation
- 安装 react-hook-form
```shell
npm install react-hook-form yup @hookform/resolvers
```
- import 
```tsx

```
## Yup Validation && form 
可以参考 [React 中的表单 form](#React%20中的表单%20form)
- 使用 yup 定义匹配规则
- 使用 useForm 
### post form 代码
```tsx
import { useForm } from 'react-hook-form'
import * as yup from 'yup'
import { yupResolver } from '@hookform/resolvers/yup'
interface CreateFormdata{
  title: string;
  description: string;
}
export const CreateForm = () => {
  const schema = yup.object().shape({ 
    title: yup.string().required("Title is required"),//匹配规则+错误提示
    description: yup.string().required("Description is required")
  });
  const { register,
    handleSubmit,
    formState: { errors } } = useForm({
    resolver: yupResolver(schema)
  });
  const onCreatePost = (data:CreateFormdata) => {
    console.log(data);
  };
  return (
    <div>
      <form onSubmit={handleSubmit(onCreatePost)}>
        <input type="text" placeholder="Title.." {...register('title', { required: true })} />
        <p>{errors.title?.message}</p> //提示错误信息
        <input type="text" placeholder="Description.." {...register('description', { required: true })} />
        <p>{errors.description?.message}</p>
        <input type='submit' />
      </form>
      </div>
    )
}
```
## Sending data to the database
- firebase.ts 中导入 getFirestore
- 定义 db 变量
```tsx
import { initializeApp } from 'firebase/app';
import { getAuth, GoogleAuthProvider } from 'firebase/auth';
import { getFirestore } from 'firebase/firestore';

// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: 'AIzaSyBlVKXm1LjmmAUo39h0sumWZ-68jNZDahw',
  authDomain: 'react-course-perdro.firebaseapp.com',
  projectId: 'react-course-perdro',
  storageBucket: 'react-course-perdro.appspot.com',
  messagingSenderId: '333562392481',
  appId: '1:333562392481:web:e0286453d6b991698065e0',
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
export const googleAuthProvider = new GoogleAuthProvider();
export const db = getFirestore(app);
```
### addDoc ,collection
- create-form.tsx  中导入 {addDoc,collection} 
- create-form.tsx  中导入 { db }
- 定义 postref 集合
- 异步实现 addDoc
```tsx
import {addDoc,collection} from "firebase/firestore"
import { db } from '../../config/firebase';

  const postsRef = collection(db, "posts");

  const onCreatePost = async (data:CreateFormdata) => {
    await addDoc(postsRef, {
      title: data.title,
      description: data.description,
      //...data
      username: user?.displayName,
      id : user?.uid,
    });
  };
```
`addDoc` 和 `collection` 是 Firebase 库中的两个函数，它们用于操作 Firebase 中的 Cloud Firestore 数据库。

1. `collection`: 这个函数用于获取一个 Firestore 集合的引用。在你的代码中，`collection(db, "posts")` 创建了一个指向 "posts" 集合的引用。`db` 是你的 Firestore 数据库实例。

2. `addDoc`: 这个函数用于向一个 Firestore 集合中添加一个新的文档。在你的代码中，`addDoc(postsRef, { title: data.title, description: data.description })` 创建了一个新的文档，并将其添加到了 "posts" 集合中。这个新文档的数据是 `{ title: data.title, description: data.description }`。

所以，`onCreatePost` 函数的作用是，当被调用时，它会创建一个新的 "post" 文档，并将其添加到 Firestore 数据库的 "posts" 集合中。这个新文档的 "title" 和 "description" 字段的值来自 `data` 参数。
### 导入登录 user 变量
```tsx
import { auth, db } from '../../config/firebase';
import { useAuthState } from 'react-firebase-hooks/auth';

const [user] = useAuthState(auth);
```
### 数据库 crud 规则

```js
rules_version = '2'; // 使用版本 2 的 Firebase 安全规则语法

service cloud.firestore { // 这个规则适用于 Firestore 服务
  match /databases/{database}/documents { // 匹配所有数据库和文档
    match /{document=**} { // ** 表示匹配任意数量的路径段，所以这里匹配所有文档
      // 对于写入、删除和更新操作，只有当请求的用户已经认证，并且请求的用户的 ID 等于文档的 userId 字段时，才允许操作
      allow write,delete,update: if request.auth != null && request.auth.uid ==request.resource.data.userId;
      // 对于读取操作，只有当请求的用户已经认证时，才允许操作
      allow read: if request.auth != null
    }
  }
}
```

这些规则的目的是保护你的 Firestore 数据库。只有当用户已经认证，并且他们的 ID 等于他们想要操作的文档的 `userId` 字段时，才允许他们写入、删除或更新那个文档。对于读取操作，只有当用户已经认证时，才允许操作。
## 提交表单数据后重定向
- 定义 `navigate = useNavigate();`
- 在 onCreatePost 中加入navigate
```tsx
import { useForm } from 'react-hook-form'
import * as yup from 'yup'
import { yupResolver } from '@hookform/resolvers/yup'
import {addDoc,collection} from "firebase/firestore"
import { auth } from '../../config/firebase';
import {db} from "../../config/firebase"
import { useAuthState } from 'react-firebase-hooks/auth';
import { useNavigate } from 'react-router-dom';

interface CreateFormdata{
  title: string;
  description: string;
}
export const CreateForm = () => {
  const [user] = useAuthState(auth);
  
  const navigate = useNavigate();
  const schema = yup.object().shape({
    title: yup.string().required("Title is required"),
    description: yup.string().required("Description is required")
  });
  const { register,
    handleSubmit,
    formState: { errors } } = useForm<CreateFormdata>({
    resolver: yupResolver(schema)
    });
  
  const postsRef = collection(db, "posts");

  const onCreatePost = async (data:CreateFormdata) => {
    await addDoc(postsRef, {
      title: data.title,
      description: data.description,
      //...data
      username: user?.displayName,
      userId : user?.uid,
    });
    navigate("/");
  };
  return (
    <div>
      <form onSubmit={handleSubmit(onCreatePost)}>
        <input type="text" placeholder="Title.." {...register('title', { required: true })} />
        <p>{errors.title?.message}</p>
        <input type="text" placeholder="Description.." {...register('description', { required: true })} />
        <p>{errors.description?.message}</p>
        <input type='submit' />
      </form>
      </div>
    )
}
```
# Firebase 项目 (第 3 部分)


# 部署 Firebase React 应用
