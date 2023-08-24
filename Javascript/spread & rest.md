# Spread
spread란 ES6에서 도입된 연산자로, 이 단어가 가진 뜻 그대로 객체나 배열을 펼칠 수 있다.


예시로 다음과 같은 객체들이 있다고 가정해보자.
```js
const slime = {
  name: "슬라임",
};

const cuteSlime = {
  name: "슬라임",
  attribute: "cute",
};

const PurpleCuteSlime = {
  name: "슬라임",
  attribute: "cute",
  color: "purple",
};

console.log(slime);
console.log(cuteSlime);
console.log(PurpleCuteSlime);

```
![image](https://github.com/min9-530/TIL/assets/104071568/29a295fe-9e39-424a-8f99-5be6c00e9a07)

위에 코드에선 먼저 slime 이란 객체를 선언하고 cuteSlime을 만들었는데,  
기존에 선언한 smile을 건드리지 않고 새로운 객체를 만들어서 slime이 가지고 있는 값을 그대로 사용하였다.  

그 다음으로 purpleCuteSlime 이라는 객체를 만들었는데,  
cuteSlime이 가지고 있는 속성을 그대로 사용하면서 추가적으로 color가 추가되었다.  

이렇게 기존의 것을 건드리지 않고 새로운 객체를 만들 때, 번거롭게 위의 코드처럼 하나하나씩 쓰는 것보다 spread를 사용하면 코드의 길이를 줄일 수 있다.

## 예시
```js
const animals = ["개", "고양이", "참새"];
const anotherAnimals = [...animals, "비둘기", "거북이"];
console.log(animals);
console.log(anotherAnimals);
```
![image](https://github.com/min9-530/TIL/assets/104071568/a3dc0ba1-22c9-4fcc-a5e4-ef691874712a)

이처럼 spread 연산자를 사용하면 기존의 animals 배열은 건들이지 않으면서,  
새로운 anotherAnimals 배열에 animals 가 가지고 있는 내용을 모두 집어넣고, '비둘기' 라는 항목을 추가적으로 넣었다.

# Rest
rest는 spread와 같이 ES6에서 도입된 연산자로, spread와 비슷하게 생겼지만 역할은 매우 다르다.  

rest는 객체, 배열, 그리고 함수의 파라미터에서 사용이 가능하다.

## 객체에서의 rest
```js
const PurpleCuteSlime = {
  name: "슬라임",
  attribute: "cute",
  color: "purple",
};

const { color, ...rest } = PurpleCuteSlime;
console.log(color);
console.log(PurpleCuteSlime);
```
![image](https://github.com/min9-530/TIL/assets/104071568/4a3bac68-c202-4b16-8dc2-049dd6c23f6b)

rest 안에 name 값을 제외한 값이 들어있다.  
rest는 객체와 배열에서 사용 할 때는 이렇게 비구조화 할당 문법과 함께 사용된다.  
주로 사용 할때는 위와 같은 rest라는 키워드를 사용하게 되는데, 추출한 값의 이름이 꼭 rest일 필요는 없다.  
```js
const purpleCuteSlime = {
  name: '슬라임',
  attribute: 'cute',
  color: 'purple'
};

const { color, ...cuteSlime } = purpleCuteSlime;
console.log(color);
console.log(cuteSlime);

const { attribute, ...slime } = cuteSlime;
console.log(attribute);
console.log(slime);
```
![image](https://github.com/min9-530/TIL/assets/104071568/da9d5d74-abab-459c-8385-89028a624286)

이렇게 여러번 사용 할수도 있다.

## 배열에서의 rest
다음으로 배열에서의 사용 예시를 알아보자.
```js
const numbers = [0, 1, 2, 3, 4, 5];

const [one, ...rest] = numbers;

console.log(two);
console.log(rest);

```
![image](https://github.com/min9-530/TIL/assets/104071568/652a2a00-2683-443c-a1b6-e019299e68df)

이렇게 배열 비구조화 할당을 통해 원하는 값을 밖으로 꺼내고 나머지 값을 rest 안에 넣었다.


## 함수 파라미터에서의 rest
rest를 함수 파라미터에서도 사용 할 수 있다.  
```js
function sum(a, b, c, d, e, f, g) {
  let sum = 0;
  if (a) sum += a;
  if (b) sum += b;
  if (c) sum += c;
  if (d) sum += d;
  if (e) sum += e;
  if (f) sum += f;
  if (g) sum += g;
  return sum;
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result);
```
위에서의 sum 함수는 7개의 파라미터를 받아오는데, 아래에서 사용 할때에는 6개만 받아온다.  
이러면 g의 값이 undefined가 되기 때문에 sum 에 더하는 과정에서 undefined를 하게 되면 NaN이 되어버린다.  

이렇게 함수의 파라미터가 몇개가 될 지 모르는 상황에서 rest 파라미터를 사용하면 매우 유용하다.
```js
function sum(...rest) {
  return rest;
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result);
```

![image](https://github.com/min9-530/TIL/assets/104071568/6ab66334-2aad-45d7-a796-9a1a057f07ac)  

여기서 result가 가르키고 있는 것은 함수에서 받아온 파라미터들로 이루어진 배열이다.  

```js
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); // 21
```
이렇게 위에서 파라미터들이 들어있는 배열을 받았으니 모두 더해주면 된다.
