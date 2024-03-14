# Class
dart도 객체지향 언어로써 Class를 가지고 있다.
```dart
class AboutMe {
  String name = 'John';
  int age = 25;
  String country = 'USA';
  // 메소드 내에 같은 이름의 변수가 있지 않는 이상 클래스의 메소드 내에서는 this를 사용하지 않는다.
  void sayHello() {
    print('제 이름은 $name 이고, 나이는 $age살 입니다. 그리고 저는 $country 에서 왔습니다.');
  }
}

void main() {
  var me = AboutMe(); 
  me.sayHello(); // 제 이름은 John 이고, 나이는 25살 입니다. 그리고 저는 USA 에서 왔습니다.
}

```


## Constructors
dart에서 생성자 함수는 클래스 이름과 같아야 한다.
```dart
class AboutMe {
  String name;
  int age;
  String country;

  AboutMe(this.name, this.age, this.country);

  void sayHello() {
    print('제 이름은 $name 이고, 나이는 $age살 입니다. 그리고 저는 $country 에서 왔습니다.');
  }
}

void main() {
  var me = AboutMe('John', 25, 'USA');
  me.sayHello(); // 제 이름은 John 이고, 나이는 25살 입니다. 그리고 저는 USA 에서 왔습니다.
  var me2 = AboutMe('Jane', 22, 'Korea');
  me2.sayHello(); // 제 이름은 Jane 이고, 나이는 22살 입니다. 그리고 저는 Korea 에서 왔습니다.
}

```

## Named Constructor Parameters
dart의 일반적인 생성자 함수는 positional로, 변수에 위치에 맞게 값을 추가해야 했는데, 이는 한눈에 알아보기도 힘들 뿐더러 변수의 양이 많아지면 위치를 헷갈릴수도 있기 때문에 변수가 명명(named)되도록 바꾼 것이다.  
```dart
class AboutMe {
  String name;
  int age;
  String country;

  AboutMe({required this.name, required this.age, required this.country});

  void sayHello() {
    print('제 이름은 $name 이고, 나이는 $age살 입니다. 그리고 저는 $country 에서 왔습니다.');
  }
}

void main() {
  var me = AboutMe(
    name: 'John',
    age: 25,
    country: 'USA',
  );
  me.sayHello();
  var me2 = AboutMe(
    name: 'Jane',
    age: 22,
    country: 'Korea',
  );
  me2.sayHello();
}
```

# Named Constructors
Named Constructors를 사용하여 클래스에 대해 여러 생성자를 구현할 수 있다.
```dart
class AboutMe {
  String name;
  int age;
  String country;

  AboutMe({
    required this.name,
    required this.age,
    required this.country,
  });

  AboutMe.createAmerican({    // named syntax
    required String name,
    required int age,
  })  : this.name = name,
        this.age = age,
        this.country = 'USA';

  AboutMe.createKorean(String name, int age)  // positional syntax
      : this.age = age,
        this.name = name,
        this.country = 'Korea';

  void sayHello() {
    print('제 이름은 $name 이고, 나이는 $age살 입니다. 그리고 저는 $country 에서 왔습니다.');
  }
}

void main() {
  var me = AboutMe.createAmerican(
    name: 'John',
    age: 25,
  );
  me.sayHello(); // 제 이름은 John 이고, 나이는 25살 입니다. 그리고 저는 USA 에서 왔습니다.

  var me2 = AboutMe.createKorean(
    'Jane',
    22,
  );
  me2.sayHello(); // 제 이름은 Jane 이고, 나이는 22살 입니다. 그리고 저는 Korea 에서 왔습니다.
}
```

## Cascade Notation
dart에선 클래스를 사용하다 보면 반복되는 부분이 생기기 마련인데, 이를 ..을 사용함으로써 해결할 수 있다.  
```dart
class AboutMe {
  String name;
  int age;
  String country;

  AboutMe({
    required this.name,
    required this.age,
    required this.country,
  });

  void sayHello() {
    print('제 이름은 $name 이고, 나이는 $age살 입니다. 그리고 저는 $country 에서 왔습니다.');
  }
}

void main() {
  var me = AboutMe(name: 'John', age: 25, country: 'USA')
    ..name = 'Amy'
    ..age = 30
    ..country = 'Korea'
    ..sayHello(); // 제 이름은 Amy 이고, 나이는 30살 입니다. 그리고 저는 Korea 에서 왔습니다.

  var me2 = AboutMe(name: 'John', age: 25, country: 'USA');
  var reMe = me2    // 이런 방법으로 class 생성 직후가 아니더라도 사용할 수 있다.
    ..name = 'James'
    ..age = 35
    ..country = 'Canada'
    ..sayHello(); // 제 이름은 James 이고, 나이는 35살 입니다. 그리고 저는 Canada 에서 왔습니다.
}
```

## Enum
enum은 우리가 클래스를 사용할 때 값을 추가할 때 실수하지 않도록 도와주는 타입이다.
```dart
enum Position {
  Top,
  Jungle,
  Mid,
  ADC,
  Support,
}

enum Tier {
  Iron,
  Bronze,
  Silver,
  Gold,
  Platinum,
  Diamond,
  Master,
  Grandmaster,
  Challenger,
}

class Player {
  String name;
  int age;
  Tier tier;
  Position position;

  Player(
      {required this.name,
      required this.age,
      required this.tier,
      required this.position});
}

void info(Player player) {
  print(
      "Name : ${player.name}, Age : ${player.age}, Tier : ${player.tier.name}, Position : ${player.position.name}");
}

void main() {
  Player player1 =
      Player(name: 'Joon', age: 19, tier: Tier.Platinum, position: Position.ADC)
        ..name = 'Faker'
        ..age = 25
        ..tier = Tier.Challenger
        ..position = Position.Mid;
  info(player1); // Name : Faker, Age : 25, Tier : Challenger, Position : Mid
}
```

## Abstract Classes
추상화 클래스란 다른 클래스들이 직접 구현 해야하는 메소드들을 모아놓은 일종의 `청사진`이라 보면 된다.  
추상 클래스에선 기능을 구현하지 않으며, 객체를 생성할 수 없다.  
따라서 메소드의 이름과 반환 타입만 정해서 정의할 수 있다.  
```dart
abstract class UserInfo {
  void deal();
} // abstract class

enum Position {
  Top,
  Jungle,
  Mid,
  ADC,
  Support,
}

enum Tier {
  Iron,
  Bronze,
  Silver,
  Gold,
  Platinum,
  Diamond,
  Master,
  Grandmaster,
  Challenger,
}

class Player extends UserInfo {
  String name;
  int age;
  Tier tier;
  Position position;

  Player(
      {required this.name,
      required this.age,
      required this.tier,
      required this.position});

  void deal() {
    print('$name is dealing damage to the enemy!');
  }
}

void info(Player player) {
  print(
      "Name : ${player.name}, Age : ${player.age}, Tier : ${player.tier.name}, Position : ${player.position.name}");
}

void main() {
  Player player1 =
      Player(name: 'Joon', age: 19, tier: Tier.Platinum, position: Position.ADC)
        ..name = 'Faker'
        ..age = 25
        ..tier = Tier.Challenger
        ..position = Position.Mid;
  info(player1);
  player1.deal();
}
```
