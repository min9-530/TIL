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
