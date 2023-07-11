# Types
타입스크립트는 일반변수, 매개변수, 객체 속성 등에 ``: TYPE``과 같은 형태로 타입을 지정할 수 있다.

## 타입 지정
```js
let a: string = 'hi'; // 문자열
let b: number = 1; // 숫자형
let c: boolean = false; // 논리형
let d: any = true; // 어떤 타입인지 모를 때
let e: string | number = 0; 문자열이나 숫자가 올 때
```

## 타입 에러
타입을 선언하고 다른 타입을 대입하거나 값이 선언된 후에 다른 타입의 값이 대입되면 에러가 발생한다.
```js
// 문자열로 선언하고 숫자를 대입하면 에러 발생
let a: string = 1; // 에러 발생

// 문자열 값이 들어가고 숫자가 대입되면 에러 발생
let b: string = "hi";
b = 0; // 에러 발생
```

# 타입 선언
타입스크립트는 ES5, ES6의 상위 확장인 언어이므로 자바스크립트의 타입을 그대로 사용하며,  
이외에도 타입스크립트 만의 고유의 타입이 추가로 제공된다.

## 논리형(Boolean)
```js
let a: boolean = false;
let b: boolean = true;
```

## 숫자형(Number)
```js
let a: number = 0;
let b: number = 3.14;
let c: number = NaN;
```

## 문자열(String)
ES6의 템플릿 문자열도 지원한다.
```js
let a: string = 'Hi'
let b: string = 'Hi ${name}';
```

## 배열(Array)
```js
// 문자열만 가지는 배열
let a: string[] = ['a','b','c'];

// 숫자형만 가지는 배열
let b: number[] = [1, 2, 3];

// 다중 타입의 문자열과 숫자를 동시에 가지는 배열
let c: (string | number)[] = [1, 'a', 2, 'b', 3, 'c'];

// 배열이 가지는 값의 타입을 추측할 수 없을 때 any 사용할 수 있다.
let d: (any)[] = [1, 'a', 2, 'b', 3, 'c'];
```

## 함수(Function)
```js

```

## 객체(Object)
```js

```

## 튜플(Tuple)
```js

```

## 열거형(Enum)
```js

```

## 모든 타입(Any)
```js

```

## 빈 타입(Void)
```js

```

## 절대 발생할 수 없는 타입(Never)
```js
```
