# Promise
+ 자바스크립트는 비동기 처리를 위한 하나의 패턴으로 __콜백 함수__ 를 사용하는데, 전통적인 콜백 패턴은 __콜백 지옥__ 으로 인해 가독성이 나쁠 뿐더러, 비동기 처리 중 발생한 에러의 처리가 곤란하며 여러개의 비동기 처리를 한번에 처리하는 데도 한계가 있다.
+ ES6에서는 비동기 처리를 위한 또 다른 패턴으로 __프로미스(Promise)__ 를 도입했는데, 프로미스는 전통적인 콜백 패턴이 가진 단점을 보완하며 비동기 처리 시점을 명확하게 표현할 수 있다는 장점이 있다.
+ 프로미스는 __Promise 생성자 함수__ 를 통해 인스턴스화한다. Promise 생성자 함수는 비동기 작업을 수행할 콜백 함수를 인자로 전달받는데 이 콜백 함수는 resolve와 reject 함수를 인자로 전달받는다.
```js
function Increase(number) {
  const promise = new Promise((resolve, reject) => {
    // resolve는 성공, reject는 실패
    setTimeout(() => {
      const result = number + 10;
      if (result > 50) {
        // 50보다 높으면 에러 발생시키기
        const e = new Error("NumberTooBig");
        return reject(e);
      }
      resolve(result); // number 값에 +10 후 성공 처리
    }, 1000);
  });
  return promise;
}

Increase(0)
  .then((number) => {
    // Promise에서 resolve된 값은 .then을 통해서 받아 올 수 있음
    console.log(number);
    return Increase(number);
  })
  .then((number) => {
    // 또 .then으로 처리 가능
    console.log(number);
    return Increase(number);
  })
  .then((number) => {
    console.log(number);
    return Increase(number);
  })
  .then((number) => {
    console.log(number);
    return Increase(number);
  })
  .then((number) => {
    console.log(number);
    return Increase(number);
  })
  .catch((e) => {
    // 도중에 에러가 발생한다면 .catch를 통해 알 수 있음
    console.log(e);
  });

```

Promise는 비동기 처리가 성공(fulfilled)하였는지 또는 실패(rejected)하였는지 등의 상태 정보를 갖는다.  
+ ``pending`` : 비동기 처리가 아직 수행되지 않은 상태
+ ``fulfilled`` : 비동기 처리가 수행된 상태 (성공)
+ ``rejected`` : 비동기 처리가 수행된 상태 (실패)
+ ``settled`` : 비동기 처리가 수행된 상태 (성공 또는 실패)
