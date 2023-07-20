# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 서희원


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네 줄 마다 주석을 작성해 쉽게 이해할 수 있었습니다
  ```python
  @tf.function() # 빠른 텐서플로 연산을 위해 @tf.function()을 사용 
  def apply_augmentation(sketch, colored):
    stacked = tf.concat([sketch, colored], axis=-1) # 1. 두 이미지가 채널축으로 연결
    
    _pad = tf.constant([[30,30],[30,30],[0,0]]) # 2. 1의 결과에 각 50% 확률로 reflect padding/constant padding이 30픽셀의 pad width만큼 적용
    if tf.random.uniform(()) < .5:
        padded = tf.pad(stacked, _pad, "REFLECT") 
    else:
        padded = tf.pad(stacked, _pad, "CONSTANT", constant_values=1.)

    out = image.random_crop(padded, size=[256, 256, 6]) # 3. 2의 결과에서 (256,256,6) 크기를 가진 이미지를 임의로 잘라냄
    
    out = image.random_flip_left_right(out) #4. 3의 결과를 50% 확률로 가로로 반전
    out = image.random_flip_up_down(out) #5. 4의 결과를 50% 확률로 세로로 반전
    
    if tf.random.uniform(()) < .5:
        degree = tf.random.uniform([], minval=1, maxval=4, dtype=tf.int32)
        out = image.rot90(out, k=degree) # 6. 5.의 결과를 50% 확률로 회전
    
    return out[...,:3], out[...,3:]  
  ```
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 네 바로바로 결과가 보였습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네 여러번 학습을 돌려 결과를 잘나오게 만들었습니다.
  ```python
  EPOCHS = 100
  
  generator = UNetGenerator()
  discriminator = Discriminator()
  history = {'gen_loss':[], 'l1_loss':[], 'disc_loss':[]}
  
  for epoch in range(1, EPOCHS+1):
      for i, (sketch, colored) in enumerate(train_images):
          g_loss, l1_loss, d_loss = train_step(sketch, colored)
          history['gen_loss'].append(g_loss)
          history['l1_loss'].append(l1_loss)
          history['disc_loss'].append(d_loss)      
              
              
          # 100회 반복마다 손실을 출력합니다.
          if (i+1) % 100 == 0:
              print(f"EPOCH[{epoch}] - STEP[{i+1}] \
                      \nGenerator_loss:{g_loss.numpy():.4f} \
                      \nL1_loss:{l1_loss.numpy():.4f} \
                      \nDiscriminator_loss:{d_loss.numpy():.4f}", end="\n\n")
  ```
- [X] 코드가 간결한가요?
  > 네

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

# 참고 링크 및 코드 개선
