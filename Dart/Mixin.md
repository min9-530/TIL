# Mixin
Mixin은 생성자가  없는 클래스를 의미한다.  
Mixin 클래스는 상속 할 때 extends가 아닌 with를 사용한다.  
Mixin 클래스를 사용하는 핵심적인 이유는 여러 클래스에 재사용이 가능하다는 점이다.  

```dart
mixin Strong {
  final double strengthlevel = 1999.0;
}

mixin QuickRunner {
  void runQuick() {
    print("ruuuuuuun!");
  }
}

mixin Tall {
  final double height = 1.99;
}

class Player with Strong, QuickRunner, Tall {
  void play() {
    print("I'm playing");
  }
}

void main() {
  var player = Player();
  player.play(); // I'm playing
  player.runQuick(); // ruuuuuuun!
  print(player.strengthlevel); // 1999.0
  print(player.height); // 1.99
}
```
