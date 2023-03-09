# HTML in JS
자바스크립트는 HTML의 Element들을 변경하고 읽을 수 있다. 따라서, 오늘은 JS로 HTML의 Element들을 변경하거나 읽어오는 방법을 정리해 볼 것이다.


## __사용법__
JS로 HTML에서 Element들을 읽어오는 방법이다.

```javascript
const title = document.getElementById(id);
```
첫번째로, 위의 코드는 우리가 HTML에서 태그에 부여하는 ID에 해당하는 element를 가져오는 코드이다.  
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

---

```javascript
const title = document.getElementByClassName(ClassName);
```
두번째로 알아볼것은 위의 코드이다.  
위의 코드는 HTML 태그에 붙는 class명을 통해 element를 읽어오는데, 이것은 값을 하나만 가져오던 ``getElementById`` 와는 다르게 HTML의 Class 속에 있는 태그들을 가져오는 것이기 때문에 배열 상태로 가져온다.  
때문에 ``getElementById``에서 가능하던 Object를 수정하는 행위는 할 수 없다.

---

```javascript
const title = document.querySelector();
```
세번째로 알아볼 것은 위의 코드이다.  
위의 코드는 CSS selector 방식으로 검색할 수 있다. ``(ex.(h1:first-child))``와 같이 원하는 요소를 선택이 가능하다.

만약 요소를 특정하지 않고 선택자만 쓴다면, 

선택자의 내부에 있는 모든 요소를 가져오는데, 여기서 만약 ``title.innerText=""``를 사용해 업데이트를 하게 되면 기존에 존재하던 모든 요소는 사라지고 저 코드로 업데이트된 요소로 대체된다.