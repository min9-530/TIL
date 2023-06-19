# Nested Routing
중첩라우팅이란 해당하는 페이지에서 조금 더 구체적으로 구분을 지어 화면을 교체(표시) 해줄 필요가 있을 때 사용된다.

## Articles.js
```js
import { Link } from "react-router-dom";

const Articles = () => {
  return (
    <ul>
      <li>
        <Link to="/articles/1">게시글 1</Link>
      </li>
      <li>
        <Link to="/articles/2">게시글 2</Link>
      </li>
      <li>
        <Link to="/articles/3">게시글 3</Link>
      </li>
    </ul>
  );
};

export default Articles;
```

## Article.js
```js
import { useParams } from "react-router-dom";

const Article = () => {
  const { id } = useParams();
  return (
    <div>
      <h2>게시글 {id}</h2>
    </div>
  );
};

export default Article;
```

## App.js
```js
import { Route, Routes } from "react-router-dom";
import About from "./pages/About";
import Home from "./pages/Home";
import Profile from "./pages/Profile";
import Articles from "./pages/Articles";
import Article from "./pages/Article";

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="/profiles/:username" element={<Profile />} />
      <Route path="/articles" element={<Articles />} />
      <Route path="/articles/:id" element={<Article />} />
    </Routes>
  );
}

export default App;

```

## Home.js
```js
import { Link } from "react-router-dom";

const Home = () => {
  return (
    <div>
      <h1>홈</h1>
      <p>가장 먼저 보여지는 페이지입니다.</p>
      <ul>
        <li>
          <Link to="/about">소개</Link>
        </li>
        <li>
          <Link to="/articles">게시글 목록</Link>
        </li>
      </ul>
    </div>
  );
};

export default Home;
```

# Outlet
이 컴포넌트는 Route의 children으로 들어가는 JSX 엘리멘트를 보여주는 역할을 한다.

## App.js
```js
import { Route, Routes } from "react-router-dom";
import About from "./pages/About";
import Home from "./pages/Home";
import Profile from "./pages/Profile";
import Articles from "./pages/Articles";
import Article from "./pages/Article";

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="/profiles/:username" element={<Profile />} />
      <Route path="/articles" element={<Articles />}>
        <Route path=":id" element={<Article />} />
      </Route>
    </Routes>
  );
}

export default App;
```

## Articles.js
```js
import { Link, Outlet } from "react-router-dom";

const Articles = () => {
  return (
    <div>
      <Outlet />
      <ul>
        <li>
          <Link to="/articles/1">게시글 1</Link>
        </li>
        <li>
          <Link to="/articles/2">게시글 2</Link>
        </li>
        <li>
          <Link to="/articles/3">게시글 3</Link>
        </li>
      </ul>
    </div>
  );
};

export default Articles;
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
