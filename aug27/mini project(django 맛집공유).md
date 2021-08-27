# 맛집 공유 사이트 mini project 2
* RestaurantShare
    * 분석
        * 첫화면
            * 음식 메뉴로 카테고리 추가 ex) 한식, 중식, 양식...
                * 카테고리 클릭 시 세부내용 보이기
                * 세부 내용은 카테고리, 맛집 이름, 링크, 추가 내용, 장소까지 저장할 수 있게
                * 카테고리 추가와 삭제할 수 있어야 함
            * 이메일 주소, 제목, 내용 적는 텍스트
                * 이메일 주소는 콤마로 분류 가능하게
                * 이메일 발송버튼 누르면 확인 창 뜨게 하기
                * 맛집 리스트 중에서 체크표시로 복수선택 선택할 수 있는 옵션이 있어야함
                * 이메일을 보낸 뒤 이메일이 발송되었다는 창으로 넘어가야 함
    * 설계
        * Model
            * django-admin  startproject RestaurantShare
            * python manage.py startapp 
            ShareRes
            * python manage.py startapp sendEmail
            * python settings.py
                * 아이피추가
                * 앱 추가
                * 시간 변경
                * SQlite3 DB로 설정
            * python manage.py createsuperuser
                * admin 계정 생성
            * code models.py
            * code admins.py
            * python manage.py makemigration
            * python manage.py migrate
            * python manage.py runserver
        * URLconf
            * python urls.py
                * url 패턴을 추가
        * Template
            * template/app/*.html
                * 실제 웹 상에서 보이는 화면을 java 문법으로 코딩
            * code views.py 
                * index() 함수 정의
        * View
            * python views.py