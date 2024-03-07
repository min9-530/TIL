# Funcion
dart의 함수는 객체이며 타입이 Function이다. 이는 함수를 변수에 할당하거나 다른 함수에 인수로 전달할 수 있음을 의미한다.  

```dart
String sayHello(String name) {
  return "Hello $name! Nice to meet you!";
}

// 하나의 표현식만 포함하는 함수 경우 단축 구문을 사용할 수 있다.
num plus(num a, num b) => a + b;

void main() {
  print(sayHello("minsu")); // Hello minsu! Nice to meet you!
  print(plus(1, 2)); // 3
}
```


## Named Parameters
Named Parameters는 명시적으로 required로 표시되지 않는  선택 사항이다.  
기본값을 제공하지 않거나 Named Parameters를 필수로 표시하지 않으면 요소들의 기본값이 null이 될 수 있다.  
따라서 default value를 지정해 주거나 required modifier를 이용해야 하는 것이다.  

```dart
String sayHello({
  String name = 'minsu',
  int age = 19,
  String country = 'Korea',
}) {
  return "Hello $name, you are $age, and you are from $country";
}

String sayHi({
  required String name,
  required int age,
  required String country,
}) {
  return "Hello $name, you are $age, and you are from $country";
}

void main() {
  print(sayHello()); // 아무것도 전달하지 않아도 default value가 이미 있으므로 null safety에 걸릴 일이 없음
  print(sayHi()); // name, age, country의 값이 모두 포함되지 않으면 dart에서 컴파일하지 않음
}
```
