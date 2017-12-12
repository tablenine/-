### 12-1 Artificial Neural Network

#### 12-1-1 Linear Classification Function

+ Linear
  + F(X) = b + 시그마 w<sub>i</sub>x<sub>i</sub>
    + b는 bias
    + w<sub>i</sub>는 x<sub>i</sub>의 weight
    + Positive 혹은 Negative를 리턴
  + dimension의 weight만 고려하기 때문에 dimension간의 상관관계를 표현하지 못함
+ Quadratic
  + F(X) = b + 시그마 w<sub>i</sub>x<sub>i</sub> + 시그마 w<sub>ij</sub>x<sub>i</sub>x<sub>j</sub>
  + pair에 대한 weight도 고려하기 위하여
+ Polynomial
  + F(X) = b + 시그마 w<sub>i</sub>x<sub>i</sub> + 시그마 w<sub>ij</sub>x<sub>i</sub>x<sub>j</sub> + 시그마 w<sub>ijk</sub>x<sub>i</sub>x<sub>j</sub>x<sub>k</sub>….
  + Linear -> Polynomial with degree = 1
  + Quadratic -> Polynomial with degree = 2


#### 12-1-2 Perceptron

+ 랜덤하게 w와 b를 셋팅
+ 무작위로 셋팅한 함수를 가지고 training데이터를 분류
+ 잘못된 데이터가 나오면 w와 b를 조금씩 틀어봄
+ 잘못된 분류가 없을때까지 계속 반복
+ Notdeterministic(비결정적??)
  + 똑같은 데이터가 주어진다 해도 w를 어떻게 셋팅하냐에 따라 결과가 달라짐
  + Boundary를 얼마만큼 조절을 해야하나, delta값을 어떻게 바꿔야하나 얼마만큼 크기로 조정을 하냐문제
  + 데이터가 선형적으로 분류가 되어있지 않으면 중지할 수 없음
+ Limited to linear functions
  + Polonomial 함수의 degree가 2 또는 3이면 분석이 어려움
    + 학습을 해야하는 변수가 수가 dimension의 갯수와 기하급수적으로 비례를 하기때문

#### 12-1-3 Multi-Layer Perceptron

+ Back-Propagation
  + Input 튜플이 주어짐
  + 네트워크를 통해서 output을 구할수 있음
  + 에러를 계산
  + 에러를 최소화 하기위해 weight를 수정
  + 반복
+ Multiclass-Classification(다중 클래스 분류)을 Neural Network로 구성을 하여 학습시키고자 함
  + 각 하나의 클래스 마다 하나의 Output Node를 할당
  + 가장 최고의 값이 나온 Output node를 분류함
  + Confidence : 가장 높은 값과 두번째높은 값의 차이  
+ 일반적으로 나쁜해석 능력을 가짐


### 12-2 Support Vector Machine I

#### 12-2-1 SVM vs. ANN

+ SVM 
  + 90년대 후반부터 2010년대 까지 많이 쓰임
  + 이후는 딥러닝이 더 떠오르면서 딥러닝을 많이 사용
  + SVM 모델은 ANN과 비교하여 튜닝 할 수있는 더 적은 하이퍼 파라미터를 필요로함
  + 딥러닝은 ANN을 확장한것
  + 지금도 정형데이터, 구조화 된 데이터는 많이 사용하고 있음
  + Deterministic한 알고리즘
  + Nonlinear 함수도 커널 트릭이라는 트릭에 의해서 Deterministic. 하게 구하는 방법론

#### 12-2-2 Linear Support Vector Machine

+ Margin의 크기로 표현 (margin이 클수록 좋은 함수)
  + Margin은 Boundary함수와 가장 가까운 데이터 간의 직각 거리(Orthgonal Distance)
+ Linearly separable 
  + 모든 데이터에 대해서 임의의 Quality( y(b+WX) > 0 )가 0보다 크게 만드는 w와 b가 존재한다면 Linearly separable하다고 한다

#### 12-2-3 Primal / Dual Problem

+ Primal form에서 Dual form으로 변환해서 풀이
  + Linear primal form 상태에서는 Nonlinear classification을 할 수 없기때문
+ Dual form
  + w대신 알파를 Optimize해야함
  + 알파를 Optimize 한 후 아래 공식으로 w를 계산
  + w = 시그마a<sub>i</sub>y<sub>i</sub>x<sub>i</sub>

#### 12-2-4 Characteristics of SVM

+ 많은 알파들이 0이 됨
+ 0이 아닌 알파들을 support vectors(SV)라고 부름
+ SVM에서 최적의 가중치 벡터 w는 support와 vector의 가중 합으로 표현됩니다.
+ SVM model
  + bias b, SV와 그에 해당하는 coefficient 알파의 리스트로 표현이 됨
  + C의 값이 클경우 에러를 줄이기 위해 노력하여 답이 나오지 않음
  + C의 값이 0일경우 에러를 줄이기 위해 노력하지 않아 아무답이나 출력함
  + 적당한 C값이 필요 -> 0부터 조금씩 늘려가면서 튜닝
  + w를 먼저 계산하지 않는 이유는 Nonlinear kernel trick을 쓰기위해서

