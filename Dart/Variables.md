# Variables
다트의 변수형에 대해 알아보자.


# 선언법
다트에선 변수를 var 또는 명시적 타입을 사용해 만들 수 있다.

## var
```dart
void main() {
  var name = 'minsu';
  name = 'aron';

  // name = 2403;
  // error: 변수 타입 변경 불가.

  // var name = 'unrin';
  // error: 재선언 불가
}
```
한번 선언하면 그 선언타입으로 고정되며 다른 타입으로 변경할 수 없다.

## explicit
```dart
void main() {
  String name = 'minsu';
}
```
명시적 타입으로 선언할 수 있다.

보통 함수나 메소드 내부에 **지역변수**를 선언할 때는 var를 사용하고  
class에서 **변수**나 **프로퍼티**를 선언할 때는 명시적 타입을 선언한다.  

사실 var를 사용하는것이 dart 스타일가이드의 권장 방식이다.

## dynamic
```dart
void main() {
  var name;
  name = 12;
  name = 'minsu';
  name = true;

  // or

  dynamic name2;
  name2 = 12;
  name2 = 'minsu';
  name2 = true;
}
```
dart는 여러 타입을 가질 수 있는 **dynamic** 타입을 지원한다.  
변수를 선언할 때 아무런 값을 지정하지 않거나, dynamic으로 선언하면 이 타입을 가지게 된다.  

dynamic 타입은 대표적으로 타입을 알기 힘들 때 사용된다. 예를 들어 json을 작업할 때 같은 경우이다.  
하지만 dynamic 타입은 다앙한 타입을 가질 수 있기 때문에 **정말 필요할 때만** 사용해야 한다.
