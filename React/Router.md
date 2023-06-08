# 라우팅이란?

라우팅이란 간단하게 사용자가 요청한 URL에 따라 해당 URL에 맞는 페이지를 보여주는 것을 의미한다.  

리액트에선 라우팅 관련 라이브러리가 많이 있는데, 이중 가장 많이 쓰이는 것은 리액트 라우터(React Router)이다.


# 리액트 라우터(React Router)
사용자가 입력한 주소를 감지하는 역할을 하며, 여러 환경에서 동작할 수 있도록 여러 종류의 라우터 컴포넌트를 제공한다.  

이중에서 가장 많이 사용되는 라우터 컴포넌트는 BrowserRouter와 HashRouter이다.

## 종류
1. BrowserRouter: HTML5를 지원하는 브라우저의 주소를 감지 한다.  
2. HashRouter : 해시 주소 (https://github.com/min9-530/TIL/blob/main/React/Router.md)를 감지한다.

## 설치
npm  
```npm install react-router-dom```

yarn  
```yarn add react-router-dom```
