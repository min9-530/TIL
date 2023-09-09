# 자바스크립트 배열 관련 메소드 총정리

## sort
> 배열을 오름차순 내림차순으로 정렬한다.
```js
const arr = [5, 3, 2, 4, 6, 1];
const rest;

res = arr.sort((a, b) => a - b);
console.log(res);
// [1, 2, 3, 4, 5, 6]

res = arr.sort((a, b) => b - a);
console.log(res);
// [6, 5, 4, 3, 2, 1]
```

## join
> 배열을 문자열로 변환한다.

```js
배열.join(); // 구분자를 넣지 않으면 컴마가 포함되어 문자열로 합쳐진다.
배열.join('.'); // 구분자를 넣어주면 아이템 사이에 구분자를 넣어서 문장으로 합쳐진다.
```

```js
const fruits = ['apple', 'banana', 'orange'];
let res;

res = fruits.join();
console.log(res);
// 'apple,banana,orange'

res = fruits.join(' ');
console.log(res);
// 'apple banana orange'
```

## split
> 문자열을 배열로 변환한다.

```js
문자열.split(); // 구분자를 넣지 않으면 문자열 한 덩어리가 배열의 아이템 1개로 들어간다.
문자열.split('.'); // 구분자를 기준으로 쪼개져서 배열로 변환된다.
```

```js
const sayHello = '안녕하세요, 저는, 김민수, 입니다.';
const arr = sayHello.split(',');

console.log(arr);
// ["안녕하세요", " 저는", " 김민수", " 입니다."]
```

## reverse
> 배열의 아이템 순서를 뒤집는다.
```js
배열.reverse();
```

```js
const array = [1, 2, 3, 4, 5];
const res = array.reverse();

console.log(res);
// [5, 4, 3, 2, 1]

console.log(array);
// [5, 4, 3, 2, 1]
```

## splice
> 인덱스로 배열의 아이템을 삭제한다.
>
> 인덱스로 배열의 아이템을 여러개 삭제한다.  
>
> 인덱스로 배열의 아이템을 삭제하고 해당 인덱스에 새로운 아이템을 추가한다.
>
> ❗단, 반환값은 때어낸(삭제한요소) 배열이다.

```js
배열.splice(인덱스, 삭제할갯수, 추가할 아이템...);
```

```js
const array = [1, 2, 3, 4, 5];
let res = array.splice(1, 3);

console.log(res);
// [2, 3, 4]
console.log(array);
// [1, 5]
```

## slice
> 배열의 특정한 부분을 리턴한다.

```js
배열.slice(시작인덱스, 끝 인덱스); // 끝 인덱스의 앞까지만 표현한다.
```

```js
const array = [1, 2, 3, 4, 5];
let res;

res = array.slice(2) // 2부터 쭉
console.log(res);
// [3, 4, 5]

res = array.slice(1, 3);
console.log(res);
// [2, 3]
```

## fill
> 배열의 시작 인덱스부터 끝 인덱스의 이전까지 정적인 값 하나로 채운다.

```js
배열.fill(배열을 채울 값[, 시작 인덱스[, 끝 인덱스]]);
```

```js
cosnt array1 = [1, 2, 3, 4];

console.log(array1.fill(0, 2, 4)); // [1, 2, 0, 0]
console.log(array1.fill(5, 1)); // [1, 5, 5, 5]
console.log(array1.fill(6)); // [6, 6, 6, 6]
```

## filter
> 주어진 조건을 만족하는 모든 요소를 모아 새로운 배열로 반환한다.

```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter((word) => word.length > 6);

console.log(result); // ["exuberant", "destruction", "present"]
```

## find
> 주어진 조건을 만족하는 **첫 번째 요소의 값**을 반환한다. (없다면, undefined를 반환)

```js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find((element) => element > 10);

console.log(found); // 12
```

## findIndex
> 주어진 조건을 만족하는 배열의 첫 번째 요소에 대한 인덱스를 반환한다. (없다면, -1을 반환)

```js
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber)); // 3
```
