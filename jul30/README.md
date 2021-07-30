## 문자열과 텍스트파일 데이터 다루기
___
* 문자열 다루기
    * 메소드(**method**) 종류
        * str.`split`([sep]), str.`split`([sep], maxsplit=n) 
            * 문자열을 구분자(separator)을 기준으로 문자열을 분리해 **리스트**로 반환
            * 대괄호는 [] 생략 가능, 구분자를 안 쓸 경우 문자열 사이에 있는 공백과 \n 를 제거하고, 분리된 문자열을 담은 리스트로 반환
            * str의 앞에서부터 n번째까지만 나누고, 리스트로 반환
        * str.`strip`([chars]])
            * 문자열 양쪽의 공백, 특수문자, 문자열을 제거할 수 있음
            * .`rstrip`(), .`lstrip`()
        * " ".`join`(seq)
            * 리스트의 모든 항목을 하나의 문자열로 만들 수 있음
        * str.`find`(search_str), str.`find`(search_str, start, end)
            * search_str 과 처음으로 일치하는 str의 위치를 출력
            * search_str 없으면 -1 을 출력    
            * 검색하려는 문자 위치의 start, end 지정 가능
            * end 는 생략 가능
        * str.`count`(search_str), str.`count`(search_str, start, end)
            * 찾으려는 문자열이 해당 범위 안에서 몇 번이나 나타나는지 확인
        * str.`startswith`(prefix), str.`startswith`(prefix, start, end)
            * prefix로 시작된 문자열을 찾기
        * str.`endswith`(suffix), str.`endswith`(suffix, start, end)
            * suffix 로 끝나는 문자열 찾기
        * str.`replace`(old, new), str.`replace`(old, new, count)
            * old 를 new 로 바꿈
        * str.`isalpha`(), str.`isdigit`(), str.`isnum`(), str.`isspace`(), str.`isupper`(), str.`islower`()
            * 알파벳만 존재, 숫자만 존재, 문자와 숫자만 존재(str.`isnum`()), 공백만 존재, 대문자만 존재, 소문자만 존재
            * 반환 값은 `True` 와 `False` 나옴
        * str.`upper`(), str.`lower`()
            * 대문자, 소문자로 바꿔줌

    ###        
    ```python
    ## str.split(maxsplit=n)

    "에스프레소 아메리카노 카페라떼 카푸치노".split(maxsplit=2) # 반환값 : ["에스트레스", "아메리카노", "카페라떼 카푸치노"]

    phone_number = "+82-01-2345-6789"
    split_num = phone_number.split("-", 4)      # ["+82", "01", "2345", "6789"]

    ## str.strip()

    str = "   Python   "
    str.strip()

    str = "aaaaPythonaaaa"
    str.strip("a")

    str = "#$$$$##$Python$$$###"
    str.strip("#$") 

    ## str.split(), str.strip() 응용

    coffee_menu = " bbaEspressoaaa, aaabbAmericanoabab,  ababCaffe Lattebbba   , bbbbCappuccinoaaa   "
    coffee_menu_list = coffee_menu.split(",")

    coffee_list = []
    for coffee in coffee_menu_list :
        temp1 = coffee.strip()
        temp2 = temp1.strip("ab")
    
    coffee_list.append(temp2)

    coffee_list             # 반환값 : ['Espresso', 'Americano', 'Caffe Latte', 'Cappuccino']

    ## .join(seq)

    coffee_str = " ".join(coffee_list)
    coffee_str              # 반환값 : 'Espresso, Americano, Caffe Latte, Cappuccino'


    ## str.find(search_str)

    coffee_str.find("sso")          # 반환값 : 5
    coffee_str.find("Americano")    # 반환값 : 7
    coffee_str.find("Cold Brew")    # 반환값 : -1
    
    ## str.find(search_str, start, end)

    coffee_str.find("af",0,25)      # 반환값 : 22
    coffee_str.find("af",40,44 )    # 반환값 : -1

    ## str.count(search_str), str.count(search_str, start, end)

    str_python = "Python is powerful. Python is easy to learn. Python is open"
    str_python.count("Python")      # 반환값 : 3
    str_python.count("Python", 0, 20) # 반환값 : 1

    ##  str.startswith(prefix), str.endswith(suffix)

    str_python.startswith("Python") # 반환값 : True
    str_python.startswith("is")     # 반환값 : False
    
    str_python.endswith("open")     # 반환값 : True
    str_python.endswith("is")       # 반환값 : False
    
    ## str.replce(old, new, count)
    
    str_python.replace("Python", "Java")
    str_python.replace("Python", "Java", 1)
    str_python.replace("Python", ' ')
    
    ```
    ###
* 텍스트 파일 속 데이터를 다루기