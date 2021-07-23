## 제어문(**Conditionals and Loops**)
___
1. 조건문(**Conditionals**)
    > `if`, `elif`, `else` (코딩 전 흐름도(**flow chart**)를 직접 그려보는 게 실력향상에 도움이 됨)

    1. `if` : 1가지 조건만 있는 경우
        * <조건문>을 만족하면(`True`)이면 그 아래의 <코드블록>을 실행하고, 만족하지 않으면(`False`) <코드블록>을 실행하지 않음
        * <조건문> 다음에는 콜론(`:`)을 입력
        * <코드블록> 입력할 때 들여쓰기(주로 4칸)을 꼭 해야함
        * 비교연산 및 논리연산을 이용
            * 비교연산 : `==`, `!=`, `<`, `<=`, `>`, `>=`
            * 논리연산 : `A and B`, `A or B`, `not A`

    2. `if` ~ `else` : 2가지 조건만 있는 경우 ex) yes or no, True or False, 크다 or 작다 . . .
        * `else`는 항상 `if`와 함께 써야함

    3. `if` ~ `elif` ~ `else` : 3가지 이상의 조건이 있을 때, 각 조건에 따라 실행하는 코드가 다를 때 사용
        * 필요에 따라 여러 개의 `elif`를 사용할 수 있음            
        * `else`는 생략을 하고 `if` ~ `elif`만 사용할 수 있음
    4. `if` ~ `else` 속 다른 `if` ~ `else` : 중첩 조건인 경우에 사용
    5. `pass` : < 코드블록 > 을 아직 만들지 않았을 때, 조건문을 그냥 넘길 때 사용


    ###
    ```python

    # 1

    if < 조건문 > :
        < 코드블록 >

    # 2

    if < 조건문 > :
        < 코드블록1 >
    else :
        < 코드블록2 >

    # 3

    x = 75

    if x >= 90 :
        print('Pass')
    else :
        print('Fail') 

    # 4 

    if < 조건문 1 > :
        < 코드블록 1 >
    elif < 조건문 2 > :
        < 코드블록 2 >
        
        ...

    elif < 조건문 n > :
        < 코드블록 n >
    else :
        < 코드블록 m > 

    # 5

    x = 85 
    if x >= 90 :
        print("Very good!")
    elif 80 <= x < 90 :         # (x >= 80) and (x < 90)으로도 표현 가능
        print("Good!")
    else :
        print("Bad!")

    # 6

    if < 조건문 1> :
        if < 조건문 1-1 > :       # 조건 1 속 또다른 조건 1-1
            < 코드블록 1-1 >
        else :                  # 조건 1 속 또다른 조건 1-2
            < 코드블록 1-2 >
    elif < 조건문 2 > :
        < 코드 블록 2 >
    else :
        < 코드 블록 3 >

    # 7

    if x >= 90 :
        if x == 100 :           # 만약에 x = 100 으로 쓰면 int가 아닌 str으로 인식
            print('Perfect!')
        else :
            print('Very good!')
    elif 80 <= x < 90 :
        print('Good!')
        
    else :
        print('Bad!')

    # 8 

    if x >= 90 :
        pass                    # 조건에 맞더라도 pass를 썼기 때문에 작동하는 코드가 없음  
    elif 80 <= x < : 
        pass                    # 조건에 맞더라도 pass를 썼기 때문에 작동하는 코드가 없음
    else :
        print('Bad!')                    

    ```
    ###


2. 반복문(**Loops**)
    > `for`, `while` : 특정 코드를 일정 횟수 혹은 범위(`range`) 지속적으로 반복 수행하게끔 하는 명령어
    1. `for` **index** in `range` : 
        * <반복 범위> 속 첫번째 데이터가 <반복 변수>에 입력되고, <코드 블록>이 실행됨
        * <반복 범위> 는 `list` 와 `range`() 함수를 이용해 설정
            * `range`() : `range`(start, stop, step)
                * start에서 stop-1 까지 step 간격으로 진행, 정수만 사용 가능
                * `list`(`range`()): `range`() 로 만들어진 숫자를 `list`로 변환 가능
                * `range`(10) == `range`(0, 10) == `range`(0, 10, 1) : start, step 생략 가능 
        * `for` 명령문도 중첩 반복문을 만들 수 있음(ex 2차원 행렬, 구구단 ...)
            * 리스트 변수 `x`, `y` 에 [`x1`, `x2`]와 [`y1`, `y2`] 할당 : 각 요소로 이루어진 (x, y) 쌍으로 된 데이터를 얻음.
        * __*여러 개의 리스트를 <반복범위>로 가질 때,*__
            * 2 개의 리스트가 <반복 범위>에 바로 들어갈 수 없음, 따라서 `len`() 와 `range`()를 활용함 
            * `zip`() : `len`(list1) == `len`(list2) 일 경우, list1 과 list2 의 각 항목이 순서대로 동시에 입력
    

    ###
    ```python
    for <반복 변수> in <반복 범위> :    # <반복 변수> = index(i), <반복 범위> = range 
        <코드 블록>

    
    for i in range(0, 10, 1) :      # range(10) 또는 range(0, 10) 모두 같음
        print(i)
    
    print(list(range(0, 20, 5)))    # 0 ~ 20 까지 5씩 증가하는 데이터를 리스트로 출력
    print(list(range(-10, 0, 2)))   # -10 ~ 0 까지 2씩 증가하는 데이터를 리스트로 출력
    print(list(range(3, -10, -3)))  # 3 ~ -10 까지 3씩 감소하는 데이터를 리스트로 출력
    print(list(range(0, -5, 1)))    # range(0, -5)와 같음


    for < 반복 변수 1 > in < 반복 범위 1 > :
        for < 반복 변수 2 > in < 반복 범위 2 > :
            < 코드 블록 >

    
    x_list = ['x1', 'x2']
    y_list = ['y1', 'y2']

    for x in x_list :
        for y in y_list :
            print(x, y)
    
        
    # len(list1) == len(list2) 일 때,

    names = ['James', 'Robert', 'Lisa', 'Mary']
    scores = [95, 96, 97, 94]
    
    ## 방법 1

    for i in range(len(names)) :
        print(names[i], scores[i])
    
    ## 방법 2

    for i, j in zip(names, scores) :
        print(i,j)
    ```
    ###    
    
    
    2. `while` <조건문> : 
        * 조건에 만족할 경우에만 <코드 블록>을 반복 수행함. 
        * 만족하지 않을 경우는 <코드 블록> 실행하지 않고 `while` 명령문에서 빠져나옴
        * 반복 범위가 없을 때 주로 이용 (반대로, 반복 범위 있을 경우 `for` 문을 주로 씀)
        * `while` True : 항상 참(`True`)이므로 <코드 블록>이 무한히 반복 수행함. 따라서 주의!
        
    
    ###
    ```python
    while <조건문> :            # <조건문>은 주로 True or False 활용
        <코드 블록>


    i = 0
    sum = 0

    while sum < 20 :          # 조건을 확인
        i = i + 1             # i를 1씩 증가
        sum = sum + i         # 이전의 sum과 현재 i를 더해서 sum을 갱신
        print(i, sum)


    while True :              # 항상 True이므로 print("Never Do This!")를 무한 반복함, 주의할 것!
        print("Never Do This!") 
    ```
    ###    