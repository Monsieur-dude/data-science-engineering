# 기초 통계(`Statistics`)
* 통계 사용 목적
    * 데이터 수집 및 정리, 데이터 집단의 특징을 확인
        * 중심화 경향치(`Central tendency`)
            * 평균(`average`) : 데이터의 공통점을 확인하기 위함
        * 산포도(`dispersion`, `scatter`, `spread`)
            * 분산(`variance`) : 데이터의 차이점을 확인하기 위함
* 통계에서 주로 사용되는 용어와 분석 방법
    * 상관관계(`correlation`) 
        * 상관계수(`correlation coefficient`) r, (-1 <= r <= 1) 
            * r = 0 : 관계 없음
            * r = 1 : 완벽한 양의 선형 관계
            * r = -1 : 완벽한 음의 선형관계
    * 회귀분석(`regression analysis`)
        * 독립변수와 종속변수를 설정하고 두 변수의 관계를 통계적으로 살펴보는 것
        * 과거의 데이터로서 *미래를 예측*하기 위함
    * 가설검증(`testing hypothesis`)
        * p-value(`probability`) >= 0.05
* 변수(`variable`)와 척도(`scale`)
    * 변수의 종류
        * 질적 변수(`qualitative variable`)
            * 특정 범주에 들어가 있는 변수, 예시) 종교, 직업
            * 명목변수(`nominal variable`)
                * 변수 사이에 순위가 존재하지 않음, 예시) 혈액형
            * 순위변수(`ordinal variable`)
                * 변수끼리 순위가 존재함, 예시) 성적
        * 양적 변수(`quantative variable`)
            * 수치로서 표현 가능한 변수, 예시) 키, 몸무게 등
            * 이산변수(`discrete variable`) : 연속적이지 않은, 개수를 알 수 있는 변수, 예시) 정수
            * 연속변수(`continous variable`)
                * 범위 내 무한한 값이 있는 변수, 예시) 실수
    * 척도(`scale`)의 종류
        * 명목척도(`nominal scale`)
            * 범주로만 구분지음
        * 순서척도(`ordinal scale`)
            * 변수 간 순서 혹은 대소관계가 자체만 의미가 있음
        * 간격척도(`interval scale`)
            * 변수끼리 일정한 간격을 두고 차이가 있음, 대소관계나 그 차이에도 의미가 있음, if 0 != None, 간격척도
        * 비율척도(`ratio scale`)
            * 변수 간 차이, 대소관계, 비례 등 모두 의미가 있음, if 0 == None, 비율척도
                
                척도|대소관계|차이|비율|예시
                :--:|:--:|:--:|:--:|:--:
                nominal|X|X|X|학생 번호
                ordinal|O|X|X|성적 순위
                interval|O|O|X|온도
                ratio|O|O|O|키
