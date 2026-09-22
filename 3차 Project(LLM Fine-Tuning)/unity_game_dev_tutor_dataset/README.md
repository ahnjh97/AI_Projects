# Unity Game Dev Tutor Dataset (Korean)

Unity/게임개발/게임수학 튜터 챗봇용 instruction 데이터셋입니다.

## Final Training File

- `unity_game_dev_tutor_ko.jsonl`: 최종 학습용 JSONL 파일
- `unity_game_dev_tutor_ko.json`: 같은 데이터의 JSON 배열 버전

## Mix Ratio

- 전문 지식: 6290개 (약 86.3%)
- 일반 대화/지시: 1000개 (약 13.7%)
- 총합: 7290개

현재 JSONL·JSON 파일의 실제 레코드 수를 기준으로 집계했습니다. `data_type`이 `expert`인 항목 6290개와 `general`인 항목 1000개로 구성됩니다.

일반 대화 데이터는 `from datasets import load_dataset` 후 `load_dataset("beomi/KoAlpaca-v1.1a", split="train")`로 불러와 `instruction`, `input`, `output` 형식을 검증한 뒤 샘플링했습니다.

## Augmentation

정확한 튜터 응답을 위해 오브젝트 풀링, FixedUpdate/Update, 점프 속도 공식, Rigidbody/CharacterController, Collider/Trigger 등 핵심 개념에 한국어 질문 변형을 추가했습니다. 답변은 대부분 2~3문장으로 짧고 정확하게 구성했으며, 코드 요청이 아닌 샘플의 코드블록과 반복/메타 문구는 제거했습니다.
