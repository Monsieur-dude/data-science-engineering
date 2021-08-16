# 파이썬의 기초와 HTML5/CSS

* HTML5 기본용어
    * 태그와 요소
        * 태그 : 요소를 만들 때 사용하는 작성법 
            * <요소>내용</요소>
        * 요소 : HTML 페이지를 구성하는 각 부품(제목, 본문 이미지)
    * 속성
        * 태그에 추가 정보를 부여함
    * 주석 
        * 코드에 대한 설명을 기록할 때 사용, 파이썬에서 # 과 비슷한 역할

* HTML5 페이지의 구조와 작성법
    * 구조[![구조](https://lh3.googleusercontent.com/proxy/TlZfbl4lpJSiJVSGLrZ1uw2uqGAFREScEmE2KKuCqIgyAy08fqzhYNc5zuVbsQB80yg6Vog1cCeWNKaKsBiHGX1lc_8Iwj54fqF3z_Ma)](http://www.devkuma.com/books/pages/115)
    * 스타일시트 작성과 실행
        * 내부 스타일 : HTML 페이지 내부에서 style 태그를 사용, 스타일시트가 짧은 경우에 사용함
        * 외부 스타일 : 스타일시트를 별도로 생성해 link 태그의 href 속성을 이용, 협업이나 프로젝트 시 사용
    * 자바스크립트 작성과 실행
        * 내부 자바스크립트 : script 태그를 HTML 페이지 내부에 작성
        * 외부 자바스크립트 : script 태그의 src 속성에 파일 경로를 입력해 HTML 에서 불러옴
    * 검사 
        * 디버그 : 버그를 잡는 것
* HTML5 기본 태그
    * heading : h1, h2, h3, h4, h5, h6 제목 글자 크기
    * p : 본문 문단 생성
    * br : 줄바꿈
    * hr(horizontal rule): 수평 줄 삽입(`___`)
    * a(anchor) : 다른 웹페이지나 내부 특정위치로 연결
        * href(hyper reference)의 속성
            * 절대경로
                * http://naver.com
                * /animal.jpg
            * 상대경로
                * animal.jpg : 웹페이지가 있는 폴더에 있는 파일
                * image/animal.jpg : 웹페이지가 있는 image 폴더 속 파일
                * ../animal.jpg : 웹페이지가 있는 상위 폴더에 있는 파일
            * 아이디경로
                * #name : id 속성이 name 태그 위치로 이동
            * 메일경로
                * mailto : emailaddress@gmail.com 해당 주소로 메일 전송
    
    
    
    
    ###
    ```html
    # 내용을 가질 수 있는 요소
    
    <h1>Hello HTML5</h1>
    <p>Happy web programming</p>
    <audio></audio>
    
    <div>
        <h1>Hello HTML5</h1>
        <p>Happy web programming</p>
    </div>
    
    # 내용을 가질 수 없는 요소
    <img>
    <br>
    <hr>
    
    # 속성
    <h1 title="header">Hello HTML5</h1>
    <h1 title="header2">HTML5</h1>
    <img src="image.png">   
    
    # 주석
    <!-- 주석 -->
    
    
    # 기본 태그
    <h1>Hello!<h1>
    <h3>Hello!<h3>
    <p>
    <br>
    <hr>
    <a href="http://hanbit.co.kr">Hanbitmedia</a>

    
    ```
    ###
    