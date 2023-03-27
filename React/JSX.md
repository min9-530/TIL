# JSX

- JSX(JavaScript XML)는 Javascript에 XML을 추가하여 확장한 문법이다.

- JSX는 React로 프로젝트를 개발할 때 사용되므로 공식적인 자바스크립트 문법은 아니다.

- 브라우저에서 실행되기 전에 번들링되는 과정에서 바벨을 사용하여 일반 자바스크립트 형태의 코드로 변환된다.

## Babel
---
```javascript
// JSX
const lable = (
    <h1 id = "lable">
    Hello World!
    </h1>
);

// Bable
import { jsx as _jsx } from "react/jsx-runtime";
const lable = /*#__PURE__*/_jsx("h1", {
  id: "lable",
  children: "Hello World!"
});
```
JSX는 Javascript만 사용한 코드보다 편리하다.
또한 HTML을 작성하는 것과 비슷하기 때문에 가독성과 편리함 때문에 JSX를 사용한다.

## JSX_part.1
---
```javascript
<!DOCTYPE html>
<html lang="en">

<body>
    <div id="root"></div>
</body>
<script src="https://unpkg.com/react@16.7.0/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@16.7.0/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
    const root = document.getElementById("root");
        const Title = (<h3 id = "title" onMouseEnter = {() => console.log("mouse enter")}>
        Hello i'm a title
        </h3>
        );  
/*         const h3 = React.createElement(
        "h3",       // HTML Tag
        {           // Props in Object
            id: "title",
            onMouseEnter: () => console.log("mouse enter"),
        }, 
        "Hello I'm a title" // content
    ); */
    const Button <button style = {{
                backgroundColor: "tomato",
            }}
            onClick = {() => console.log("im clicked")}
            >
            Click me
            </button>
/*         const btn = React.createElement(
        "button",
        {
            onClick: () =>  console.log("im clicked"),
            style: {
                backgroundColor: "tomato",
            },
        },
        "Click me"
    );  */
    const container = React.createElement("div", null, [Title, Button]);
    ReactDOM.render(Container, root);
</script>

</html>
```

## JSX_part.2 (함수, 컴포넌트)
---
```javascript
    <!DOCTYPE html>
<html lang="en">

<body>
    <div id="root"></div>
</body>
<script src="https://unpkg.com/react@16.7.0/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@16.7.0/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
    const root = document.getElementById("root");
    const Title = () => (
        <h3 id = "title" 
    onMouseEnter = {() => console.log("mouse enter")}>
    Hello I'm a title
    </h3>
    );
    const Button = () => (
        <button style = {{
        backgroundColor: "tomato",
    }} 
    onClick = {() => console.log("im clicked")}>
    Click me
    </button>
    );
    const Container = 
        <div>
            <Title />
            <Button />
        </div>
    ReactDOM.render(Container, root);
</script>

</html>
```

JSX에선 위의 Title과 Button같은 컴포넌트나 함수를 렌더링할때, HTML 태그처럼 사용해야 하며, 컴포넌트의 첫 글자는 반드시 대문자여야 한다.  
왜냐하면 만약 소문자로 적는다면 React와 JSX는 HTML 태그로 인식하기 때문이다.