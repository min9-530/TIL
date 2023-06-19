# 라우팅이란?

라우팅이란 간단하게 사용자가 요청한 URL에 따라 해당 URL에 맞는 페이지를 보여주는 것을 의미한다.  

리액트에선 라우팅 관련 라이브러리가 많이 있는데, 이중 가장 많이 쓰이는 것은 리액트 라우터(React Router)이다.


# 리액트 라우터(React Router)
사용자가 입력한 주소를 감지하는 역할을 하며, 여러 환경에서 동작할 수 있도록 여러 종류의 라우터 컴포넌트를 제공한다.  

이중에서 가장 많이 사용되는 라우터 컴포넌트는 BrowserRouter와 HashRouter이다.

## 종류
1. BrowserRouter
  + HTML5의 history API를 활용한 라우터이다.
  + SSR(Server Side Rendering)에 적합하다.
  + 새로고침하거나 url로 직접 접근할 경우 경로를 찾지 못해 에러가 발생한다.
  + 이때문에 배포하기가 좀 더 복잡하다.
2. HashRouter
  + URL의 hash를 사용한 라우터이다.
  + CSR(Client Side Rendering)에 적합하다.
  + 라우터에 # 가 붙는다.
  + 해시를 사용하면 서버에 요청하지 않기 때문에 url로 직접 접근해도 에러가 발생하지 않는다.
  + 따라서 배포가 좀 더 간단하다.
  + 하지만 # 를 검색 엔진이 읽지 못하기 때문에 최적화가 좋지 않다.

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

## Home.js
```js
import { Link } from "react-router-dom";

const Home = () => {
  return (
    <div>
      <h1>홈</h1>
      <p>가장 먼저 보여지는 페이지입니다.</p>
      <Link to="/about">소개</Link>
    </div>
  );
};

export default Home;
```

# URL Parameter
+ URL 파라미터 예시: /profile/min2u  

URL 파라미터는 주소의 경로에 유동적인 값을 넣는 형태이다.  
또한, URL 파라미터는 주로 ID 또는 이름을 사용하여 특정 데이터를 조회할 때 사용한다.  
  
# useParams
useParams는 URL 파라미터를 조회할 때 사용하는 React Hook으로, 라우트 설정을 할 때 Route 컴포넌트의 path props를 통해 설정한다.
  
## Profile.js
```js
  import { useParams } from "react-router-dom";

const data = {
  minsu: {
    name: "김민수",
    description: "프론트엔드 개발자를 꿈꾸는 학생",
  },
  brother: {
    name: "김현수",
    description: "현재 군인",
  },
};

const Profile = () => {
  const params = useParams();
  const profile = data[params.username];

  return (
    <div>
      <h1>사용자 프로필</h1>
      {profile ? (
        <div>
          <h2>{profile.name}</h2>
          <p>{profile.description}</p>
        </div>
      ) : (
        <p>존재하지 않는 프로필입니다.</p>
      )}
    </div>
  );
};

export default Profile;

```
## App.js
```js
import { Route, Routes } from "react-router-dom";
import About from "./pages/About";
import Home from "./pages/home";
import Profile from "./pages/Profile";

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="/profiles/:username" element={<Profile />} />
    </Routes>
  );
}

export default App;
```


# useNavigate
Link 컴포넌트를 사용하지 않고 다른 페이지로 이동해야 하는 상황에 사용하는 Hook이다.

## Layout.js
```js
import { Outlet, useNavigate } from "react-router-dom";

const Layout = () => {
  const navigate = useNavigate();

  const goBack = () => {
    // parameter가 숫자타입이라면 그 숫자만큼 페이지가 뒤로가거나 앞으로 이동한다.
    navigate(-1);
  };

  const goArticles = () => {
    // 해당 주소로 이동할 때 현재 페이지를 기록에 남기지 않는다.
    navigate("/articles", { replace: true });
  };

  return (
    <div>
      <header style={{ background: "lightgray", padding: 16, fontSize: 24 }}>
        <button onClick={goBack}>뒤로가기</button>
        <button onClick={goArticles}>게시글 목록</button>
      </header>
      <main>
        <Outlet />
      </main>
    </div>
  );
};

export default Layout;

```


# NavLink
+ 링크에서 사용하는 경로가 현재 라우트의 걍로와 일치하는 경우  
특정 스타일 또는 CSS 클래스를 적용하는 컴포넌트이다.
+ 이 컴포넌트의 style과 className은 { isActive: boolean }을 파라미터로 전달받는 함수 타입의 값을 전달한다.
```jsx
<NavLink
  style={({isActive}) => isActive ? activeStyle : undefined}
/>

<NavLink
  className={({isActive}) => isActive ? 'active' : undefined}
/>
```

## Articles.js
```js
import { NavLink, Outlet } from "react-router-dom";

const Articles = () => {
  return (
    <div>
      <Outlet />
      <ul>
        <ArticleItem id={1} />
        <ArticleItem id={2} />
        <ArticleItem id={3} />
      </ul>
    </div>
  );
};

const ArticleItem = ({ id }) => {
  const activeStyle = {
    color: "green",
    fontSize: 21,
  };
  return (
    <li>
      <NavLink
        to={`/articles/${id}`}
        style={({ isActive }) => (isActive ? activeStyle : undefined)}
      >
        게시글 {id}
      </NavLink>
    </li>
  );
};

export default Articles;

```
