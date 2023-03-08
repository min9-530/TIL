# 함수

function은 계속 반복해서 사용할 수 있는 코드 조각이다. 또한 function의 값은function 안에서만 존재한다.

## 선언법
---
```javascript
function 함수명(변수명){
};
```
기본적으로 function은 위와 같이 선언 할 수 있다.

```javascript
function sayhello(name, age) {
    console.log("Hello my name is " + name + " and my age is " + age + ".");
}
```
기본적인 function 코드를 활용해보면 이런 코드를 작성 할 수 있다.

## 사용법
---
기본적으로 위에서 작성한 function을 사용하는 방법은 아래와 같다.
```javascript
sayhello("Minsu", 18);
```
실행결과는, 
![](https://cdn.discordapp.com/attachments/1019884911802454016/1082956263752749066/image.png) 이렇게 된다.

또, 위의 코드를 object와 함께 사용해보면,
```javascript
const player = {
    sayHello: function(nameOfperson){
    console.log("Hello " + name + " nice to meet you!");
    },
};
player.sayHello("Minsu");
```
이런 코드를 작성할 수 있는데, 사용해보면, 
![](https://cdn.discordapp.com/attachments/1019884911802454016/1082957931953258506/image.png) 이렇게 나오는것을 알 수 있다.