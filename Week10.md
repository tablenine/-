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
