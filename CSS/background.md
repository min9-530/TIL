# Background
``background`` 속성은 "배경"을 이미지 파일을 사용해서 삽입하는 것이다.

# Background-repeat
``background-repeat``은 배경 이미지를 반복을 할지 안할지에 대한 속성이다.

## 속성값
+ repeat
  + 배경 이미지를 남는 공간에 반복해서 나열시킨다.
+ no-repeat
  + 배경 이미지를 반복하지 않는다.
+ repeat-x, repeat-y
  + 배경 이미지를 x축과 y축으로 반복한다.
+ space
  + 요소가 잘리지 않을 만큼 이미지를 반복한다. 가장 처음 이미지와 마지막 반복 이미지는 양 끝에 고정된다.
+ round
  + 이미지가 들어갈 수 있는 영역이 생기면 반복 이미지가 늘어나 여백을 남기지 않는다.
 

# Background-position
``background-position``은 '좌측 상단의 모서리를 기준으로 배경 이미지의 배치를 어디에 할 것인가'를 지정하는 속성이다.

## 속성값
+ 키워드: top, bottom, left, right, center 등이 있다.
+ 단위값: 대표적으로 px을 가장 많이 사용하며 em, ch 등 다양한 단위를 사용할 수 있다.
+ % : 백분율을 사용할 수 있다.


![image](https://github.com/min9-530/TIL/assets/104071568/17661632-d385-4e79-8fdf-60994282ecff)
위의 이미지는 키워드 값으로 정렬했을떄 배경의 위치를 나타낸 것으로, 설정 시 설정한 곳으로 딱 붙은 다음 이미지와 닿는 부분의 중심을 영역의 중심에 맞춘다.