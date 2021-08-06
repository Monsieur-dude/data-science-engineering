## NumPy
___

* 배열(`Array`)
    > 순서가 있는 같은 종류의 데이터가 저장된 집합
    * 배열 생성하기
        * np.array(seq_data) : 시퀀스 데이터에서 배열을 생성
        * np.arange([start,] stop[, step]) : 범위를 지정해서 배열을 생성
        * np.arange(seq_data).reshape(m, n) : m x n 2차원 구조의 행렬로 구조를 변경
            * arr_obj.shape() : array의 형태를 반환
        * np.linspace(start, stop[, num]) : start 부터 stop 까지 num 개수의 데이터를 갖는 배열 생성, num 기본값은 50 
        * 모든 원소가 0 또는 1인 다차원 행렬
            * arr_zeros_n = np.zeros(n), arr_zeros_mxn = np.zeros((m, n))
            * arr_ones_n = np.ones(n), arr_ones_n = np.ones((m, n))            
        * 단위행렬(`Identity matrix`) : 어떤 행렬과도 곱해도 자기 자신이 나오게 하는 행렬, 1과 같은 역할
            * np.eye(n) : n x n 의 단위행렬을 갖는 2차원 배열
        * 배열의 데이터 타입 변환
            * arr_obj.astype(dtype)
        * 난수 배열을 생성
            * np.random.rand(m,n) : 0 ~ 1 사이의 실수로 된 난수를 m x n 형태로 출력
            * np.random.randint([low,]high[,(m,n)]) : low ~ high 까지 m x n 형태에 정수로 된 난수배열을 생성
    * 배열의 연산
        * 배열의 형태(shape)가 같다면, 연산이 가능함
            * 기본 연산 : 사칙연산, 비교연산이 가능함
            * 통계를 위한 연산 : sum(), mean(), min(), max(), std(), var(), cumsum(), cumprod() 이외에 여러 메서드가 존재함
            * 행렬 연산 
                * 행렬 A 와 B가 있을 때...
                    * `np.dot`(A,B) 또는 `A.dot`(`B`) : 행렬곱(`matrix product`)
                    * `np.transpose`(A) 또는 `A.transpose`() : 전치행렬(`transpose matrix`)
                    * `np.linalg.inv`(A) : 역행렬(`inverse matrix`)
                    * `np.linalg.det`(A) : 행렬식(`determinant`)
    * 배열의 인덱싱, 슬라이싱            
        * 배열 인덱싱
            * np.array[`i`], np.array[[`i`, `j`, `k`]]
            * 배열이 2차원일 경우,
                * np.array[`[row_1, row_2, ..., row_n]`, `[column_1, column_2, ..., column_n]`] == [[행1, 행2, ..., 행n], [열1, 열2, ..., 열n]]
            * 배열에 조건을 지정할 수 있음
                * array_name[condition]
        * 배열 슬라이싱
            * np.array[i_start : i_end]
            * 배열이 2차원일 경우,
                * np.array[`row_start : row_end`, `column_start : column_end`]
    
    ###
    ```python
    ## 시퀀스 데이터에서 배열을 생성
    
    import numpy as np

    data1 = [0, 1, 2, 3, 4, 5]
    a1 = np.array(data1)
    
    data2 = [0.1, 5, 4, 12, 0.5]
    a2 = np.array(data2)           # int, float 섞여있을 땐, float으로 모두 변환

    ## 범위를 지정해서 배열을 생성
    np.arange(0, 10, 2)            # array([0, 2, 4,  6, 8])
    np.arange(1, 10)               # array([1, 2, 3, 4, 5, 6, 7, 8, 9])
    np.arange(5)                   # array([0, 1, 2, 3, 4])
    
    ## 1차원 array 에서 2차원 행렬로 구조를 변경
    np.arange(12).reshape(4, 3)
    b1 = np.arange(12).reshape(4,3)
    b1.shape                       # 결과값 (4,3)
    b2 = np.arange(7)
    b2.shape                       # 결과값 (7, )
    
    ## np.linspace()
    np.linspace(1, 10, 10)         # array([ 1.,  2.,  3.,  4.,  5.,  6.,  7.,  8.,  9., 10.])
    np.linspace(0, np.pi, 3)

    ## np.zeros(n), np.zeros((m, n)), np.ones(n), np.ones((m, n))
    np.zeros(6)
    np.zeros((3,2))                # np.zeros(6).reshape(3,2) 과 동일함
    np.ones(10)
    np.ones((2,5))                 # np.ones(10).reshape(2,5) 과 동일함
    
    ## 단위행렬(identity matrix)
    np.eye(3)                      
    np.eye(3).shape                # 결과값 (3, 3)
    np.eye(8)
    np.eye(8).shape                # 결과값 (8, 8)

    ## arr_obj.astype(dtype)
    str_a1 = np.array(['1.567', '0.123', '5.123','9', '8'])
    num_a1 = str_a1.astype(float)
    num_a1

    str_a1(dtype)                  # 결과값 dtype('<U5')
    num_a1(dtype)                  # 결과값 dtype('float64')
    
    ## 난수 배열의 생성
    np.random.rand()
    np.random.rand(2,3,4)
    np.random.randint(1, 10, (2,4))
    np.random.randint(25)
    ```
    ###
    ###
    ```python
    ## 배열의 연산
    # 기본연산
    arr1 = np.array([10, 20, 30, 40])
    arr2 = np.array([5, 10, 15, 20])

    arr1 + arr2
    arr1 - arr2
    arr1 * arr2
    arr1 / arr2
    arr1 **2 / arr2
    arr1 > 15 
    arr2 <= 20
    
    # 통계에 사용되는 연산
    arr3 = np.array([1,3,5,7,9])
    
    arr3.sum()
    arr3.mean()
    arr3.std()                     # 표준편차   standard deviation
    arr3.var()                     # 분산      variation
    arr3.cumsum()
    arr3.cumprod()

    # 행렬 연산
    A = np.array([0,1,2,3]).reshape(2,2)
    B = np.array([3,2,0,1]).reshape(2,2)
    np.dot(A,B)                    # A.dot(B) 와 같음
    np.dot(B,A)                    # B.dot(A) 와 같음
    np.transpose(A)                # A.transpose()
    np.transpose(B)                # B.transpose()
    np.linalg.inv(A)
    np.linalg.det(B)
    ```
    ###
    ###
    ```python
    ## 배열의 인덱싱
    # 1차원 배열 인덱싱
    a1 = np.array([0,10,20,30,40,50])
    a1[3]                          # 30
    a1[5] = 70
    a1                             # [0,10,20,30,40,70]
    a1[0, 2, 3]                    # [0,20,30]

    # 2차원 배열 인덱싱
    a2 = np.array(10, 100, 10).reshape(3,3)         # array([[10, 20, 30],
                                                    #        [40, 50, 60],
                                                    #        [70, 80, 90]])
    a2[0,2]                        # 30                       
    a2[2,2] = 95                   # 90 -> 95
    a2[1]                          # array([40, 50, 60])
    a2[1] = np.array([45,55,65])   # array([45, 55, 65])
    a[[0,2], [0,1]]                # array([10, 80])
    

    # 조건에 맞는 배열 인덱싱
    a = np.array[1, 2, 3, 4, 5, 6]
    a[a > 3]                       # array([4,5,6])
    a[(a % 2) = 0]                 # array([2,4,6])
    
    ## 배열의 슬라이싱
    # 1차원 배열 슬라이싱

    b1 = np.arange(0,60,10)        # array[0, 10, 20, 30, 40, 50]
    b1[1:4]                        # array([10, 20 ,30])
    b1[:3]                         # array([0, 10 ,20])
    b1[2:]                         # array([20, 30, 40, 50])
    
    b1[2:5] = np.array([25,35,45]) # array([0, 10, 25, 35, 45, 50])
    b1[3:6] = 60                   # array([0, 10, 25, 60, 60, 60])
    
    # 2차원 배열 슬라이싱
    b2 = br.arange(10,100,10).reshape(3,3)         # array([[10, 20, 30],
                                                   #        [40, 50, 60],
                                                   #        [70, 80, 90]])
    
    b2[1:3, 1:3]                                   # array([[20, 30],
                                                   #        [50, 60],
                                                   #        [80, 90]])
    
    b2[1][0:2]                                     # array([40, 50])
    
    b2[0:2, 1:3] = np.array([[25, 35], [55, 65]])  # array([[10, 25, 35],
                                                   #        [40, 55, 65],
                                                   #        [70, 80, 90]])
    ```
    ###