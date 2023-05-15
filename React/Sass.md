# Sass
Sass(Syntactically Awesome Style Sheets: 문법적으로 짱 멋진 스타일시트)는 CSS 전처리기로서, 복잡한 작업을 쉽게 할 수 있게 해 주고,  
코드의 재활용성을 높여줄 뿐만 아니라 코드의 가독성을 높여주어 유지보수를 더욱 쉽게 해준다.  

Sass에서는 두 가지의 확장자 (.scss/sass)를 지원한다.  
Sass가 처음 나왔을땐 sass만 지원되었으나 나중에 개발자들의 요청에 의해 .scss 확장자도 지원하게 되었다.  

# 문법
## sass
```sass
$font-stack: Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color
```

## scss
```scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;


body  {
  font: 100% $font-stack;
  color: $primary-color;
}
```
여기서 주요 차이점들을 찾아보면, .sass 확장자는 중괄호와 세미콜론을 사용하지 않는다.  
반면에, .scss 확장자는 기존 CSS를 작성하는 방식과 비교해서 문법이 크게 다르지 않다.
