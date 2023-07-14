# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : [이태훈](https://github.com/git-ThLee)


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 네! 
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네! 주석을 통해 이 코드를 왜 썼는지 이해됨.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 네! 
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네!
- [X] 코드가 간결한가요?
  > 네! 

# 근거's
- [X] 주석을 보고 작성자의 코드가 이해되었나요?

```python
data_dir = os.getenv('HOME') + '/aiffel/kaggle_kakr_housing/data'

train_data_path = join(data_dir, 'train.csv')
sub_data_path = join(data_dir, 'test.csv')      # 테스트, 즉 submission 시 사용할 데이터 경로

print(train_data_path)
print(sub_data_path)
```

- [X] 코드가 에러를 유발할 가능성이 없나요?

```python
fig, ax = plt.subplots(9, 2, figsize=(20, 60))

# date 변수는 제외하고 분포를 확인합니다.
count = 1
columns = data.columns
for row in range(9):
    for col in range(2):
        sns.kdeplot(data=data[columns[count]], ax=ax[row][col])
        ax[row][col].set_title(columns[count], fontsize=15)
        count+=1
        if count == 19 :
            break
```


- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?

```python
def AveragingBlending(models, x, y, sub_x):
    for m in models : 
        m['model'].fit(x.values, y)
    
    predictions = np.column_stack([
        m['model'].predict(sub_x.values) for m in models
    ])
    return np.mean(predictions, axis=1)

print('얍💢')
```

- [X] 코드가 간결한가요?

```python
y_pred = AveragingBlending(models, x, y, sub)
print(len(y_pred))
y_pred
```


# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
