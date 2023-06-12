# QueryString
쿼리스트링은 사용자가 입력 데이터를 전달하는 방법중의 하나로, 요청하고자 하는 URL에 부가적인 정보를 포함하고 싶을 때 사용한다.    

## 형태
![image](https://github.com/min9-530/TIL/assets/104071568/947149e0-8461-4769-913f-c508f3f901c7)  
쿼리스트링은 이름 그대로 문자열 타입으로 key = value로 표현된다. 또한 URL의 일부로 쿼리스트링의 시작점은 "?"으로 표시된다.  

``https://www.example.com/products?sort=popular&direction=desc``
key=value의 개수에 제한은 없고 구분할 때는 "&"을 기입한다.

# useLocation
location 객체를 반환하며 사용자가 현재 보고있는 페이지의 정보를 지니고 있다.  

## location 객체의 속성값
+ pathname: 현재 주소의 경로
+ search: 맨 앞의 ? 문자를 포함한 쿼리스트링 값
+ hash: 주소의 # 문자열 뒤의 값
+ state: 페이지로 이동할 때 임의로 넣을 수 있는 상태 값
+ key: location 객체의 고유값, 초기에는 default이며 페이지가 변경될 때마다 고유의 값이 생성

## About.js
