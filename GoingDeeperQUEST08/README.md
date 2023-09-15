# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 조준규


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - Simplebaseline Model과 Hourglass Network를 성공적으로 구현하고 결과를 비교 분석 하였다.
```python
# 모델 구현 및 학습 부분
# history를 저장하여 모델의 loss 그래프를 확인하고자 하였다.
best_sb_model_file, sb_history = train('sb', epochs, learning_rate, num_heatmap, batch_size, train_tfrecords, val_tfrecords)
best_hg_model_file, hg_history = train('hg', epochs, learning_rate, num_heatmap, batch_size, train_tfrecords, val_tfrecords)
```
```python
# 모델 결과 비교 분석 부
# 여러 장의 이미지를 통해 다양한 결과를 비교하고자 하였다.
for t_img in test_images:
    test_image = os.path.join(os.getcwd(), 'sample_data', t_img)

    image, keypoints = predict(model, test_image)
    plt.figure(figsize=(12, 6))
    draw_keypoints_on_image(image, keypoints)
    draw_skeleton_on_image(image, keypoints)
    plt.show()
```
    
- [ ]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
  주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 코드 블록 별로 어떤 역할을 하는지 적혀져 있지만, 다른 자세한 주석이 많은 편은 아니었다.
  
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
  ”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 학습 진행시 발생했던 문제와 해결방안을 회고 부분에서 제시하였다.
```
- Simplebaseline model을 학습시킬 때 trainer의 compute_loss에서 error가 발생하였다.
- type 통일이 되지 않아서 생긴 문제인 것 같은데, for문을 제거하였더니 코드가 잘 돌아갔다.
```
```python
# for문 제거한 부분
def compute_loss(self, labels, outputs):
        loss = 0
#         for output in outputs:
        weights = tf.cast(labels > 0, dtype=tf.float32) * 81 + 1
        loss += tf.math.reduce_mean(
            tf.math.square(labels - outputs) * weights) * (
                1. / self.global_batch_size)
        return loss
```
  
- [X]  **4. 회고를 잘 작성했나요?**
    - 모델이 나타내는 현상들을 최대한 비교 분석하였다.
```
- Simplebaseline model과 Hourglass Network 모두 10 epoch 씩 학습하였다.
- 둘 다 결과가 꽤 잘 나왔고, 서로 결과가 비슷하기도 하다.
- 다만, simplebaseline model은 hourglass network 보다는 성능이 조금 떨어지는 것 같았다.

- 앉아있는 이미지의 경우에는 괜찮은 결과를 냈지만 기울어진 이미지의 경우에는 결과를 잘 내지 못했다.
- data augmentation이 없어서 생긴 문제점이라고 생각한다.
```
    
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 반복문과 함수를 적극적으로 사용하여 결과를 쉽고 간결하게 뽑아낼 수 있도록 하였다.
```python
# test_images에 다양한 이미지들을 할당해놓고 반복문을 통해 이미지를 시각화했다.
for t_img in test_images:
    test_image = os.path.join(os.getcwd(), 'sample_data', t_img)

    image, keypoints = predict(hg_model, test_image)
    plt.figure(figsize=(12, 6))
    draw_keypoints_on_image(image, keypoints)
    draw_skeleton_on_image(image, keypoints)
    plt.show()
```


# 참고 링크 및 코드 개선
```python
# Hourglass Network는 for 문을 제거하기 전에 학습한 결과인 것으로 알고 있습니다.
# for 문을 제거한 후 학습하여 compute_loss의 for 문이 의미하는 바를 알아보는 것도 좋을 것 같습니다.😁
```
