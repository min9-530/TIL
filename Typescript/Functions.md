# Functions
타입스크립트에서의 함수 사용법

# Description
```ts
function 함수이름(매개변수: 타입) : 리턴값의 타입 {
  // 코드 작성
};
```

# Usage
```ts
function Multiple(a: number, b: number) {
  return a * b;
}

Multiple(1, 2);
Multiple(3, 4, 5); // error, too many parameters
```

# Optional
> 타입스크립트에선 **선택적(Optional) 키워드**인 **물음표(?)** 를 사용해서 **정의된 매개변수의 갯수 만큼 인자를 넘기지 않아도 되게** 만들 수 있다.
```ts
function sum(a: number, b?: number): number { 
  return a + b;
}
sum(10, 20); // 30
sum(10); // 10, 타입 에러 없음
```  

```ts
function sum(a?: number, b: number): number { 
  return a + b;
}
sum(10, 20); // error
```
> 단, 선택적 매개변수가 필수 매개 변수 앞에 위치하면 안된다.

# OverLoading
> 타입스크립트에선 함수명은 같지만, 매개뱐수와 변환 타입이 다른 함수를 여러개 선언할 수 있다.
```ts
function add(a: string, b: string): string;
function add(a: number, b: number): number;
function add(a: any, b: any): any {
  return a + b;
}

```
> 가장 일반적인 함수 (매개변수를 any 타입으로 선언)의 **시그니처**를 가장 아래에 선언하고 그 위에 구체적인 타입을 명시한 함수의 시그니처를 쌓는 방식으로 선언해야 한다.
