---
tags: [fsd, architecture, layers, responsibility]
---

# Questions
- [Could you explain the seven layers of FSD and the specific responsibility of each layer?](#could-you-explain-the-seven-layers-of-fsd-and-the-specific-responsibility-of-each-layer)
  - [[TODO] What is the key difference between 'Entities' and 'Features' in FSD?](#todo-what-is-the-key-difference-between-entities-and-features-in-fsd)
  - [[TODO] What is the key difference between 'App' and 'Pages' in FSD?](#todo-what-is-the-key-difference-between-app-and-pages-in-fsd)

---

# Answers

## Could you explain the seven layers of FSD and the specific responsibility of each layer?

### Keywords
FSD, Layers, Responsibility

### Official Answer
#### App
Everything that makes the app run — routing, entrypoints, global styles, providers.

#### Pages
Full pages or large parts of a page in nested routing.

#### Widgets
Large self-contained chunks of functionality or UI, usually delivering an entire use case.

#### Features
Reused implementations of entire product features, i.e. actions that bring business value to the user.

#### Entities
Business entities that the project works with, like user or product.

#### Shared
Reusable functionality, especially when it's detached from the specifics of the project/business, though not necessarily.

### Reference
- [Feature-Sliced Design Official Documentation](https://feature-sliced.design/docs/get-started/overview)

---

## [TODO] What is the key difference between 'Entities' and 'Features' in FSD?
### Keywords

### Official Answer

### Reference

---

## [TODO] What is the key difference between 'App' and 'Pages' in FSD?
### Keywords

### Official Answer

### Reference
