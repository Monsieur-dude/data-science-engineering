## 모듈(`Module`)
_______ 
* 모듈
    > 상수,변수, 함수, 클래스 등을 모아둔 파일
    * 규모가 큰 프로그램을 만들 때, 기능별로 나눈 후 여러 파일에서 해당 기능의 코드를 구현하기 위함
    * 코드 작성 및 관리가 용이
    * 따라서 공동작업 시 편리하게 됨
* 모듈 생성 및 호출
    * 모듈 생성
        * `%%writefile` : 모듈을 생성한 뒤, 코드를 파일로 저장
            * `%%writefile` [-a] filename.py : 셀에 있는 코드를 파이썬 코드 파일로 저장하기
            * `%%load` filename.py : 저장된 파이썬 코드 불러오기
            * `%%run` filename.py : 파이썬 코드 파일 실행하기
    * 모듈 호출
        * `import` module_name : 모듈을 불러오기
            * 모듈을 불러온 후에 사용하려면, *'module_name.변수'*, *'module_name.함수()'*, *'module_name.클래스()'* 와 같이 입력하여 사용
            * `dir`(module_name) : import 한 모듈에서 사용할 수 있는 변수, 함수, 클래스를 확인함
        * `from` module_name `import` 변수, 함수, 클래스 이름 
            * 간편하게 모듈 속 변수, 함수, 클래스를 쓸 수 있음
            * 콤마를 이용해서 여러 개를 한 번에 import 가능
        * `from` module_name `import *`
            * 모듈 내 모든 변수, 함수, 클래스를 import
            * 모듈을 2개 이상 쓸 때는 import 되는 변수, 함수, 클래스 등이 겹칠 수 있으므로, 사용에 주의해야 함
    * 모듈명을 별명으로 선언
        * `import` module_name `as` 별명(alias)
        * `from` module_name `import` 함수, 변수, 클래스 `as` 별명(alias)
    * 모듈을 직접 실행 vs import 후 실행
        * `if __name__ == "__main__" :`  같은 모듈에서 코드를 직접 실행할때만 코드 블록이 작동
        * `else :` 모듈을 import 한 뒤에 실행

    ###
    ```python
    ## 모듈 만들기
    
    %%writefile my_first_module.py 
    
    def my_function() :
        print("This is my first module")

    ## 파일이 생성됐는지 확인
    !cat "my_fist_module.py"
    
    ## 모듈 불러오기

    import my_first_module

    my_first_module.my_fuction()

    ## 모듈을 불러와서 도형의 면적 구하기 실습

    %%writefile my_area.py

    Pi = 3.14       

    def square_area(a) :
        return a ** 2
    def circle_area(r) :
        return Pi * r ** 2

    import my_area

    print("pi =", my_area.Pi)                       # 모듈에서 지정한 변수값을 불러오기  
    print("square area =", my_area.square_area(5))  # 모듈에서 지정한 함수를 실행
    print("circle area =", my_area.circle_area(2))  # 모듈에서 지정한 함수를 실행

    ## dir(module_name)

    dir(my_area)        # 반환값 : ['Pi', 'circle_area', 'square_area']

    ## from module_name import variable, fuction, class

    from my_area import Pi                  # 모듈의 변수 바로 불러오기
    from my_area import square_area         # 모듈의 함수 바로 불러오기
    from my_area import circle_area         # 모듈의 함수 바로 불러오기

    print('square area =', square_area(5))
    print('circle area =', circle_area(2))

    ## 여러 개를 한 번에 불러오기

    from my_area import Pi, square_area, circle_area
    
    ## 모든 변수, 함수, 클래스를 불러오기

    from my_area import * 

    ## alias 사용

    import my_area as area 

    print('Pi =', area.Pi)
    print('square area =', area.square_area(5))
    print('circle area =', area.circle_area(2))

    ## from module_name import 변수,함수,클래스 as alias
    
    from my_area import Pi as pi
    from my_area import square_area as square
    from my_area import circle_area as circle

    print('pi =', pi)
    print('square area =', square(5))
    print('circle area =', circle(2))

    ## 모듈에서 직접 실행 vs import 후 실행

    # 예시 1

    %%writefile my_module_test1.py

    def func(a) :
        print("input number :", a)
    func(3)         # 함수가 잘 작동하는지 확인하기 위해 임시로 실행한 코드임, 따라서 import 를 하면 작동되어선 안됨

    %run my_module_test1    # 모듈 내 함수가 작동하는지 확인, 결과값 : input number : 3

    import my_module_test1  # 모듈 내에 func(3) 이미 있으므로, 결과값은 : input number : 3 을 얻음. 이것은 원하는 결과가 아님. 왜냐하면 모듈을 import 한 것은 모듈 내 함수를 사용하겠다는 의미이지 임시로 입력한 코드를 원하는 건 아니기 때문

    # 예시 2

    %%writefile my_module_test3.py

    def func(a):
        print("input number :", a)
        
    if __name__ = "__main__" :      # 모듈을 %run my_module_test3 로 직접 실행한 경우
        print("모듈을 직접 실행")
        func(5)
        func(7)
    else :                          # 모듈을 import my_module_test3 한 경우 
        print("모듈을 import 후에 실행")

    ```
    ###

* 내장 모듈(`built-in modules`)
    * `import random` : 난수 모듈(`random`)
        * random.`random`() 
            * 0.0 <= 실수 < 1.0 랜덤 실수를 반환
        * random.`randint`(a,b)
        * random.`randrange`(start, end, step)
            * 홀,짝수를 발생 혹은 특정 숫자 단위로 난수 발생 시 사용함
        * random.`shuffle`(list)
            * list 내 항목 값을 랜덤으로 섞음
        * random.`choice`(seq)
            * 공백값을 제외한 랜덤 값을 반환
        * random.`sample`(population, k)
            * 모집단에서 중복되지 않은 k개의 인자 반환
    * `import datetime` : 날짜 및 시간(`datetime`)
        * date 클래스, time 클래스, datetime 클래스
        * 객체변수 = `module_name.class_name`(variable)
        * 빼기 연산도 가능함
        * `{:Y %m %d, %H %M %S}`.format(now), 대소문자 구분을 해야함
    * `import calendar` : 달력 생성(`calendar`)
        * 모듈 속 요일에 해당하는 상수
            * `calendar.MONDAY` = 0 
            * `calendar.SUNDAY` = 6 
        * 모듈 속 함수
            * `.calendar`(year, m) : 전체 달력을 문자열로 반환, m 은 표시할 일 간 공백의 숫자 (기본은 3)
            * `.month`(year, month) : 해당 연월을 문자열로 반환
            * `.monthrange`(year, month) : 지정한 연도와 월의 시작 날짜와 일수를 반환
            * `.firstweekday`() : 달력에 표시되는 일주일의 시작 요일을 알 수 있음
            * `.setfirstweekday`(weekday) : 일주일 시작 요일을 지정
            * `.weekday`(year, month, day) : 원하는 날짜의 요일을 확인함
            * `.isleap`(year) : 해당 년도가 윤년인지 아닌지 boolean 값으로 출력
        

    ###
    ```python
    
    ## random

    import random()
    
    random.random()     # 0 ~ 1 사이의 임의의 실수 반환
    random.randint(3,36)
    random.randrange(0,86,3)

    list1 = [3, 6, 2, 10, 96, 33, 75, 10000, 4]
    random.shuffle(list1)
    list1

    random.choice("My names is James")      # 공백 제외한 랜덤 값 반환
    random.sample("My name is James", 4)    # 중복되지 않은 값 4개를 반환

    ## datetime
    
    import datetime

    date_obj = datetime.date(year, month, day)
    time_obj = datetime.time(hour, minute, second)
    datetime_obj = datetime.datetime(year, month, day, hour, minute, second)

    set_day = datetime.date(2021, 8, 4)
    print(set_day)

    print("{}, {}, {}".format(set_day.year, set_day.month, set_day.day))

    ## 빼기 연산
    
    day1 = datetime.date(2021, 4, 1)
    day2 = datetime.date(2021, 7, 10)
    diff_day = day2 - day1
    print(diff_day)

    type(day1)      # 결과값 : datetime.date 클래스값
    type(diff_day)  # 결과값 : datetime.timedelta 
    
    ## today()

    print(datetime.date.today())

    ## time 클래스

    set_time = datetime.time(15,30,45)
    print(set_time)

    set_dt = datetime.datetime(2021, 8, 4, 10, 20 ,0)
    print(set_dt)

    print('Date {0}, {1}, {2}'.format(set_dt.date.year, set_dt.month, set_dt.day))
    print("Time {0}, {1}, {2}".format(set_dt.hour, set_dt.minute, set_dt.second))
    
    now = datetime.datetime.now()
    print(now)
    
    ##

    print("{:%Y %m %d, %H %M %S}".format(now))

    ## 좀 더 간편하게 datetime 쓰기

    from datetime import date, time, datetime
    print(date(2021, 7, 1))
    print(date.today())
    ```
    ###
* 패키지(`package`)
    > 여러 개의 모듈을 모아둔 것. 폴더 단위로 관리함
    * `__init__.py` 파일을 폴더에 생성시키는게 유리 
    * 호출 방법
        * `import` package.folder.module
            * 호출 시 패키지 이름 > 폴더이름 > 모듈이름 순으로 입력
        * `from` package.folder `import` module
        * `from` package.folder.module `import` function1, function2, ...
    
    ```python
    %%writefile image/io_file/imgread.py

    def pngread() :
        print("pngread in imgread module")
    def jpgread() :
        print("jpgread in imgread module")
    
    ## 호출 방법

    # 1
    
    import image.io_file.imgread         # image: 패키지이름 io_file: 패키지가 존재하는 폴더, imgread: 모듈 import
    image.io_file.imgread.pngread()

    # 2

    from image.io_file import imgread
    imgread.pngread()

    # 3 

    from image.io_file.imgread import pngread()
    pngread()

    # 4

    from image.io_file.imgread import pngread(), jpgread()
    pngread()
    jpgread()
    
    # 5

    from image.io_file.imgread import *   # 모든 모듈을 import
    pngread()
    jpgread()

    # 6

    from image.io_file.imgread import pngread() as pread
    from image.io_file.imgread import jpgread() as jread
    pread()
    jread()
    ```