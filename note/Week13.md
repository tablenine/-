### 13-1 Support Vector Machine II

#### 13-1-1 Nonlinear Support Vector Machine

+ naive way
  + 기존의 데이터를 새로운 high dimensional space(고차원 공간)에서 projection을 함
  + high dimensional space(고차원 공간)에서 project(투영) 된 데이터를 이용하여 선형 함수를 구함
  + original space에서는 Nonlinear Function
  + projection 시간이 많이 소모 됨
  + 어떤 새로운 feature space를 transform 해야 할지 명확하지 않음
+ SVM "Kernel trick"
  + 위 과정을 함축적으로 할 수 있음
  + 같은 효과가 나타날 수 있도록 수학적인 트릭을 써서 계산