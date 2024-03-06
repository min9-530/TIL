# Set
dart에서의 `Set`은 `List`와 매우 유사하면서도 다른데, Set에 속한 모든 아이템들이 유니크해야 할 때 사용한다.  

Set은 리스트와 달리 모든 요소들이 유니크하기 때문에 같은 요소를 여러번 추가해도 하나만 존재한다.

```dart
void main() {
  Set numbers = {1, 2, 3, 4};
  numbers.add(1);
  numbers.add(1);
  numbers.add(1);
  numbers.add(1);
  numbers.add(1);
  print(numbers); // 1, 2, 3, 4
}
```
