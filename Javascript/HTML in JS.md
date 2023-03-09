# HTML in JS
자바스크립트는 HTML의 Element들을 변경하고 읽을 수 있다. 따라서, 오늘은 JS로 HTML의 Element들을 변경하거나 읽어오는 방법을 정리해 볼 것이다.


## __사용법__
첫번째로 HTML에서 Element들을 읽어오는 방법이다.

```javascript
const title = document.getElementById(id);
```
위의 코드는 우리가 HTML에서 태그에 부여하는 ID에 해당하는 element를 불러오는 코드이다.
또한, 
```javascript
console.log();
```
가 아닌 
```javascript
console.dir();
```
을 사용하면 태그 하나에서 가져올 수 있는 수많은 HTML의 object들을 볼 수 있다.

그리고 이 object들을 JS에서 변경 할 수 있다는 것이다.