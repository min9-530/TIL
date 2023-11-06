# Generator
자바스크립트에서 일반 함수는 하나의 값만을 반환한다.  
하지만 제너레이터 함수는 여러 개의 값을 필요에 따라 하나씩 반환(yield)할 수 있다.  

# Generator Function
제너레이터 함수를 만드려면 일반 함수와는 다른 **제너레이터 함수**라고 불리는 특별한 문법 구조인 ``funtion*``가 필요하다. 
```js
function* generaterFunction() {
  console.log("제너레이터 함수 실행 중...");
  yield 1;
  console.log("제너레이터 함수 실행 완료...")
  yield 2;
  return 3;
}
```
이렇게 제너레이터 함수를 작성하고 호출해보면 코드가 실행되는게 아닌 실행을 처리하는 특별 객체인 **제너레이터 객체**가 반환된다.

```js
const generator = generatorFunction();

generator.next();
// 제너레이터 함수 실행 중...
//{value: 1, done: false}
generator.next();
// 제너레이터 함수 실행 완료...
// {value: 2, done: false}
generator.next();
// {value: 3, done: true}
```

이 제너레이터 객체가 처음 만들어지면 함수의 흐름은 멈춰있는 상태이다. next()가 호출되면 다음 yield가 있는 곳까지 호출하고 다시 멈춘다.  
이처럼 제너레이터 함수를 사용하면 함수를 도중에 멈출 수 있고, 순차적으로 여러 값들을 반환할 수 있다.  

```js
function* sumGenerator() {
  console.log("sumGenerator가 만들어졌습니다.")
  let a = yield;
  let b = yield;
  yield a + b;
}

const sum = sumGenerator();
sum.next();
// sumGenerator가 만들어졌습니다.
// {value: undefined, done: false}
sum.next(1);
// {value: undefined, done: false}
sum.next(2);
// {value: 3, done: false}
sum.next();
// {value: undefined, done: true}
```

```js
function* watchGenerator() {
  console.log("모니터링 중...");
  let prevAction = null;
  while(true) {
  const action = yield;
  console.log("이전 액션: ", prevAction);
  prevAction = action;
  if(action.type === 'HELLO') {
      console.log("안녕하세요!")
    }
  }
}

const watch = watchGenerator();
watch.next();
// 모니터링 중..
// {value: undefined, done: false}
watch.next({ type : 'TEST' })
// 이전 액션: null
// {value: undefined, done: false}
watch.next(type : 'HELLO')
// 이전 액션: TEST
// {value: undefined, done: false}
```
