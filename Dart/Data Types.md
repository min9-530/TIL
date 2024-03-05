# Data types
dart도 다른 언어들과 다름없이 String, bool, int, double 같은 타입이 있다.  
하지만, dart에선 모든 자료형들이 모두 객체로 이루어져 있다.  
심지어는 function 도 객체이다.  
따라서 해당 자료형들이 가지는 메소드들을 import 할 필요 없이 사용할 수 있는 것이다.  
그중 int와 double은 num 으로부터 파생된 자료형으로, num을 사용하면 그 값이 integer인지 double인지 모른다. 
이게 dart가 진정한 객체 지향 언어라고 불리는 이유이다.

```dart
void main() {
  String name = "minsu";
  bool isAble = true;
  int age = 19;
  double money = 5.25;
  num x = 12;
  num y = 1.2;
}
```
