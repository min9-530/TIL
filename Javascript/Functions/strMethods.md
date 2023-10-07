# 자바스크립트 문자열 관련 메소드 총정리
 
## length
> 문자열 길이 반환
```js
let hi = "Hello, My Name is Minsu!";
console.log(hi.length); // 24
```

## slice, substring
> 시작 인덱스부터 끝 인덱스의 -1자리까지 출력한다. 전달된 값이 음수라면 인덱스를 뒤에서부터 출력한다.
```js
slice(start_idx, end_idx)
substring(start_idx, end_idx)
```

```js
let ex = "Hello! My Name is Minsu";

// 2번째 인덱스부터 끝까지 출력
console.log(ex.slice(2));  // llo! My Name is Minsu

// 3번째 인덱스부터 8번째 인덱스까지 출력
console.log(ex.slice(3, 9));  // lo! My  
console.log(ex.substring(3, 9));  // lo! My

// 2번째 인덱스부터 뒤에서 3번째 인덱스까지 출력
console.log(ex.slice(2, -3));  // llo! My Name is Mi
```

## substr
> 시작 인덱스부터 n의 길이만큼 출력한다.

```js
substr(start_idx, n)
```

```js
// 3번째 인덱스부터 9글자가 될 때까지 출력
let ex = "Hello! My Name is Minsu";

console.log(ex.substr(3, 9)); // lo! My Na
```

## toUpperCase, toLowerCase
> 대/소문자로 치환시킨다.

```js
let ex = "Hello! My Name is Minsu";

console.log(ex.toUpperCase()); // HELLO! MY NAME IS MINSU
console.log(ex.toLowerCase()); // hello! my name is minsu
```

## includes
> 해당 문자열이 포함되었는지 여부를 반환한다.

```js
let fruits = "사과, 배, 딸기, 귤, 오렌지";

console.log(fruits.includes("딸기")); // true
console.log(fruits.includes("수박")); // false
```
