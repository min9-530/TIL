# TypeDef
TypeDef란 자료형에 사용자가 원하는 alias를 붙일 수 있게 해준다.
```dart
// typedef를 사용하기 전
List<int> reverseListOfNumbers(List<int> list) {
  var reversed = list.reversed; // List를 reversed 하면 List 랑은 좀 다른 iterable이 돼서 다시 List로 반환해줘야 한다. 
  return reversed.toList();  
}

// typedef를 사용한 후
typedef ListOfInts = List<int>;

ListOfInts reverseListOfNumbers(ListOfInts list) {
  var reversed = list.reversed;
  return reversed.toList();
}
```
