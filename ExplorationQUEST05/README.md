# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 황인준


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
  : 성공적으로 인물사진, 동물사진, 배경변경 사진을 만들어냈습니다.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
   ```python
       #  mask가 255인 부분(사람) - 원본 이미지, 나머지 부분(배경) - 블러 이미지
        img_concat = np.where(img_mask_color==255, img_orig, img_bg_blur)

        plt.figure(figsize=(15,15)) # 이미지 크기 조정
        plt.axis('off') # 축 없애기
   ```
- [X] 코드가 에러를 유발할 가능성이 없나요?
  
  : 코드를 cell 별로 작성돼서 에러에 대응이 쉽도록 작성됐습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?

  : 만들어진 사진에 대해서 문제점을 지적하고 그것에 대한 해결책을 제시함으로써 학습 내용에대한 파악이 됐음을 알 수 있습니다.

  > 'ex) Canny Edge detection은 thresholding을 이용하여 객체의 edge를 검출해내는 방식이다.
  > 이 방식은 굉장히 오래된 edge 검출 방식이고, 이후 edge 검출을 위해 많은 방식이 태어났다.
  > Edge를 잘 검출하게 되면 객체에 대한 segmentation이 수월해진다.
  > 이미지 상의 객체를 나누는 기준을 edge로 정하면 되기 때문이다.
  > Segmentation에서 가장 중요한 부분은 픽셀 단위에서 각 픽셀이 어느 객체에 속하는 지 확인하는 것이라고 생각한다.
  > 그리고 이를 위해 가장 중요하게 찾아야 하는 것은 edge 부분이라고 생각한다.
  > Edge를 찾는 또 다른 방법은 depth camera를 이용하는 방법이다.
  > 기존의 카메라는 이미지의 rgb 값의 차이로 edge를 구분했다면, depth camera는 거리의 차이로 edge를 구분할 수 있다.
  > Edge를 검출하는 기법을 적절히 융합한다면 segmentation의 mask를 좀 더 확실하게 할 수 있을 것이라 생각한다.'
- [X] 코드가 간결한가요?
  코드가 간결하게 작성됐습니다.



# 참고 링크 및 코드 개선
  > Canny Edge detection을 통해서 얻은 경계선이 뚜렷한 사진을 orig에 입혀서 동일한 segmentation모델에 사용해보는 방법도 추천해 드리고 싶습니다.
  > 경계면이 두꺼워짐으로 인해서 발생하는 trade-off도 있을것 같아서 걱정이 되긴하지만, 더 깔끔하게 seg image를 얻을 수 있지 않을까 생각합니다.
