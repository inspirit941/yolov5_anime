```sh
# 예시

python detect.py --weights ./weights/yolov5x.pt --source ./videos/msPAGYZvKTE/image --output ./result/msPAGYZvKTE --save-txt

```

## 되는 것

- bounding box 생성해주기 (얼굴 자체는 확실히 잘 됨. confidence score도 그럴듯 함.)
- txt 파일 생성해주기 (label, x, y, w, h 값을 txt로 만들어주는데, 지금 사용하는 라벨 규칙과 유사해 보임.)

## 코드 변경범위 파악한 부분 -> 주석으로 남아 있음.

- bounding box 색깔 -> 빨간색으로 고정되도록 변경.
- item / confidence score가 그려지는데, 안 그려질 수 있도록 코드 변경 -> label 정의 부분을 수정하면 된다.
- 사이즈 크기 너무 작으면 수집하지 말라는 가이드에 맞게 bounding box 크기 제한로직. -> xyxy2xywh() 함수에서 픽셀 간 거리 체크 -> 크기 작으면 pass

## 기대할만한 점

- Tesla P100 + pivix 2d캐릭터 데이터 8000장으로 yolov5를 fine tuning한 모델.
- 라벨링한 데이터를 classification 용도로 학습했을 때, 투입할 수 있는 리소스 대비 효율이 좋을 것으로 예상.
  - pretrained된 yolo, opencv 등의 face detection 모델은 2d 캐릭터의 인식률이 좋지 않은데, 이 모델은 인식률이 굉장히 높음.

우리가 보유한 라벨 데이터로 training + 라벨로 분류할 수 있는 것만 미리 표시하도록 하면
- 라벨링 검수할 때 작업속도가 빨라지지 않을까?



