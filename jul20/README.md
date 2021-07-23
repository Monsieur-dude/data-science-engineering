## 변수(**variable**)와 자료형(**data type**)

___
1. 변수(**variable**)
    > 어떤 문자를 내가 원하는 데이터 타입으로 변형시킬 때 사용 ex)  `int` a -> 정수형 데이터 타입의 변수 a, `float` f -> 실수형 데이터 타입의 변수 f
    * 변수를 활용하면 숫자나 문자를 반복적으로 쓸 필요가 없어 변수를 효율적으로 연산을 할 수 있음
    * 컴퓨터의 임시 저장 공간(메모리)에 저장
    * 등호(=)를 통해 변수를 지정함 ex) a = 30, b = Hello World c = [a, b, c] ...
    * 변수는 문자, 숫자, 밑줄 (**_**) 사용함 ex) a, book1, my_student2, mydog_, my_number
        ###

        1. 대소문자 구분
        2. 숫자로 시작할 수 없음
        3. 공백 포함하지 않음
        4. 밑줄 (**_**)외 기호는 사용 불가
        5. 예약어(**Reserved word**)는 변수로 사용 불가 ex) _None, True, False, and, as, assert, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield_    
        ###

2. 문자열(**string**, `str`)
    > ' ', " ", ''' ''' 로 둘러쌓은 문자의 집합 ex) 'Hello World', 'Macbook Air 2020' 
    * `type`() = `str`
    * 문자열끼리 덧셈, 곱셈이 가능
    ###
``` python
    a = 'Enjoy '
    b = 'python!'
    c = a + b
    d = 3 * a
    
    type(a)												# str
    print(c)											# Enjoy python!
    print(d)											# Enjoy python!Enjoy python!Enjoy python!
```
###

3. 리스트(`list`)
    > 순서가 있는 데이터의 나열, 수정이 가능함
    * `list`[]
        * 숫자, 문자열, 불, 리스트 등 여러 데이터 타입을 넣을 수 있음
        * 리스트 속 각 값의 데이터 타입은 달라도 상관 없음 ex) [1, 'apple', [1,2,3], True]
        * 데이터가 없는 빈 리스트 생성 가능(받아 올 데이터가 어느 정도일지 모를 때 유용함)
        * 여러 개의 리스트 덧셈, 곱셈이 가능
    * `list` 기능
        * `list`[i] 리스트의 인덱스 값
        * `list`[i] = new_data 
            * 기존 데이터를 새 데이터로 변경 가능
        * `list`[**i_start:i_end:i_stem**]
            * i_start 부터 (i_end-1) 까지 리스트를 i_stem 간격으로 데이터를 가져옴
        * `del` `list`[i] 리스트 인덱스 데이터 삭제
        * `i` in `list`[]
            * boolean 으로 출력 
    * 메서드(`method`)
        1. .`apprend`() 리스트 마지막 인덱스에 데이터를 추가
        2. .`insert`(i, data) i번째 인덱스에 data를 추가하고 나머지 데이터들은 인덱스가 하나씩 뒤로 밀림
        3. .`extend`([data1, data2, data3, ...]) 리스트 확장

###
```python
    list1 = []
    type(list1)
    
    student1 = [10, 9, 8, 7, 6]
    student1 [0]              # 10
    student1 [4]              # 6
    student1 [2] = 300        # 2번째 index를 300으로 바꿈
    student1 [-1] = 50000     # -1번째 index를 50000으로 바꿈
    print(student1)           # [10,9,300,7,50000]
    student1 [0:2]            # [10, 9, 8]
```
###

4. 튜플(`tuple`)
    > 순서가 있는 데이터의 나열, 튜플 속 데이터를 수정할 수 없음(`list`와 차이점)
    * `tuple`()
        * 데이터 처리 속도에서 효율적이기 때문에 머신러닝, 딥러닝 시 `list` -> `tuple` 로 변경시켜 관리
        * `list` 와 특징이 매우 유사함
        * `tuple` 속 데이터는 변경, 삭제 불가
    * `tuple` 기능
    * 메서드(`method`)
        1. .`index`(data) data 인덱스 값 
        2. .`count`(data) data 개수
                ###
```python
    tuple1 = (10, 150, 702, 3054, 33, 10, 10)
    type(tuple1)
    tuple1.index(150)  # data 150의 인덱스 위치 1
    tuple1.count(10) # 10의 갯수 3개
```
###


5. 세트(`set`)
    > 수학에서 집합이라는 개념과 유사
    * `set` = {}
        * 데이터의 순서가 없고, 데이터가 중복될 수 없음
        * 교집합, 합집합, 차집합 등이 있고, 메서드를 통해 구현 가능

    * 세트의 종류 및 구현 방법
        1. 교집합(intersection) : `A ∩ B` 또는 `A & B`, `and` 의 개념, A.`intersection`(B)
        2. 합집합(union) : `A ∪ B` 또는 `A | B`, `or` 의 개념, A.`union`(B)
        3. 차집합(difference) : A - B, `A ^ B`, A.`difference`(B)

    * 리스트, 튜플, 세트 간 타입 변환
        * `list`(), `tuple`(), `set`() 이용해서 변환 가능

###

```python
set1 = {1, 2, 3}
set2 = {1, 2, 3, 3}

type(set1)                  # set
print(set1)                 # {1, 2, 3}
print(set2)                 # {1, 2, 3} 중복된 3은 한 번만 출력

A = {1, 2, 3, 4, 5}         # set A
B = {4, 5, 6, 7, 8, 9, 10}  # set B
A.intersection(B)           # A ∩ B , {4, 5}
A.union(B)                  # A ∪ B , {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
A.difference(B)             # {1, 2, 3}


a = [1, 2, 3, 4, 5]
type(a)                     # list
print(a)                    # [1, 2, 3, 4, 5]
b = tuple(a)
type(b)                     # tuple
print(b)                    # (1, 2, 3, 4, 5)
c = set(a)
type(c)                     # set
print(c)                    # {1, 2, 3, 4, 5}
```
###


6. 딕셔너리(`dict`)
    > `key` 와 `value` 값이 쌍으로 구성
    * `dict`{key0:value, key1:value, key2,value} 
        * `key` 와 `value` 가 쌍으로 구성되어있기 때문에, 데이터의 순서가 없음
        * 인덱스가 아닌 `key`, `value` 로 데이터를 찾고 다룰 수 있음
        * JSON 형태의 데이터
        * `key` 는 숫자(`int`, `float`)와 문자열(`str`), `value` 는 어떤 데이터 형태(`type`)도 가능함 
    * `dict` 기능
        * `dict`[`key`] = `value` 
            * 새로운 `key` 혹은 기존의 `key` 를 변경
        * `del` `dict`[`key`]
            * `key` 와 그에 해당하는 `value` 값을 삭제
    * 메서드(`method`)
        > 메서드 활용하여 주로 `list`()로 변형함
        1. .`keys`()   `key` 를 `dict_keys` 타입으로 출력 
        2. .`values`()   `value` 를
        `dict_values` 타입으로 출력
        3. .`items`()   `key`와 `value`를 한 쌍으로 하는 `tuple` 형태의 `dict_items` `type` 으로 나옴
        4. .`clear`() 모든 `key`, `value` 를 삭제함
        5. .`update`(`dict_new`) 기존에 있는 딕셔너리에 `dict_new`를 추가함
                ###

```python
    dict1 = {1:'seoul', 2:'busan', 3:'daegu', 4:'ulsal',5:'suwon'}  
    type(dict1) # dict
    
    dict1[100] = 'japan' 
    print(dict1) # dict1 = {1:'seoul', 2:'busan', 3:'daegu', 4:'ulsal',5:'suwon', 100:'japan'}
    
    del dict1[3]
    print(dict1) # dict1 = {1:'seoul', 2:'busan', 4:'ulsal',5:'suwon'}
    
    
    ## .keys()
    dict1.keys() # dict_keys ([1, 2, 4, 5, 100])
    type(dict1.keys()) # dict_keys
    dict1_keys = list(dict1.keys()) # dict1 의 key 를 list 타입으로 변경
    print(dict1_keys) # [1, 2, 4, 5, 100]
    
    ## .values()
    dict1.values() # dict_values ([seoul, busan, ulsal, suwon, japan])
    type(dict1.values()) # dict_values
    dict1_values = list(dict1.values()) # dict1 의 value 를 list 타입으로 변경
    print(dict1_values) # [seoul, busan, ulsal, suwon, japan]
    
    ## .items()
    dict1.items() 		s# dict_items ([(1, 'seoul', (2, 'busan'), (4, 'ulsal'), (5, 'suwon'), (100, 'japan')])
    type(dict1.items()) # dict_items
    dict1_items = list(dict1.items()) # key 와 value 쌍으로 존재하는 튜플을 한 데이터로 갖는 list 타입으로 변경 
    print(dict1_items) # [(1, 'seoul', (2, 'busan'), (4, 'ulsal'), (5, 'suwon'), (100, 'japan')]
    
    ## .clear()
    print(dict1.clear()) # {}
    
    ## .update()
    
    dict1_new = {1000: 'barcelona', 500: 'paris', 32: 'paros', 9999: 'lyon'}
    dict1.update(dict1_new) # 기존에 있는 dict1 딕셔너리에 dict1_new 를 추가함
    print(dict1) # {1: 'seoul',2: 'busan',4: 'ulsal',5: 'suwon', 32: 'paros', 100: 'japan', 500: 'paris', 1000: 'barcelona', 9999: 'lyon'}
```
###