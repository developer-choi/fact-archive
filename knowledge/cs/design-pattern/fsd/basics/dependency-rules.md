---
tags: [fsd, dependency, rules, unidirectional]
---

# Questions
- [Why is the unidirectional dependency rule important, and what happens if we violate it?](#why-is-the-unidirectional-dependency-rule-important-and-what-happens-if-we-violate-it)
  - [Why is it forbidden for a slice to reference another slice within the same layer?](#why-is-it-forbidden-for-a-slice-to-reference-another-slice-within-the-same-layer)
- [[TODO] What is the role of the 'Public API' (index.ts) in an FSD slice?](#todo-what-is-the-role-of-the-public-api-indexts-in-an-fsd-slice)

---

# Answers

## Why is the unidirectional dependency rule important, and what happens if we violate it?
### Keywords
Stability, Refactoring, Isolation

### Official Answer
A module on one layer cannot use other modules on the same layer, or the layers above.

The key difference of Feature-Sliced Design from an unregulated code structure is that pages cannot reference each other.

This allows you to make isolated modifications without unforeseen consequences to the rest of the app.

> AI Annotation:
> - ❌ **Bad (Layer Violation)**: `entities/user` 슬라이스에서 상위 계층인 `features/auth`의 함수를 가져다 쓰는 경우. (하위 계층이 상위 계층을 알게 되면 순환 참조와 의존성 지옥이 시작됨)
> - ✅ **Good (Layer Flow)**: `pages/profile` -> `features/update-password` -> `entities/user` 순서로 호출. 의존성이 위에서 아래로만 흐르므로 각 계층을 독립적으로 테스트하고 교체하기 쉬움.

### Reference
https://feature-sliced.design/docs/get-started/overview

---

## Why is it forbidden for a slice to reference another slice within the same layer?

### Keywords
Cohesion, Coupling, Circular Dependency

### Official Answer
Slices cannot use other slices on the same layer, and that helps with **high cohesion and low coupling.**

> AI Annotation:
> - **순환 참조 방지 (Preventing Circular Dependencies)**: A가 B를, B가 A를 참조하면서 생기는 무한 루프와 꼬인 의존성을 원천 차단합니다.
> - **낮은 결합도 (Low Coupling)**: 각 슬라이스를 독립된 조각으로 유지하여, 하나를 수정하거나 삭제할 때 다른 슬라이스가 깨지지 않도록 보호합니다.
> - **예측 가능한 구조 (Predictable Structure)**: 코드가 어디에서 오고 어디로 가는지 항상 상하 관계로만 흐르게 하여 흐름을 파악하기 쉽게 만듭니다.

### Reference
- [Feature-Sliced Design Official Documentation](https://feature-sliced.design/docs/get-started/overview)

---

## [TODO] What is the role of the 'Public API' (index.ts) in an FSD slice?
### Keywords

### Official Answer

### Reference
