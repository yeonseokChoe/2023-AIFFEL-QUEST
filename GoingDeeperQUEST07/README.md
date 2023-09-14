# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 서희원


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
      퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
    
    |평가문항|상세기준|
    |---|---|    
    |1. multiface detection을 위한 widerface 데이터셋의 전처리가 적절히 진행되었다.|tfrecord 생성, augmentation, prior box 생성 등의 과정이 정상적으로 진행되었다.|
    |2. SSD 모델이 안정적으로 학습되어 multiface detection이 가능해졌다.|inference를 통해 정확한 위치의 face bounding box를 detect한 결과이미지가 제출되었다.|
    |3. 이미지 속 다수의 얼굴에 스티커가 적용되었다.|이미지 속 다수의 얼굴의 적절한 위치에 스티커가 적용된 결과이미지가 제출되었다.|

- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
  주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    ```
    자카드 유사도를 계산하는 메소드가 준비되었습니다. 아래 encode_tf는 이를 이용해서 TFRecord 데이터셋의 라벨을 가공하는 메소드입니다. 내용을 정리하면 다음과 같습니다.

    jaccard 메소드를 이용해 label의 ground truth bbox와 가장 overlap 비율이 높은 matched box를 구한다.
    _encode_bbox 메소드를 통해 bbox의 scale을 동일하게 보정한다.
    전체 default box에 대해 일정 threshold 이상 overlap되는 ground truth bounding box 존재 여부(positive/negative)를 concat하여 새로운 label로 업데이트한다.
    ```
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
  ”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
      실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    ```python
    def crown(img, boxes, classes, scores, box_index, class_list):
        img_height = img.shape[0]
        img_width = img.shape[1]
    
        x_min = int(boxes[box_index][0] * img_width)
        y_min = int(boxes[box_index][1] * img_height)
        x_max = int(boxes[box_index][2] * img_width)
        y_max = int(boxes[box_index][3] * img_height)
    
        if classes[box_index] == 1:
            color = (0, 255, 0)
        else:
            color = (0, 0, 255)
        sticker_path = '/content/E-8-3.png' # 왕관 이미지의 경로
        img_sticker = cv2.imread(sticker_path) # 스티커 이미지를 불러옵니다 // cv2.imread(이미지 경로) → image객체 행렬을 반환
        img_sticker = cv2.resize(img_sticker, (img_width,img_height))
        bbox = (x_min, y_min, x_max, y_max)
        img.paste(img_sticker, bbox)
        #cv2.rectangle(img, (x_min, y_min), (x_max, y_max), color, 2)
    ```
  
- [ ]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    ```python
    def _create_head_block(inputs, filters):
        x = tf.keras.layers.Conv2D(filters, kernel_size=(3, 3), strides=(1, 1), padding='same')(inputs)
        return x
    ```

# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
