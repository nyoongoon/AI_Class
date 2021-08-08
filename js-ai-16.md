### Deep NN (Neural Network)의 특징
- 임의의 모양의 패턴을 분류할 수 있음.
- 노드가 많을 수록, 은닉 계층이 많을 수록
- Overfitting가 잘나는 특징이 있음
- 학습 정확도 > 테스트 정확도
- 방지기술이 발달함 - 학습 정확도 = 테스트 정확도

### 하이퍼 파라미터(신경망)

- 히든레이어 수 / 노드 수
- 활성화 홤수(ReLU, ...)
- 최적화(GD, SGD, Adam ..) + Learning Rate
- epoch(학습회수, 전파/역전파)

- 과적합 방지 기술
:DropOut/DropConnect
:노드/레이어수 줄이기
:L1/L2 정규화
:가중치 초기값 최적화
:Batch Normaliztion

### DropOut
: 각 Epoch마다 일정 수의 노드를 랜덤하게 drop시킨 후 학습시키는 방식
: 전체 중 dropout비율 지정
: 현재 신경망(ReLU + CIFAR + DropOut의 특징)
: 학습시간이 많이 걸림 

### DropConnect
: 노드를 drop 시키는 것이 아닌 에지(연결선)을 drop시킴
: 효과가 좀 더 좋은 (DropOut)보다
: 최신개념 텐서플로 버전 2.2에서 지원

### Regularization (집중 투자 개념)
: 가중치값이 조정될 때 규제를 적용
: 특정한 가중치에 의존도가 높은 경우 낮추는 작업
: L1Regularization - 절대값에 비례하는 비용을 적용
: L2Regularization - 절대값의 제곱에 비례하는 비용을 적용

kernel_regularizer = regularizers.l2(0.001),

### 가중치 초기값 최적화
- 초기 가중치가 난수를 사용한 경우 재수(운)에 따른 결과가 나옴
- LeCun Initialization(CNN을 처음 제안)
- Xavier Initialization(sogmoid MLP에 적합)
:tf.keras.initializers.GlorotNormal()
- He Initialization(ReLU에 적합)
:tf.keras.initializers.HeNormal()
:최근 대부분의 모델에서는 He 초기화를 주로 선택

### Batch Normalization
- Internal Covariance Shift
- Layer / Activation 마다 입력의 분포가 달라지는 현상
- Whitening 기법
: 입력의 분포를 정규분포라고 가정
: 표준정규분포 N(0,1)이 되도록 조정
: 원래값으로 환원
: 많은 계산 필요
: 분포의 특성이 변형

- 장점 
: 전파시 파라미터(인자)의 scale에 영향을 받지 않는다.
Learning rate를 크게 잡을 수 있고 빠른 학습이 가능해진다.
: 자체적인 regularization 효과
: Dropout과 유사하지만 학습속도도 향상됨

		cf) 정규분포의 특성
		: N(m, sigma^2) -m이 평균, sigma가 표준편자
		: m - sigma <= m <= + sigma(68%)
		: M - 2*sigma <= m < m+2*sigma(95%)
		: M - 3*sigma <= m < m+2*sigma(99%)

- Q-Q plot : 정규분포와의 차이를 보여주는 그래프. 

 ### CNN (convolutional Convolutional Neural Network)
: 영상처리/이미지 처리에 적합한 딥뉴럴 네트워크(DNN)
: 영상처리를 통해서 MLP가 처리해야하는 데이터를 줄임
:하지만 플요한 특성 정보손실은 최소화

 ### 픽셀과 퍼셉트론
 몇개의 픽셀을 하나의 퍼셉트론이 담당하는가? 6.125
 - 28x28x1 -> 784개의 픽셀 -> MLP(128퍼센트론 -> 10 퍼셉트론) 

### 해결첵은 해상도 / 컬러뎁스 낮추기
- 처리량 줄이기 -> 결과는 유지 또는 향상
- 컬러 -> 그레이스케일 이미지로 변경해 입력(데이터크기 감소/ 사람)
- CNN = 영상처리 레이어(정보유지하면서 처리량 줄이기) + 신경망(MLP)
- 이미지 리사이즈(해상도 낮추기) + 정보손상 최소화
: Convolution(Conv2D) + Subsampling(maxPooling2D: 리사이즈)
: Blue(블러:이미지 흐릿하게) + Resize(ReduceMax 방식 :2번 반복(다단계리사이즈)) 

### Resize(MaxPooling2D)
- 4k이미지(3840x2160) -> FullHD(1920x1080) 모니터에서 표시하려면
- 가로 해상도 절반/세로 해상도 절반
- 2x2 픽셀(점 4개) -> 1x1 픽셀 (점 1개)로 대표

: 평균값으로 대표 (ReduceMean)
: 최소값으로 대표 (ReduceMin)
: 최대값으로 대표 (ReduceMax)

: CNN의 ReduceMax과정(리사이즈, subsampling) 과정에서 일종의 과적합 발생. 이를 개선하기 위해 Batch Normalization 적용
: ReduceMax의 결과에 Batch Normalization(BN)을 적용하는 것이 궁합이 좋음
- cnn에서는 bn을 많이 사용함
