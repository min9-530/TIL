# Variables
다트의 변수형에 대해 알아보자.


# 선언법
```dart
void main() {
  var name = 'minsu';
}
```

```dart
void main() {
  String name = 'minsu';
}
```

다트에서 변수를 선언할땐 **var**를 사용하거나 **String, int**와 같이 명시적으로 변수의 타입을 지정해줄 수 있다.  
여기서 **var**는 함수나 메소드 내에 지역 변수를 선언할 때 사용하고,  
**String, int**와 같은 명시적인 선언법은 class 내에서 property와 변수를 선언할 때 사용한다.  
사실, 함수나 메소드 내에 지역 변수를 선언할 때, 컴파일러가 변수를 어떻게 선언하든 타입을 알고 있기 때문에 둘중 아무 방식이나 사용해도 된다.
