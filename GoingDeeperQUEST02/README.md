# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 최연석


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네 augmentation 별로 분류하여 코드를 작성 하였고 플로우에 따라 적절한 주석을 달았습니다.
  '''
  > CutMix
  > Mixup
  > #전처리 적용된 데이터 확인하기
  > #모델 만들기
  > #사용할 모델 compile
  > #모델 학습 진행
  > #결과화면 그래프로 그려보기
  '''
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 고정된 입력데이터로 코드가 에러를 유발할 가능성은 적어 보입니다.
  > '''
  > input_shape=(224,224,3)
  > mixed_imgs = tf.reshape(tf.stack(mixed_imgs), (batch_size, img_size, img_size, 3))
    mixed_labels = tf.reshape(tf.stack(mixed_labels), (batch_size, num_classes))
  > '''
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 해당 코드를 작성하고 비교 분석 및 문제점을 추가로 작성하였습니다.
  > '''
  > 각 Augmentation 기법을 적용하고, 그에 따른 성능 비교 분석 및 문제점
cutmix, mixup은 no_aug, aug와는 다르게 train loss가 validation loss보다 높게 나타났다.
그리고 4가지 모델의 validation loss는 cutmix, mixup이 살짝 높긴 하지만 전체적으로 비슷한 경향을 나타내었다.
이는 이미지를 섞어서 학습을 시켜도 정제가 되어있지 않은 validation dataset에 대해 좋은 성능을 나타낸다는 것을 의미한다.
CutMix, MixUp은 학습 데이터를 혼합하여 모델이 더 일반회된 특성을 학습하도록 도와준다.
학습중에 모델은 더 다양한 입력 형태와 패턴을 다루게 되는데, 이로 인해 모델이 복잡한 문제에 대처하려고 노력하게 된다.
따라서 train 데이터셋에서 cutmix, mixup 방법을 통한 데이터 증강은 모델이 더 어려운 학습 과정을 겪게 하므로 일반적으로 아무런 데이터 증강을 적용하지 않은 원본이미지로 구성된 validation loss보다 train loss가 더 높게 나타난다.
  > '''
- [X] 코드가 간결한가요?
  > 필요한 코드의 함수화 및 비교 모델을 변수로 저장하여 구분하기 쉬웠습니다.
  > '''
  > def cutmix(image, label, prob=1.0, batch_size=16, img_size=224, num_classes=120):
  > def mixup(image, label, prob=1.0, batch_size=16, img_size=224, num_classes=120):
  > def normalize_and_resize_img(image, label):
  > def augment(image, label):
  > resnet50 = keras.models.Sequential([ ~
  > aug_resnet50 = keras.models.Sequential([ ~
  > cutmix_resnet50 = keras.models.Sequential([ ~
  > mixup_resnet50 = keras.models.Sequential([ ~
  > '''

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python
# 사칙 연산 계산기
class calculator:
    # 예) init의 역할과 각 매서드의 의미를 서술
    def __init__(self, first, second):
        self.first = first
        self.second = second
    
    # 예) 덧셈과 연산 작동 방식에 대한 서술
    def add(self):
        result = self.first + self.second
        return result

a = float(input('첫번째 값을 입력하세요.')) 
b = float(input('두번째 값을 입력하세요.')) 
c = calculator(a, b)
print('덧셈', c.add()) 
```

# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
