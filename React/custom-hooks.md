# Custom Hooks
커스텀 훅은 개발자가 직접 만드는 hook이다. 반복되는 로직을 묶어 하나의 컴포넌트로 만드는 것처럼 반복되는 메서드를 하나로 묶어 사용한다.  
보통 Input과 Fetch를 관리할 때 자주 쓰인다.

## 사용 이유?
커스텀 훅은 리액트에서 컴포넌트를 만드는 과정을 생각하면 되는데, 
1. 코드, 로직이 간결해지고 가독성이 좋아진다.
2. 필요없는 반복을 줄이고 재사용성을 높인다.
3. 수정사항이 있을 시 커스텀 훅에서만 수정하면 되기 때문에 유지보수에 용이하다.

## 규칙?
리액트 내장훅과 마찬가지로 __커스텀 훅의 이름은 use로 시작해야된다.__
