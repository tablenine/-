### 9-1 Statistics for Big Data(빅데이터 통계) II

+ Benford's Law
  + 실제 데이터로부터 통계 값을 구해낼 경우, 통계 값들의 첫 번째 자릿수가 1인 경우가 많다는 법칙 (뒤로 갈수록 적어짐)
  + [테스트링크](http://testingbenfordslaw.com)

+ Benford's Law to Detect Fraud

  + 공식과 결과 값이 다르다면 조작된 데이터라고 판별 할 수 있음

+ Benford's Law Intuition

  + 1, 2, 3 … 999999 카드가 있음
  + 한장 씩 뽑아 모자에 넣는다
  + 모자에 카드를 넣다가 어느 시점에서 "모자에서 카드를 뽑았을 때 그것의 첫 번째 digit이 1일 확률"을 계산 해 볼 수 있다
  + 카드를 추가 할 수록 1일 확률이 줄어들다 늘어났다를 반복 함
  + 이러한 이유로, 여러 번 random한 시점에서 카드를 뽑았을 때 첫번째 digit이 1일 확률이 평균을 구하면 가장 높음

+ Multiple Hypothesis Testing

  + 같은 샘플로 hypothesis testing을 반복하면 오류를 범할 수 있다
  + 실제 차이가 없는데 차이가 있다고 감지할 확률 : a = 0.05
  + 실제 차이가 없어서 차이가 없다고 뽑힐 확률 : 1 - a
  + k번의 실험에서 실제 차이가 없어서 차이가 없다고 뽑힐 확률 : (1 - a)<sup>k</sup>
  + 최소한 한번의 실험에서 실제 effect를 발견할 확률 : 1 - (1 - a)<sup>k</sup>
  + a를 0.05로 계속 고정하면 위에 따라 실험이 늘어날때마다 한 번은 잘못된 finding이 발견될 확률이 계속 증가하게 된다.(Familywise Error Rate)

+ Familywise Error Rate Corrections

  + a를 0.05보다 낮추어야 한다

  + Bonferroni Corrections : a를 k로 나누어서 낮추는 방법

    -> 과장되어 더 낮추어짐

  + Sidak Corrections : a = 1 - (1 - a<sub>c</sub>)<sup>k</sup>

    ->  a<sub>c</sub> = 1 - (1 - a) <sup>1/k</sup>

    0.05로 계속 유지 되어 더 안정적

+ statistical test를 빅데이터 시대에서는 기존처럼 하면 안되고, 조금 더 conservative(보수적?)하게 해야 한다

+ The "Curse" of Big Data?

  + 큰데이터의 저주는 수십억 또는 수조의 데이트 포인트와 수천개의 메트릭이 포함 된 매우 큰 데이터세트 에서 패턴을 검색 할 때 예측력이 없는 우연의 일치가 발생한다 - Vinvent Granville

+ 빅데이터 통계와 기존의 통계와 다른점

  + Big P (Number of Variables(columns)) vs. Big N (Number of records)
  + 데이터의 record가 커지면 variance가 줄어들기 때문에 sampling을 조심해서 해야 함

### 9-2 Machine Learning Basics

+ 지도학습 vs 비지도학습
  + Supervised Learning(classfication) : 지도학습
    + label이 있는 상태에서 knowledge를 추출 하는 것
  + Unsupervised Learning(clustering) : 비지도 학습
    + label이 없는 상태에서 knowledge를 추출 하는 것

+ 머신러닝의 기본 task

  + Classfication vs. Regession vs. Ranking

    + 지도학습이라는 공통점이 있음
    + Classfication : label이 categorical한 값이다
      + 의학적 진단, fraud dectection(사기 탐지)
      + Multi-Step Process
        + Data Preprocessing
          + Data Cleaning
          + integration
          + reduction
          + transformation (normalization, discretization)
        + Training (learning model)
          + 모델 생성 (다양한 모델이 있음)
        + Validation (tuning model)
          + training set에 포함 되지 않은 test데이터를 가지고 model에 perfomance를 예측
          + 모델의 perfomance를 최대로 만드는 hyperparameter를 tuning하여 최적화
          + 방법
            + k-fold Cross Validation
              + 전체 데이터를 k등분하여 나누고 k-1개의 그룹을 training데이터로 사용하고 나머지 한 개의 그룹을 test 데이터로 사용하는 과정을 테스트 그룹을 바꿔가며 k번 반복하여 평균을 내는 방법
            + Stratfied cross validation
              + k-fold cross validation을 적용할 때, 각 그룹 안의 데이터들이 original population의 class distribution을 따르도록 sampling 되어야 한다는 것
            + Holdout method
              + 데이터 셋을 두개로 나누어 하나는 training 하나는 test에 사용
              + 가장 단순
            + Leave-one-out test
              + k-fold cross validation의 k를 전체 데이터 sample의 size로 설정한 경우
              + 시간이 많이 소요되고 느림
        + Deploy
      + Issues : Evaluationg Learning Methods
        + Accuracy (정확성)
        + Speed
        + Robustness : noise데이터나 놓치는 값
        + Interpretability : 해석이 가능한 모델이냐
        + Overfitting
          - training 데이터에 너무 정확하게 학습이 되면 바람직하지 않을 수 있다 이 경우가 overfitting.
          - underfitting : test와 traing data에서 모두 에러가 높은 상태
          - overfitting과 underfitting의 사이의 중간부분에 존재하는 모델을 잘 선택하여야 함
    + Regression : label이 실수, 숫자, numerical, continuous real 값이다
    + Ranking : 
      + 까다로운 부분이 있음 
      + 잘 사용하지 않음
      + target label이 서로 독립적이지 않고 서로 간의 distance나 ordering이 존재할 때 이것을 ranking라고 한다.(ex: 학점을 예측하는 경우)

    ​
