# Class
dart도 객체지향 언어로써 Class를 가지고 있다.
```dart
class AboutMe {
  String? name;
  String? age;
  String? country;
  AboutMe({this.name, this.age, this.country});

  void sayHello() {
    // 메소드 내에 같은 이름의 변수가 있지 않는 이상 클래스의 메소드 내에서는 this를 사용하지 않는다.
    print('제 이름은 $name 이고, 나이는 $age살 입니다. 그리고 저는 $country 에서 왔습니다.'); 
  }
}

void main() {
  var me = AboutMe(name: 'John', age: '25', country: 'USA');
  me.sayHello(); // 제 이름은 John 이고, 나이는 25 입니다. 그리고 저는 USA 에서 왔습니다.

}
```
