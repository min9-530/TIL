# Map
dart에서의 `map`은 JS나 TS의 `object` 같은 것으로, key와 value를 연결하는 객체이다.  
각각의 키는 한 번만 발생하지만 동일한 값을 여러 번 사용할 수 있다.
```dart
void main() {
  var player = {
    // Key:Value
    'name': 'nico',
    'xp': 199.99,
    'superpower': false
  };
// Map 생성자를 사용하여 동일한 객체를 만들 수 있다.
  var player = Map();
  player['name'] = 'nico';
  player['xp'] = 199.99;
  player['superpower'] = false;
}
```
또한 map을 선언할 때 key와 value의 자료형을 명시적으로 정의해 줄 수 있다.

```dart
void main() {
  Map<int, bool> player = {
    1: true,
    2: false,
    3: true
  }
}
```
