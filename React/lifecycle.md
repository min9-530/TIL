# LifeCycle
모든 리액트 컴포넌트에는 라이프사이클(수명 주기)이 존재하고,  
컴포넌트의 수명은 페이지에 렌더링되기 전인 준비 과정에서 시작하여 페이지에서 사라질 때 끝난다.

라이프사이클의 메서드의 종류는 총 9가지이다. __Will__ 접두사가 붙은 메서드는 어떤 작업을 작동하기 __전__에 실행하는 메서드이고,  
__Did__ 접두사가 붙은 메서드는 어떤 작업을 작동한 __후__에 실행되는 메서드이다.  

라이프사이클은 총 세 가지, 즉 __마운트, 업데이트, 언마운트__ 카테고리로 나눈다. 

# Mount
## DOM이 생성되고 웹 브라우저상에 나타나는 것
# 마운트가 호출하는 메서드
+ constructor: 컴포넌트를 새로 만들 때마다 호출되는 클래스 생성자 메서드
+ getDerivedStateFromProps: props에 있는 값을 state에 넣을 때 사용하는 메서드
+ render: 준비한 UI를 렌더링하는 메서드
+ componentDidMount: 컴포넌트가 웹 브라우저상에 나타난 후 호출하는 메서드

# Update
컴포넌트는 다음과 같이 총 네 가지 경우에 업데이트한다.
1. props가 바뀔 때
2. state가 바뀔 때
3. 부모 컴포넌트가 리렌더링될 때
4. this.forceUpdate로 강제로 렌더링을 트리거할 때

# 컴포넌트를 업데이트할 때 호출하는 메서드
+ getDerivedStateFormProps
  + 마운트 과정에서 호출되며 업데이트가 되기 전에도 호출되는 메서드이다.  
  props의 변화에 따라 state 값에도 변화를 주고 싶을 때 사용한다.
+ shouldComponentUpdate
  + 컴포넌트가 리렌더링을 해야 할지 말아야 할지 결정하는 메서드이다.  
  이 메서드에서는 true 혹은 false 값을 반환해야 하며, true를 반환할 시 다음 라이프사이클 메서드를 계속 실행하고, false를 반환하면 작업을 중지하며 컴포넌트가 리렌더링되지 않는다.
+ render
  + 컴포넌트를 리렌더링한다.
+ getSnapshotBeforeUpdate
  + 컴포넌트 변화를 DOM에 반영하기 바로 직전에 호출하는 메서드이다. 
+ componentDidUpdate
  + 컴포넌트의 업데이트 작업이 끝난 후 호출하는 메서드이다.

# UnMount 
## 마운트의 반대 과정, 즉 컴포넌트를 DOM에서 제거하는 것
# 언마운트할 때 호출하는 메서드
+ componentWillUnmount
  + 컴포넌트가 웹 브라우저상에서 사라지기 전에 호출하는 메서드