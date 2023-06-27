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
+ async는 function 앞에 사용한다. function 앞에 async를 붙이면 __해당 함수는 항상 프로미스를 반환__ 한다. 프로미스가 아닌 값을 반환하더라도 __이행 상태의 프로미스(resolved Promise)__ 로 값을 감싸 이행된 프로미스가 반환되도록 한다.

```js
async function f() {
  return 1;
}

f().then(alert); // 1
```
위의 함수를 호출하면 결과가 1인 이행 프로미스가 반환된다.  
위의 함수에서 1을 ``Promise.resolve``로 감싸도 같은 결과를 반환한다.  
```js
async function f() {
  return Promise.resolve(1);
}

f().then(alert); // 1
```
즉, ``async``가 붙은 함수는 반드시 프로미스를 반환하고, 프로미스가 아닌 것은 프로미스로 감싸 반환한다.

# Await
+ await는 async 함수 안에서만 동작한다. await는 '기다리다' 라는 뜻을 지닌 영단어로, 프로미스가 처리될 떄 까지 기다리는 역할을 한다. 그리고 결과는 그 이후 반환된다.
```js
async function f() {

  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("완료!"), 1000)
  });

  let result = await promise; // 프라미스가 이행될 때까지 기다림 (*)

  alert(result); // "완료!"
}

f();
```
+ 함수를 호출하고, 함수 본문이 실행되는 도중에 ``(*)``표시한 줄에서 실행이 잠시 '중단' 되었다가 프로미스가 처리되면 실행이 재개된다.
+ 이때 프로미스 객체의 ``result`` 값이 변수 result에 할당된다. 따라서 위 예시를 실행하면 1초 뒤에 '완료!' 가 출력된다.
