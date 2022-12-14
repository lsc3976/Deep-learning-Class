
# 1. 회귀 (regression)란?

<br>

![img121.png](https://raw.githubusercontent.com/lsc3976/P_deeplearning1/main/image/121.png)



회귀분석(regression analysis)은 영국 학자 프랜시스 골턴(Francis Galton)에 의해 <br>
'평균으로의 회귀'(regression to the mean)현상을 증명하기위해 처음 고안되었다.  <br>
'평균으로의 회귀'는 부모와 아이 키의 상관관계를 분석할때 부모의 키가 아주 크더라도 <br>
자식의 키가 부모보다 더 커서 세대를 이어가면서 무한정 커지는(발산) 것은 아니며, <br>
부모의 키가 아주 작더라도 자식의 키가 부모보다 더 작아서 세대를 이어가며 무한정 작아지는(수렴)것이 아니라는 것. <br>
즉, 극단적인 값이 오더라도, 다음 측정값은 평균으로 회귀하는 경향성을 일반화하기위해 쓴 용어이다. <br>
현대에서는 회귀(regress), 즉 평균으로 돌아간다는 의미는 거의 사라지고, <br>
독립변수와 종속변수를 설정하고 이들의 관계를 통계적으로 살펴보는 방법론들을 회귀분석이라고 한다. <br>

<br>

## 회귀분석의 정의

<br>

``` 
"원인에 대한 결과를 수치로 예측하는 기법" 
```
<br>
회귀분석은 주어진 자료들이 어떤 특정한 경향성을 띠고 있다는 아이디어로부터 비롯된다. <br>
주어진 변수들 사이에서 나타나는 경향성을 설명하는 것을 주 목적으로 하기 때문에, <br>
변수들 사이의 함수적인 관련성을 규명하기 위해 어떤 수학적 모형(회귀식)을 가정하고 <br>
이 회귀식을 측정된 변수들의 자료로부터 추정하는 통계적 분석 방법이다.<br><br>

<img src="https://camo.githubusercontent.com/8681409014533c107893ef59733c79d5351a7cdf0903104b9a8d6e4141d1b3e1/687474703a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3133524c47514b4175365061326f65614558794770586b774c76545a4658707952"><br>

이때 영향을 주는 원인을 독립변수라 하고 영향받아나온 결과를 종속변수라고한다. <br><br>

따라서 독립변수들의 패턴을 찾아 관련성을 회귀식으로 추정해내고 <br>
나아가 새로운 변수를 주었을때의 결과까지 수치로 예측하는것을 회귀분석이라고 할수있다.<br>

$Y = W_1 X_1 + W_2 X_2 + W_3 X_3 + ... + W_n X_n $

위와같은 선형회귀식을 예로들면 Y는 종속변수(결과값). <br>
$X_1,X_2,X_3, ... X_n$은 독립변수(원인). <br>
$W_1,W_2,W_3, ... W_n$은 독립변수의 값에 영향을 주는 회귀 계수(Regression coefficients)이다. <br>
머신 러닝의 관점에서보면 독립변수는 입력값, 종속변수는 결과값이다. <br>
머신 러닝 회귀 예측의 핵심은 주어진 입력값과 결과값 기반의 학습을 통해 __최적의 회귀계수__ 를 찾아내는것이다. <br><br>



## 회귀분석의 종류

회귀분석의 종류는 회귀 계수의 선형/비선형 여부, 독립변수의 개수, 종속변수의 개수에 따라 여러가지 유형으로 나눌 수 있다. <br>
회귀에서 가장 중요한 것은 회귀 계수이며, 이 회귀 계수가 선형인지 아닌지에 따라 선형 회귀와 비선형 회귀로 나눌 수 있다. <br>
그리고 독립변수의 개수가 한 개인지 여러 개인지에 따라 단일 회귀, 다중 회귀로 나뉜다. <br><br>


### 단순 회귀분석 (Simple Regression Analysis)

![ima122.png](https://github.com/lsc3976/P_deeplearning1/blob/main/image/122.png?raw=true)<br>
종속변수에 영향을 미치는 독립변수가 1개이면 단순 회귀분석이라고한다.<br>
(ex : 독립변수를 근무년수로, 월급을 종속변수로 설정하여 인과관계를 분석)<br><br>

### 다중 회귀분석 (Multiple Regression Analysis)

![ima122.png](https://github.com/lsc3976/P_deeplearning1/blob/main/image/123.png?raw=true)<br>
2개 이상의 독립변수를 통해 종속변수에 미치는 인과관계를 분석한다.<br>
(ex : 독립변수를 나이, 근무년수, 이직횟수 등으로 다양화 하여 종속변수인 월급을 분석)<br><br>

각 독립변수들이 실제로 종속변수에 영향을 미친다면 다중 회귀분석이 더욱 정확한 결과값을 예측할수있다.<br><br>


### 선형 회귀
일반적으로 사용되는 회귀로써 실제 값과 예측값의 차이를 최소화하여, 직선형 회귀선을 최적화하는 방식이다.<br>
선형 회귀 모델은 규제(Regularization)방법에 따라 다시 여러 유형으로 나뉠 수 있다.<br>
규제는 일반적인 선형 회귀의 과적합 문제를 해결하기 위해서 회귀 계수에 패널티 값을 적용하는 것을 말한다.<br><br>


### 비선형 회귀
비선형 회귀란 독립변수와 종속변수간의 관계에 대해 회귀 계수가 비선형적인 모델을 사용하는 방법이다.<br>
기존의 선형 회귀와 달리 임의의 관계(비선형적인)로 계수를 추정하는것이 비선형 회귀법이다. <br><br>




# 2. Linear Regression (선형 회귀)

 
<br><br>

## 선형 회귀(Linear Regression)란?

머신 러닝의 가장 큰 목적은 실제 데이터를 바탕으로 모델을 생성하고 <br>
다른 특정 입력 값을 넣었을때 발생할 아웃풋을 예측하는데에 있다. <br>
선형 회귀(Linear Regression)는 직관적이고 데이터의 경향성을 가장 잘 설명하는 하나의 직선을 예측하는 지도학습 기법이다. <br>
독립변수와 종속변수 데이터를 주고 모델을 트레이닝시켜서 정확도를 높이고, <br>
주어진 독립변수 X에 해당하는 실제 값으로 타겟 Y(종속변수)를 예측할때 이 회귀식의 계수(입력 피처)들이 선형조합으로 표현된다. <br>


<br><BR>

## 선형 회귀의 정의
  
  
  
  
  ### 1) 단순 선형 회귀
  

  
  

  <img src='https://github.com/lsc3976/P_deeplearning1/blob/main/image/10.png?raw=true' /><br>
  (일반적인 단순 선형회귀)
  <br><br>
  
  예를 들어 집의 크기(독립 변수)를 사용해서 주택 가격(종속 변수)을 예측할때
  
  $Y$(price) $= w_0 + w_1 * X$(size)
  
  라는 1차 함수식(회귀식)으로 모델링 할수있다.
  이때 기울기 $w_1$과 절편인 $w_0$을 회귀 계수(Regression coefficients)로 지칭한다. <br>
  
  실제값과 회귀 모델의 예측값 차이에 따른 오류값을 남은 오류, 즉 잔차(residual)라 부른다. <br>
  __최적의 회귀 모델을 만든다는 것__ 은 전체 데이터의 잔차(오류값)합이 최소가 되는 모델을 만든다는 의미이며, <br>
  동시에 오류값 합이 최소가 될 수 있는 __최적의 회귀 계수를 찾는다__ 는 의미이다.
  <br>
  
  <img src="https://github.com/lsc3976/P_deeplearning1/blob/main/image/55525.png?raw=true" /> <br>
  ex) 회귀계수를 구하는 한가지 방법인 최소제곱법의 해 (a,b : 각각 기울기와 절편)<br><br>
  
  
  
  
  ### 2) 다중 선형 회귀

  사실 주택 가격은 단순히 집의 크기(하나의 독립변수)만으로 결정되지않고 <br>
  방의 개수, 주변 교통수단과의 거리 등 다양한 요소로부터 영향을 받는다. <br>
  

  $Y = w_1X_1 + w_2X_2 + w_3X_3 +  ...  + w_nX_n + b$

  이러한 다수의 독립 변수를 가지고 주택 가격을 예측할때 Y(종속변수)는 여전히 1개 이지만 <br>
  X(독립변수)는 여러개가 된다. 이것을 다중 선형 회귀 분석이라고 한다.
  <br><br><br>
  
  
## 손실 함수

<br>
<img src="https://github.com/lsc3976/P_deeplearning1/blob/main/image/117.png?raw=true" /><br>
 
```
실제 y값(정답)과 모델 h(x)(예측값)의 차이를 구하는 함수이다. Loss 라고도 한다.
```

회귀식을 모델링 할 경우 당연히 실제 데이터와 회귀식에는 오차가 발생 한다. <br>
선형회귀는 위에 언급된 오류값(잔차)의 합이 최소가 되는 최적 회귀 계수를 찾는 것 <br>
(가장 정확한 예측선을 긋는 것)이 궁극적인 목표가 된다.<br>

* 어떠한 문제를 해결하고자 하는가에 따라 적절한 손실함수를 설정해야 좋은 결과를 얻을 수 있다. <br>
<br>
 
<img src="https://github.com/lsc3976/P_deeplearning1/blob/main/image/116.png?raw=true"> <br>
평균 제곱 오차 (Mean Squre Error, MSE)의 경우<br>
n은 총 데이터, y는 출력결과이고 t는 실제 데이터의 값이다. <br>

예측결과 - 실제데이터의 차이를 제곱(음수가 나오는걸 방지)한뒤 평균을 내어 표현하고있다. <br>
제곱을 하기 때문에 아웃라이어(특이치)에 민감하다는 특징이 있다. <br><br>
  
  
 ### 비용 함수
 
 머신러닝 알고리즘에서 최적화(obtimization)는 비용함수의 값이 가장 작아지는 최적의 파라미터를 찾는 과정을 말한다. <br>
 이를 달성하기 위해서, 경사하강법(Gradient Descent) 방식이 가장 기본이 되는 알고리즘이다. <br>

 비용함수란, 최적화 알고리즘에서 최소값을 찾아야하는 함수를 말한다. <br>
 즉, 비용함수는 최적화 알고리즘의 목적함수이다. <br>
 오차인 loss(손실)를 줄여야 최적의 모델을 만드는 것이므로 각 x(입력값)에 대한 손실 함수의 합이 비용 함수이다. <br>
 이 비용함수를 경사하강법을 통해 최소로 만드는것이 모델을 최적화 하는것이라고 할 수 있다.
 
<br><br>


  
## 비선형 회귀(Non-linear Regression)란?
  

  <br>
<img src='https://github.com/lsc3976/P_deeplearning1/blob/main/image/12.png?raw=true' /><br>

비선형 모델은 입력되는 데이터(독립 변수, 종속 변수)를 어떻게 변형 하더라도 <br>
회귀 계수를 선형 결합식으로 표현할 수 없는 모델을 말한다. <br>
  
선형 회귀 모델은 파라미터(회귀 계수)에 대한 해석이 단순하지만 <br>
비선형 회귀 모델은 모델의 형태가 복잡할 경우 해석이 어려워진다. <br>
그래서 보통 모델의 해석을 중시하는 통계 모델링에서는 비선형 회귀 모델을 잘 사용하지 않는다. <br>
하지만 회귀 모델의 목적이 해석이 아니라 결과값의 예측에 있다면 비선형 모델은 대단히 유연하기 때문에 <br>
복잡한 패턴을 갖는 데이터에 대해서도 모델링이 가능하고 충분히 많은 데이터를 갖고 있어서 오류값을 줄일수있고 <br>
예측 자체가 목적인 경우(딥 러닝)에 비선형모델은 매우 뛰어난 도구가 된다.
  
<br><br><br>
 

## 활성화 함수
  
  <br>
  
  
  
### 뉴런에서 해답 가져오기
  
  
  <img src='https://github.com/lsc3976/P_deeplearning1/blob/main/image/133.png?raw=true' /><br>
  인간은 컴퓨터와 달리 목소리, 사진, 언어 와 같은 Unstructrued Data(비구조화 데이터)를 쉽게 이해하고 활용 가능하다. <br>
  그것은 뇌의 뉴런, 수상돌기로부터 특정 정보 $x_n$를 받아들이고 시냅틱 가중치 $w_i$를 적용하는 일련의 과정을 거치기때문이다.<br>
  이 가중치는 입력에 얼마나 반응해야하는지를 정의한다. ( $x_n$ $w_i$를 통해 결합)<br>
  이 값들은 뉴런 핵에서  $y=\sum_i x_i wi+b$ 로 통합되고 일정 수준을 넘어서면 활성화되어 해당 정보를 축삭(axon)으로 보내져서<br>
  다른 프로세스를 거치는데, 일반적으로 σ(y)를 통해서 비선형처리가 된다. 이 후 최종 목적지를 거쳐 다른 뉴런으로 보내진다. <br>
  이처럼, 인간의 뇌가 작동하는 방식을 모방해 비선형 회귀 모델을 구축하면 놀랍게도 컴퓨터가 마치 인간처럼<br>
  구조화되지않은 자료(보이스,사진,언어)를 이해하고 활용할수 있게된다. 이것이 비선형 회귀의 강력한 핵심이다.
<br><br><br>
  
  

  ### 활성화 함수의 정의
  

  <img src="https://github.com/lsc3976/P_deeplearning1/blob/main/image/1110.png?raw=true" /><br>
  뉴런에서 처럼 입력 신호의 총합을 특정한 출력 신호로 변환하는 함수를 활성화 함수라고 한다. <br>
  위 그림은 신경망 그림으로 가중치(w)와 인풋값(x)의 곱연산과 편향(b)의 합을 계산하고<br>
  그 다음에 활성화 함수에 넣어 출력하는 흐름을 보여준다.<br>
 
  <br><br>
 
  <br>
  
  ### 1) 시그모이드(Sigmoid) 함수

  <br><br>
  <img src='https://github.com/lsc3976/P_deeplearning1/blob/main/image/778.png?raw=true' /><br>
  
  $sigmoid(x) = \frac{1}{1 +e^{-x}}$ <br>
  
  시그모이드 함수는 Logistic 함수라고 불리기도 하며, <br>
  x의 값에 따라 0~1의 값을 출력하는 S자형 비선형 활성화 함수이다. <br>
 

 
 
  
 
  <br>
  



  ### 2) ReLU (Rectified Linear Unit) 함수
<br>
  <img src='https://github.com/lsc3976/P_deeplearning1/blob/main/image/783.png?raw=true' /><br>
  레이어의 층이 깊어질수록 활성화 함수로 ReLU 를 사용하게 되는데, <br>
  이 함수는 쉽게 말해 0보다 작은 값이 나온 경우 0을 반환하고, <br>
  0보다 큰 값이 나온 경우 그 값을 그대로 반환하는 함수이다.<br>
  역전파를 위해 미분 과정중 Vanishing gradient 문제를 해결해준 매우 고마운 활성화함수이다. <br>
  <br>

  시그모이드와 ReLU 이외에도 여러가지 활성화 함수가 있다. <br><br>

  
