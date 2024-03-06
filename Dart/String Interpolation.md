# String Interpolation
`String Interpolation`이란 text에 변수를 추가하는 방법이다.

```dart
void main() {
  var name = 'minsu';
  var greeting= 'Hello everyone, my name is $name!';
  print(greeting) // Hello everyone, my name is minsu!
}
```

기본적으로 변수를 추가할 땐 $(달러) 기호를 붙이고 사용할 변수를 적어주면 된다.  
만약 무언가를 계산하거나 리스트의 프로퍼티를 추가할 땐 $와 함께 {}도 사용해 주어야 한다.
