# 프로젝트 기여 가이드

이 문서는 fact-archive 프로젝트에 문서를 추가하거나 수정할 때 따라야 할 규칙을 정의합니다.

동시에, meta/ 폴더 안에 들어있는 모든 문서의 최상위 문서입니다.

---

## 프로젝트 구조 상세

```
fact-archive/
├─ knowledge/                        # 지식 보관소 (객관적 사실만)
│
├─ meta/                             # 프로젝트 관리 가이드
│  ├─ agent.md                       # AI 전역 규칙
│  ├─ instructions/                  # 작업별 가이드
│  │  ├─ add-note.md                 # 필기 추가
│  │  ├─ convert.md                  # 외부 문서 변환
│  │  ├─ scaffold.md                 # 질문 스캐폴딩
│  │  ├─ organize.md                 # 문서 정리
│  │  └─ validate.md                 # 양식 검사
│  ├─ rules/                         # 공통 규칙 (재사용)
│  │  ├─ document-structure.md       # 문서 구조 규칙
│  │  ├─ file-placement.md           # 파일 위치 선정 규칙
│  │  └─ content-format.md           # 내용 작성 규칙
│  ├─ template.md                    # 문서 표준 양식
│  ├─ tags.md                        # 공식 태그 목록
│  ├─ folder-blueprint.md            # 폴더 구조 계획
│  └─ search-guide.md                # 3-Way Search Protocol
│
├─ playbook/                         # 활용 가이드
│  └─ review.md                      # 기술 면접 모드 복습
│
├─ instruction-map.md                # 문서 라우팅 맵 (사용자 요청 → 가이드 매핑)
├─ CONTRIBUTING.md                   # 프로젝트 관리 가이드 최상위 문서
└─ README.md                         # 프로젝트 소개
```

---

## 핵심 원칙

### 1. Fact-First (사실 우선)

**이 저장소는 객관적인 사실(Fact)만을 기록합니다.**

- ✅ 공식 문서 원문, 검증 가능한 기술 사양, 표준화된 개념
- ❌ 개인적 의견, 추측, 회사 특정 정보, 출처 불명확한 내용

개인적 해석이나 보충 설명은 `> User Annotation` 또는 `> AI Annotation`으로 명확히 구분합니다.

### 2. 출처 명시 필수

Official Answer는 반드시 Reference에 출처를 명시해야 합니다.

### 3. 라우팅은 instruction-map.md에만

**핵심 철학:**
- **meta/instructions/ 하위 문서**: "이 작업이 무엇인지" 설명 (What)
- **instruction-map.md**: "이 작업을 언제, 어떻게 하는지" 설명 (When, How)

각 가이드 문서는 **순수하게 그 작업 자체의 내용**만 담아야 합니다.
사용자가 "언제 이걸 써야 하는지", "어떤 키워드로 찾는지"는 `instruction-map.md`에서 관리합니다.

이렇게 분리하면:
- 가이드 문서는 내용에만 집중 (변경 빈도 낮음)
- instruction-map.md만 보면 모든 사용법 파악 (사용자 진입점 단일화)
- 새 문서 추가 시 instruction-map.md만 업데이트

### 4. 공통 규칙 재사용

중복을 제거하고 일관성을 유지하기 위해 공통 규칙을 `meta/rules/`에 분리했습니다.

- **document-structure.md**: Questions-Answers 순서, 계층 구조, TODO 처리
- **file-placement.md**: 폴더 선택, 파일명 작성, 검색 최적화
- **content-format.md**: Tags, Keywords, Official Answer, Reference 형식

모든 가이드 문서는 이 규칙들을 참조합니다.

### 5. 가이드와 체크리스트 통합

가이드와 체크리스트를 분리하면 내용이 중복되고 동기화 문제가 발생합니다.
**가이드 안에 체크리스트를 대괄호 `[ ]`로 통합하세요.**

**✅ 올바른 예:**
```markdown
### Step 1. 파일 위치 선정

[파일 위치 선정 규칙](../rules/file-placement.md)을 따라 적절한 폴더와 파일명을 결정합니다.

#### 체크리스트
- [ ] 폴더 선택 (파일 위치 선정 규칙 참조)
- [ ] 파일명 결정
```

---

## 문서 작성/수정 시

문서를 추가하거나 수정할 때는 다음을 반드시 따르세요:

1. **공통 규칙 준수**: [meta/rules/](meta/rules/) 하위 규칙 파일 참조
2. **표준 양식 사용**: [meta/template.md](meta/template.md) 참조
3. **instruction-map.md 업데이트**: 새로운 가이드 추가 시 라우팅 맵에 등록
