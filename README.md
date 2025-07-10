# yolo-coco-project
## 필요 프로그램 설치
python install <br />
https://www.python.org/downloads/release/python-3135/ <br />
"Add python.exe to PATH" 옵션을 반드시 체크하세요.

VScode install <br />
https://code.visualstudio.com/
<br />
python, c++ install

VScode setup install <br />
https://visualstudio.microsoft.com/ko/thank-you-downloading-visual-studio/?sku=Community&channel=Release&version=VS2022&source=VSLandingPage&cid=2030&passive=false

<img width="636" height="541" alt="Image" src="https://github.com/user-attachments/assets/9c547296-cdd3-4cbc-8d13-5bf5a8524880" />

git bash install <br />
https://git-scm.com/downloads

바탕화면에 "yolo-coco-project" 파일 생성
<br />
gitbash 실행 후 생성한 파일로 이렉토리 이동
```bash
cd /Desktop/yolo-coco-project
```
디렉토리 이동 후 파이썬 가상환경 설정
```bash
python -m venv ~/Desktop/yolo-coco-project/
```
가상환경 실행
```bash
source ~/Desktop/yolo-coco-project/Scripts/activate
```

## 가상환경에 필요 라이브러리 다운로드
```bash
pip3 install torch torchvision torchaudio
pip install ultralytics
pip install opencv-python
```
user-script 폴더 생성


## 라이브러리 설치 확인 코드 
파일명 check.py 로  user-script에 저장
```python
import torch
import cv2
import ultralytics

print(f"PyTorch version: {torch.__version__}")
# CPU 버전을 설치했으므로 False가 나와야 정상입니다.
print(f"Is CUDA available: {torch.cuda.is_available()}")
print(f"OpenCV version: {cv2.__version__}")
print(f"Ultralytics YOLO version: {ultralytics.__version__}")

print("\nAll good! Your environment is ready.")
```
아래 명령어를 프롬포트에 입력하여 코드를 실행
```bash
python check.py
```
## 실행코드
파일명 main.py 로 user-script에 저장
```python
# 1. 라이브러리 임포트
from ultralytics import YOLO
import cv2

# 2. 모델 로드
model = YOLO('yolov8n.pt')

# 3. 웹캠 초기화
cap = cv2.VideoCapture(0)

if not cap.isOpened():
    print("Error: Could not open webcam.")
    exit()

# 💻 사용자가 조절 가능한 창 생성
window_name = "YOLOv8 Live Object Detection"
# cv2.WINDOW_NORMAL: 사용자가 창 크기를 조절할 수 있게 함
cv2.namedWindow(window_name, cv2.WINDOW_NORMAL) 

# 아래 라인을 삭제 또는 주석 처리하여 사용자가 직접 창을 조절하게 합니다.
# cv2.setWindowProperty(window_name, cv2.WND_PROP_FULLSCREEN, cv2.WINDOW_FULLSCREEN)

# 4. 메인 반복문
while True:
    ret, frame = cap.read()
    if not ret:
        print("Error: Failed to capture frame.")
        break

    # 5. 프레임에서 객체 탐지 수행
    results = model(frame)

    # 6. 결과 시각화
    annotated_frame = results[0].plot()

    # 7. 화면에 프레임 표시
    cv2.imshow(window_name, annotated_frame)

    # 8. 'q' 키를 누르면 반복문 종료
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

# 9. 자원 해제
cap.release()
cv2.destroyAllWindows()
```
아래 코드로 메인코드 실행
```bash
python main.py
```
