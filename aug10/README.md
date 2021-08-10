# 기초 통계(`Statistics`)
* 1 차원 데이터 정리
    * 데이터 중심의 지표
        * 평균값(mean)
            * `np.mean`(data)
            * `sum`(data) / `len`(data)
            * 절사평균(`trimmed mean`) : 양 쪽을 자르고 나머지의 평균
                * 이상치(`outlier`) 영향이 적음
        * 중앙값(`median`)
            * `np.median`(data)
            * `pd.DataFrame`(data).`median`()
        * 최빈값(`mode`)
            * `pd.Series`(data).`mode`()
    * 데이터의 산포도(`degree of dispersion`, 흩어짐) 지표
        * 편차(`deviation`) : 각 데이터가 평균과 얼마나 떨어져 있는가
            * `np.mean`(data) - data
        * 분산(`variance`) : 편차의 제곱 합의 평균
            * `np.var`(scores)
        * 표준편차(`standard deviation`) : 분산의 제곱근
            * `np.std`(scores, ddof=0)
    * 범위(`range`), 사분위 범위(`interquartile range`)
        * 범위
            * `np.max`(data) - `np.min`(data): 최대값과 최소값의 차이
        * 사분위 범위
            * 이상치를 찾아내고, 이걸 사용할지 말지 결정하기 위함
            * 데이터 하위로부터 25%, 50%, 75%에 위치한 값. 각 각 제1사분위(Q1), 제2사분위(Q2), 제3사분위(Q3) 부름
            * 사분위 범위 IQR = Q3 - Q1
            * np.percentile(data, 25)
    * 데이터의 정규화(`normalization`) : 데이터를 통일된 지표로 변환함. 그러면 어느 데이터든 상대적 비교가 수월함
        * 표준화(`standardization`)
            * z = (np.mean(data) - data) / np.std(data)
            * 편차 / 표준편차
            * 평균은 0, 표준편차는 1
        * 편차값
            * `standardization delta` 또는 `z-score` = 50 + 10 * z(표준화)
            * 50 + 10 * 표준화된 데이터
            * 평균이 50, 표준편차가 10 이 되도록 정규화한 값            
    * 데이터의 시각화
        * 도수분포표(`frequency distribution table`)
            * 계급 (`class`)
            * 도수 (`frequency`)
            * 계급폭 (`class width`)
            * 계급수
            * 계급값 (`class value`)
* 2차원 데이터 정리
    * 두 데이터 사이의 관계를 나타내는 지표 
        * 공분산(`covariance`)
            * `np.cov`(data1, data2, ddof=0)
        * 상관계수(`correlation coefficient`)
            * `no.corrcoef`(data1, data2, ddof=0)
            * 두 데이터의 상관관계를 나타내는 지표, -1 <= `r` <= 1
    * 데이터의 시각화
        * 산점도(`scatter plot`)
        * 회귀직선(`regression line`)
 
    ###
    ```python
    import numpy as np
    import pandas as pd

    %precision 3        # 소수점 이하 3자리만 출력
    pd.set_option('precision', 3)

    df = pd.read_csv("scores_em.csv", index_col = "student number")
    df.head()           # print first 5 lines

    scores = np.array(df["english"])[:10]     # 9번째 데이터까지 슬라이싱

    scores_df = pd.DataFrame(data = scores, index=pd.Index(["A","B","C","D","E","F","G","H","I","J"], name = "student"))
    scores_df.columns = ["score"]
    
    # 데이터 중심의 지표
    ## mean
    np.mean(scores)
    scores_df.mean()            # DataFrame 으로 구성된 데이터

    ## median    
    np.median(scores)
    scores_df.median()

    
    sorted_scores = np.sort(scores)         # 데이터를 크기 순서로 나열함
    
    n = len(sorted_scores)                  # 데이터의 개수
    
    if n % 2 == 0 :                         # 데이터의 개수가 짝수일 때,
        m0 = sorted_scores[n // 2 - 1]      # 중앙값
        m1 = sorted_scores[n // 2]          # 중앙값
        median = ( m0 + m1 ) / 2            # 두 중앙값의 평균

    else :                                  # 데이터의 개수가 홀수
        median = sorted_scores[n // 2]         
    median
    
    ## mode
    pd.Series([1,1,2,3,3]).mode()
    ```
    ###

    ###
    ```python
    # 데이터 흩어짐 지표
    ## deviation
    mean = np.mean(scores)
    deviation = scores - mean                           # 편차 값이 큼 = 흩어짐의 정도가 크다
    
    another_scores = [50, 60, 58, 54, 51, 56, 57, 53, 52, 59]
    another_mean = np.mean(another_scores)
    another_deviation = another_scores - another_mean   # 편차 값이 작다 = 흩어짐의 정도가 작다

    ## variance
    np.var(scores)                                      
    np.mean(deviation ** 2)
    
    ## standard deviation
    np.std(scores)
    np.sqrt(np.var(scores, ddof=0))

    ## 범위, 사분위범위
    ### 범위
    np.max(scores) - np.min(scores)

    ### 사분위범위
    scores_Q1 = np.percentile(scores, 25)
    scores_Q2 = np.percentile(scores, 50)
    scores_Q3 = np.percentile(scores, 75)
    scores_IQR = scores_Q3 - scores_Q1

    pd.Series(scores).describe()
    ```
    ###
    ###
    ```python
    # 데이터의 정규화
    ## 표준화
    z = ( scores - np.mean(scores) ) / np.std(scores)           # 편차 / 표준편차
    
    ## 편차값
    z = 50 + 10 * ( scores - np.mean(scores) ) / np.std(scores) # 평균이 50, 표준편차는 10 으로 변환
    ```
    ###