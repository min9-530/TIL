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
