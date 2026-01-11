# 개요

AI 에이전트가 적절한 가이드 문서를 찾아 로드하기 위한 라우팅 맵입니다.

사용자가 작업을 요청하면 AI는 이 맵을 참조하여 필요한 문서를 로드합니다.

## 사용법 & AI 실행 규칙

- 사용자: "React Hooks 공부한 내용 정리해줘"
- AI: "meta/instructions/add-note.md를 로드하고 작업을 진행하겠습니다"

## 검색 우선순위

1. **파일명/키워드 매칭**: 아래 목록에서 파일명/키워드로 검색 후 매칭되는 것이 있다면 사용자 승인 없이 로드합니다.
   - 예: "변환" → `meta/instructions/convert.md` 검색
   - 예: "복습" → `playbook/review.md` 검색

2. **설명 기반 매칭**: 위 방법 실패 시 각 항목의 설명(불렛 포인트)에서 의미 매칭 후 사용자 승인 요청을 거칩니다.
   - 예: "필기하고 싶어" → 설명 검색 → "meta/instructions/add-note.md를 로드할까요?"

---

## 1. 지식 추가 (Add Knowledge)

### 1-1. 필기 추가

```bash
meta/instructions/add-note.md
```
- 공부하면서 새로운 지식 기록
- 기존 질문에 답변 추가
- 새로운 질문과 답변 동시 추가
- **키워드**: 필기, 정리, 기록, 학습, 공부

### 1-2. 외부 문서 변환

```bash
meta/instructions/convert.md
```
- 구글 문서 → fact-archive 형식 변환
- PDF/MD 파일 변환
- **키워드**: 변환, convert, 구글 문서, PDF

---

## 2. 지식 복습 (Review Knowledge)

### 2-1. 기술 면접 모드

```bash
playbook/review.md
```
- 시니어 면접관 페르소나로 복습
- 질문 → 답변 → 검증 → 피드백
- 학습 리포트 제공
- **키워드**: 복습, review, 면접, 테스트

---

## 3. 지식 관리 (Manage Knowledge)

### 3-1. 질문 스캐폴딩

```bash
meta/instructions/scaffold.md
```
- TODO 질문 → knowledge 등록
- 답변 없이 뼈대만 생성
- **키워드**: scaffold, TODO, 질문 등록

### 3-2. 문서 정리

```bash
meta/instructions/organize.md
```
- 문서 분할 및 구조 개선
- Questions-Answers 순서 조정
- **키워드**: 정리, organize, 분할, 구조

### 3-3. 양식 검사

```bash
meta/instructions/validate.md
```
- 표준 양식 준수 검증
- 문서 품질 관리
- **키워드**: 검사, validate, 검증, 양식

