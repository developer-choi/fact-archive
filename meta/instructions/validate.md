# 양식 검사 가이드

`knowledge/` 하위 문서들이 정해진 양식을 잘 준수하고 있는지 AI가 검사하는 가이드입니다.
전체 문서의 일관성을 유지하기 위해 사용합니다.

---

## 참고 자료
- [문서 구조 규칙](../rules/document-structure.md)
- [파일 위치 선정 규칙](../rules/file-placement.md)
- [내용 작성 규칙](../rules/content-format.md)
- [표준 양식](../template.md)
- [공식 태그](../tags.md)
- [검색 가이드](../search-guide.md)

---

## AI 행동 가이드

### 검사 항목

다음 규칙들을 기준으로 문서를 검사합니다:

1. **문서 구조**: [document-structure.md](../rules/document-structure.md)
   - Questions와 Answers 순서 일치 여부
   - 계층 구조 적절성
   - TODO 질문 형식 준수

2. **파일 위치**: [file-placement.md](../rules/file-placement.md)
   - 폴더 위치 적절성
   - 파일명 규칙 준수
   - 검색 최적화 (Tag/Filename/Directory)

3. **내용 형식**: [content-format.md](../rules/content-format.md)
   - Frontmatter (tags) 형식
   - Keywords, Official Answer, Reference 형식
   - 문장 단위 줄바꿈 적용 여부

4. **표준 양식**: [template.md](../template.md)
   - 전체 구조 일치 여부

### 검사 결과 보고

검사 완료 후 다음 형식으로 보고합니다:

```markdown
## 검사 결과

### ✅ 준수하는 항목
- ...

### ❌ 위반하는 항목
- 파일명: 위반 내용 (참고: 규칙 링크)

### 💡 개선 제안
- ...
```