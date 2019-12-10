# Tensorflow TIL

Machine Learning Lecture: 모두를 위한 딥러닝 시즌 2 on Youtube

### Requirements

1. Python 3.6.4 (virtual env)

   1. [Python.org](https://www.python.org/downloads/windows/) 에서 Python 3.6.4 - Download [Windows x86-64 web-based installer](https://www.python.org/ftp/python/3.6.4/python-3.6.4-amd64-webinstall.exe)

   2. 시스템 환경 변수 편집 >> 환경변수 >> 사용자 변수 >> Path

      ```
      C:\Users\LSJ\AppData\Local\Programs\Python\Python36
      C:\Users\LSJ\AppData\Local\Programs\Python\Python36\Scripts
      ```

      위의 내용을 추가하고 상단에 위치시킨다.

   3. 가상환경을 만들고자 하는 위치에서 가상 환경 생성

      `python -m venv [venv_name]`

   4. (선택) 원래의 버전으로 돌아가고자 한다면 환경변수를 삭제해준다. 
   5. venv on / off
      1. on: `source ./[venv_name]/Script/activate`
      2. off: `deactivate`

2. Repository

   `pip list` 를 통해 설치를 확인

   1. Tensorflow 2.0.0 >> `pip install tensorflow`
   2. Jupyter 1.0.0 >> `pip install jupyter` 



## 1. Machine Learning Basic 

- What is ML?

  - Why we use? Limitations of explicit programming
  - Arthur Samuel(1959) : Field of study that gives computers the ability to learn without being explicitly programmed

- What is learning?

  1. Supervised learning: learning with labeled examples (= training set)
     - Most commom problem: Image labeling, Email spam filter, Predicting exam score
     - Training data set?
       - y: data의 label
       - x: data의 feature
       - Training data set을 통해 model을 만들게 되고, test input을 넣어 예상값을 얻는다.
     - Type of supervised learning
       - Regression : 범위 안의 값으로 예측
         - ex) Predicting final exam score(0~100) based on time spent
       - Binary classification
         - ex) Pass/non-pass
       - multi-label classification
         - ex) Grade(A, B, C, D, F)

  2. Unsupervised learning: un-labeled data (데이터를 보고 스스로 학습)



## 2. Linear Regression

선형적인 예상이 주변에 많이 있다. 예를들면, 집의 크기에 따른 부의 정도, 시간투자에 따른 시험 결과

- Hypothesis: H(x) = Wx + b
  - Which hypothesis is better?
    - 실제 데이터와 가설간의 거리가 가까울 수록 좋다.

- Cost(Loss) function: (H(x) - y)^2

  - 차이가 음수일 수도 있기 때문에 제곱하여 계산한다.
    $$
    cost = \frac{1}{m} \sum_{i=1}^m (H(x_i)-y_i)^2
    $$

- cost를 가장 작게하는 W & b를 구하는 것



## 3. How to minimize cost

$$
cost(W) = \frac{1}{m} \sum_{i=1}^m (H(x_i)-y_i)^2
$$

- Hypothesis 를 간략화하여 H(x) = Wx 라 하고 cost(W)를 구해본다.
  - W=1, cost(W) = 0
  - W=0, cost(W) = 4.67
  - W=2, cost(W) = 4.67
  - ...

- Gradient descent algorithm: 경사를 따라 내려가는 알고리즘(?)

  - W, b 뿐만 아니라 더 많은 인자를 갖고 있는 경우에도 쓰일 수 있다.

  - 어떤 지점에서 시작해도 상관 없다!

  - W를 바꾸면서 경사도를 구하기를 반복한다.

  - Cost(W)를 미분할 경우
    $$
    cost(W) = \frac{1}{2m} \sum_{i=1}^m (Hx_i-y_i)^2
    $$

- 

$$
W := W - \alpha \frac{\delta}{\delta W}cost(W)
$$

​		- alpha: Learning rate

- Gradient descent algorithm
  $$
  W := W - \alpha \frac{1}{m}\sum_{i=1}^m (Wx_i-y_i)x_i
  $$

- **Linear Regression의 경우, Convex function인 경우에만 Gradient descent algorithm을 사용**
  - Convex function(볼록 함수)

