### 활성화 함수 + gpgpu 
-> ai 연구의 활성화.
## 옵티마이저
- 손실함수(loss함수)를 목표치까지 구할 때 사용하는 최적화 기법
- 문제(회귀/분류-이항, 다항)별로 다양한 손실함수가 제안됨
- 기본적인 옵티마이저- 경사하강법(GD:Gradient Descent)

### 옵티마이저 / 학습률

- 수학패턴
: f(x)가 있다. 주어진 구간 안에서 최대, 최소값을 구하세요
- 실제 패턴
: f(x)를 모르지만 경향(추세선)을 알 수 있다.
: 미분(경사-기울기)
- 딥러닝 옵티마이저는 경사(기울기) 하강법
: 기울기만 보고 판단(올릴지 내릴지) 하겠다. 

### 옵티마이저의 종류 (9가지)
- Gradient Descent
- Stochastic(확률적) GD(SGD)
- Momentum
...



### Gradient Descent
### LearningRate (러닝 레이트 = 샘플링 간격)
: 경사하강법에서 기울기에 학습률(보폭)을 곱해 다음 값을 결정
: 최적값을 구하기 쉽지 않은 문제가 있음(경험, 다 돌려봐야)

### Momentum (관성이라는 관점)
https://www.google.com/url?sa=i&url=https%3A%2F%2Fyngie-c.github.io%2Fdeep%2520learning%2F2020%2F03%2F19%2Ftraining_techs%2F&psig=AOvVaw1q7GFKG-YC-uzGrXySusNy&ust=1628421309566000&source=images&cd=vfe&ved=0CAsQjRxqFwoTCOCY_Z_knvICFQAAAAAdAAAAABAD

## 이항분류 

### softmax
- hardmax에 대비되는 과정

### one-hot Encoding
: 하나의 주 성분만 가지도록 처리

### 다항분류 과정
: 이항 분류 함수를 각각 적용
: softmax처리 - 전체합을 1로 만드는 작업
: one-hot인코딩 - 주성분만 남기고 나머지를 버리를 작업 (categoricalCrossentropy가 원핫 인코딩과 비슷한 개념)


### MNIST 데이터 셋
- 손 글씨로 쓴 샘플 데이터
: 60000개의 학습용 데이터/10.000개의 테스트용 데이터
: 28\*28 사이즈의 그레이스케일 데이터

### CIFAR-10/100 데이터 셋
```javascript
function getModel(){
const model = tf.sequential();

model.add(tf.layers.flateen());//28*28 => 784(2차원 이미지 -> 1차원 데이터)
model.add(tf.layers.dense({units: 64, activation: 'relu'
  }));
model.add(tf.layers.dense({units: 64, activation: 'relu'
  }));
model.add(tf.layers.dense({units: 10, activation: 'softmax'
  }));

const optimizer = tf.train.adam();
//컴파일
model.complil({optimizer: optimizer, loss: 'categoricalCrossentropy', metrics: ['accuracy']});
			

			//문제	//정답	//5번 학습
model.fit(x_train, y_train, epochs=5)
			
model.evaluate(x_test,  y_test, verbose=2)


return model;
}
```
## 과소적합/적합/과적합
- 과소적합(Under-fitting)
: 선형회귀, 구간 별로 다른 기울기
: 구간 별로 다른 기울기
- 적합(JustFitting)
: 시그모이드
: 특이한 케이스를 설명 가능함
- 과(대)적합(Over-fitting)
: 신경망
: 노드수/레이어수..

### 과적합 방지기술

### CNN (Convolutional Neural Network)
- 영상처리ㅣ/
