# COVID_CT_Classification
CNN 기반으로 코로나 바이러스 감염 여부를 분류
<br><br>

![1](https://user-images.githubusercontent.com/55770741/136551370-9afd35b6-9e2a-40eb-8ae7-be182a6e8db7.JPG)
<br><br>

## 1차 시도 :open_mouth:
- 매우 간단한 Conv  - MaxPool - Flatten - Dense model로 구현
- val_acc가 1로 정확하게 나왔지만 Dataset이 딥러닝 모델을 돌리기에 너무 적기 떄문에 과적합이 발생했다.
Train Loss : 1.0
Test Loss : 1.0

## 2차 시도 :hushed:
- 기본적인 CNN Model로 구현
- 이 방법 또한 val_acc가 1로 정확하게 나왔지만 과적합이 발생했다
Train Loss : 1.0
Test Loss : 1.0

## 3차 시도 :sweat_smile:
- 과적합을 방지하기 위해서 다양한 방법시도  
=> Train/val/test Dataset의 %를 7 : 1 : 2 => 5 : 1 : 4로 변경
=> Dropout Layer를 추가하여 과적합 방지
=> Dense node 수 down
- 그래프를 통해서 전보다 과적합이 줄어들었지만 여전히 과적합 존재
Train Loss : 1.0
Test Loss : 1.0

## 4차 시도 :smile:
- Augmentation을 이용하여 데이터량 증가(과적합 방지에 가장 효과가 좋을것이라고 예상)
- rescale, rotation_range, width_shift_range, height_shift_range, shear_range, zoom_range, horizontal_flip, fill_mode 등 다양한 기법 사용
- 과적합 방지 성공!!
Train Loss : 0.68
Test Loss : 0.78

## 5차 시도  :disappointed_relieved:
- 이미지 처리를 사용하여 연산 속도 증가 및 예측 정확도 향상
- 이미지 자르기 및 히스토르갬 평활화를 사용
Train Loss : 0.66
Test Loss : 0.68

## Inception-v3 Model
- X-ray Classification에서 많이 사용된다고 하여 사용, GoogleNet의 기반이 되는 모델
Train Loss : 0.68
Test Loss : 0.70
![inception](https://user-images.githubusercontent.com/55770741/139357584-5ede86d5-b4aa-48aa-ada9-f1d991a00528.JPG)<br>

## Reduce Inception-v3
- Convolution 1x1 Layer를 이용아여 dimension을 줄여, AlexNet보다 12배만큼 적은 파라미터로 훈련
Train Loss : 0.63
Test Loss : 0.68
![reduce_inception](https://user-images.githubusercontent.com/55770741/139357614-ea48eb44-8543-464e-b196-3cd6e4056864.JPG)


# Review
현업에 가서 문제에 부딪힐 때 내가 원하는대로 데이터가 주어져있다고 생각하지 않는다. 그래서 데이터량이 적은 Dataset을 찾았고 그 중 내가 가고싶은 분야인 의료쪽 Data를 생각하고 있었다.
그래서 COVID-19 Dataset을 선택하여 진행했다.
이 프로젝트를 하면서 가장 배운점은 Over Fitting을 방지하기 위해서 다양한 방식을 사용하고, 성능을 높이기 위해서 여러가지 Fine Tuning을 해봤다는 것인데, 파라미터들을 조정하고, Model Layer를 추가하며 val_acc를 높이는 작업이 매우 재미있었다.(결과가 나올때 떨렸습니다 ㅎ) 이미지 처리도 사용해보고 여러가지 기초를 다지는 프로젝트였던것같다.

# Requirement
+ Python
+ Tensorflow
+ Pandas
+ Numpy
+ Matplotlib
+ OpenCV
