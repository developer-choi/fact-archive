# 질문 스캐폴딩 가이드 (Scaffold Questions)

복습 중 막혔거나 답변하지 못한 질문(`TODO`)을 영구적인 지식 저장소(`knowledge`)로 옮겨 **다음 학습을 위한 뼈대(Scaffold)**를 만드는 작업입니다.

---

## 참고 자료
- [문서 구조 규칙](../rules/document-structure.md)
- [파일 위치 선정 규칙](../rules/file-placement.md)
- [내용 작성 규칙](../rules/content-format.md)
- [표준 양식](../template.md)
- [문서 정리 가이드](organize.md)

---

## 1. 기본 원칙
1.  **답변 금지**: 이 작업의 목적은 **'질문 등록'**입니다. 답변은 사용자가 공부하며 직접 채우거나 AI 힌트를 붙여넣을 수 있도록 **완전히 비워둡니다.**
2.  **적절한 위치 선정**: 질문의 주제를 분석하여 [파일 위치 선정 규칙](../rules/file-placement.md)에 따라 적절한 파일을 선택하거나 생성합니다.

## 2. 작업 순서

### Step 1. 파일 위치 선정
- [파일 위치 선정 규칙](../rules/file-placement.md)을 참고하여 질문이 들어갈 적절한 파일을 찾거나 생성합니다.

### Step 2. 질문 등록 (Scaffolding)

[문서 구조 규칙 - TODO 질문 처리](../rules/document-structure.md#todo-질문-처리)를 따라 질문을 등록합니다.

파일 내 두 군데에 내용을 추가해야 합니다:

1.  **상단 TOC (Questions)**: 질문을 리스트에 추가하고, 답변 섹션으로 이동하는 앵커 링크를 겁니다.
2.  **본문 (Answers)**: 질문 제목으로 헤더를 생성하고, 내용은 **아무것도 적지 않고 공란으로 둡니다.**

### Step 3. 원본 정리
- 질문을 옮긴 후, `TODO.md`나 요청받은 리스트에서 해당 항목을 삭제하여 중복을 방지합니다.

## 3. 예시

**입력 (TODO.md)**
> - What is Kernel?

**출력 (knowledge/cs/os/linux-kernel.md)**
```markdown
# Questions
- [What is Kernel?](#what-is-kernel)

...

# Answers

...

## What is Kernel?

```