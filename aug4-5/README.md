## 객체와 클래스(`objects and classes`)
___
* 객체(`object`)
    > 속성과 행위로 구성된 대상을 의미함. 프로그래밍에선 변수(속성)와 함수(행위,기능)의 묶음
    * 클래스 선언(`class declaration`) 
        * 설계도에 해당하는 클래스(`class`)를 선언해야만 객체를 생성할 수 있음
        * `class` *`Class_name`*() : 기능, 행위등을 설정하기 위함
        * class Bicycle() :
    * 클래스 생성 및 활용
        * 예시) 자전거 클래스, *`Bicycle()`*
            * `object_name` =  *`Class_name`*
                * 클래스 선언 후에, 객체를 생성할 수 있음
                * my_bicycle = Bicycle
            * `object_name.variable_name` 
                * my_bicycle.wheel_size, my_bicycle.color 
                * 속성 : 바퀴 크기, 색상
            * `def function`(`self, factor`)
                * my_bicycle.move(30), my_bicycle.turn("right")
                * 기능 : 이동, 좌/우 회전, 정지
            * `def __init__`(`self, f1, f2, f3, ..., fn`)
                * 객체 초기화 함수, 클래스를 설정하면서 객체의 속성을 바로 설정할 수 있음
                * my_bicycle = Bicycle(26, "Black")
    * 클래스 속 변수(`variable`)와 함수(`function`)
        * 변수(`variable`)
            * *`Class_name`*.variable_name : 클래스 내 전체에 적용되는 변수
            * `self`.variable_name : 특정 인스턴스 내에만 적용되는 변수
        * 함수(`function`)
            * 인스턴스 메서드(`instance method`)
                * 인스턴스 내에서만 작동하는 함수
                * `def` method_name(`self`, f1, f2, ...)
                * `__init__` 도 인스턴스 함수
                * `self`.method_name() 
            * 정적 메서드(`statice method`)
                * 클래스나 인스턴스에 무관하게 작동하는 함수
                * `@staticmethod` 를 입력해야 함
                * `def` method_name(f1, f2, ...)
                * 시간, 달력, 환율, 단위변환 등
                * *`Class_name`*.method_name() 
            * 클래스 메서드(`class method`)
                * 클래스 내에서만 작동하는 함수
                * `def` method_name(`cls`, f1, f2, ...)
                * `@classethod` 를 입력해야 함
                * 생성된 전체 객체의 수 등 클래스 전체를 관리하는 함수로 주로 이용
                * *`Class_name`*.method_name()
    * 클래스 상속(`class inheritance`)
        * 부모(`parent class, super class`), 자식 클래스(`child class, sub class`) 
        * 자식클래스는 부모 클래스의 속성, 메소드를 그대로 이어받거나 자식 클래스 내에 따로 추가할 수 있음
        * `class` *`ChildClass`*(`ParentClass`) :

    ### 
    ```python
    ## 클래스 선언

    class Class_name() :
        variable1
        varibale2
        ...
        variablen
        def func1(self, f1, f2, ..., fn) :
            < 코드 블록 >
        def func2(self, f1, f2, ..., fn) :
            < 코드 블록 >
    
    ## Bicycle class

    class Bicycle() :
        pass
    
    ## 객체 생성

    my_bicycle = Bicycle() # my_bicycle 은 Bicycle 의 인스턴스
    
    ## 객체에 속성(변수)을 설정

    my_bicycle.wheel_size = 26
    my_bicycle.color = 'Black'

    print("Wheel Size :", my_bicycle.wheel_size)
    print("Color: ", my_bicycle.color)

    ## 객체 기능(함수)을 설정

    class Bicycle() :

        def move(self, speed) :
            print("Bicycle: moving forward {} per hour".format(speed))
        def turn(self, direction) :
            print("Bicycle: {} turn".format(direction))
        def stop(self) :
            print("Bicycle({}, {}): stop".format(self.wheel_size, self.color)

    ## __init__ 함수를 설정

    class Bicycle() :

        def __init__(self, wheel_size, color) :
            self.wheel_size = wheel_size
            self.color = color     

        def move(self, speed) :
            print("Bicycle: moving forward {} per hour".format(speed))
        def turn(self, direction) :
            print("Bicycle: {} turn".format(direction))
        def stop(self) :
            print("Bicycle({}, {}): stop".format(self.wheel_size, self.color)

    my_bicycle = Bicycle(25, "Black")
    your_bicycle = Bicycle(35, "Red")

    ## class variable, instance variable

    class Car() :
        instance_count = 0      # 클래스 변수, 클래스 내 모든 영역에 적용됨
    
        def __init__(self, size, color) :
            self.size = size     # 인스턴트 변수 생성
            self.color = color   # 인스턴트 변수 생성
            Car.instance_count = Car.instance_count + 1
            print("The number of cars now is {}".format(Car.instance_count))

    car1 = Car("Big", "Red")
    car2 = Car("Middle", "Blue")
    ```
    ###

    ###
    ```python
    ## 클래스 속 변수
     
    class Car2() :
        count = 0
        
        def __init__(self, size, num) :
            self.size = size
            self.count = num
            Car2.count = Car2.count + 1
            
            print("Counting...{} car(s)".format(Car2.count))            # 클래스 변수 적용됨
            print("Counting for instance... {}".format(self.count))      # 인스턴스 변수 적용됨

    car1 = Car2("Middle-small", 5)
    car2 = Car2("Biggest", 100)

    ## 클래스 속 함수

    class Car() :
        instance_count = 0                      # 클래스 변수 

        def __init__(self, size, color) :       # 인스턴스 함수
            self.size = size
            self.color = color
            Car.instance_count = Car.instance_count + 1

        @staticmethod                           # 데코레이터
        def check_type(model_code) :            # 스태틱 함수
            if model_code >= 20 :
                print("This is electric vehicle")
            elif 10 <= model_coe < 20 :
                print("This is gasolin-based vehicle")
            else :
                print("This is diesle-based vehicle")

        @classmethod                            # 데코레이터
        def count_instance(cls) :               # 클래스 함수
            print("The number of car(s) is: {}".format(cls.instance_count))

    Car.count_instance()                        # 인스턴스 개수 : 0

    car1 = Car("small", "red")                  # 첫번째 객체 추가
    Car.count_instance()                        # 총 인스턴스 개수 1

    car2 = Car("big", "green")                  # 두번째 객체 추가
    Car.count_instance()                        # 총 인스턴스 개수 2
    ```
    ###

    ###
    ```python
    ## 클래스 상속 (Class inheritance)

        class Bicycle() :                                            # Super class

        def __init__(self, wheel_size, color) :
            self.wheel_size = wheel_size
            self.color = color     
        def move(self, speed) :
            print("Bicycle: moving forward {} per hour".format(speed))
        def turn(self, direction) :
            print("Bicycle: {} turn".format(direction))
        def stop(self) :
            print("Bicycle({}, {}): stop".format(self.wheel_size, self.color)
    
    
        class FoldingBicycle(Bicycle) :                             # Sub class
            def __init__(self, wheel_size, color, state) :      # sub class에 state 속성 추가
                
                Bicycle.__init__(self, wheel_size, color)           # super().__init__(wheel_size, color) 로 대체 가능
                self.state = state

            def fold(self) :            # sub class 에 메서드 추가
                self.state = "folding"
                print("Bicycle : folding, state = {}".format(self.state))

            def unfold(self) :          # sub class 에 메서드 추가
                self.state = "unfolding"
                print("Bicycle : unfolding, state = {}".format(self.state))
    
    ```
    ###