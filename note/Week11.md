### 11-1 EnsembleMethods

### 11-1-1 앙상블 메소드란?

+ 정확도가 상당히 높음
+ 기본 원리는 한 사람이 결정을 내리는 것보다 다수가 결정을 내리는 것이 더 현명한 결정일 확률이 높다라는 것
+ base classifier or weak learner : 어떤 데이트로부터 여래개의 작은 모델들
+ 많은 수의 base classifier를 만들고 prediction은 그 각 만들어진 작은 모델들의 다수결의 원칙으로 예측함
+ 동작예제
  + 25개의 base classifiers 만듬
  + 각각의 base classifier는 35%의 에러를 발생한다고 가정
  + 각각의 모든 classifier가 전부 다 똑같은 identical 한 classifier라면 35%의 에러를 발생시킬 것
  + 만약 각각의 classfier가 같지 않고 **독립적**이며 서로 idependently 성장을 해서 모델이 생성 되었다면 그리고 각각의 error들이 코릴레이션이 없고 independent 하다면 error rate를 계산할 수 있는 공식이 있음
  + error 발생 확률이 6%로 감소함