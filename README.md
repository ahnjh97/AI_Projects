<div align="center">

# AI Projects

**데이터 예측, 컴퓨터비전, LLM을 웹 서비스로 연결한 세 가지 프로젝트**

Python, Flask, Machine Learning, Computer Vision, LLM

[![Respiratory Forecast](https://img.shields.io/badge/01-Respiratory_Forecast-167D9A?style=for-the-badge)](./1%EC%B0%A8%20Project%28Flask%2C%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D%29/)
[![PreDect](https://img.shields.io/badge/02-PreDect-287C67?style=for-the-badge)](./2%EC%B0%A8%20Project%28Computer%20Vision%29/)
[![Unity GameDev Tutor](https://img.shields.io/badge/03-Unity_GameDev_Tutor-6750A4?style=for-the-badge)](./3%EC%B0%A8%20Project%28LLM%20Fine-Tuning%29/)

</div>

<br>

## 프로젝트 소개

모델 학습에 그치지 않고 **데이터 준비 → 학습과 평가 → 추론 → API → 사용자 화면**으로 이어지는 과정을 구현했습니다. 각 프로젝트 폴더의 README에서 주요 기능, 설계, 구현 포인트를 확인할 수 있습니다.

### 호흡기 건강 예보

서울시 25개 자치구의 감기와 천식 발생률과 환자 수를 D0~D+3으로 예측하고 지도와 차트로 비교하는 웹 서비스

**핵심 기술:** Flask, Oracle DB, XGBoost, scikit-learn

[프로젝트 보기 →](./1%EC%B0%A8%20Project%28Flask%2C%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D%29/)

### PreDect

영상 속 보행 신호, 사람, 공 등을 탐지하고 탐지 영상과 위험도 지표를 API로 제공하는 컴퓨터비전 프로젝트

**핵심 기술:** YOLO11n, OpenCV, OpenVINO, Flask-RESTX

[프로젝트 보기 →](./2%EC%B0%A8%20Project%28Computer%20Vision%29/)

### Unity/GameDev 튜터

Unity, 게임개발, 게임수학 질문에 한국어로 답하는 도메인 특화 LLM 챗봇

**핵심 기술:** Instruction Dataset, Flask-RESTX, MCP, vLLM

[프로젝트 보기 →](./3%EC%B0%A8%20Project%28LLM%20Fine-Tuning%29/)


## 구현 범위

- **예측 서비스:** 데이터 수집과 정제, 다중 출력 회귀, Oracle 저장, 지도 및 차트 시각화, 입력값 시뮬레이션
- **영상 인식:** 자동 라벨 후보 생성과 사람 검수, YOLO11n 학습과 검증, OpenVINO 변환, MJPEG, JSON API
- **LLM 서비스:** 한국어 instruction 데이터 구성, 도메인 튜닝, MCP 도구 연결, 프롬프트와 응답 후처리

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
│  └─ restx-mcp-server/            # REST API, MCP, 추론 서버 연결
└─ 1. 프로젝트 수행 결과서.pptx
```

1차 프로젝트의 Flask 앱에는 PreDect와 LLM 튜터의 웹 화면도 포함되어 있습니다. 각 추론 API는 별도 프로세스로 동작합니다.

## 관련 문서

- [프로젝트 수행 결과서](./1.%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%88%98%ED%96%89%20%EA%B2%B0%EA%B3%BC%EC%84%9C.pptx)
- 모델 성능은 저장된 검증 로그 기준이며, 예측값과 위험도는 프로젝트에서 구현한 실험 지표입니다.

## 개발자

[안정현, ahnjh97](https://github.com/ahnjh97)
