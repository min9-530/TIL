# Redux-Thunk
redux-thunk는 리덕스를 사용하는 프로젝트에서 비동기 작업을 처리할 때 가장 기본적으로 사용하는 미들웨어이다.  

# Thunk
thunk는 특정 작업을 나중에 할 수 있도록 미루기 위해 함수 형태로 감싼 것을 의미한다. 예를 들어
```js
const addOne = x => x + 1;
addOne(1); // 2
```
이 코드를 실행하면 addOne을 호출했을 때 바로 1 + 1이 연산된다. 하지만 이 연산 작업을 나중에 하고싶다면
```js
const addOne = x => x + 1;
function addOneThunk (x) {
  const thunk = () => addOne(x);
  return thunk;
}

const fn = addOneThunk(1);
setTimeout(() => {
  const value = fn(); // fn이 실행되는 시점에 연산
  console.log(value); // 2
}, 1000);
```
이렇게 하면 특정 작업을 나중에 하도록 미룰 수 있다.
