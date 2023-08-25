# 인공지능 1

## 1. Supervised Learning

- X와 Y의 관계를 찾는 것
- 라벨(Y)이 필요하다.

### 1) Training set and Test set

- Training set(About 80%)

  - 학습에 사용되는 데이터

- Test set(About 10%)

  - 테스트에 사용되는 데이터
  - For checking accuracy
    - underfitting: 학습이 부족한 경우
    - balanced: 적당한 학습
    - overfitting: 학습 데이터에만 잘 맞는 경우

- Validation set(About 10%)

  - 테스트 데이터의 과적합을 방지하기 위해 사용

### 2) Linear Regression(선형 회귀)

- 범주형 데이터를 예측하는 것이 아닌 `연속형 데이터`를 `선형으로` 예측하는 것

  - 가격이나 확률과 같은 연속된 값의 출력을 예측하는 것
  - X와 Y의 관계를 선형적(Y = WX + b)으로 분석
  - ex) 온도

- Example: [자동차 연비 예측하기: 회귀](https://www.tensorflow.org/tutorials/keras/regression?hl=ko)

### 3) Non-linear Regression(비선형 회귀)

- 범주형 데이터를 예측하는 것이 아닌 `연속형 데이터`를 `비선형으로` 예측하는 것

  - 가격이나 확률과 같은 연속된 값의 출력을 예측하는 것
  - ex) 온도

- 선형으로만 분석할 수 없는 경우

### 4) Linear Classification(선형 분류)

- 연속형 데이터를 예측하는 것이 아닌 `범주형 데이터`를 `선형으로` 예측하는 것
  - X와 Y의 관계를 선형적(Y = WX + b)으로 분석
  - ex) 등급, 옷 종류
- Example: [기본 분류: 의류 이미지 분류](https://www.tensorflow.org/tutorials/keras/classification?hl=ko)

### 5) Non-linear Classification(선형 분류)

- 연속형 데이터를 예측하는 것이 아닌 `범주형 데이터`를 `비선형으로` 예측하는 것
  - ex) 등급, 옷 종류
- 선형으로만 분석할 수 없는 경우

## 2. Unsupervised Learning

- 답을 알려주는 라벨이 필요없다.
- 비슷한 성질을 가진 데이터끼리 묶는다.

### 1) Autoencoders

- encoder와 decoder로 구성
  - encoder: 입력을 압축한 값
    - 압축된 값은 원본보다 작은 차원을 가짐
    - 시각화하면 비슷한 데이터끼리 뭉쳐있음
  - decoder: 압축된 값을 복원한 값
    - 복원된 값은 원본과 같은 차원을 가짐
    - 원본 이미지와는 다른 이미지가 나오지만 형태는 남아있음
- 분류, 추천 기능 구현에 사용

## 3. Deep Learning Techniques

### 1) Hyperparameter tuning

- Learning rate: 학습 속도
  - 예측값과 실제값의 차이를 줄이기 위해 W, b를 조정하는 속도
    - WX + b = 예측값 <-> Y = 실제값
  - learning Rate Sceduling: 학습 속도를 조정하는 것
    - ex) 1 epoch마다 learning rate를 0.9배씩 줄이기
- Batch size: 한 번에 학습하는 데이터의 양
- Finding Optimal Hyperparameter
  - Grid search: 최적의 Hyperparameter를 찾기 위해 모든 경우의 수를 다 해보는 것
    - 시간이 오래 걸림
  - Random search: 랜덤으로 몇 개의 경우의 수를 해보는 것
    - 시간이 적게 걸림
    - 추천
  - Auto ML: 자동으로 하이퍼파라미터를 찾아주는 것
    - ex) Katib, AutoKeras
    - 시간이 적게 걸림
    - 추천

### 2) Prevent Overfitting

- Collect more data
  - 주로 데이터 수가 적어서 오버피팅이 발생하는 경우가 많다.
- Early Stopping
  - Loss가 더 이상 줄어들지 않는 지점에서 학습을 일찍 멈추는 것
- Regularization
  - W의 값이 너무 커지지 않도록 제한하는 것
    - 네트워크가 복잡해지면 W의 값이 커지기 쉽다.
    - W의 값이 너무 커지면 오버피팅이 발생할 수 있다.
    - Regularization을 통해 W의 값이 커지지 않도록 제한한다.
      - 네트워크(Dense Layer)가 단순해진다.
  - L1, L2 Regularization
    - L1 Regularization
      - W의 절대값을 더해줌
    - L2 Regularization
      - W의 제곱을 더해줌
- Dropouts
  - 학습 중에 랜덤하게 뉴런을 끄는 것
    - 심플한 모델들의 조합의 효과를 낼 수 있다.(앙상블)

### 3) Weight Initialization

## 3. CNN(Convolutional Neural Network)

## 4. RNN(Recurrent Neural Network)
