# display()
Displays an overview containing descriptive stats for the Series provided.

테스트 결과를 텍스트 형태로 보여주는 함수

## 전체 항목

```
res.display()

Stat                 SPY
-------------------  ----------
Start                2006-02-05
End                  2022-07-11
Risk-free rate       0.00%

Total Return         318.85%
Daily Sharpe         0.54
Daily Sortino        0.83
CAGR                 9.11%
Max Drawdown         -55.17%
Calmar Ratio         0.17

MTD                  1.85%
3m                   -12.28%
6m                   -17.60%
YTD                  -18.50%
1Y                   -10.52%
3Y (ann.)            10.46%
5Y (ann.)            11.59%
10Y (ann.)           13.22%
Since Incep. (ann.)  9.11%

Daily Sharpe         0.54
Daily Sortino        0.83
Daily Mean (ann.)    10.72%
Daily Vol (ann.)     19.93%
Daily Skew           -0.09
Daily Kurt           14.82
Best Day             14.51%
Worst Day            -10.94%

Monthly Sharpe       0.65
Monthly Sortino      1.06
Monthly Mean (ann.)  9.84%
Monthly Vol (ann.)   15.16%
Monthly Skew         -0.65
Monthly Kurt         1.41
Best Month           12.70%
Worst Month          -16.51%

Yearly Sharpe        0.55
Yearly Sortino       1.02
Yearly Mean          10.22%
Yearly Vol           18.67%
Yearly Skew          -1.16
Yearly Kurt          1.43
Best Year            32.30%
Worst Year           -36.78%

Avg. Drawdown        -1.73%
Avg. Drawdown Days   21.17
Avg. Up Month        3.18%
Avg. Down Month      -3.96%
Win Year %           81.25%
Win 12m %            82.89%
```

## 항목별

```
Start                2006-02-05
End                  2022-07-11
Risk-free rate       0.00%
```
### Risk-free rate

무위험 수익률. 일반적으로 정기예금, 국채 등의 수익률.

https://www.investopedia.com/terms/r/risk-freerate.asp

아래 함수로 설정 가능
```
res.set_riskfree_rate(0.03)
```

argument는 float으로, 0.03은 3%를 의미

risk-free rate를 입력시 다른 값은 변화가 없지만, sharpe 지수와 sortino  지수만은 변한다.

이 둘을 계산할 때 무위험 수익률을 사용하기 때문.

잘 설명된 블로그 링크: https://jack-jack.tistory.com/196

```
Total Return         318.85%
Daily Sharpe         0.54
Daily Sortino        0.83
CAGR                 9.11%
Max Drawdown         -55.17%
Calmar Ratio         0.17
```

### Total Return

전략기간동안의 누적 수익률

### CAGR

연평균 수익률

### Max Drawdown (MDD)

최대 낙폭.

포트폴리오를 운영시 고점에서 최대 얼마나 떨어졌는지를 나타냄

낙폭이기 때문에 항상 마이너스값으로 표기

예제의 SPY는 전략기간동안  -55.17% 가 빠졌다는 뜻

포트폴리오의 효과를 측정하는 대표적인 척도 중 하나

### Calmar ratio

MDD 대비 수익률을 측정하는 지수

무위험 수익률을 사용하지 않아, risk-free ratio 설정과 관계 없이 수치가 동일

https://www.investopedia.com/terms/c/calmarratio.asp

```
MTD                  1.85%
3m                   -12.28%
6m                   -17.60%
YTD                  -18.50%
1Y                   -10.52%
3Y (ann.)            10.46%
5Y (ann.)            11.59%
10Y (ann.)           13.22%
Since Incep. (ann.)  9.11%
```

### MTD

Month To Date의 약자로, 이달초부터 현시점까지의 누적수익률

즉, 이번달 수익률임

### YTD

Year to Date의 약자로, 연초부터 현시점까지의 누적수익률

즉, 올해 수익률

### 3m, 6m, 1Y, 3Y, 5Y, 10Y

3개월, 6개월, 1년, 3년, 5년, 10년 수익률

(ann.)이 붙은 건 연환산 수익률

### Since Incep.

Inception Date, 시작일로부터의 누적 수익률

```
Daily Sharpe         0.54
Daily Sortino        0.83
Daily Mean (ann.)    10.72%
Daily Vol (ann.)     19.93%
Daily Skew           -0.09
Daily Kurt           14.82
Best Day             14.51%
Worst Day            -10.94%
```

구간별 분석은, Daily, Monthly, Yearly 로 보여줌

구간만 다르고 항목은 같다

### Mean (ann.)
### Vol (ann.)

이 두개는 정확히 무슨 뜻인지 모르겠다 ㅜ.ㅠ

### Skew

skewness의 약자로, 왜도를 의미

분포가 정규분포에 비해서 얼마나 비대칭인지 나타내는 척도

대략 +/- 2 정도면 치우침이 없는 것으로 간주한다.

### Kurt

Kurtosis의 약자로, 첨도를 의미

이 값이 크면 (보통 3보다) 아웃라이너가 많다는 것을 의미

Skew, Kurt를 제대로 이해하려면 통계학적 지식이 필요해 보인다.

잘 설명된 블로그를 링크: https://m.blog.naver.com/yk60park/222100758577

찾다보니 왜도와 첨도와 주식수익률에 관한 논문도 있다.

요약을 보면, 장기투자에서 왜도와 수익률의 관계는 유의미하지 않고, 첨도와 수익률을 양의 관계에 있다고 한다.

https://www.dbpia.co.kr/Journal/articleDetail?nodeId=NODE08783041

### Best day, Worst day

최고 수익률, 최악 수익률을 기록한 날의 수익률

```
Avg. Drawdown        -1.73%
Avg. Drawdown Days   21.17
Avg. Up Month        3.18%
Avg. Down Month      -3.96%
Win Year %           81.25%
Win 12m %            82.89%
```
### Avg. Drawdown

평균 하락폭

### Avg. Drawdown Days

평균 하락일

전체 측정 기간 중 21.17일 하락했다는 의미가 아니라,

한번 하락하면 평균 21.17일 동안 하락하고 다시 올라왔다는 의미

### Avg. Up month,  Avg. Down Month

상승한 달의 평균 수익률, 하락한 달의 평균 수익률

### Win Year %

연단위로 끊었을 때 승리한 연도의 비율

### Win 12m %

최근 12개월의 승률
