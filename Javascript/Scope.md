# Scope
자바스크립트에서 Scope란 우리가 변수 혹은 함수를 선언하게 될 때 해당 변수 또는 함수가 유효한 범위를 의미한다.  
Scope에는 총 3가지의 종류가 있는데,  
1. Global (전역) Scope
    + 코드의 모든 범위에서 사용이 가능하다.
3. Function (함수) Scope
    + 함수 안에서만 사용이 가능하다.
5. Block (블록) Scope
    + if, for, switch 등 특정 블록 내부에서만 사용이 가능하다.
  
## Global Scope
```js
const value = "hello!";

function myFunction() {
  console.log("myFunction: ");
  console.log(value);
}

function otherFunction() {
  console.log("otherFunction: ");
  const value = "bye!";
  console.log(value);
}

myFunction();
otherFunction();

console.log("global scope: ");
console.log(value);

```
![image](https://github.com/min9-530/TIL/assets/104071568/9215a3a1-bb81-4168-85d2-5b1080e2175b)

코드의 맨 윗줄에 선언된 value 값은 Global Scope로 선언된 값으로, 어디서든 사용이 가능하다.  

otherFunction에서, 함수 내부의 value 값을 'bye!'로 새로 선언을 해주었다.  
이렇게 되면, value 값은 Function Scope 로 지정되서 해당 값은 otherFunction 의 내부에서만 유효한 값이 된다.  

이렇게 값을 설정한다고 해서 기존의 Global Scope 로 선언된 value 값이 바뀌지 않는다.

## Function Scope

```js
const value = "hello!";

function myFunction() {
  const value = "bye!";
  const anotherValue = "world";
  function functionInside() {
    console.log("functionInside: ");
    console.log(value);
    console.log(anotherValue);
  }
  functionInside();
}

myFunction();
console.log("global scope: ");
console.log(value);
console.log(anotherValue);
```
![image](https://github.com/min9-530/TIL/assets/104071568/30600883-a270-4794-b7b5-85b9a006cf6e)  

myfunction 내부에 anotherValue 라는 새로운 값을 선언하고, functionInside 라는 함수도 선언을 했다.  
functionInside 함수에서는 myFunction 에서 선언한 value 값과 anotherValue 값을 조회 할 수 있지만,  
myFunction 밖에서는 anotherValue 를 조회 할 수 없다.

## Block Scope
```
const value = "hello!";

function myFunction() {
  const value = "bye!";
  if (true) {
    const value = "world";
    console.log("block scope: ");
    console.log(value);
  }
  console.log("function scope: ");
  console.log(value);
}

myFunction();
console.log("global scope: ");
console.log(value);
```
![image](https://github.com/min9-530/TIL/assets/104071568/a26de087-9ae5-4758-b889-1816e425874f)  

const 로 선언한 값은 Block Scope 로 선언이 된다.  
따라서 if 문 값은 블록 내에서 새로운 변수/상수를 선언하게 된다면, 해당 블록 내부에서만 사용이 가능하며, 블록 밖의 범위에서 똑같은 이름을 가진 값이 있다고 해도 영향을 주지 않는다. 
