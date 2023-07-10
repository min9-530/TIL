# Context API
> context를 이용하면 단계마다 일일이 props를 넘겨주지 않고 단 한번으로도 컴포넌트 트리 전체에 데이터를 제공할 수 있다.  

Context API란 리액트에서 제공하는 built-in API로 상태 관리를 외부 라이브러리 없이도 할 수 있게 해줄 뿐더러, 리액트에서 이것을 위해 훅스도 제공해준다.  

상태 관리 라이브러리는 대표적으로 리덕스, MobX, recoil.js 등이 있다.  

# Context 만들기
> contexts/color.js
```js
import { createContext } from "react";

const ColorContext = createContext({ color: "black" });

export default ColorContext;
```

# Consumer 사용하기
> components/ColorBox.js
```js
import ColorContext from "../contexts/color";

const ColorBox = () => {
  return (
    <ColorContext.Consumer>
      {(value) => (
        <div
          style={{
            width: "64px",
            height: "64px",
            background: value.color,
          }}
        />
      )}
    </ColorContext.Consumer>
  );
};

export default ColorBox;
```
이번엔 색상을 props로 받아오는 것이 아니라 ColorContext 안에 들어있는 Consumer라는 컴포넌트를 사용하여 색상을 불러왔다.  
Consumer 사이에 중괄호를 열어서 그 안에 함수를 넣어 주었는데 이러한 패턴을 Function as a child, 혹은 Render Props라고 한다. 

# Provider
> App.js
```js
import "./App.css";
import ColorContext from "./contexts/color";
import ColorBox from "./components/ColorBox";

function App() {
  return (
    <ColorContext.Provider value={{ color: "red" }}>
      <div>
        <ColorBox />
      </div>
    </ColorContext.Provider>
  );
}

export default App;
```
provider를 사용하면 Context의 value를 변경할 수 있다.  
기존에 createContext 함수를 사용할 때는 매개변수로 Context의 기본값을 넣어 주었는데, 이 기본값은 Provider를 사용하지 않았을 때만 사용되며, Provider는 사용했는데 value를 명시하지 않았다면, 기본값을 사용하지 않기 때문에 오류가 발생한다.
