# useEffect
useEffect는 리액트 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook이다.  
클래스형 컴포넌트의 componentDidMount와 componentDidUodate를 합친 형태로 보아도 무방하다.
# 사용법
## 기본 사용법
```javascript
useEffect(() => {
  수행할 코드
}, [의존값]);
```

useEffect는 의존값을 설정하지 않는다면 특정 작업이 항상 실행되고, 의존값을 설정한다면 의존값이 바뀔 때만 특정 작업이 실행된다.
