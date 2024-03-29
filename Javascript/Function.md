# Function(함수)

function은 계속 반복해서 사용할 수 있는 코드 조각이다. 또한 function의 값은 function 안에서만 존재한다.

## __선언법__
---
```javascript
function 함수명(변수명){
};
```
기본적으로 function은 위와 같이 선언 할 수 있다.

```javascript
function sayhello(name, age) { // 여기서 name, age는 파라미터,
    console.log("Hello my name is " + name + " and my age is " + age + "."); // 여기서 name, age는 인자이다.
}
```
기본적인 function 코드를 활용해보면 이런 코드를 작성 할 수 있다.

## __사용법__
---
기본적으로 위에서 작성한 function을 사용하는 방법은 아래와 같다.
```javascript
sayhello("Minsu", 18);
```
실행결과는,  
![](https://cdn.discordapp.com/attachments/1019884911802454016/1082956263752749066/image.png)  
이렇게 된다.

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
![](https://cdn.discordapp.com/attachments/1019884911802454016/1082957931953258506/image.png)  
이렇게 나오는것을 알 수 있다.

위에서 function의 값은 function 안에만 존재한다고 했는데,  
return을 사용하면 function의 값을 __외부로 끌어와서 사용__ 할 수 있으며,  
function이 한번 return을 하면,  
function은 작동을 멈추고 결과 값을 return하고 __끝나버린다.__  
즉, function 안에선 return 다음에 __무슨 코드가 있든 작동을 하지 않는다는 소리다.__
