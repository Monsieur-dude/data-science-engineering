함수(`Function`)
___
> 인자값(**factor**)이 특정 기능을 거쳐 반환값(**return value**) 출력하는 것
* 기본 구조 :
    * def 함수이름([인자1, 인자2, 인자3, ..., 인자n]) 
    * 인자(`factor`)는 없을 수도 있음
    * 반환값(`return value`)이 있을 경우 `return` 을 쓰고 없을 경우 생략해도 됨
    * 따라서 세 가지 경우가 있음
        1.  factor X, return X
        2. factor O, return X
        3. factor O, return O
    * 인자가 있을 경우 반드시 써주고, 인자의 개수와 순서는 같아야 함
* 변수의 범위 :
    * 변수를 정의한 위치에 따라 유효범위(`scope`)가 달라짐
    * 변수 저장 공간: `local` -> `global` -> `built-in` 순서로 변수의 유무 확인
        * 지역 영역(`local scope`)
        * 전역 영역(`global scope`)
        * 내장 영역(`built-in scope`)
    * 변수 종류:
        * 지역변수(`local variable`) : 함수 내에 있는 코드 블록에만 적용되는 변수
        * 전역변수(`global variable`) : 함수 밖을 포함한 모든 범위에 적용되는 변수


    ###
    ```python

    ## 함수의 기본 구조

    def 함수_이름([인자1, 인자2, 인자3, ..., 인자n])
        < 코드 블록>
        return < 반환 값 >
    
    ## factor X, return X

    def my_func() :
        print("My first fuction!")
        print("This is a function!")
    
    ## factor O, return X

    def my_friend(friendName) :
        print("{} is my friend.".format(friendName))
    my_friend('James')      # 출력값 : James is my friend.
    
    ## factor O, return O

    def my_calculation(x, y ,z) :
        w  = x * y + z
        return w
    my_calcutation(3, 5, 10)        # 출력값 : 25
    
    ## 변수의 유효범위

    a = 5                       # 전역 변수

        def func1() :
            a = 1               # 지역 변수
            print("local variable for func1, a =", a)
        def func2() :
            a = 2               # 지역 변수
            print("local variable for func2, a =", a)
        def func3() :           # 전역 변수
            print("global variable for func3, a =", a)
        def func4() :
            global a            # 전역 변수 재설정
            a = 1000            # 전역 변수
            print("global variable for func4,  a =", a)
    
    ```
    ###


 * 함수의 종류
    * 람다 함수((`lambda function`)
        * `lambda` < 인자 > : < 인자 활용 수행 코드 >
            * 한 줄로 함수를 단순히 표현이 가능
            * 구성이 간단한 간단한 연산에 주로 사용됨

    * 형 변환 함수(`type conversion function`)
        * `int`(), `float`(), `str`(), `list`(), `tuple`() ...
        * `list`(), `set`(), `tuple`() 사용해 서로 타입을 변환할 수 있음

    * bool 함수(`bool function`)
        * `bool`() :
            * 인자가 숫자인 경우 : 0 은 `False`, 0 이외의 정수, 실수는 `True` 
            * 인자가 문자열인 경우 : 문자열이 있으면 `True`, 없으면 `False`
            * 인자가 리스트, 튜플, 세트일 경우 : 항목이 있으면 `True`, 없으면 `False`

    * 최소값, 최대값을 구하는 함수
        * `min`(), `max`() :
            * 리스트, 튜플, 세트의 항목이나 문자열 중에서 최소값, 최대값을 구할 수 있음
            * ASCII 코드에 따라 문자열, 특수문자, 대문자, 소문자 값을 비교 가능(소문자 > 대문자 > 숫자 > 특수문자)

    * 절대값과 전체 합을 구하는 함수
        * `abs`(), `sum`()
            * `sum`() 은 리스트, 튜플, 세트 데이터의 모든 항목의 합을 결과값으로 출력함

    * 항목의 개수를 구하는 함수
        * `len`() :
            * 문자열, 리스트, 튜플, 세트, 딕셔너리 데이터의 길이,  즉 데이터가 포함하는 항목의 개수를 구할 수 있음
    
    
    ###
    ```python
    
    # 함수의 종류

    ## Lambda function

    lambda_square_func = lambda x, y : (x * y) ** 2

    ## 만약 인자값이 정해져있을 때,

    (lambda x, y : (x*y)**2) (5,3)

    ## bool function

    bool(3)
    bool(2.59028914)
    bool(-5.3942)
    bool(0)

    bool("a")
    bool(" ")   # 공백도 문자열로 포함.
    bool("")    # 문자열 없음
    bool(None)  

    myFriends = []
    bool(myFriends) 
    myNum = ()
    bool(myNum)
    mySetA = {}
    bool(mySetA)
    

    ## min(), max()
    myStr = 'xyzabc'
    min(myStr)
    max(myStr)
    
    myNum = 1, 2, 3, 4, 5, 6
    min(myNum)
    max(myNum)


    ## abs(), sum(), len()
    abs(-4,5)
    abs(10.358)

    myList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    myDictionary = {"a" : 10, "b" : 20, "c" : 30}
    sum(myList)
    len(myDictionary)

    ```
    ###