# AI Agent 전역 규칙

이 문서는 Claude Code, Gemini CLI 등 모든 AI 에이전트가 fact-archive 프로젝트에서 작업할 때 따라야 하는 전역 규칙입니다.

---

## 기본 원칙

### Fact-First (사실 우선)

**이 저장소는 객관적인 사실(Fact)만을 기록합니다.**

- ✅ 공식 문서 원문, 검증 가능한 기술 사양, 표준화된 개념
- ❌ 개인적 의견, 추측, 회사 특정 정보, 출처 불명확한 내용

개인적 해석이나 보충 설명은 `> User Annotation` 또는 `> AI Annotation`으로 명확히 구분합니다.

### 출처 명시 필수

모든 Official Answer는 반드시 Reference에 출처를 명시해야 합니다.
출처가 없는 내용은 기록하지 않습니다.

---

## instruction-map.md 사용법

사용자가 작업을 요청하면:

1. [instruction-map.md](../instruction-map.md) 파일을 읽으세요
2. 해당 파일의 검색 규칙에 따라 적절한 문서를 찾으세요
3. 찾은 문서를 로드하고 작업을 진행하세요

**instruction-map.md가 모든 검색 로직과 경로 매핑을 담당합니다.**

---

## 선택적 로딩 원칙 (Critical)

### 필요한 것만 점진적으로 로드

**토큰을 절약하기 위해 현재 작업에 필요한 파일만 선택적으로 로드하세요.**

### ✅ 올바른 예시

```
User: "React Hooks에 대해 공부한 내용 정리해줘"
AI:
1. instruction-map.md 읽음
2. "필기 추가" 작업 → meta/instructions/add-note.md 로드
3. add-note.md에서 참조하는 규칙 파일만 필요시 로드
   - meta/rules/document-structure.md (Questions 작성 시)
   - meta/rules/file-placement.md (파일 위치 결정 시)
   - meta/rules/content-format.md (내용 작성 시)
→ 필요한 것만 단계적으로 로드
```

### ❌ 잘못된 예시

```
User: "React Hooks에 대해 공부한 내용 정리해줘"
AI:
1. instruction-map.md 읽음
2. meta/ 전체 읽음
3. playbook/ 전체 읽음
4. knowledge/ 샘플 파일들 읽음
→ 불필요한 파일까지 모두 로드 (토큰 낭비)
```

---

## 핵심 워크플로우

### 1. 지식 추가 작업

```
1. instruction-map.md에서 add-note.md 또는 convert.md 찾기
2. 해당 가이드 읽기
3. 가이드에서 참조하는 규칙 파일 필요시 로드
4. 작업 진행
```

### 2. 지식 복습 작업

```
1. instruction-map.md에서 playbook/review.md 찾기
2. review.md 읽기
3. 복습 대상 파일 로드 (3-Way Search Protocol 사용)
4. 질문 제시 → 답변 검증 → 피드백
```

### 3. 문서 관리 작업

```
1. instruction-map.md에서 organize.md 또는 scaffold.md 찾기
2. 해당 가이드 읽기
3. 필요한 규칙 파일만 로드
4. 작업 진행
```

---

## 공통 규칙 준수 (모든 작업에서)

모든 작업에서 다음 규칙을 반드시 따라야 합니다:

- **[문서 구조 규칙](rules/document-structure.md)**: Questions-Answers 순서, 계층 구조, TODO 처리
- **[파일 위치 선정 규칙](rules/file-placement.md)**: 폴더 선택, 파일명 작성, 검색 최적화
- **[내용 작성 규칙](rules/content-format.md)**: Tags, Keywords, Official Answer, Reference 형식

---

## 3-Way Search Protocol

문서를 검색할 때는 다음 3가지 방법을 모두 사용하여 누락 없이 찾아야 합니다:

1. **Tag Search**: `tags` 필드에서 키워드 검색
2. **Filename Search**: 파일명에 키워드 포함된 파일 검색
3. **Directory Search**: 관련 폴더 내 모든 파일 검색

자세한 내용은 [검색 가이드](search-guide.md)를 참고하세요.

---

## 문서 작성/수정 시

**문서를 수정하거나 추가할 때는 [CONTRIBUTING.md](../CONTRIBUTING.md)를 반드시 참고하세요.**

- 프로젝트 구조 이해
- 핵심 원칙 준수
- 표준 양식 따르기
