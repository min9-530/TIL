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
let a2: Array<string> = ['a', 'b', 'c']; // 제네릭

// 숫자형만 가지는 배열
let b: number[] = [1, 2, 3];
let b2: Array<number> = [1, 2, 3]; // 제네릭

// 다중 타입의 문자열과 숫자를 동시에 가지는 배열
let c: (string | number)[] = [1, 'a', 2, 'b', 3, 'c'];
let c2:Array<string | number> = [1, 'a', 2, 'b', 3, 'c']; // 제네릭

// 배열이 가지는 값의 타입을 추측할 수 없을 때 any 사용할 수 있다.
let d: (any)[] = [1, 'a', 2, 'b', 3, 'c'];
let d2: Array<any> = [1, 'a', 2, 'b', 3, 'c']; // 제네릭
```

## 함수(Function)
함수는 파라미터에 각각 타입을 선언해 주며, 파라미터 우측에는 해당 함수의 리턴값 타입도 선언해 주면 된다.
```js
function sum(a: number, b: number): number {
    return a+b;
}
console.log(sum(2, 3)); // 5
```

## 객체(Object)
```js
let obj: object = {};
let arr: object = [];
let func: object = function() {};
let date: object = new Date();
```
보다 정확하게 타입 지정을 하기 위해 객체 속성들에 대한 타입을 개별적으로 지정할 수 있다.
```js
let player: {
    name: string;
    age?: number;
} = {
    name: "minsu"
}
```
?를 : 앞에 붙이면 optional 처리가 되어서 optional 처리가 된 속성을 사용하든 안하든 상관이 없게 된다.
## 튜플(Tuple)
배열과 유사하지만 정해진 타입의 요소 개수 만큼의 타입을 미리 선언 후 배열을 표현한다.
```js
let tuple: [string, number];
tuple = ['a', 0];
```

정해진 요소의 순서 및 개수가 다르면 오류가 발생한다.
```js
let tuple: [string, number];
tuple = [0, 'a']; // error
tuple = ['a', 0, 'b']; // error
```

데이터를 개별 변수로 지정하지 않고, 단일 튜플 타입으로 지정해 사용할 수도 있다.
```js
// 기존 변수
let name: string = 'woonrin';
let age: number = 18;

// 튜플
let user: [string, number] = ['woonrin', 18];
```

값으로 타입을 대신할 수도 있다. 하지만 처음 선언할 때의 값과 다른 값이 할당 되면 에러가 발생한다.
```js
let user: ['woonrin', number];
user = ['woonrin', 17]; // ["woonrin", 17]
user = ['woonrin', 18]; // ["woonrin", 18]
user = ['aron', 18]; // error
```

튜플은 정해진 타입과 고정된 길이의 배열이지만, 값을 할당할때만 해당된다. push나 splice같은 메소드를 통해 값을 넣는것은 막을 수 없다.
```js
let user: [string, number];
user = ['woonrin', 18];  // ["woonrin", 18]
user.push(2413);  // ["woonrin", 18, 2413]
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
