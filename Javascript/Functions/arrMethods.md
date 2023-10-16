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

console.log(array1.fill(0, 2, 4));
// [1, 2, 0, 0]
console.log(array1.fill(5, 1));
// [1, 5, 5, 5]
console.log(array1.fill(6));
// [6, 6, 6, 6]
```

## filter
> 주어진 조건을 만족하는 모든 요소를 모아 새로운 배열로 반환한다.

```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter((word) => word.length > 6);

console.log(result);
// ["exuberant", "destruction", "present"]
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

## findLast
> 배열을 **역순으로 순회하며** 주어진 조건을 만족하는 **첫 번째 요소의 값**을 반환한다. (없다면, undefined를 반환)

```js
const array1 = [5, 12, 50, 130, 44];

const found = array1.findLast((element) => element > 45);

console.log(found); // 130
```

## findLastIndex
> 배열을 **역순으로 순회하며** 주어진 조건을 만족하는 **첫 번째 요소의 인덱스**를 반환한다. (없다면, -1을 반환)

```js
const array1 = [5, 12, 50, 130, 44];

const isLargeNumber = (element) => element > 45;

console.log(array1.findLastIndex(isLargeNumber)); // 3
```

## flat
> 모든 하위 배열 요소를 지정한 깊이까지 재귀적으로 이어붙인 새로운 배열을 생성한다.

```js
const newArr = arr.flat([depth]);
// depth는 중첩 배열 구조를 평탄화할 때 사용할 깊이 값으로 기본값은 1이다.
// 반환 값은 하위 배열을 이어붙인 새로운 배열이다.
```

```js
const arr1 = [1, 2, [3, 4]];
console.log(arr1.flat());
// [1, 2, 3, 4]

const arr2 = [1, 2, [3, 4, [5, 6]]];
console.log(arr2.flat());
// [1, 2, 3, 4, [5, 6]]

const arr3 = [1, 2, [3, 4, [5, 6]]];
console.log(arr3.flat(2));
// [1, 2, 3, 4, 5, 6]

const arr4 = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];
console.log(arr4.flat(Infinity));
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

// 배열의 구멍도 제거 가능
const arr5 = [1, 2, , 4, 5];
console.log(arr5.flat());
// [1, 2, 3, 4]
```

## forEach
> 주어진 함수를 배열 요소 각각에 대해 실행한다.

```js
const array1 = ['a', 'b', 'c'];

array1.forEach((element) => console.log(element));
// "a"
// "b"
// "c"

// for문도 대체 가능
const items  = ["item1", "item2", "item3"];
const copy = [];

// 이전
for (let i = 0; i < items.length; i++) {
  copy.push(items[i]);
}

// 이후
items.forEach(function (item) {
  copy.push(item);
});
```

## from
> 유사 배열 객체나 반복 가능한 객체를 얕게 복사해 새로운 배열 객체를 만든다.

```js
console.log(Array.from('foo'));
// ["f", "o", "o"]

console.log(Array.from([1, 2, 3], (x) => x + x));
// [2, 4, 6]
```

## map
> 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환한다.

```js
const array1 = [1, 4, 9, 16];

const map1 = array1.map((x) => x * 2);

console.log(map1);
// [2, 8, 18, 32]
```

## reduce
> 배열의 각 요소에 대해 주어진 리듀서 (reducer) 함수를 실행하고, 하나의 결과값을 반환한다.

```js
const array1 = [1, 2, 3, 4];

const initialValue = 0;
const sumWithInitial = array1.reduce((acc, cur) => acc + cur, 0);

console.log(sumWithInitial);
// 10
```

## toString
> 지정된 배열 및 그 요소를 나타내는 문자열을 반환한다.

```js
const array1 = [1, 2, 'a', '1a'];

console.log(array1.toString());
// "1,2,a,1a"
```

## concat
> 두 개 이상의 배열을 병합하는 데 사용되며, 기존 배열이 아닌 새 배열을 반환한다.

```js
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// ["a", "b", "c", "d", "e", "f"]
```
