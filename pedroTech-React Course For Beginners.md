
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
# React 中的表单
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
## React Hook Form
##   Validation with Yup
##   Resolvers
##  Error Messages
## 代码
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
00:00 | Intro
01:02 |  Project Introduction
## 02 :02 |  Package Installation
```js
# Redux + 普通 JS 模版
npx create-react-app my-app --template redux

# Redux + TypeScript 模版
npx create-react-app my-app --template redux-typescript
```
02:39 |  What is a Store?
04:07 |  Store Configuration
05:30 |  Provider in Redux
07:01 |  Creating Reducers for the Store
07:27 |  What is a Slice?
08:52 |  Creating the Slice
15:29 |  Configuring the Login Page
24:22 | Typescript In Redux
# Firebase 项目 (第 1 部分)

# Firebase 项目 (第 2 部分)

# Firebase 项目 (第 3 部分)

# 部署 Firebase React 应用