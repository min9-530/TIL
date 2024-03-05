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

## final
```dart
void main() {
  final name = 'minsu';
  name = '2403'; // 수정 불가

  final String name = 'minsu';
  name = '2403'; // 수정 불가
}
```
var 대신 final로 변수를 만들게 되면 이 변수는 수정할 수 없게 된다. (딱 한 번만 설정될 수 있다.) JS나 TS의 const와 비슷다.

## late
```dart
void main() {
  late final String name;
  name = 'minsu';
}
```
late는 초기 데이터 없이 변수를 선언할 수 있게 해준다. 즉, 선언과 초기화를 다른 시점에 할 수 있기 때문에 이를 지연 초기화라고 한다. 또한, late를 사용한 변수를 초기화 하기 전에 접근하려고 한다면 dart에서 late 변수는 값을 초기화 하기 전에는 접근하지 않아야 한다는 것을 알려준다. 이로 인해 [null safety](https://github.com/min9-530/TIL/blob/main/Dart/Null%20Safety.md)가 보장된다.

## const
```dart
void main() {
  const name = "minsu"; // 컴파일 시점에 바뀌지 않는 값
  final username = fetchAPI(); // 컴파일 시점에 바뀌는 값
}
```
dart의 const는 JS나 TS와 다르다. 여기서 const는 compile-time constant(컴파일 시간에 초기화 값을 알 수 있는 상)를 만들어준다.  
또한 const는 컴파일할 때 알고 있는 값을 사용해야 한다.  
만약 어떤 값인지 모르고, 그 값이 API 로부터 오거나 사용자가 화면에서 입력해야 하는 값이라면 final이나 var를 사용해야 한다.
