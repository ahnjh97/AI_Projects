<div align="center">

# AI Projects

**Machine Learning, Computer Vision, LLM Fine-Tuning을 웹 서비스로 연결한 세 가지 프로젝트**

[![호흡기 건강 예보 (Machine Learning)](https://img.shields.io/badge/%ED%98%B8%ED%9D%A1%EA%B8%B0%20%EA%B1%B4%EA%B0%95%20%EC%98%88%EB%B3%B4%20%28Machine%20Learning%29-167D9A?style=for-the-badge)](./1%EC%B0%A8%20Project%28Flask%2C%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D%29/)
[![PreDect (Computer Vision)](https://img.shields.io/badge/PreDect%20%28Computer%20Vision%29-287C67?style=for-the-badge)](./2%EC%B0%A8%20Project%28Computer%20Vision%29/)
[![Unity/GameDev Tutor (LLM Fine-Tuning)](https://img.shields.io/badge/Unity%2FGameDev%20Tutor%20%28LLM%20Fine--Tuning%29-6750A4?style=for-the-badge)](./3%EC%B0%A8%20Project%28LLM%20Fine-Tuning%29/)

</div>

<br>

## 프로젝트 소개

모델 학습에 그치지 않고 **데이터 준비 → 학습과 평가 → 추론 → API → 사용자 화면**으로 이어지는 과정을 구현했습니다. 각 프로젝트 폴더의 README에서 주요 기능, 설계, 구현 포인트를 확인할 수 있습니다.

### 01. 미세먼지 기반 서울시 호흡기 건강 예보 (2026.03 ~ 2026.04) &nbsp;&nbsp; [![프로젝트 폴더 열기](https://img.shields.io/badge/-%E2%86%97-24292F?style=flat-square&logo=github&logoColor=white)](./1%EC%B0%A8%20Project%28Flask%2C%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D%29/)

서울시 25개 자치구의 감기와 천식 발생률, 환자 수를 당일부터 3일 뒤까지 예측하는 웹 서비스입니다. 대기환경, 인구, 과거 질환 데이터를 활용해 지역별 예측 결과를 지도와 차트로 비교할 수 있습니다.

- 원천 데이터 수집과 정제부터 예측 모델 학습, 데이터베이스 저장, 웹 화면까지 구현했습니다.
- 사용자가 입력값을 바꾸면서 예측 결과의 변화를 확인하는 시뮬레이션 기능을 제공합니다.

**핵심 기술:** XGBoost, LightGBM, Random Forest, Multi-Output Regression, pandas, Flask, Oracle DB, SQLAlchemy

---

### 02. PreDect (2026.05 ~ 2026.05) &nbsp;&nbsp; [![프로젝트 폴더 열기](https://img.shields.io/badge/-%E2%86%97-24292F?style=flat-square&logo=github&logoColor=white)](./2%EC%B0%A8%20Project%28Computer%20Vision%29/)

**PreDect**는 영상 속 보행자 신호등의 빨간불과 녹색불을 판별하고 사람, 공 등을 탐지하며 탐지 결과를 바탕으로 위험도 지표를 계산하는 Computer Vision 프로젝트입니다. 객체가 표시된 영상과 분석 결과를 웹 화면에서 확인할 수 있도록 API로 연결했습니다.

- 자동으로 생성한 라벨 후보를 사람이 검수하고, 정리한 데이터로 객체 탐지 모델을 학습하고 검증했습니다.
- 탐지 영상을 스트리밍으로 제공하고, 최신 탐지 목록과 위험도 지표를 별도 API로 전달합니다.

**핵심 기술:** YOLO11n Fine-Tuning, Roboflow, OpenCV, OpenVINO, Flask-RESTX

---

### 03. Unity/GameDev LLM Tutor (2026.05 ~ 2026.05) &nbsp;&nbsp; [![프로젝트 폴더 열기](https://img.shields.io/badge/-%E2%86%97-24292F?style=flat-square&logo=github&logoColor=white)](./3%EC%B0%A8%20Project%28LLM%20Fine-Tuning%29/)

Unity 사용법, 게임개발 개념, 게임수학 질문에 한국어로 답하는 LLM Tutor입니다. **Llama 3.2 3B**에 KoAlpaca 기반 instruction tuning과 Unity/GameDev 도메인 fine-tuning을 적용하고, 모델의 답변을 웹 화면으로 전달하는 흐름을 구현했습니다.

- Unity/GameDev 전문 데이터와 일반 대화 데이터를 합쳐 총 7,290개의 한국어 instruction dataset을 구성했습니다.
- 웹 API와 모델의 응답을 연결하고 프롬프트 구성과 응답 후처리를 적용했습니다.

**핵심 기술:** Llama 3.2 3B, QLoRA, SFT, Instruction Tuning, Domain Fine-Tuning, AWQ, Flask-RESTX

KoAlpaca instruction tuning과 Unity/GameDev 도메인 fine-tuning을 모두 QLoRA 기반 SFT로 진행했습니다. 학습 후 LoRA adapter를 병합하고 AWQ 4-bit 양자화로 추론용 모델을 경량화했습니다.

---

## 구현 범위

- **예측 서비스:** 데이터 수집과 정제, 다중 출력 회귀, Oracle 저장, 지도 및 차트 시각화, 입력값 시뮬레이션
- **영상 인식:** 자동 라벨 후보 생성과 사람 검수, YOLO11n fine-tuning과 검증, OpenVINO 변환, MJPEG, JSON API
- **LLM 서비스:** instruction dataset 구성, QLoRA 기반 SFT, instruction tuning과 도메인 fine-tuning, AWQ 양자화, 프롬프트와 응답 후처리

## 저장소 구조

```text
AI_Projects/
├─ 1차 Project(Flask,머신러닝)/
│  ├─ DB/                         # 원천 데이터 수집, DB 구성
│  ├─ ML/                         # 전처리, 모델 학습, SQL
│  └─ flask/                      # 웹 서비스와 공통 화면
├─ 2차 Project(Computer Vision)/
│  ├─ notebooks/                  # Labeler, 최종 모델 학습 및 변환
│  └─ __init__.py                 # PreDect 영상과 위험도 API
├─ 3차 Project(LLM Fine-Tuning)/
│  ├─ unity_game_dev_tutor_dataset/ # 한국어 학습 데이터
│  └─ README.md                   # 챗봇 기능과 데이터 구성 설명
└─ 1. 프로젝트 수행 결과서.pptx
```

1차 프로젝트의 Flask 앱에는 PreDect와 LLM 튜터의 웹 화면도 포함되어 있습니다. 각 추론 API는 별도 프로세스로 동작합니다.

## 관련 문서

- [프로젝트 수행 결과서](./1.%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%88%98%ED%96%89%20%EA%B2%B0%EA%B3%BC%EC%84%9C.pptx)
- 모델 성능은 저장된 검증 로그 기준이며, 예측값과 위험도는 프로젝트에서 구현한 실험 지표입니다.
