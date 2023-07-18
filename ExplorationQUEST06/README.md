# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 어윤석

# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [ ] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 코드는 정상적으로 동작하였지만 headline 데이터 전처리에 실수가 있었습니다.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 필요한 사항에 주석으로 설명이 되어있어 코드 이해에 도움이 되었습니다.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 데이터 설정이 잘못되었지만 코드에 에러를 유발하지 않았습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 코드를 잘 이해하고 작성하였습니다.
- [X] 코드가 간결한가요?
  > 필요한 코드로 간결하게 작성되었습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
### 코드 전처리시 print를 출력하여 경과를 확인하였습니다.
```python
# 전체 text 데이터에 대한 전처리
clean_text = []
n = 1
for sentence in data['text']:
    clean_text.append(preprocess_sentence(sentence))    
    if n % 1000 == 0:
        print(f"{n} / {len(data['text'])}")        
    n += 1

print("text 전처리 결과 :", clean_text[:5])
```

# 참고 링크 및 코드 개선
### headline 데이터 전처리에 text데이터 코드가 잘못 입력되어 전체적인 결과에 영향을 주었습니다.
```python
# 전체 headlines 데이터에 대한 전처리
clean_headlines = []
n = 1
# for sentence in data['text']:
for sentence in data['headline']:
    clean_headlines.append(preprocess_sentence(sentence, False))    
    if n % 10000 == 0:
        print(f"{n} / {len(data['headlines'])}")        
    n += 1

print("headlines 전처리 후 결과 :", clean_headlines[:5])
```
