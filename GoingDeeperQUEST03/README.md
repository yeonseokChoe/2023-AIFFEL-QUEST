# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 어윤석


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 코드가 정상적으로 잘 동작하고 CAM과 Grad-CAM 각각에 대해 원본이미지합성, 바운딩박스, IoU 계산 과정을 통해 비교분석하였습니다.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 필요한 내용에 대해 주석으로 잘 설명되어있어 코드를 이해하는데 도움이 되었습니다.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 에러를 유발할 것 같은 코드를 발견하지 못했습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 코드를 잘 이해하고 작성하였습니다.
- [X] 코드가 간결한가요?
  > 필요한 코드로 간결하게 작성되었습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python
# 샘플 갯수 만큼 미리 준비한 데이터셋을 기준으로 예제를 진행하여 이미지별 결과를 비교할 수 있었습니다.
SAMPLE_NUM = 5
sample_ds = list(ds_test.take(SAMPLE_NUM).as_numpy_iterator())

cam_image_list = []
for i, d in enumerate(sample_ds):
    cam_image = generate_cam(cam_model, d)
    cam_image_list.append(cam_image)

cam_merged_image_list = []
for i, d in enumerate(sample_ds):
    cam_merged_image = visualize_cam_on_image(d['image'], cam_image_list[i])
    cam_merged_image_list.append(cam_merged_image)

grad_5_cam_image_list = []
for i, d in enumerate(sample_ds):
    grad_5_cam_image = generate_grad_cam(cam_model, 'conv5_block3_out', d)
    grad_5_cam_image_list.append(grad_5_cam_image)

cam_bbox_list = []
for i, img in enumerate(cam_image_list):
    rect = get_bbox(img)
    bbox_image = copy.deepcopy(sample_ds[i]['image'])
    bbox_image = cv2.drawContours(bbox_image, [rect], 0, (0,0,255), 2)
    cam_bbox_list.append(bbox_image)

print("CAM IoU of classes")
for i, img in enumerate(cam_image_list):
    rect = get_bbox(img)
    pred_bbox = rect_to_minmax(rect, img)
    print(f"{sample_ds[i]['label']}: {get_iou(pred_bbox, sample_ds[i]['objects']['bbox'][0])}")

print("Grad-CAM IoU of classes")
for i, img in enumerate(grad_5_cam_image_list):
    rect = get_bbox(img)
    pred_bbox = rect_to_minmax(rect, img)
    print(f"{sample_ds[i]['label']}: {get_iou(pred_bbox, sample_ds[i]['objects']['bbox'][0])}")
```

# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
