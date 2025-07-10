## yolo-coco-project
# 필요 프로그램 설치
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
```
cd /Desktop/yolo-coco-project
```
디렉토리 이동 후 파이썬 가상환경 설정
```
python -m venv ~/Desktop/yolo-coco-project/
```
가상환경 실행
```
source ~/Desktop/yolo-coco-project/Scripts/activate
```

# 가상환경에 필요 라이브러리 다운로드
```
pip3 install torch torchvision torchaudio
pip install ultralytics
pip install opencv-python
```

# 라이브러리 설치 확인 코드 
check.py 로 저장
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
