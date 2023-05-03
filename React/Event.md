# Event

리액트에서 이벤트 시스템은 웹 브라우저의 HTML 이벤트와 인터페이스가 동일하기 때문에 사용법이 꽤 비슷하다.

# 주의 사항

## 1. 이벤트 이름은 카멜 표기법으로 작헝해야 한다.
## 2. 이벤트에 실행할 자바스크립트 코드를 전달하는 것이 아니라, 함수 형태의 값을 전달해야 한다.
## 3. DOM 요소에만 이벤트를 설정할 수 있다.

# 이벤트 종류

리액트에서 지원하는 이벤트의 종류는 다음과 같다.  
``Clipboard``, ``Touch``, ``Composistion``, ``UI``,  
``Keyboard``, ``Wheel``, ``Focus``, ``Media``,  
``Form``, ``Image``, ``Mouse``, ``Animation``,  
``Selection``, ``Transition`` 등이 있다.

# 이벤트 설정

```javascript
function EventPractice() {
    return(
        <div>
            <h1>이벤트 연습</h1>
            <input
            type="text"
            name="message"
            placeholder="아무거나 입력해 보세요"
            onChange={
                (e) => {
                    console.log(e.target.value);
                }
            }
            />
        </div>
    );
}

export default EventPractice;
```
대충 이런 형식으로 작성하면 된다.
