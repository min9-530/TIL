# Inheritance
dart에선 부모 클래스를 extends 키워드를 사용해 상속하고 super를 사용해 부모 클래스의 생성자를 호출할 수 있다.  
```dart
class Human {
  final String name;
  Human({required this.name});
  void sayHello() {
    print('Hi my name is $name');
  }
}

enum Team {
  red,
  blue,
}

class Player extends Human {
  final Team team;

  Player({required this.team, required String name}) : super(name: name); // positional parameters의 경우 super(name) 으로 사용해야 한다.

  @override
  void sayHello() {
    super.sayHello();
    print('and I Play For ${team.name}');
  }
}

void main() {
  var player = Player(
    name: 'John',
    team: Team.red,
  );
  player.sayHello(); // Hi my name is John
                     // and I Play For red
}
```
