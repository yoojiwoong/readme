모델 실행 가이드
===============

* 본 모델은 .xml 데이터를 읽어와 이미지 파형 그래프로 변환한뒤 생성된 이미지를 분류하는 모델입니다.
* 변수 normal_validation_path와 arrhythmia_validation_path에 정상 및 부정맥 .xml 파일이 들어있는 폴더 경로를 입력해주시면 됩니다.
* 파일 경로를 입력하면 draw_graph_and_save_image() 함수를 통해 각 경로에 있는 .xml 파일을 읽어와 WaveFormData를 읽어온뒤 디코딩 작업을 진행합니다.
* 여러개의 Leads 중 랜덤한 하나의 파형을 선택하여 임시로 tmp_img.PNG을 생성하고 OpenCV로 읽어와 변수(validation_normal_imgs, validation_arrhythmia_imgs)에 할당합니다.
* 할당된 데이터에 라벨을 지정하여 dataset을 생성합니다.
* 여기서 라벨값은 {0:정상, 1:부정맥} 입니다.
* 다음으로 CNNClass() 클래스를 통해 모델을 생성하고 ecg_classification_model.pt 모델 가중치 파일을 로드합니다.
* 다음으로 성능 평가 과정을 통해 auc score를 출력합니다.

* 여기서 수정하실 부분은 test .xml 파일이 있는 폴더의 경로와 모델이 위치한 경로 두 부분을 수정해 주시면 됩니다.

환경
====

* 본 모델이 학습된 환경은 다음과 같습니다.
* CPU: AMD Ryzen 7 3700X 8-Core
* RAM: 64.0GB
* GPU: NVIDIA GeForce RTX 3070

파일
====

* 보내드리는 학습 코드는 .ipynb 파일로 다음과 같습니다
* Data xml to image.ipynb: .xml 파일을 읽어와 이미지로 변환하여 저장하는 코드입니다.
* ECG Classification - ver3.ipynb: 저장한 이미지를 불러와 모델을 학습한 코드입니다.
* ECG_Classification.ipynb: 위의 두 파일을 하나로 합쳐 경로를 입력 후 자동으로 이미지 형태로 변환, 전처리, 모델 Load, 학습은 제외한 평가 부분만 포함된 코드입니다. 이 코드를 돌리시면 됩니다.

감사합니다.
