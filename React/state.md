# State

- state란 React 컴포넌트 내에서 지속적으로 변경이 일어나는 값을 관리하기 위해 사용된다.
- state는 여태까지 해왔던 것들과는 달리 state의 값이 변경되어 재 렌더링이 필요한 경우에 React가 자동으로 계산하여 변경된 부분을 렌더링 한다.


## State 사용법
---
```javascript
import { useState } from "react";

const App = () => {
    const [value, setValue] = useState(초기값);
    return ...
}
```

state는 위와 같이 사용할 수 있다.
- 하지만 State의 값을 변경하기 위해선 반드시 setState 함수를 사용해야 하며, state의 값을 임의로 변경해서는 안된다.

## State의 값을 직접 변경한다면
---
```javascript
import { useState } from 'react';
 
function Example() {
    const [count, setCount] = useState(0);
    return (
        <div>
            <p>버튼을 {count}번 눌렀습니다.</p>
            <button 
            onClick={() => {count = count + 1;}}>
            클릭
            </button> // 이렇게 하면 안 된다.
            
        </div>
    );
}
```
위의 코드는 state의 값을 직접 변경한 경우를 나타낸 것이다.
- State의 값을 직접 변경하게 되면 React는 컴포넌트를 다시 렌더링 할 타이밍을 알아차리지 못하게 되므로, 반드시 setState 함수를 사용해야 한다.