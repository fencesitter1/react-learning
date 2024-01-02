
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
  // 这里的代码会在每次渲染后执行 第一阶段+第二阶段
});

useEffect(() => {
  // 这里的代码只会在组件挂载后执行 第一阶段
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

# React 中的表单

# 自定义 Hooks

# TypeScript, 类型安全

# Redux Toolkit

# Firebase 项目 (第 1 部分)

# Firebase 项目 (第 2 部分)

# Firebase 项目 (第 3 部分)

# 部署 Firebase React 应用