# COVID_CT_Classification
CNN 기반으로 코로나 바이러스 감염 여부를 분류
<br><br>

![1](https://user-images.githubusercontent.com/55770741/136551370-9afd35b6-9e2a-40eb-8ae7-be182a6e8db7.JPG)
<br><br>

## 1차 시도
- 기본적인 CNN Model을 사용하여 예측
- 예측 성능은 좋았으나 Dataset이 딥러닝 모델을 돌리기에 너무 적기 때문에 과적합 발생

## 2차 시도
- 과적합을 피하고 general한 모델 구축을 위해 아래와 같이 네 가지를 시도
1. Train/val/test Dataset의 %를 50%/10%/40%으로 변경
2. 과적합을 방지하기 위해서 Dropout 추가
3. 데이터 증강
4. 이미지의 픽셀을 작게하여 과적합을 방지
- Accuracy가 많이 감소하게 되고, Test Accurac로 0.7~ 0.8 출력
