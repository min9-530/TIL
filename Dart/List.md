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
print (case1); // 1, 2, 3, 4, 5, 6
}
```

## Collection for
`collection for`는 코드 내에서 for문을 사용하여 기존의 리스트에 다른 리스트를 반복문으로 호출하여 새롭게 추가할 수 있다.  
```dart
void main() {
  var friends = ["tom", "james", "sam"]
  var family = [
"john",
"mike",
for(var friend in friends) "*new* friend"
];
print (family); // [john, mike, *new* tom, *new* james, *new* sam]
}
```
