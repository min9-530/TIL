# Box-Model(박스 모델)
모든 HTML 요소는 박스(box) 모양으로 구성되며, 이것을 박스 모델(box model)이라고 부른다.  
박스 모델은 HTML 요소를 패딩(padding), 테두리(border), 마진(margin), 그리고 내용(content)로 구분한다.  
![](https://github.com/min9-530/TIL/assets/104071568/e56547ab-6b65-4f5c-be6c-b580023bcff9)
1. 내용(content): 텍스트나 이미지가 들어있는 박스의 실질적인 내용 부분이다.
2. 패딩(padding): 내용과 테두리 사이의 간격이다. 패딩은 눈에 보이지 않습니다.
3. 테두리(border): 내용과 패딩 주변을 감싸는 테두리이다.
4. 마진(margin): 테두리와 이웃하는 요소 사이의 간격이며, 눈에 보이지 않는다.
```CSS
<style>
  div {
    background-color: red;
    padding: 50px;
    border: 20px solid maroon;
    margin: 50px;
  }
</style>
```
