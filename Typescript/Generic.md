# Generic
> C# 및 Java와 같은 언어에서 사용되는 문법  
> 대규모 소프트웨어를 구축할 수 있는 가장 유연한 기능 제공  
> ``<T>``와 같은 괄호 사용  
> 여러 타입을 한번에 받을 수 있음

# Usage
```ts
function 함수명<타입 변수 지정>(arg: 타입 인자): 타입 반환 {
  return arg;
}
```

# Before Using Generic
```ts
function getInfo(arg: string | number | string[] | number[]): string | number | string[] | number[] {
  return arg;
}

console.log(getInfo('Word')); // string
console.log(getInfo(123));  // number
console.log(getInfo([1, 2]));  // number[]
console.log(getInfo(['C', 'T']));  // string[]
```
여기서 ``any`` 타입을 사용하지 않은 이유는, ``any``를 사용하면 어떤 타입이든 받을 수 있지만, 어떤 타입인지에 대한 정보는 **얻을 수 없기 때문에** 타입스크립트를 사용하지 않는 것과 같아져 사용하지 않았다.

# After Using Generic
```ts
function getInfo<T>(arg: T): T {
  return arg;
}

console.log(getInfo('Word')); // 굳이 <String>을 쓰지 않아도 어떤 타입인지 알고 있다.
console.log(getInfo(123)); // number
console.log(getInfo([1, 2])); // number[]
console.log(getInfo(['C', 'T'])); // string[]
```
확실히 제네릭을 사용하지 않을 때보다 코드가 간결해지고 유연해진다.
