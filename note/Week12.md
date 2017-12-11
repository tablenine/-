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


