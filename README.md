# Current_Project

- 아마도 텍스트 마이닝을 해야할 것 같아... (NLP를 본격적으로 해보자)
- 간만에 크롤링하기

# TIL
1. ConnectionError: ('Connection aborted.', OSError("(10054, 'WSAECONNRESET')")) \*07.13 
  - 원인: 웹페이지에서 안티 크롤링 시행
  - 상태: selenium으로는 크롤링 가능하지만, bs4에서는 불가능 -> 크롤링 속도 높이기 위해 bs4를 통해 해야만 하는 상황
  - 해결: requests에서 header옵션을 준다. User-Agent에서 Mozilla/5.0으로 변경하는 코드 삽입
   `re=requests.get(url,header={'User-Agent':'Mozilla/5.0'})`
