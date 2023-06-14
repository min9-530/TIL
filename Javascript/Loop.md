# 반복문
반복문은 특정 작업을 반복적으로 할 때 사용할 수 있는 구문이다.  

## for
for 문은 가장 기본적인 반복문으로, 특정 값에 변화를 주어가면서 정해진 조건이 만족된다면 계속 반복한다.  
```js
for (let i = 0; i < 10; i++) {
  console.log(i);
}
```

## while
while문은 특정 조건이 참이라면 계속해서 반복하는 반복문이다.  
for문은 특정 숫자를 가지고 숫자의 값을 비교하고, 증감해주면서 반복을 하지만, while문은 조건을 확인만 하면서 반복을 하기 때문에 조건문 내부에서 변화를 직접 주어야 한다.
```js
let i = 0;
while (i < 10) {
  console.log(i);
  i++;
}
```

## for...of
``for...of``문은 배열에 관한 반복문을 돌리기 위해서 만들어진 반복문이다.
```js
let numbers = [10, 20, 30, 40, 50];
for (let number of numbers) {
  console.log(number);
}
```

## for...in
객체를 위한 반복문이다.
```js
let obj = {
  fish: '물고기',
  bird: '새',
};

for (let i in obj) {
  // obj의 key가 i에 할당
  console.log(i);
}
```
