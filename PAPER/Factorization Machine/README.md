# Factorization Machines

## 1. Abstract

FM 모델은 SVM 모델의 강점을 결합한 새로운 모델이다.

SVM과 비교할 때 아래의 공통점과 차이점을 보인다.
- 공통점 : 실제 값의 피처 벡터로 작동되는 일반적인 예측기이다.
- 차이점 : factorized 파라미터들을 이용하는 변수들 간에 상호작용이 일어난다.

즉, SVM이 할 수 없는 고도의 sparsity로부터 상호작용을 평가할 수 있다.

비선형 SVM과 달리 dual form에서 변환이 불필요하고 모델의 파라미터들은 서포트 벡터 없이 직접 계산이 가능하다.

SVD++, PITF, FPMC 등 다양한 factorization 모델이 있다. -> 해당 모델들은 특정 Input 데이터에만 작동이 잘 된다.

반면 FM 모델은 Input 데이터를 특정하면서 위의 모델들을 모방할 수 있다.

즉, FM 모델에 전문적 지식이 없더라도 쉽게 구현이 가능하다.

## 2. Introduction

SVM은 머신러닝과 데이터 마이닝에 뛰어난 모델임에도 불구하고 협업 필터링 같은 현업에서는 유용하지 않다.

tensor factorization model과 specialized factorization model의 약점은 일반적 예측 데이터에 적합하지 않다는 것이다.

또한 speicialized model은 학습 알고리즘의 설계와 모델링에 노력이 요구되기 때문에 개별적으로 파생된다.

따라서 해당 논문에서는 높은 sparsity 하에 의존적인 파라미터들을 측정할 수 있는 FM 모델을 소개한다.

FM 모델들은 모두 복잡한 변수 상호작용(SVM의 polynomial kernel과 대조)이지만 SVM 처럼 dense한 parameterization 대신 factorized parameterization을 사용한다.

해당 논문에서는 다음 두 가지를 보여준다.
- FM 모델의 수식은 linear time 내에 게산된다.
- linear한 수의 파라미터에만 의존한다.

이로 인해 예측을 위해 서포트 벡터와 같은 학습 데이터를 별도로 저장하지 않아도 모델 파라미터 저장과 최적화를 할 수 있다.

비선형 SVM은 학습 데이터에 의존한 예측과 dual form에 최적화 되어 있다.

FM 모델의 이점은 아래와 같다.
- 1) SVM이 할 수 없는 매우 sparse한 데이터에 대한 파라미터 추정을 할 수 있다.
- 2) 선형 복잡성을 갖고 있어 최적화 될 수 있고 서포트 벡터에 의존하지 않는다.
- 3) 
