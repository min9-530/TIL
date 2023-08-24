# ESLint?
``ESLint``란 **ES** 와 **Lint**를 합친 것이다.  
ES는 Ecma Script의 준말로, Ecma(European Computer Manufacturers Association)라는 기구에서 만든 Script로, 표준 Javascript를 의미한다.  
그리고 Lint는 에러가 있는 코드에 표시를 달아놓는 것을 의미한다.  

따라서 ``ESLint``는 자바스크립트 문법에서 에러를 표시해주는 도구이다.  
우리는 에러로서, 정말 문제가 되는 부분만을, 아니면 전반적인 코딩스타일까지 지정할 수도 있다.  

이런 기능으로 인해 많은 사람들과 협업을 진행핳때 ESLint는 매우 유용하다.  
에러와 코딩 스타일을 하나로 잡아주기 때문에 한 사람이 코딩한 것처럼 되기 때문이다.

# 명령어
설치  
```npm install eslint --save-dev```  
세팅  
```npx eslint --init```  
검사하기  
```npx eslint 검사하고 싶은 파일명.js```  
검사하고 자동 교정  
```npx eslint 검사하고 싶은 파일명.js --fix```  
``ESLint``를 사용해 파일을 검사하면 터미널 창에 오류를 알려준다.  
그리고 자동 교정 명령어를 사용하면 자동으로 교정이 된다. 
