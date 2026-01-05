# Search & Retrieval Strategy

AI가 질문에 답하거나 문서를 찾을 때, **빠트리는 내용 없이 검색(Comprehensive Search)**하기 위해 지키는 규칙입니다.

---

## 3-Way Search Protocol

"~관련 내용 찾아줘"라고 하면, 아래 3가지 방법을 **동시에 또는 순서대로 다 써서** 나온 결과를 **모두 합쳐야(Union)** 합니다.

### 1. Tag Search (태그 기반)
문서 맨 위 `tags`를 검색합니다. 문서의 **의도**를 파악하기 가장 좋습니다.
- **Pattern**: `tags:.*[키워드]` (Regex 활용)
- **Example**: "React 관련 문서" → `tags`에 `react`가 있는 파일 검색

### 2. Filename Search (파일명 기반)
가장 직관적인 방법입니다.
- **Pattern**: `**/*[키워드]*.md`
- **Example**: `react-query.md`, `react-hooks.md`

### 3. Directory Search (폴더 기반)
관련된 주제의 폴더가 통째로 있는지 확인합니다.
- **Pattern**: `**/*[키워드]/**/*.md` (해당 키워드 폴더 아래 모든 md 파일)
- **Example**: `knowledge/react/` 폴더가 있으면, 그 안의 모든 `.md` 파일을 포함

---

## 검색 결과 처리 (Action)

위 3가지 방법으로 찾은 파일 경로 목록(중복 제거)을 가지고 이렇게 행동합니다:

1. **목록 요청 시**: "다음 파일들에서 관련 내용을 찾았습니다:" 라고 하면서 경로 목록을 보여줍니다.
2. **내용/질문 추출 시**:
   - 찾은 파일들을 읽습니다.
   - `# Questions` 섹션이나 `# [Title]`을 확인해서 사용자에게 답해줍니다.
   - **주의**: 파일이 너무 많으면(5개 이상), 먼저 목록을 보여주고 어떤 파일을 읽을지 물어봅니다.

---

## Execution Example (Scenario)

**User**: "리액트(React) 관련 질문 리스트 뽑아줘"

**AI Action Plan**:

1.  **Tag Search**: tags 필드에서 "react" 패턴 검색 (`tags:.*react`)
    *   Found: `knowledge/ui-ux/performance.md` (tags에 react 포함됨)
2.  **Filename Search**: 파일명에 "react" 포함된 .md 파일 검색 (`**/*react*.md`)
    *   Found: `knowledge/ui-ux/react-hooks.md`
3.  **Directory Search**: react 폴더 내 모든 .md 파일 검색 (`**/react/**/*.md`)
    *   Found: `knowledge/react/core.md`, `knowledge/react/rendering.md`

**Result Union**:
- `knowledge/ui-ux/performance.md`
- `knowledge/ui-ux/react-hooks.md`
- `knowledge/react/core.md`
- `knowledge/react/rendering.md`

**Final Response**:
"React와 관련된 총 4개의 문서를 찾았습니다. (리스트 출력...) 내용을 읽어올까요?"

---

## 요약
> **검색 범위 = (Tag 매칭) ∪ (파일명 매칭) ∪ (폴더 내 파일)**
