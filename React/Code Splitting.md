# Code Splitting
코드 스플리팅이란 파일을 분리하는 작업을 뜻한다.
더 나은 사용자 경험을 위해 코드를 비동기적으로 로딩하는 방법이다.

예를 들어 페이지가 `/main`, `/post`, `/search` 이렇게 세 가지 페이지로 이루어진 `SPA`를 개발한다고 하면 
`/main`으로 들어가는 동안 `/post`와 `/search` 페이지 정보는 사용자에게 필요하지 않는데, 이러한 파일들을 분리하여 지금 사용자에게 필요한 파일만 불러와서 로딩 속도와 트래픽을 줄여 사용자 경험을 개선하는 것이다.  
지금 당장 필요한 코드가 아니면 따로 분리시켜서, 나중에 필요할 때 불러와서 사용할 수 있다.
