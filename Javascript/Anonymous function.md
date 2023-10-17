# 익명함수
자바스크립트에서 익명 함수는 함수명 대신 변수에 함수 코드를 저장하는 구현 방식으로, 재사용 하지 않으며, 한번만 사용할 함수를 위한 것이다.

## 장점
익명함수는 단 한번만 사용되는 함수이기 때문에 해당 함수가 필요한 위치에서만 함수가 구현되고 사라지기면서 메모리를 아낄 수 있게 된다.

## 단점
호이스팅이 적용되지 않는다.
```js
data();

let data = function(){
    console.log('Hi');
}

// TypeError: data is not a function
```

## 기본 구조
```js
let 변수명 = function( 매개변수 )
{
  실행문
};
```

## 익명함수 + 반환문
```js
let hi = function() {
    let string = "Hello World!";
    return string;
};

console.log(hi());
// Hello World!
```

## 익명함수의 변수명 변경
익명 함수는 함수 코드가 변수명에 저장된 형태이기 때문에, 변수값으로 구성된 함수 코드를 다른 변수명에 대입하듯이 이동시킬 수 있다.
```js
let apple = function() {
  console.log("This is Mango.");
};

let orange = apple;

orange();
// This is Mango.
```

