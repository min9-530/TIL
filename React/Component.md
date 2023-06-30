# **Component**

리액트에서 UI 요소를 구분할 때 사용하는 단위이다.  
만약 레고로 집을 쌓게 된 경우,  
레고 블록 하나하나가 컴포넌트라고 할 수 있으며,  
컴포넌트는 크게 두가지로 나뉜다.

# **1. 클래스형 컴포넌트**

state 기능 및 라이프 사이클 기능을 사용할 수 있고 임의 메서드도 정의할 수 있다.  
render 함수가 꼭 있어야하며, 그 안에서 보여 주어야 할 JSX를 반환해야 한다.

```javascript
import { Component } from "react";

class ClassExample extends Component {
  render() {
    return 코드코드;
  }
}

export default ClassExample;
```

# **2. 함수형 컴포넌트**

클래스형 컴포넌트보다 선언하기가 편하며 메모리 자원도 덜 사용한다.  
React Hooks가 도입되며 원래 사용하지 못했던 state와 라이프사이클 API가 사용이 가능해졌다.

```javascript
function FunctionExample() {
  return 코드코드;
}
```

# **컴포넌트의 구성요소**

1. property(props)

- 부모 컴포넌트에서 자식 컴포넌트로 전달되는 데이터이다. props값은 자식 컴포넌트에서 수정할 수 없다.

2. state

- 컴포넌트의 상태를 저장하고 수정 가능한 데이터이다.

3. context

- 부모 컴포넌트에서 생성하여 모든 자식 컴포넌트에게 전달하는 데이터이다.
