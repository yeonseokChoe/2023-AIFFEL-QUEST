# AIFFEL Campus Online 5th Code Peer Review Template
- 코더 : 조준규
- 리뷰어 : 최지수


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?  
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
- [X] 코드가 에러를 유발할 가능성이 없나요?
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
- [X] 코드가 간결한가요?


# 참고 링크
저희끼리 얘기하다가 object detection 할 때 차선도 고려해서 운전자 기준으로 양쪽 차는 배제시키면 안되나?
하고 찾아보았던 자료 입니다.
https://blogs.nvidia.co.kr/2019/05/10/drive-labs-path-perception/

LaneNet과 PathNet이라는데 비슷한 CNN기반 백본에 멀티클래스 분류면, object detection이랑 path, lane 디텍션 한번에 되는
모델을 만들면 완전체가 되겠다 라는 생각이 듭니다.

그러려면 학습 라벨을 적절히 만들어줘야 하는데, 나중에 어떤식으로 접근하면 좋겠다 싶은 인사이트가 있으시면 알려주세요 :)
저는 막연한게 모델 구조는 object detection을 가져가되 라벨 데이터에 클래스만 추가하면 되는거 아녀? 이러고 있습니다.
