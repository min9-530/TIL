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
```ts
interface Student {
  name: string;
  age?: number;
}

const Person: Student = {
  name: 'aron'
  // age를 선언하지 않아도 오류가 나지 않음
}

```


