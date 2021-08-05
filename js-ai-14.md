
### mlp의 조건
1. 완전연결
2. 모든 에지별로 가중치 
3. 히든 레이어 ( 은닉계층) - 하나 이상 존재
(은닉 계측이 2단 이상인 네크워크를 딥 신경망)

### 신경망의 학습
- 에포크 = 전파 1회 + 역전파 1회
- 전파(순전파)
: 최종 출력값이 원하는 결과값이 아닐 경우 오차값 줄이기 위해 
- 역전파
: 최종 출력값이 원하는 결과값이 아닐 경우 오차값을 줄이기 위해
: 편미분(최종결과값에서 입력값의 기여도 계산)

### Vanishing Gradient
- 신경망이 딥해지면 학습이 안되는 경우
- 시그모이드를 사용하는 뉴럴네트워크에서는 역전파시 시그모이드의 편미분 값을 계산해야함
- 편미분시 최대값 100 -> 25로 줄어 여러 단이 추가될 때마다 최대값이 급격하게 감소 


### 시드모이드
- 지수 함수로 인위적으로 만든 함수
- 신경망에서 많이 사용하는 활성화함수
- 회귀/ 분류에서 효과적
- y 값이 0 에서 1 사이 
- 시그모이드의 편미분 = y값이 0에서 0.25

## 돌파구 - ReLU(Rectified Linear Unit)
- 히든레이어가 깊어져도 결과값이 나옴
- 역전파과정에서 가중치값이 제대로 값이 나옴
- 시드모이드의 대체재
- 빠른계산, 학습 가능
- maxOut 특성을 이용
- 역전파시 계산 난이도 하락 
-> 딥러닝의 빅뱅

### 돌파구 GPU
- 계산량 문제
- 표준 OpenCl
- CUDA


### MLP(TensorFlow.js)
``` javascript
function getModel(){
const model = tf.sequential();

model.add(tf.layers.flateen());
model.add(tf.layers.dense({units: 64, activation: 'relu'
  }));
model.add(tf.layers.dense({units: 64, activation: 'relu'
  }));
model.add(tf.layers.dense({units: 10, activation: 'softmax'
  }));

const optimizer = tf.train.adam();
model.complil({optimizer: optimizer, loss: 'categoricalCrossentropy', metrics: ['accuracy']});

return model;
}
``` 
