# Interface
1. 인터페이스는 일반적으로 타입 체크를 위해 사용되며 변수, 함수, 클래스에 사용할 수 있다.
2. 타입스크립트에서의 인터페이스는 다음과 같은 범주에 대해 약속을 정의할 수 있다.
    + 객체의 스펙(속성과 속성의 타입)
    + 함수의 파라미터
    + 함수의 스펙(파라미터, 반환 타입 등)
    + 배열과 객체를 접근하는 방식
    + 클래스

# Usage
## Union
> 기본 생성 방식
```ts
interface Student {
  name: string;
  age: number;
  grade: number;
}

const person: Student = {
  name: "minsu",
  age: 18,
  grade: 2, 
};

console.log(person.name); // minsu
console.log(person.age); // 18
console.log(person.grade); // 2
```

## Optional
> 있어도 되고 없어도 되는 속성으로 생성 (? 사용)
```ts
interface 인터페이스_이름 {
    속성?: 타입;
}
```

```ts
interface Student {
  name: string;
  age?: number;
}

const Person: Student = {
  name: 'aron'
  // age를 옵션 속성으로 선언했기 때문에 선언하지 않아도 오류가 나지 않음
}

```

## Readonly
> 생성할 때만 할당이 가능하고 후엔 재할당이 불가능한 읽기 전용 속성으로 생성
```ts
interface Student {
    readonly age: number; // 인터페이스로 객체를 생성할 때만 값을 할당하고 그 이후에는 변경할 수 없다.
}

let Person: Student = {
    age: 18;
};

Person.age = 17; // error
```

```ts
let arr: ReadonlyArray<T> = [1, 2, 3, 4]; // ReadonlyArray<T>를 사용하여 읽기 전용 배열도 생성 가능

arr.push(5); // error
arr[0] = 100; // error
```

## Index
> 여러 속성 정보를 받을 때 사용
```ts
interface Alphabet {
    [num:number]: string;
}

let english:Alphabet = {
    1: "A",
    2: "B",
    3: "C",
};
```

## Function
> 함수의 매개변수와 리턴값의 타입을 정의할 때 사용
```ts
interface Add {
    (num1: number, num2: number): number;
}

const add: Add = (x, y) => {
    return x + y;
}

console.log(add(10, 20)); // 30
```

## Class
> 클래스가 일정 조건을 만족하도록 타입 규칙을 정할 때 사용
```ts
interface user {
    username: string;
    print(name: string): void;
}

class Login implements user {
    username: string = 'sol';
    print(name: string) {
        console.log(name);
    }
constructor() {}
}
```
