# 라우팅이란?

라우팅이란 간단하게 사용자가 요청한 URL에 따라 해당 URL에 맞는 페이지를 보여주는 것을 의미한다.  

리액트에선 라우팅 관련 라이브러리가 많이 있는데, 이중 가장 많이 쓰이는 것은 리액트 라우터(React Router)이다.


# 리액트 라우터(React Router)
사용자가 입력한 주소를 감지하는 역할을 하며, 여러 환경에서 동작할 수 있도록 여러 종류의 라우터 컴포넌트를 제공한다.  

이중에서 가장 많이 사용되는 라우터 컴포넌트는 BrowserRouter와 HashRouter이다.

## 종류
1. BrowserRouter: HTML5를 지원하는 브라우저의 주소를 감지 한다.  
2. HashRouter : 해시 주소 (https://github.com/min9-530/TIL/blob/main/React/Router.md) 를 감지한다.

## 설치
npm  
```npm install react-router-dom```

yarn  
```yarn add react-router-dom```  

# 기본 라우터 사용법

## index.js
```js
import "./index.css";
import App from "./App";
import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

## Home.js
```js
const Home = () => {
  return (
    <div>
      <h1>홈</h1>
      <p>가장 먼저 보여지는 페이지입니다.</p>
    </div>
  );
};

export default Home;
```

## About.js
```js
const About = () => {
  return (
    <div>
      <h1>소개</h1>
      <p>리액트 라우터를 사용해 보는 프로젝트입니다.</p>
    </div>
  );
};

export default About;
```

## App.js
```js
import { Route, Routes } from "react-router-dom";
import About from "./pages/About";
import Home from "./pages/home";

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
    </Routes>
  );
}

export default App;
```

# Link 컴포넌트 사용법

## Link
웹 페이지에선 원래 링크를 보여줄 때 <a> 태그를 사용하지만 <a> 태그는 페이지를 이동시키면서 새로고침한다.  
이렇게 되면 원래 리액트 앱의 상태들이 초기화되고 새로 렌더링을 하게 된다.  
반면에 Link 컴포넌트는 <a> 태그를 사용하긴 하지만, 페이지가 새로고침 되는 것을 막고 History API를 통해 브라우저 주소의 경로만 바꾸는 기능이 내장되어 있다.  

## App.js
```js
import { Route, Routes } from "react-router-dom";
import About from "./pages/About";
import Home from "./pages/home";

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
    </Routes>
  );
}

export default App;
```
