# TensorFlow.js 이해
- 파이썬 버전의 텐서플로우의 마이그래이션
- 코드가 좀 복잡 -> 쓰기 어려움
- 객체지향 기술의 도움이 필요
- 캡슐화(코드 감추기) / 상속
- 자바스크립트가 상대적으로 코드가 짧은  

### run()
- 일종의 캡슐화(로직)
- 정보은닉
- 관리가능성(함수없는 코드) ->함수로 만들어 관리
- 객체지향의 상속까지 결합가능

cf) ERP 전사적 자원관리

cf) 파이썬 실행방식
1. 객체지향
2. 함수스타일의 프로그램 (C형태로) - main()
3. 함수가 없어도 됨

### Keras모델(파이썬) 모델 변환하기
``` python
model.save(filename)

```

``` 
pip3 install tensorflowjs
tensorflowjs_converter --input_format keras  path/to/my_model.h5  path/to/tfjs_target_dir
```

### Keras모델 (자스) 모델 변환하기
``` javascript
import * as tf from '@tensorflow/tfjs';

const model = await tf.loadLayersModel('https://foo.bar/tfjs_artifacts/model.json');

const example = tf.fromPixels(webcamElement);  // example
const prediction = model.predict(example);
```

### node.js -> tensorflow.js
- node.js tensorflow.js 예제 
$ docker exec -it  ubuntu2 bash
```language


# apt update
# apt install nano
# apt install nodejs
# apt install npm
# npm install -g typescript
# mkdir sample  
# cd sample
# npm init -y -> package.json 생성
# npm install -g @tensorflow/tfjs -> node_modules 가 생성되고 설치됨

```
```
const tf = require('@tensorflow/tfjs')
const model = tf.sequential();
model.add(tf.layers.dense({ units: 1, inputShape: [200] }));
model.compile({
  loss: 'meanSquaredError',
  optimizer: 'sgd',
  metrics: ['MAE']
});


// Generate some random fake data for demo purpose.
const xs = tf.randomUniform([10000, 200]);
const ys = tf.randomUniform([10000, 1]);
const valXs = tf.randomUniform([1000, 200]);
const valYs = tf.randomUniform([1000, 1]);


// Start model training process.
async function train() {
  await model.fit(xs, ys, {
    epochs: 100,
    validationData: [valXs, valYs],
    // Add the tensorBoard callback here.
    callbacks: tf.node.tensorBoard('/tmp/fit_logs_1')
  });
}
train();
```

## 
