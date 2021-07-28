## 입력(`input`)과 출력(`output`)
___
- 코딩 실행 결과를 화면 혹은 파일로 출력해야할 때
- 입력을 키보드로 받거나, 파일에 있는 데이터를 읽어서 처리해야 할 때
- 키보드와 화면으로 입출력(`input`, `output`), 파일로 입출력(`import`, `export`)하는 방법

### 키보드와 화면의 입출력

1. 화면 출력
    * 기본 출력 
        * `print`() : 문자열(`string`), 숫자(`integer`)를 출력
            * 여러개의 문자열을 `,` 포함해서 입력하면, 한 칸 공백이 포함해서 출력됨
            * `sep` : **separator**, 여러 출력값을 구분짓게 하는 문자열을 추가해서 출력 가능
            * `+` 이용해서 문자열을 연결 가능
            * `,` 와 `+` 동시에 사용 가능
            * 문자열과 숫자는 데이터 타입이 다르기 때문에, `+`로 연결 할 수 없음
            * `\n` :줄을 바꿔서 출력
            * `end`="str" : 출력값 끝에 문자열을 추가해서 출력 
    * 형식 지정 출력
        * print(`%type` `% data`) : 형식과 위치를 지정해서 출력
            * |data type|표기|
              |:--:|:--:|
              |`string`|%s|
              |`integer`|%d|
              |`float`|%f|
            * print(``%type %type`` `% (data1, data2)`) : 서로 다른 데이터 타입이 2개 이상일 경우
                * 각 데이터마다 타입을 지정해줘야 하는 번거러움이 있음
            * print("{0} {1} {2} ... {n}"`.format(data_0, data_1, data_2, ..., data_n)`) :
                *  데이터의 위치만 맞춰주면 출력이 가능해서 편리함
                * `{n}` 의 위치를 변경하면 데이터 출력 위치를 변경 가능
                * `{}` 숫자를 생략하면, data_n의 순서에 따라서 출력


    ###
    ```python
    
    print('Hello', 'Python', 'Learners', sep = ' - : - ')       # 출력값 : Hello - : - Python - : - Learners

    print('Hello', 'Python' + 'Learners')           # 출력값 : Hello PythonLearners

    print('Hello','\nPython')                       #  출력값 : Hello
                                                    #         Python

    print('Hello', end="....")                      # 출력값 : Hello....Python


    ## 형식 지정 출력

    print(%type % data)
    
    name = 'James'
    print('%s is my friend.' % name)                # 출력값 : James is my friend.
    
    ##

    print(%type %type % (data1, data2)))

    r = 3
    Pi = 3.14592653 
    print('radius: %i, Pi: %f' % (r, Pi))           # data type 2 개(integer, float)


    ##

    print('{0}, {1}, {2} ... {n}'.format(data_0, data_1, data_2, ..., data_n))

    animal_0 = 'cat'
    animal_1 = 'dog'
    animal_2 = 'fox'

    print('Animal: {0}'.format(animal_0))   # 출력값 : Animal : cat
    print('Animal: {0}, {1}, {2}'.format(animal_0, animal_1, animal_2))
    print('Animal: {}, {}, {}'.format(animal_0, animal_1, animal2))       # 출력값 : Animal : cat, dog, fox
    
    ```
    ###

2. 키보드 입력 (`input`)
    * `input`("string") :
        * "string" 은 화면에 표시
        * 키보드로 데이터 입력하면
        * 입력된 데이터는 `str` 타입으로 데이터 변수에 대입

    ###
    ```python
    yourName = input("What's your name? ")
    print("Your names is {}".format(yourName))

    yourBirth = input("When is your birthday? ")            # 실수로 받기 위해서는 int(yourBirth) 값을 설정해야 함
    print("Your birthday is {}".format(yourBirth))          # 출력값의 데이터 타입은 string

    ```
    ###


### 파일의 입출력
1. 파일열기
    * f = `open`(filename, mode) : 파일에서 데이터를 읽거나 쓰기위해 사용
        * filename 은 파일의 이름. 그 이름의 파일이 없을 경우, 새로 만듦
        * mode :
            |mode|의미|
            |:--:|:--:|
            |`r`|읽기모드, 기본으로 지정되는 모드|
            |`w`|쓰기모드, 같은 이름의 파일 있으면 기존 내용은 삭제됨|
            |`x`|쓰기모드, 같음 이름의 파일이 있으면 오류 발생
            |`a`|추가모드로 파일 열기, 같은 이름의 파일 없으면 w와 기능이 같음|
            |`b`|바이너리 모드로 파일 열기|
            |`t`|텍스트 파일 모드로 파일 열기, 기본으로 텍스트 모드로 지정됨|
        * mode를 혼합해서 사용 가능
        * 읽기 : `open`() -> `read`() -> `close`() 
        * 쓰기 : `open`() -> `write`() -> `close`() 
    * 파일 쓰기 
        * f = `open`(file_name, 'w') -> `f.write`(문자열) -> `f.close`()
        * `write`()에서는 `print`() 함수에서 쓰는 출력 방식을 사용 가능, 차이점은 파일출력과 화면출력
        * `!cat`(맥, colab) 또는 `!type`(윈도우) 파일 확인 가능
        
    * 파일 읽기
        * f = `open`(file_name,'r') 또는 f = oepn(`file_name`) -> data = f.`read`() -> f.`close`()
        * `read`() 로 읽은 파일의 내요은 모두 data 변수에 할당함
        * 화면 출력을 원할경우 `print`(data)

    * 반복문을 활용해 파일 읽기, 쓰기
        * 파일에 문자열 한 줄씩 쓰기
            1. f = `open`(filename,`'w'`)
            2. `for` 문 (`print`() 함수에서 쓰는 출력 방식을 활용할 수 있음)
            3. f`.write`() 
            4. f`.close`()
            5. `!cat`
        * 파일에서 문자열 한 줄씩 읽기
            1. f = `open`(filename,`'r'`)
            2. f`.readline`()
            3. f`.close`()
            * `readlines`() : 파일 안에 모든 줄을 읽은 뒤, 한 줄을 하나의 요소로 갖는 리스트타입으로 변환

        * `with`() 사용해서 파일 읽기, 쓰기
            * `with` `open`(filename, mode) `as` f :
            *  코드 실행이 끝나면 자동으로 닫힘. `.close`() 를 써줄 필요가 없음

    ###
    ```python
    
    ## 파일 쓰기
    
    f = open('myFile.txt','w')      # myFile.txt 파일 쓰기 모드로 열기
    f.write('This is my first file.')       # 열려있는 파일에 문자열 쓰기
    f.close()                               # 파일 닫기
    

    ## 파일 읽기

    f = open(myFile.txt, 'r')       # myFile.txt 파일을 읽기
    file_text = f.read()            # 파일 내용을 변수에 저장
    f.close()                       # 파일 닫기

    print(file_text)                # 변수에 저장된 데이터를 출력

    ## 구구단 만들기

    f = open('two_times_table.txt', 'w')

    for i in range(1,10) :
        format_string = " 2 * {0} = {1} \n".format(i, 2*i)
        f.write(format_string)
    f.close()

    !cat 'two_times_table.txt' 
    
    ## 문자열 한 줄씩 읽기

    f = open("two_times_table.txt", 'r')    # 파일을 읽기 모드로 열기
    line1 = f.readline()    # 한 줄씩 문자열 읽기
    line2 = f.readline()
    f.close()               # 파일 닫기
    print(line1, end="")     # 줄 바꿈 없이 문자열 출력
    print(line2, end="")

    ## while을 활용해서 문자열 한 줄씩 읽기

    f = open("two_times_table.txt", 'r')
    line = f.readline()

    while line :                # line 이 빈 문자열이면 False,  비어 있지 않으면 True
        print(line, end="")
        line = f.readline()
    f.close()

    ## for 를 활용해서 문자열 한 줄씩 읽기

    f = open("two_times_table.txt", 'r')
    for line in f:                  # 여기서 f == f.readlines()
        print(line, end="")
    f.close()
    
    ## with 을 사용해서 파일 읽기, 쓰기
    
    with open("two_times_table.txt", 'r') as f :    # ==> f = open("two_times_table.txt", 'r') 과 같음
        for line in f:
            print(line, end="")
    ```
    ###
