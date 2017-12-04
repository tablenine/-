### 10-1 Decision Tree
#### 10-1-1 What is Decision Tree?
+ 어떤 attribute를 root노드로 정할지 잘 결정 해야함
+ 엔트로피 = 불확실성
+ 어떤 attribute로 나누었을 경우 나누어진 데이터들의 분포를 살펴서 엔트로피가 낮을수록 잘 선택한 attribute이다.
+ information gain으로 엔트로피를 계산( 높을수록 적합)
+ information gain : 가지고 있는 총 데이터의 엔트로피를 계산 -> 어떤 attirbute로 나누어진 데이터들의 분포를 엔트로피로 계산 -> 엔트로피가 가장 줄어든 attribute를 선택

#### 10-1-2 Decition Tree Induction
+ 모든 튜플들이 root노드에서 시작

+ attribute 설정

  + attribute가 categorical하면 그냥 사용
  + continuous-value라면 먼저 구간별로 나누어 사용(discretize) : 전처리로 수행하여야함

+ 선택된 attribute에 따라 각조건에 맞는 branch로 tuple들이 분할

+ branch로 간 tuple들을 가지고 다른 attribute로 condition을 정해서 계속 반복적으로 tree를 생성

+ Conditions for stopping partitioning( 언제 branch out을 그만할까) 

  + 특정 branch에서 모든 tuple들이 하나의 class를 가지고 있을때 까지

  + tuple의 개수가 적어지게 되면 branch를 계속 만들기 보다는 이 시점에서 majority vote를 해서 branch out을 하는 것 보다 classfy를 하는것이 더 좋다

  + Leaf node에 몇개의 tuple이 나오면 더이상 branch out을 하지 않겟다는 hyper parameter도 decision tree에 포함

#### 10-1-3 Attribute Selection Algorithms

+ p<sub>i</sub> : 특정 tuple이 클래스 c<sub>i</sub>에 속하는 확률
+ GAIN(A) = Info(D) (전체 데이터의 엔트로피) - Info<sub>a</sub>(D) (attribute로 나눈 후의 엔트로피) 이 값이 제일 큰것을 선택
  + 복수 값 속성에 편향됨
+ GainRatio(A) = Gain(A) / SplitInfo(A) : Information gain을 어떤 값에 의해서 정규화 시킨, 정규화된 Information Gain
  + 하나의 파티션이 다른 파티션보다 훨씬 작은 불균형 분할을 선호하는 경향이 있다.
+ 여러가지 방식들이 있지만 큰 성능차를 보이지 않음

#### 10-1-4 Tree Prunning

+ decision tree도 overfitting이 발생할 수 있음
+ Prunning(가지치기)
  + PrePruning
    + tree를 계속 키우는 중에 어떤 condition을 계속 체크하면서 condition을 만족하면 tree를 키우지 않음
  + PostPruning
    + tree를 키우고 난 후 어떤 condition에 따라 가지치기를 실행
    + Subtree Replacement
      + 너무 끝까지 branch out 될 경우 마지막 leaf node에 있는 tuple의 갯수가 적어져서 overfitting이 되면 leaf node에 있는 몇개의 node를 하나로 뭉치는 것
      + leaf node를 하나로 뭉치면서 위에 있는 non leaf node들을 leaf node로 만듬
    + Subtree Raising
      + 복잡함
    + Two postprunning method
      + C4.5 prunning 
        + 통계적 수치를 체크
        + 수치를 넘어가면 가지치기를 진행
      + Reduced-error prunning
        + Vallidation을 통해서 tree의 가지치기를 진행
        + 우리에게 주어진 training set을 전부다 사용하지 않고 일부만 사용하기 때문에 tree를 만들 때 많은 training data를 사용하지 못한다는 단점이 있음
        + grow된 tree의 형태가 C4.5 보다는 덜 정확함
        + C4.5 prunning  보다 더 정확하게 예측이 가능
  + 일반적으로 성능이 더 좋은 PostPrunning을 많이 사용

#### 10-1-5 Decision Tree Based Classification

+ Decision Tree 장점
  + 모델이 해석 가능함
  + 시간이 오래걸리지 않음(다른 모델링에 비해서)
+ Decision Tree 단점
  + attribute가 discretize 되어야 한다. (Information loss가 발생)
  + 일반적으로 SVM, deep learning 같은 복잡한 최신 기계학습 방법에 비해 성능이 높지 않음(그렇게 많이 나지는 않음)
+ decision tree를 freature space상에서의 형태를 살펴보면, decision boundary 형태는 축에 시직인 boundary를 생성(decision tree 모델의 한계)

### 10-2 Exercise : Weka I

