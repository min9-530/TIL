# useEffect
useEffect는 리액트 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook이다.  
클래스형 컴포넌트의 componentDidMount와 componentDidUodate를 합친 형태로 보아도 무방하다.
# 사용법
## 기본 사용법
```javascript
useEffect(() => {
  수행할 코드
}, [의존값]);
```

useEffect는 의존값을 설정하지 않는다면 특정 작업이 항상 실행되고, 의존값을 설정한다면 의존값이 바뀔 때만 특정 작업이 실행된다.

# side effect
side effect 란 React 컴포넌트가 렌더링 된 후 비동기적으로 처리해야 하는 작업들을 말한다.  
예를 들어, API를 호출하는 경우 데이터를 비동기적으로 가져와야 하는데, 만약 그렇지 않다면 데이터를 가져오는 시간동안 렌더링이 지연될 수도 있기 때문이다.

# 클래스 컴포넌트에서의 side effect
side effect를 수행하는 시점은 리액트가 DOM을 업데이트 하고 난 이후이다. 때문에 클래스 컴포넌트에서 side effect를 수행하려면 ``componentDidMount``, ``componentDidUpdate`` 안에 두면 된다.  

## 클래스 방식에서 side effect를 수행하는 방법
```javascript
import React from "react";

class Hello extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: "Mary",
      surname: "Poppins",
    };
    this.handleNameChange = this.handleNameChange.bind(this);
    this.handleSurnameChange = this.handleSurnameChange.bind(this);
  }

  // side effect
  componentDidMount() {
    document.title = this.state.name + " " + this.state.surname;
  }

  componentDidUpdate() {
    document.title = this.state.name + " " + this.state.surname;
  }

  handleNameChange(e) {
    this.setState({
      name: e.target.value,
    });
  }

  handleSurnameChange(e) {
    this.setState({
      name: e.target.value,
    });
  }

  render() {
    return (
      <section>
        <div>
          <label>Name : </label>
          <input value={this.state.name} onChange={this.handleNameChange} />
        </div>
        <div>
          <label>Suename : </label>
          <input
            value={this.this.state.surname}
            onChange={this.handleSurnameChange}
          />
        </div>
      </section>
    );
  }
}

export default Hello;

```

# 함수 방식에서 side effect를 수행하는 방법
```javascript
import { useEffect, useState } from "react";

function Hello2() {
  const [name, setName] = useState("Mary");
  const [surname, setSurname] = useState("Poppins");

  useEffect(() => {
    document.title = name + " " + surname;
  });

  const handleNameChange = (e) => {
    setName(e.target.value);
  };

  const handleSurnameChange = (e) => {
    setSurname(e.target.value);
  };

  return (
    <section>
      <div>
        <label>Name : </label>
        <input value={name} onChange={handleNameChange} />
      </div>
      <div>
        <label>Surname : </label>
        <input value={surname} onChange={handleSurnameChange} />
      </div>
    </section>
  );
}

export default Hello2;

```
``useEffect``의 첫번째 인자로 오는 함수(effect)를 React는 기억하는데 DOM을 업데이트 하고 난 후에 이 effect가 실행된다.  

기본적으로 첫 렌더링과 그 이후의 모든 업데이트에 대해 effect를 수행하게 되는데, 이는 클래스 방식에서 사용한 ``componentDidMount``, ``componentDidUpdate``를 합쳐놓은 것과 같다.
