# **Props**

props는 properties를 줄인 표현으로 컴포넌트 속성을 설정할 때 사용하는 요소이다.  
또한 읽기 전용 데이터이기 때문에 자식 컴포넌트에서 props를 수정할 수 없고 props를 전달해준 부모 컴포넌트에서 값을 변경 할 수 있다.

# **부모에서 값 지정**

## App.js
```javascript
import MyComponent from './MyComponent';

function App() {
  return <MyComponent name="Minsu" />;
};

export default App;
```

## MyComponent.js
```javascript
function MyComponent({name}) {
  return (
  <div>
    안녕하세요, 제 이름은 {name} 입니다.
  </div>
  );
};

export default MyComponent;
```
위의 코드를 실행해보면, 
![image](https://user-images.githubusercontent.com/104071568/235654922-a4a481e1-0e3e-4b6a-a558-835d8ed2fa1d.png)

이렇게 App.js에서 지정한 props의 값이 지정된 것을 볼 수 있다.

# 기본값 설정: defaultProps

## App.js
```javascript
import MyComponent from './MyComponent';

function App() {
  return <MyComponent />;
};

export default App;
```
먼저 App.js를 이렇게 해놓고 시작해보자. 
## MyComponent.js
```javascript
function MyComponent({name}) {
  return (
  <div>
    안녕하세요, 제 이름은 {name} 입니다.
  </div>
  );
};

MyComponent.defaultProps = {
  name: '기본 이름'
};

export default MyComponent;
```
위의 코드를 실행해보면, 
![image](https://user-images.githubusercontent.com/104071568/235655737-21115e3c-ab9b-461b-ac12-fa1e43a9ac58.png)

이렇게 App.js에서 props의 값을 지정해주지 않았을 때 defaultProps의 값이 보여지게 된다.

# children
이번에는 리액트 컴포넌트를 사용할 때 컴포넌트 태그 사이의 내용을 보여 주는 props 인 children을 알아볼 것이다.

## App.js
```javascript
import MyComponent from './MyComponent';

function App() {
  return <MyComponent>리액트</MyComponent>;
};

export default App;
```

## MyComponent.js
```javascript
function MyComponent(props) {
    return (
    <div>
      안녕하세요, 제 이름은 {props.name} 입니다. <br />
      children 값은 {props.chidren} 입니다.
    </div>
    );
  };
  
  MyComponent.defaultProps = {
    name: '기본 이름'
  }
  export default MyComponent;
```
위 코드를 실행해보면, 
![image](https://user-images.githubusercontent.com/104071568/235657439-ba105b1e-93cb-438d-88f3-13c42aadbd70.png)
이렇게 `{props.children}`이 컴포넌트 태그 사이에 지정된 내용을 보여주게 된다.
