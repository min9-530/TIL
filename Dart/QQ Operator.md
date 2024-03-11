# QQ Operator
QQ Operator 란 `??` 연산자를 뜻한다.  
`??` 연산자를 사용하면 왼쪽의 값이 null 이라면 오른쪽 값을 return 시킨다.

```dart
String capitalizeName(String? name) =>
  name?.toUpperCase() ?? 'ANON';

void main() {
  print(capitalizeName('minsu')); // MINSU
  print(capitalizeName(null)); // ANON
}
```

# QQ Equals
QQ Equals란 `??=` 연산자를 뜻한다.  
`??=` 연산자를 사용하면 변수의 값이 null 일때 값을 할당해준다.

```dart
void main() {
  String? name;
  name ??= 'minsu';
  print(name); // minsu
}
```
