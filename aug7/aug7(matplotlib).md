## matplotlib
___
그래프를 얻어 데이터 시각화를 위해 활용
* 그래프 종류
    * 선그래프(`line graph`)
        * plt.plot([x,] y[,fmt])
            * plt.plot(y [,fmt])
            * plt.plot(x, y [,fmt])
        * 여러 그래프 그리기
            * plt.plot(x, y1, x, y2, x, y3)
            * plt.figure() : 그래프를 하나 하나씩 그리기
                * Plt.figure(n) : n번째 그래프에 새로운 그래프 그리기
        * 그래프 출력 범위 지정
        * 그래프 꾸미기
    * 산점도(`scatter graph`)
        * plt.scatter(x, y)
    * 막대그래프(`bar graph`)
        * plt.bar(x, height)  : 수직 막대그래프
        * plt.barh(x, height) : 수평 막대그래프
    * 히스토그램(`histogram`)
        * plt.hist(x, [,bins = bins_n])
    * 파이그래프(`pie graph`)
        * plt.pie(x)
* 그래프 저장하기
    * plt.savefig(file_name)