# map
map 함수는 자바스크립트 내장 함수로 반복되는 컴포넌트를 랜더링할 수 있다.
map 함수는 파라미터로 전달된 함수를 사용해서 배열 내 각 요소를 원하는 규칙에 따라 변환한 후 그 결과로 새로운 배열을 생성한다.

# 문법
```javascript
const mapEx = (arr.map(callback, [thisArg]));
```
이 함수의 파라미터는 다음과 같다.
+ callback : 새로운 배열의 요소를 생성하는 함수로 파라미터는 다음 세 가지이다.
  + currentValue : 현재 처리하고 있는 요소
  + index : 현재 처리하고 있는 요소의 index 값
  + array : 현재 처리하고 있는 원본 배열
 + thisArg(선택 항목) : callback 함수 내부에서 사용할 this 레퍼런스
 
 
 # key 값이 없을때
 ```javascript
 import React from "react";

function Friends() {
  const list = ["한준", "이운린", "정영운", "이아론"];
  const namelist = list.map((list) => <li>{list}</li>);
  return <ul>{namelist}</ul>;
}

export default Friends;
 ```
 
 # key 값을 지정했을때
 ```javascript
 import React, { useState } from "react";

function Friends() {
  const [list, setList] = useState([
    { id: 1, text: "한준" },
    { id: 2, text: "이아론" },
    { id: 3, text: "정영운" },
    { id: 4, text: "이운린" },
  ]);
  const namelist = list.map((list) => <li key={list.id}>{list.text}</li>);
  return <ul>{namelist}</ul>;
}

export default Friends;
 ```
 
 # Key
 Key는 React가 어떤 항목을 변경, 추가 또는 삭제할지 식별하는 것을 돕는다.  
 ``key``는 ``element``에 안정적인 고유성을 부여하기 위해 배열 내부의 엘리멘트에 지정해야한다.  
 ``key``는 배열 안에서 형제 사이에서만 고유해야 하고 전체 범위에선 고유할 필요가 없다.  
 따라서 두 개의 다른 배열을 만들 때는 동일한 ``key``를 사용할 수 있다.  
 대부분의 경우 데이터의 ID를 Key로 사용한다.  

 # Key Props를 부여하는 이유
map()을 사용할 때 key props를 부여해주지 않으면 리액트는 어떤 항목이 변경, 추가, 삭제되었는지를 식별하는 데 어려움을 겪게 되고, 이 이유로 인해 전체를 리렌더링하며 속도 저하나 의도치 않은 오류등을 발생시킬 수 있기 때문에 key props를 부여해주는 것이 좋다.
