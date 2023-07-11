# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 신유진


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 전혀 문제 없다. 
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 주석을 안달아주셔도, 코드가 워낙 깔끔하지만, 있으니 더 이해하기 쉽다.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 없다. 덕분에 내 코드의 개선점까지도 배우게 됐다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 넵, 덕분에 내 코드의 개선점까지도 배우게 됐다.
- [X] 코드가 간결한가요?
  > 깔끔 그 잡채, 덕분에 model함수가 이렇게 간결하게 작성 가능한지도 배우게 됐다.

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
1. 2-1  손 볼 곳이 없다. 덕분에 model을 간결하게 만들 수 있는 점까지도 배우게 됐다.
2. 2-2도 손 볼 곳이 없다. 
```
