* to-do list 프로젝트
    * 분석
        1. 메모 내용 칸 
            * 1000자 미만, 
        2. 리스트 생성
            * 오늘의 할일, 내일의 할일, 데이터사이언스, 데이터 엔지니어링 총 4개 테이블 생성
            * 메모 내용을 각 리스트에 저장하는 기능
            * 날짜, 글자 수 등을 표시
    * 설계 
        * Model
            * models.py
                * `django-admin startproject projectname` 
                    * 프로젝트를 생성
                * `python manage.py startapp appname`
                    * 어플리케이션을 생성
                * `models.py` , `admins.py`
                    * 모델을 생성하고 웹 admin 페이지에서 확인할 수 있게 생성
                * `settings.py`
                    * 설정 파일을 확인 및 수정
                * `python manage.py makemigrations` 
                    * 수정된 models.py 를 서버에 적용하기 위한 DB에 틀을 생성
                * `python manage.py migrate`
                    * DB에서 실제로 테이블 생성
                * `python manage.py dbshell`
                    * 장고 dbshell 로 접근 후 실제로 db 안에 생성이 됐는지 확인
                * `python manage.py runserver` port number
                    * 해당 포트를 갖는 서버를 돌림
        * URL configuration
            * `url.py` 열어서 View 와 연결시킴
        * Template
            * 하위 폴더 속 Templates, `.html` 
            * 웹 페이지에 나타나는 화면 UI 설정
        * View
            * `views.py`


    ```python
    # Model
    
    ## models.py 파일 내에서..

    from django.db import models


    # url configuraiton
    
    ## urls.py 파일 내에서..
    from django.urls import path, include

    urlpatterns = [
        path('', include('my_to_do_app.urls')),
        path('admin/', admin.site.urls),
    ]
    
    
    ```