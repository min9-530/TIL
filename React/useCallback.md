# useCallback
useCallback은 useMemo와 상당히 비슷한 함수이다.  
주로 렌더링 성능을 최적화해야 하는 상황에서 사용하는데, 이 Hook을 사용하면 만들어 놨던 함수를 재사용할 수 있다.

# 사용법
```javascript
import { useCallback, useMemo, useState } from "react";

const getAverage = (numbers) => {
  console.log("평균값 계산중..");
  if (numbers.length === 0) return 0;
  const sum = numbers.reduce((a, b) => a + b);
  return sum / numbers.length;
};

const Average = () => {
  const [list, setList] = useState([]);
  const [number, setNumber] = useState("");

  const onChange = useCallback((e) => {
    setNumber(e.target.value);
  }, []); // 컴포넌트가 처음 렌더링될 때만 함수 생성
  const onInsert = useCallback(() => {
    const nextList = list.concat(parseInt(number));
    setList(nextList);
    setNumber("");
  }, [number, list]); // number 혹은 list가 바뀌었을 때만 함수 생성

  const avg = useMemo(() => getAverage(list), [list]);

  return (
    <div>
      <input value={number} onChange={onChange} />
      <button onClick={onInsert}>등록</button>
      <ul>
        {list.map((value, index) => (
          <li key={index}>{value}</li>
        ))}
      </ul>
      <div>
        <b>평균값</b> {avg}
      </div>
    </div>
  );
};

export default Average;
```
``useCallback``의 첫 번째 파라미터에는 생성하고 싶은 함수를 넣고, 두 번째 파라미터에는 배열을 넣으면 된다.  
이 배열에는 어떤 값이 바뀌었을 때 함수를 새로 생성해야 하는지 명시해야 한다.  
만약, 위의 ``onChange``처럼 비어 있는 배열을 넣게 되면 컴포넌트가 렌더링될 때 만들었던 함수를 계속해서 재사용하게 되며 onInsert처럼 배열 안에 number와 list같이 값을 넣어주게 되면 인풋의 내용이 바뀌거나 새로운 항목이 추가될 때 새로 만들어진 함수를 사용하게 된다.  

함수 내부에서 상태 값에 의존해야 할 때는 그 값을 반드시 두 번째 파라미터 안에 포함시켜 주어야 한다.  
예를 들어, onChange와 같은 경우 기존의 값을 조회하지 않고 바로 설정만 하기 때문에 배열이 비어 있어도 상관없지만, onInsert와 같은 경우는 기존의 number와 list를 조회해서 nextList를 생성하기 때문에 배열 안에 number와 list와 같은 값을 넣어 주어야 한다.
