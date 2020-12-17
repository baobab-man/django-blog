# 코드리뷰
### 장고 요청/응답 FLOW
1. tistory 디렉토리 - urls.py - 첫 화면(/blogs/post)에서 첫번째 경로 /blogs 확인
2. include('blogs.urls') : blogs 디렉토리 - urls.py 확인
3. /post 경로 확인 - views.py에 있는 posts_list 함수 확인
4. posts_list 함수 요청 - models.py에 있는 Post 클래스에서 객체를 불러와서 정렬한 데이터를 posts에 변수로 선언
   - order_by('-created_at') : default는 오름차순 정렬, - 가 붙으면 내림차순 정렬
5. 선언한 posts를 반환해주고 templates으로 넘겨줌
6. templates의 posts_list.html에 넘겨준 posts는 템플릿 태그에 의해 for문을 돌면서 화면에 출력됨 
   - {% tag %} : 템플릿태그, 반복문(for문)이나 제어문(if문)을 사용하여 흐름을 제어
   - {{ 변수 }} : 템플릿변수, 뷰에서 템플릿으로 context 전달(함수에서 html문서로 객체를 보내는 수단)
   - {{ 변수 | 필터 }} : 템플릿필터, 템플릿 변수의 값을 특정 형식으로 변환시 사용
### 게시글 생성 FLOW
##### @ : 데코레이터(Decorator)란?
- 함수를 받아 명령을 추가한 뒤 이를 다시 함수의 형태로 반환하는 함수
- 함수의 내부를 수정하지 않고 기능에 변화를 주고 싶을 때 사용
- 함수의 전처리나 후처리에 대한 필요가 있을 때 사용
- 반복을 줄이고 메소드나 함수의 책임을 확장함
- 대상 함수를 wrapping하고, 이 wrapping 된 함수의 앞뒤에 추가적으로 꾸며질 구문들을 정의해서 손쉽게 재사용 가능하게 해주는 것
1. POST 메소드를 이용하여 _get_post 함수로 title이란 키에 해당하는 value값을 넣어줌
   - strip() : 인자로 전달된 문자를 String의 왼쪽과 오른쪽에서 제거(공백이 있을시 공백제거)
   - 함수내에서 if문 사용시 긍정문보다 부정문이 먼저 오는 코드가 좋은 코드