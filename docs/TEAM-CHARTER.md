# 팀 헌장 · 3팀

> - **한눈에**: 3팀 다섯 명의 역할, 목표, 범위, 결과물에 영향을 준 협업 규칙을 적은 문서입니다. 11/5 주제 승인과 함께 확정했습니다.
> - 팀원마다 워크플로우 파일을 하나씩 맡았고, 파일끼리 주고받는 형식(공통 계약, `00-DESIGN.md`·`contracts/examples/`)을 먼저 맞춘 뒤 합쳤습니다.
> - 11/6에 기능을 동결했고, VM 배포는 팀장만 기본 브랜치에서 했습니다.

## 1. 팀

| 이름 | 역할 (주 담당) | 함께 보는 역할 | 맡는 파일 |
| --- | --- | --- | --- |
| 문태웅 | 팀장 (통합) + 시험 · 품질 | 연동 (Jira · Slack) · 데이터 검수 · 화면 QA | `team3-ticket.json` · `team3-alert.json`, `infra/`, `packs/`, `tools/packs.py`, `cases/common.json`(확인), `runs/`, `docs/EXECUTION-RESULT.md` / 병합과 VM 배포 |
| 손영민 | 부팀장 · RAG | 지식 문서 | `team3-index.json` · `team3-search.json`, `packs/*/knowledge/` 검수 |
| 한다영 | 오케스트레이션 | 화면 QA | `team3-support.json` |
| 오병훈 | 연동 · 안정성 + 뒷단 | 보안 | `team3-handoff.json` · `team3-errors.json`, `api/` |
| 차해든 | 화면 | 실행 결과서 5절 (화면) | `web/`, `docs/qa/screen-qa.md` 반영 칸 |

## 2. 목표 (한 문장)

주제 (11/5 강사 승인, [`TOPIC.md`](TOPIC.md)): **가상 창고형 약국의 근무 직원을 위한 업무 지원 자동화**

"회수 · 마감 · 어르신 약 질문 · 내 접수 건 네 유형의 문의에 약국 문서 근거와 함께 답하고, 돈 · 약 판단 · 긴급 건은 반드시 약사 · 약국장에게 넘긴다."

## 3. 범위

| 처리할 문의 유형 | 처리 방식 | 근거 문서 |
| --- | --- | --- |
| 회수 공지가 떴어요 | 근거 + 이관 (긴급) | `recall-first-response`, `recall-customer-guide` |
| 혼자 하는 첫 마감 | 자동 답변 (차액 · 온도 이탈은 이관) | `closing-checklist`, `closing-cash-mismatch` |
| 어르신 약 질문 | 자동 답변 + AI 고지 (판단 질문 · 위험 신호는 이관) | `senior-*` 3개 |
| 내 접수 건 확인 | 접수 조회 | `request-records-guide` |

하지 않을 것 (범위 밖): 진단, 약 추천, 용량 정하기, 실제 문자·메일 발송, 실제 약국·손님 데이터 사용, 청구 전송(월간 업무), 사진 읽기.

## 4. 규칙

- 공통 계약(요청 · 응답 칸, `route` 값, 하위 웹훅 주고받는 칸, API 모양)을 바꿔야 하면 `00-DESIGN.md` · `contracts/examples/`부터 고칩니다.
- 한 사람이 한 파일을 맡습니다.
- 키 · 토큰은 n8n Credential과 `.env`에만 둡니다. 커밋 전에 `tscan staged`로 검사합니다.
- 먼저 가짜 구현으로 만들고, 실제 구현이 준비되면 설정값을 바꿔 끼웁니다. 본체는 `SEARCH`·`HANDOFF`, 화면은 `NEXT_PUBLIC_API_MODE` 값으로 바꿉니다.
- 11/6에 기능을 동결합니다. 그 뒤로는 시험, 고치기, 문서, 발표 준비만 합니다.
- VM에는 팀장만 배포합니다 (기본 브랜치에서 배포하고, 배포 뒤 공통 시나리오를 돌립니다).

## 5. 저장소 · 환경

| 항목 | 값 |
| --- | --- |
| 개발 저장소 | GitHub `twlaude/aio-p4-3rd-team-pharm` (비공개) |
| 웹훅 경로 | `team3-support` (하위 `team3-index` · `team3-search` · `team3-handoff`) |
| 팀 VM | 팀장이 관리 (주소 · 비밀번호는 저장소에 쓰지 않음) |
