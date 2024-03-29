# 실행 컨텍스트
실핼 컨텍스트란 자바스크립트 코드가 실행되는 환경이다.  
모든 자바스크립트 코드는 실행 컨텍스트 내부에서 실행된다고 생각하면 된다.  

즉 함수가 실행되면 함수 실행에 해당하는 **실행 컨텍스트가 생성**되고, 자바스크립트 엔진에 있는 콜 스택에 쌓이게 된다.

콜 스택은 **후입선출(LIFO)의 구조**로 가장 위에 쌓여있는 컨텍스트와 관련있는 코드를 실행하며, **전체적인 코드의 환경과 순서를 보장**하게 된다.  

또한 실행 컨텍스트는 식별자(변수, 함수, 클래스 등의 이름)를 등록하고 관리하는 스코프와 코드 실행 순서 관리를 구현한 내부 매커니즘으로, 자바스크립트의 **핵심 원리**라고 할 수 있다.

# 종류
실행 컨텍스트에는 3가지의 종류가 있다,
+ 전역 실행 컨텍스트
  + 실행 컨텍스트의 기본이자 기초로서, 모든 스크립트 코드는 전역 실행 컨텍스트 안에서 실행되며, 프로그램에 단 한 개만 존재한다.
  + 함수 밖의 코드는 전역 실행 컨텍스트에 있다.
  + 브라우저의 경우 ``window`` 객체, Node.js의 경우엔 ``global`` 객체가 전역 실행 컨텍스트가 된다. 
+ 함수 실행 컨텍스트
  + 함수가 실행될 때마다 새로 만들어지는 실행 컨텍스트이다.
  + 각 함수는 고유의 실행 컨텍스트를 가지며, 함수가 실행되거나 call 될 때에만 생성된다.
+ eval 실행 컨텍스트
  + eval() 함수에 의해 생성되는 실행 컨텍스트이다.
  + 하지만 eval() 함수는 속도와 보안에 관련해서 문제가 있기 때문에 사용되지 않는다.

