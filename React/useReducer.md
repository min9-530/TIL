# useReducer
useReducer는 useState보다 더 다양한 컴포넌트 상황에 따라 다양한 상태를 다른 값으로 업데이트해 주고 싶을 때 사용하는 Hook이다.  
Reducer는 현재 상태, 그리고 업데이트를 위해 필여한 정보를 담은 액션 값을 전달받아 새로운 상태를 반환하는 함수이다.  
Reducer 함수에서 새로운 상태를 만들 때는 반드시 불변성을 지켜 주어야 한다.

```javascript
function reducer(state, action) {
  switch (action.type) {
  ...
     return state;
  }
}
```
## 구성요소
+ Dispatch - state의 업데이트를 위한 요구를 하는 역할
+ Action - dispatch의 요구내용
+ Reducer - dispatch의 action값을 받아 state를 업데이트 하는 역할

# Counter 구현
```javascript
import { useReducer } from 'react';

function reducer(state, action) {
  // action.type에 따라 다른 작업 수행
  switch (action.type) {
    case 'INCREMENT':
      return { value: state.value + 1 };
     case 'DECREMENT':
      return { value: state.value - 1 };
     default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { value: 0 });
  
  return (
    <div>
      <p>
        현재 카운터 값은 <b>{state.value}</b>입니다.
      </p>
       <button onClick={()=>dispatch({type: 'INCREMENT' })}>+1</button>
       <button onClick={()=>dispatch({type: 'INCREMENT' })}>-1</button>
    </div>
  );
};

export default Counter;
```
