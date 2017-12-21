### 8-2 Statistic for Big Data I

- Background : 통계적 추론
  - 표본 데이터로부터 모집단에 대한 결론을 도출하는 방법

- Two Key method
  - Hypothesis Tests (sighificance tests)
    - H<sub>0</sub> : Null hypothesis(영가설)
      - 실험그룹이 서로 차이가 없음

    - H<sub>a</sub> : Alternative hypothesis(대립가설)
      - 실험그룹이 차이가 있음

    - 예

      - 새 광고를 한 후 광고 전과 광고 후의 판매율을 비교

      - 제약회사 신약의 효과를 보기위해 가짜약과 신약을 투여해 비교

    |                        |     Do not reject H<sub>0</sub>      |    Reject H<sub>0</sub>     |
    | :--------------------: | :----------------------------------: | :-------------------------: |
    | H<sub>0</sub> is true  |        Correct Decision 1 - a        | Type 1 error a (실제로 같지만 다르다고 가정) |
    | H<sub>0</sub> is false | Type 2 error b (실제로는 차이가 있지만 차이가 없다고 가정) |   Correct Decision 1 - b    |

    + p-value : 실제 차이가 없지만 우연에 의해서 다른 결과가 나올 확률
      + 100번의 실험 중 90번의 같은결과와 10번으 다른 결과가 나오면 p-value = 0.1
      + p-value가 0.05 보다 낮으면, 결과가 stastistically significant(통계적으로 유의미) 함 (특별한 의미는 없음 일반적으로 사용 하는 값 0.01을 기준으로 할 수도 있음)
    + Effect Szie : 얼마나 significant 한가 / Result의 차이가 얼마나 큰지를 표현하는 척도
      + 주로 meta-analysis에 많이 쓰임
      + 0.2 정도 작다, 0.5 정도 중간 0.8 정도 큼

  -  Confidence intervals(신뢰구간)

     - 1 - (p-value)

- Publication bias
  - meta-analysis : 기존에 analysis(분석)했던 많은 결론들을 모아서 그것을 통계적으로 다시 analysis 하는 것
  - 빅데티어 시대에 들어서 어떤 alternative hypothesis가 true라는 결론이 많이 나오는데, 점점 과장이 심해지고 있다는 뜻
  - Type 1 에러가 점점 증가하게 됨
