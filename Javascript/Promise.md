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


# 후속 처리 메서드
후속 처리 메서드에는 대표적으로 ``then``(Promise 반환)과 ``catch``(예외)가 있다.

## then
+ then 메소드는 두 개의 콜백 함수를 인자로 전달 받는다.  
+ 첫 번째 콜백 함수는 성공(fulfilled, resolve 함수가 호출된 상태) 시 호출된다.
+ 두 번째 함수는 실패(rejected, reject 함수가 호출된 상태) 시 호출된다.
+ then 메소드는 기본적으로 프로미스를 반환한다.

## catch
+ catch 메소드는 비동기 처리 혹은 then 메소드 실행 중 발생한 에러(예외)가 발생하면 호출된다.
+ catch 메소드 역시 프로미스를 반환한다.


# Promise 체이닝
비동기 함수의 결과를 가지고 비동기 함수를 호출해야 하는 경우, 함수의 호출이 중첩되어 복잡도가 높아지는 콜백 지옥이 발생할 수 있다.  
프로미스는 후속 처리 메소드인 ``then``이나 ``catch``로 __메소드를 체이닝__ 하여 프로미스를 반환하는 여러개의 비동기 함수들을 연결하여 사용할 수 있다.

# 정적 메소드

## Promise.resolve
__Promise.resolve__ 메소드는 인자값을 래핑하여 프로미스를 반환한다. __(fulfilled)__

## Promise.reject
__Promise.reject__ 메소드 역시 인자값을 래핑하여 프로미스를 반환한다. __(rejected)__

## Promise.all
__Promise.all__ 메소드는 프로미스가 담겨있는 배열과 같은 이터러블 객체를 인자로 받는다.  
인자로 전달받은 모든 프로미스를 병렬로 처리하고 그 결과값을 배열에 담아 __resolve__ 로 반환한다.

## Promise.race
__Promise.race__ 메소드는 __Promise.all__ 메소드와 동일하게 프로미스가 담겨있는 이터러블 객체를 인자로 받지만, __Promise.all__ 과 달리 병렬로 처리하지 않고 가장 먼저 끝나는 프로미스의 결과값을 __resolve__ 로 반환한다.

## Promise.allSettled
__Promise.allSettled__ 메소드 역시 __Promise.all__ 메소드와 동일하게 프로미스가 담겨있는 이터러블 객체를 인자로 받고 병렬로 처리한다.  
다만 __Promise.all__ 의 경우 프로미스를 수행하던 도중 하나라도 에러(rejected)가 발생하면 __rejected__ 상태가 되고 수행을 종료하게 되지만, __Promise.allSettled__ 메소드의 경우 __rejected__ 상태가 되어도 수행을 종료하지 않고, 프로미스가 수행된 상태와 결과값을 배열에 담아  __resolve__ 로 반환한다.
