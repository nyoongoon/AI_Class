### 자바스크립트 기반 TensorFlow.js

- javascript(+html)
- Node.js(+Typescript?)
- Tensorflow(Python)
: TensorBoard 
: CNN
: RNN -> 자연어처리 계열 
- PyTorch(OOP기반 파이썬)

### 텐서(배열/행렬)의 세가지 속성
- rank(차원) / shape(행,열) / dtype(데이터타입)

train_image.shape

cf)파이썬) 28 x 560(2차원) => reshape(numpy) =>28 * 28 * 20(3차원)


### predict() 함수
- 훈련된 모델을 사용하여 이미지에 대한 예측을 만듬.

### 신경망 정확도 높이기
: 오답을 고쳐서 정확도를 맞추는 방식이 아니라
: 코드 앞단에 신경망 레이어를 늘리고 과적합 방지를 시키고, 영상처리(블러, 리사이즈) 레이어를 추가시키는 방식 등으로 정확도를 높인다

### model.fit()
- fit()을 더 돌리면 이미 진행된 상황에서 이어서 진행된다. 

### 과적합
- 학습 정확도와 테스트 정확도의 차이가 점점 벌어짐.

### 과적합 방지(케라스)
- 드랍아웃(Dropout(0.2))
- 배치정규화(BatchNormalization())
- SGD 옵티마이저(optimizers.SDG(learning_rate=0.001)
- He 초기화
- L1 정규화 
- L2 정규화


