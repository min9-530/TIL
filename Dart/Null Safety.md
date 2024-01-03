# null safety
null safety란 개발자가 null값을 참조할 수 없도록 하는 것이다.  
기본적으로 모든 변수는 non-nullable(null이 될 수 없음)이다.

```dart
bool isEmpty(String string) => string.length == 0;
void main() {
  isEmpty(null)
}
```
위의 코드를 실행하면 NoSuchMethodError가 발생한다.  
왜냐하면 String을 보내야 할 곳에 null 값을 보냈기 때문이다.  
또한 null에는 length라는 속성이 없기 때문이기도 하다.

이러한 에러는 컴파일러에서 잡을 수 있는 에러가 아니다.
하지만 이러한 에러때문에 null을 삭제하기엔 null 값은 매우 유용하다.  

이런 경우에는 dart에서는 변수가 null이 될 수 있음을 명확히 표시해야 한다.  

```dart
void main() {
  String name = 'minsu';
  name = null;
}
```
이 코드는 에러가 난다. name이 null값을 참조할 수 있다고 알려주지 않고 null값을 참고하기 때문이다.

```dart
void main() {
  String? name = 'minsu';
  name = null;
}
```
이 코드는 에러가 나지 않는다.  
`?`를 변수에 붙임으로써 이 변수에서는 null 값이 참조될 수 있음을 알려주는 것이다.  
만약 `?`를 붙인 변수는 이 변수가 null인지 아닌지 확인해야 한다.

```dart
void main() {
  String? name = 'minsu';
  name = null;
  if(name != null) {
    name.isNotEmpty;
}

  // or

  String? name2 = 'minsu2';
  name2 = null;
  name2?.isNotEmpty;
}
```
