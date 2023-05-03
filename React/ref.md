# ref
HTML에서 id를 사용하여 DOM에 이름을 다는 것처럼 리액트 프로젝트 내부에서 DOM에 이름을 다는 방법이 있는데, 바로 ref(reference의 줄임말) 개념이다.

## ref를 사용해야 할 상황
ref를 사용해야 할 상황은 바로 __DOM을 꼭 직접적으로 건드려야 할 때__ 이다.  
예를 들어 바닐라 자바스크립트 및 jQuery로 만든 웹 사이트에서 input값을 검증할 때는 특정 id를 가진 input에 클래스를 설정해 줘야 하지만,  
리액트에선 굳이 DOM에 접근하지 않고 state로 구현할 수 있다. 

## ValidationSample.js
```javascript
import { useState } from "react";

function ValidationSample() {
  const [valid, setValid] = useState({
    password: "",
    clicked: false,
    validation: false,
  });

  const handleChange = (e) => {
    setValid({
      password: e.target.value,
    });
  };

  const handleButtonClick = () => {
    setValid({
      clicked: true,
      validation: valid.password === "0000",
    });
  };

  return (
    <div>
      <input
        type="password"
        value={valid.password}
        onChange={handleChange}
        className={
          valid.clicked ? (valid.validation ? "success" : "failure") : ""
        }
      />
      <button onClick={handleButtonClick}>검증하기</button>
    </div>
  );
}

export default ValidationSample;
```
input에서는 onChange 이벤트가 발생하면 handleChange를 호출하여 state의 password 값을 업데이트하게 하고,  
button에서는 onClick 이벤트가 발생하면 handleButtonClick을 호출하여 clicked 값을 참으로 설정하고. validated 값을 검증 결과로 설정했다.
