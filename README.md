# Current_Project

- 기업데이터 다뤄보기
  - 내부 규정상, 데이터는 업로드 불가이지만 코드는 올려야징
 
- 기업 내부 데이터 이외에 추가 데이터 필요함
- 아마도 텍스트 마이닝을 해야할 것 같아... (NLP를 본격적으로 해보자)
- 간만에 크롤링하기~!!
- 음,, 기본적인 분석 파이프라인을 짜보자!!! 머리야 돌아가라아아ㅏㅇ
- 페이퍼로만 보았던 GNN을 적용시켜 보기로 했다.. 나.. 잘 할 수 있겟지??????
  - 페이퍼만 봐도 머리 터질 것 같았는데ㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠ

# TIL
1. ConnectionError: ('Connection aborted.', OSError("(10054, 'WSAECONNRESET')")) \*07.13 
  - 원인
    - 웹페이지에서 안티 크롤링 시행(무분별한 크롤링 막아내기 위함)
  - 상태
    - selenium으로는 크롤링 가능하지만, bs4에서는 불가능 
    - 특히 requests자체 불가능 
    - 하지만 크롤링 속도 높이기 위해 bs4를 통해 해야만 하는 상황
  - 해결
    - requests에서 header옵션을 준다. User-Agent에서 Mozilla/5.0으로 변경하는 코드 삽입
    - `re=requests.get(url,header={'User-Agent':'Mozilla/5.0'})`
    - 크롤링할 페이지의 html 파일을 보고, 가장 상위에 있는 `data-useragent` 확인 후, header 딕셔너리 User-Agent키에 해당하는 값으로 넣는다.

2. While 문 \*08.09
- while 문은 되도록이면 쓰지 말자
- 약 500만개의 데이터를 돌려보면서, while 문을 넣어봤는데 26줄짜리 코드가 2시간이 지나도 output이 안나왔다.
- 처음에는 데이터가 많아서 그런 줄알았는데, while문은 시간복잡도가 크기 때문에 현업에서 쓰이지 않는 다는 이야기를 들었다.
  - 다음에는 시간복잡도를 계산하는 방법도 알아보자!
- for if 문으로 바꿔서 구현하기~!
