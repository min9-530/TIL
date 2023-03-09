# Event(이벤트)

이번에 알아볼 것은 JS에서 이벤트를 처리하는 방법이다.

## __사용법__

```javascript
const title = document.querySelector(".hello");

function handleClickevent(){
    alert("Click! ");
}

title.addEventListener("click", handleClickevent);
```
위의 코드에서, 처음보는것이 있을텐데, ``addEventListener``라는 것은 위의 ``title``에 EventListener를 추가시켜주는 것이다. EventListener는 말 그대로 event를 listen 해주는 것이다.   
또한, EventListener 다음에 있는 괄호의 의미를 궁금해할텐데, 
괄호에서 첫번째에 쓰여져있는 것이 JS에 무슨 event를 listen하고 싶은지 알려주는 것이다.  
그리고 두번째로 쓰여져있는 것은 지정된 event가 발생되었을 때 실행될 함수를 지정해준 것이다.

----
또한, ``console.dir(변수명);``를 입력하면 엄청 많은 property들을 콘솔에 출력해주는데, 여기서 property 이름 앞에 on이 붙어있다면, 그게 바로 event listener 이다.
## __TIP__
아래 링크는 listen 하고싶은 event를 찾는데 유용한 사이트이다.

https://developer.mozilla.org/ko/docs/Web/API/HTMLElement