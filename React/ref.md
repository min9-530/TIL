# ref
HTML에서 id를 사용하여 DOM에 이름을 다는 것처럼 리액트 프로젝트 내부에서 DOM에 이름을 다는 방법이 있는데, 바로 ref(reference의 줄임말) 개념이다.

# ref를 사용해야 할 상황
ref를 사용해야 할 상황은 바로 __DOM을 꼭 직접적으로 건드려야 할 때__ 이다.  
예를 들어 바닐라 자바스크립트 및 jQuery로 만든 웹 사이트에서 input값을 검증할 때는 특정 id를 가진 input에 클래스를 설정해 줘야 하지만,  
리액트에선 굳이 DOM에 접근하지 않고 state로 구현할 수 있다. 

# DOM을 꼭 사용해야 하는 상황
+ 특정 input에 포커스 주기
+ 스크롤 박스 조작하기
+ Canvas 요소에 그림 그리기 등
+ 애니메이션을 직접적으로 실행시킬때
+ 서드 파티 DOM 라이브러리를 리액트롸 같이 사용할 때

# 사용법?

1. React Hooks인 useRef를 사용한 설정  
``const input = useRef();``
2. createRef를 사용한 설정  
``input = React.createRef();``
3. 콜백 함수를 통한 설정  
``<input ref={(ref) => {this.input=ref}} />``

# 스크롤 박스 조작

## ScrollBox.js
```javascript
import React, { Component } from "react";

class ScrollBox extends Component {
  ScrollToBottom = () => {
    const { scrollHeight, clientHeight } = this.box;
    /*  앞 코드에는 비구조화 할당 문법 사용
            const scrollHeight = this.box.scrollHeight;
            const clientHeight = this.box.clientHeight;
        */
    this.box.scrollTop = scrollHeight - clientHeight;
  };

  render() {
    const style = {
      border: "1px solid black",
      height: "300px",
      width: "300px",
      overflow: "auto",
      position: "relative",
    };

    const innerStyle = {
      width: "100%",
      height: "650px",
      background: "linear-gradient(white, black)",
    };

    return (
      <div
        style={style}
        ref={(ref) => {
          this.box = ref;
        }}
      >
        <div style={innerStyle} />
      </div>
    );
  }
}

export default ScrollBox;
```

## App.js
```javascript
import { Component } from "react";
import ScrollBox from "./ScrollBox";

class App extends Component {
  render() {
    return (
      <div>
        <ScrollBox ref={(ref) => (this.ScrollBox = ref)} />
        <button onClick={() => this.ScrollBox.ScrollToBottom()}>
          맨 밑으로
        </button>
      </div>
    );
  }
}

export default App;

```
