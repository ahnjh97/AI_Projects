<div align="center">

# Unity / GameDev 한국어 튜터 [프로젝트 링크](https://github.com/ahnjh97/AI_Projects/tree/main/3%EC%B0%A8%20Project%28LLM%20Fine-Tuning%29)

**Unity, 게임개발, 게임수학 질문을 위한 도메인 특화 LLM 챗봇**

[주요 기능](#주요-기능) &nbsp;&nbsp; [데이터셋](#데이터셋) &nbsp;&nbsp; [아키텍처](#아키텍처) &nbsp;&nbsp; [전체 프로젝트](../README.md)

</div>

<br>

## 프로젝트 소개

Unity 학습자가 한국어로 개념과 구현 방법을 질문할 수 있는 튜터형 LLM 서비스입니다. 일반 질의응답 데이터와 게임개발 전문 데이터를 구성하고, 모델의 답변을 웹 화면으로 전달하는 Flask REST API를 구현했습니다.

답변이 불필요하게 길어지거나 학습용 구분자를 다시 출력하는 문제를 줄이기 위해 **도메인 프롬프트, stop sequence, 중복 제거와 길이 제한**을 함께 적용했습니다.

## 주요 기능

- **한국어 튜터**: Unity, C#, 게임개발, 게임수학 질문과 답변
- **학습 데이터**: 전문 지식과 KoAlpaca 일반 지시 및 대화 데이터의 혼합
- **REST API**: 질문 입력 검증, 응답 포맷, 상태 확인
- **응답 제어**: 학습 구분자 제거, 중복 문장 제거, 코드 요청 여부에 따른 출력 제어
- **연결 처리**: 추론 서버 주소, 모델, 키 설정, 타임아웃, 연결 오류 메시지

## 기술 스택

- **API**: Python, Flask, Flask-RESTX, Flask-CORS (입력 검증과 JSON 응답)
- **Dataset**: JSONL, KoAlpaca instruction data (한국어 지시문과 답변 구성)

이 저장소에는 데이터셋과 서비스 연결 코드가 포함되어 있으며, 파인튜닝 학습 스크립트와 최종 LLM 가중치는 포함되어 있지 않습니다.

## 데이터셋

- Unity, 게임개발, 게임수학 전문 지식: 6,290개 (약 86.3%)
- 일반 대화 및 지시: 1,000개 (약 13.7%)
- **합계**: **7,290**개 (**100%**)

저장소의 JSONL, JSON 파일을 직접 집계한 수치입니다. 전문 지식과 일반 데이터는 각 레코드의 `data_type`으로 구분합니다.

- 학습 형식: `instruction`, `input`, `output`
- 학습 파일: `unity_game_dev_tutor_dataset/unity_game_dev_tutor_ko.jsonl`
- JSON 배열 버전과 [데이터 설명](./unity_game_dev_tutor_dataset/README.md), [출처 문서](./unity_game_dev_tutor_dataset/SOURCES.md) 포함
- 오브젝트 풀링, Update/FixedUpdate, Rigidbody/CharacterController, Collider/Trigger 등 핵심 개념의 한국어 질문 변형 구성
- 비코드 질문의 코드블록과 반복, 메타 문구를 정리하고 간결한 답변 형식으로 구성

## 아키텍처

```mermaid
flowchart LR
    U[사용자 질문] --> F[Flask REST API]
    F --> P[도메인 프롬프트]
    P --> V[모델 추론]
    V --> R[응답 후처리]
    R --> F
```

## 구현 포인트

### 출력 형식의 일관성

- 한국어 도메인 프롬프트로 답변 범위와 용어 사용 지시
- stop sequence와 후처리로 `### 입력:`, `### 응답:` 등 구분자의 재출력 정리
- 동일 문장을 제거하고 일반 질문은 최대 3개, 코드 요청은 최대 5개 문장 단위로 후처리
- 코드, C#, 구현, 스크립트를 명시한 요청에서만 코드블록 허용

이 설정은 출력 제어를 위한 구현이며 답변 정확도나 코드의 실행 가능성을 보장하는 평가 결과는 아닙니다.

## 주요 API

- HTTP `GET /health`: Flask API 상태 확인
- HTTP `POST /chat`: `question`을 받아 `status`, `answer`, `via` 반환

[← 전체 프로젝트](../README.md)
