# 객체

자바스크립트에서 object(객체)는 property(특성)을 가진 데이터를 저장해주며, 배열과 달리 {}(중괄호)를 사용한다.

## 선언법
---
```javascript
const player ={
    name: "MinSu",
    points: 10,
    fat: true,
};
```
자바스크립트에서의 객체는 위와 같이 선언한다.  
하지만 다른 언어들과 달리 자바스크립트는 객체 안에서 __=__ 를 사용하지 않고, 대신에 __:__ 를 사용한다.  
또한 한 개의 property를 작성하고 나면  콤마(,)를 사용해야 하는데,  
 왜냐면 다른 property가 하나 더 올 수 있기 때문이다.


 ## 사용법
 ---
 객체를 사용하는 방법은 배열과 비슷하면서도 다르다.

```javascript
console.log(player);
console.log(player.name);
```
위의 코드를 작성 후 실행해보면,

![](https://cdn.discordapp.com/attachments/1019884911802454016/1082937396087246848/image.png)  
보다시피 첫번째로 작성한 코드는 player 객체의 모든 property 값을 보여주고,  
두번째로 작성한 코드는 name이란 property의 데이터값을 보여준다.

다른 방법으로는
```javascript
console.log(player["name"]);
```
이런 방법도 있다.  
이 코드의 실행결과는 윗윗코드의 두번째 코드와 같다.

이번엔 객체 안의 property의 값을 수정하는 방법이다.

```javascript
console.log(player.name);
player.name = "Aron";
console.log(player.name);
```
위 코드를 실행해보면
![](https://cdn.discordapp.com/attachments/1019884911802454016/1082942216898621471/image.png) 
player.name의 값이 Minsu에서 Aron으로 바뀐것을 볼 수 있다.  
그런데 여기서 const는 수정할 수 없는데 name의 값이 수정된것을 궁금해 할 수 있는데,  이것이 가능한 이유는 const 자체의 값을 바꾸는게 아니라 객체 안의 무언가를 바꾸는 것이라 가능한 것이다.


또 우리는 property를 추가 할 수도 있다.
```javascript
player.lastName = "Kim";
console.log(player);
```
위 코드의 실행결과는  
![](https://cdn.discordapp.com/attachments/1019884911802454016/1082946416747487343/image.png) 이렇게 player 객체에 lastName 이라는 property가 추가되게 된다.