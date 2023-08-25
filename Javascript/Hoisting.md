# Hoisting
Hoisting 이란, 자바스크립트에서 아직 선언되지 않은 함수/ 변수를  
끌어올려서 사용할 수 있는 자바스크립트의 작동 방식을 의미한다.

## 예시
```js
myFunction();

function myFunction() {
  console.log('hello world!');
}
```
위 코드에서는 ``myFunction`` 함수를 선언하기 전에, ``myFunction()`` 을 호출하였는데, 함수가 아직 선언되지 않았음에도 불구하고,  
코드는 정상적으로 작동하게 된다.  

이게 잘 작동하는 이유는, 자바스크립트 엔진이 위의 코드를 해석하는 과정에서 이렇게 받아들이기 때문이다.  

```js
function myFunction() {
  console.log('hello world!');
}

myFunction();
```
이러한 작동 방식을 Hoisting 이라고 부른다.  

변수 또한 Hoisting 되는데,  

```js
console.log(number);
```

![image](https://github.com/min9-530/TIL/assets/104071568/595262d2-4405-4c39-a372-70046a4c7bd5)  
위의 코드를 실행한다면 이런 오류가 발생하게 된다.  

```js
console.log(number);
var number = 2;
```
![image](https://github.com/min9-530/TIL/assets/104071568/856d28e0-4b74-4fea-a08b-f41c8fd168b8)  
하지만 이런 코드를 입력하면 ``undefined`` 가 출력된다.  

자바스크립트가 위 코드를 해석할 때는 이렇게 받아들이게 된다.
```js
var number;
console.log(number);
number = 2;
```
Hoisting 은 자바스크립트 엔진이 갖고 있는 성질로, Hoisting 을 일부러 할 필요는 없지만 방지하는 것이 좋다.  
