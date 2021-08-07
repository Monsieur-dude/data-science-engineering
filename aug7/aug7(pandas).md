## pandas
___

* Series 데이터 구조
    * 데이터 내 데이터 타입이 달라도 사용할 수 있음
    * `pd.Series`([seq_data])
    * `index` 와 `value` 로 구성됨
    * 날짜 자동 생성
        * `pd.date_range`(start="", end="", periods=, freq="")
            * 시작날짜, 끝나는 날짜, 얻고자 하는 데이터의 개수, 주기설정 
            * [![Frequency](https://t1.daumcdn.net/cfile/tistory/9950C43F5E046BEB09)](https://rfriend.tistory.com/503)
                * D(Day), B(Business), W(Week), M=Month(월말), S=Start(월초), Q=Quarter(분기말), A=Annual(연말), H(Hour), T, min(minute), s(second)
                
            * pd.Series([seq_data, index = index_seq])
    * DataFrame으로 데이터 생성
        * `pd.DataFrame`(data[, index=index_data, columns=columns_data])
        * `index`(세로축 라벨), `columns`(가로축 라벨), `values`(그 외 데이터)
            * [![DataFrame](https://dandyrilla.github.io/images/2017-08-12/fig0.png)](https://dandyrilla.github.io/2017-08-12/pandas-10min/)
            * **data의 행 개수와 index 요소의 개수, data 열 개수와 columns 요소의 개수가 같아야 함**
            * DataFrame 간 사칙연산도 가능, 연산을 못하는 부분은 `NaN`(Not a Number)으로 출력
            * pd.DataFrame`.mean`(), `.std`(), `.min`(), `.max`() 등 여러 메서드 사용 가능
            * `.describe`() 통계에 사용되는 여러 값을 구함
            * `.describe()`.T 하면 index 와 columns을 바꿈 
    * 데이터를 원하는 대로 선택하기
    * 데이터 통합
        * index 증가하는 방향으로
        * columns 증가하는 방향으로
        * 특정 column 을 기준으로 
    * 데이터 파일을 읽기, 쓰기
    ###
    ```python
    ## Series를 활용해 데이터 생성
    import pandas as pd
    
    s1 = pd.Series([10,20,30,40])
    s1
    s1.index 
    s1.values

    ## 데이터에 특정 원소 없음을 표시
    import numpy as np
    
    s2 = pd.Series([np.nan,10,30])          # NaN == Not a Number
    s2

    ## 날짜 자동 생성
    pd.date_range(start='2021/08/01', end='2021/09/01)
    pd.date_range(start='2021/08/01', periods=20, freq="B") 
    pd.date_range(start='2021/08/01', freq="BH") 
    
    

    index_date = pd.date_range(start='2021/08/01', periods=5, freq="D")
    pd.Series([51,62,55,49,58], index=index_date)


    ```