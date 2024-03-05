# List
dart에서 List를 선언하는 방법은 두 가지가 있다.
```dart
void main() {
  var case1 = [1, 2, 3, 4,];
  List case2 = [1, 2, 3, 4,];
}
```
dart의 유용한 점은 `collection if`와 `collection for`를 지원하는 것이다.  

## Collection if
`collection if`를 사용하면 존재할 수도 안 할수도 있는 요소를 가져올 수 있다.
```dart
void main() {
  var caseNumber = 6;
  var case1 = [
  1,
  2,
  3,
  4,
  5,
  if(caseNumber > 5) caseNumber;,
];
}
```
