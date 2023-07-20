# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 최연석


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네 주석 처리가 잘 되어 있어 코드가 이해하기 쉬웠습니다.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 런타임 시 에러가 발생하는 부분은 없습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 수집, 전처리, 모델구축, 학습, 평가 등 순서대로 이해하고 코드를 작성하였습니다.
- [X] 코드가 간결한가요?
  > 구간 별로 분류하였으며 함수화하여 간결하게 코드를 확인 할 수 있었습니다.

# 예시
### loss accuracy 확인
'''
plt.plot(history.history['loss'], label='train')
plt.plot(history.history['accuracy'], label='test')
plt.legend()
plt.show()
'''

### 챗봇 테스트하기
'''
print(*sentence_generation('누구세요?'), sep='\n')
입력 : 누구세요?
출력 : 저는 위로해드리는 로봇이에요 .
'''

### 모델 성능 평가까지 이루어져 구축한 모델에 대한 신뢰도를 얻을 수 있었습니다.


