# 배열

자바스크립트에서 배열은 다른 언어와 다를 게 없다.
 ## 선언법
 ---- 
```javascript
const week = ["mon", "tue", "wed", "thu", "fri", "sat", "sun"];
```
위의 코드는 자바스크립트에서 배열을 선언하는 방법이다.


## 사용법
---
```javascript
console.log(week[4])
```

배열을 사용하는 방법은 다른 언어들과 다를 것 없이 위와 같이 쓸 수 있다. 저 코드의 실행 결과는 
![](https://media.discordapp.net/attachments/1019884911802454016/1082918476496240680/image.png?width=176&height=65)  
이렇게 나오게 되는데, 배열은 0부터 값이 할당되기 때문이다.

또, push라는 것은 배열에 값을 추가해 주는데,
```javascript
week.push(123);
```
위의 코드를 작성한 후 실행해보면, 
![](https://cdn.discordapp.com/attachments/1019884911802454016/1082919704361975849/image.png)
이렇게 배열에 123이 추가된것을 볼 수 있다. 