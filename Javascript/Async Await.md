# Async / Await
__async__ 와 __await__ 는 자바스크립트의 비동기 처리 패턴 중 가장 최근에 나온 문법이다.  
기존의 처리 방식인 콜백 함수와 프로미스의 단점을 보완하고 개발자가 읽기 좋은 코드를 작성할 수 있도록 도와준다.  
특히, 복잡했던 기존의 __Promise__ 를 조금 더 편하게 사용할 수 있다.  
__async await__ 의 기본 문법은 아래와 같다.
```js
 async function 함수명() {
  await 비동기_처리_메서드_명();
}
```

# Async
+ async는 function 앞에 사용한다. function 앞에 async를 붙이면 해당 함수는 항상 프로미스를 반환한다.
