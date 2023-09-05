# Functions
타입스크립트에서의 함수 사용법

# Description
```js
function 함수이름(매개변수: 타입) : 리턴값의 타입 {
  // 코드 작성
};
```

# Usage
```js
function Multiple(a: number, b: number) {
  return a * b;
}

Multiple(1, 2);
Multiple(3, 4, 5); // error, too many parameters
```

# Optional
타입스크립트에선 **선택적(Optional) 키워드**인 **물음표(?)** 를 사용해서 **정의된 매개변수의 갯수 만큼 인자를 넘기지 않아도 되게** 만들 수 있다.
```js
function sum(a: number, b?: number): number { 
  return a + b;
}
sum(10, 20); // 30
sum(10); // 10, 타입 에러 없음
```  

```js
function sum(a?: number, b: number): number { 
  return a + b;
}
sum(10, 20); // error
```
단, 선택적 매개변수가 필수 매개 변수 앞에 위치하면 안된다.
