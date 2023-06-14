# QueryString
쿼리스트링은 사용자가 입력 데이터를 전달하는 방법중의 하나로, 요청하고자 하는 URL에 부가적인 정보를 포함하고 싶을 때 사용한다.    

## 형태
![image](https://github.com/min9-530/TIL/assets/104071568/947149e0-8461-4769-913f-c508f3f901c7)  
쿼리스트링은 이름 그대로 문자열 타입으로 key = value로 표현된다. 또한 URL의 일부로 쿼리스트링의 시작점은 "?"으로 표시된다.  

``https://www.example.com/products?sort=popular&direction=desc``
key=value의 개수에 제한은 없고 구분할 때는 "&"을 기입한다.

# useLocation
location 객체를 반환하며 사용자가 현재 보고있는 페이지의 정보를 지니고 있다.  

## location 객체의 속성값
+ pathname: 현재 주소의 경로
+ search: 맨 앞의 ? 문자를 포함한 쿼리스트링 값
+ hash: 주소의 # 문자열 뒤의 값
+ state: 페이지로 이동할 때 임의로 넣을 수 있는 상태 값
+ key: location 객체의 고유값, 초기에는 default이며 페이지가 변경될 때마다 고유의 값이 생성

## About.js
```js
// 주소: http://localhost:3000/about?detail=true&mode=1

import { useLocation } from "react-router-dom";

const About = () => {
  const location = useLocation();

  return (
    <div>
      <h1>소개</h1>
      <p>리액트 라우터를 사용해 보는 프로젝트입니다.</p>
      <p>쿼리스트링: {location.search}</p>
      {/*location.search의 값: ?detail=true&mode=1*/}
    </div>
  );
};

export default About;
```

# useSearchParams
useSearchParams는 쿼리스트링을 더욱 쉽게 다룰 수 있게 해주는 React Hook 이다.  
useSearchParams는 배열 타입의 값을 반환하며, 첫 번째 원소는 쿼리파라미터를 조회하거나 수정하는 메서드들이 담긴 객체를 반환한다.  
get 메서드를 통해 특정 쿼리파라미터를 조회할 수 있고, set 메서드를 통해 특정 쿼리파라미터를 업데이트할 수 있다. 만약 조회 시 쿼리파라미터가 존재하지 않는다면 null로 조회된다.  
두 번째 원소는 쿼리파라미터를 객체 형태로 업데이트할 수 있는 함수를 반환한다.

## About.js
```js
// 주소: http://localhost:3000/about?detail=true&mode=1

import { useSearchParams } from "react-router-dom";
import "./About.scss";

const About = () => {
  const [searchParams, setSearchParams] = useSearchParams();
  const detail = searchParams.get("detail");
  const mode = searchParams.get("mode");

  const onToggleDetail = () => {
    // detail의 boolean 상태 변환
    setSearchParams({ mode, detail: detail === "true" ? false : true });
  };

  const onIncreaseMode = () => {
    // mode 값 증가
    const nextMode = mode === null ? 1 : parseInt(mode) + 1;
    setSearchParams({ mode: nextMode, detail });
  };
  // mode 값 감소
  const onDecreaseMode = () => {
    const prevMode = mode === null ? 1 : parseInt(mode) - 1;
    setSearchParams({ mode: prevMode, detail });
  };
  // mode 값 초기화
  const OnResetMode = () => {
   const resetMode = mode === null ? 0 : 0;
    setSearchParams({ mode: resetMode, detail });
  };

  return (
    <div>
      <h1>소개</h1>
      <p>리액트 라우터를 사용해 보는 프로젝트입니다.</p>
      <p>detail: {detail}</p>
      <p>mode: {mode}</p>
      <button onClick={onToggleDetail}>Toggle detail</button>
      <button onClick={onIncreaseMode}>IncreaseMode</button>
      <button onClick={onDecreaseMode}>DecreaseMode</button>
      <button onClick={OnResetMode}>ResetMode</button>
    </div>
  );
};

export default About;
```
