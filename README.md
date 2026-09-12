# Say It Simple

一套協助非英語母語軟體工程師使用 Technical English 與 AI 協作的 Language Assistance System；中文作為理解上的輔助層。

## 1. Project Overview

這個 project 的目標不是「學好英文之後再使用 AI」，而是建立一套 **Language Assistance System**，讓非英語母語的 software engineer 可以把 English 當作 AI 與 software engineering artifact 的主要 working language，同時保留中文作為 comprehension layer。

核心方向：

> **English = working language**  
> **Chinese = comprehension fallback**

這套 system 應該降低中英文切換帶來的 friction，同時逐步提升使用者直接使用 Technical English 與 AI、GitHub、CLI、Markdown 文件互動的能力。

最終理想狀態：

```text
現在：

想法
  ↓
中文
  ↓
/en
  ↓
Technical English
  ↓
AI


未來：

想法
  ↓
Technical English
  ↓
AI

/en 與 /zh 只在需要時使用
```

這不是 translation project，也不是 traditional English course。

它是一個會隨著使用者能力提升而逐漸降低存在感的 **Language Assistance System**。

---

# 2. Goals

## 2.1 Primary Goal

讓非英語母語者能夠順暢地以 English 與 AI 進行 software engineering 工作。

包含：

- 使用 English 向 AI 輸入 instruction
- 使用 English 與 CLI agent 互動
- 撰寫與維護 English Markdown
- 閱讀 AI 產生的 English output
- 閱讀 GitHub 上的 English documentation
- 閱讀與理解 `CLAUDE.md`
- 閱讀與理解 `AGENTS.md`
- 閱讀與理解 `SKILL.md`
- 閱讀與理解 `spec.md`
- 閱讀與理解 `architecture.md`
- 閱讀 GitHub Issue / PR / README
- 在需要時快速取得中文 explanation

---

## 2.2 Non-goals

這個 project **不是**：

- English grammar course
- TOEIC / TOEFL preparation
- vocabulary memorization system
- automatic full-document translation system
- bilingual documentation generator
- ASD-STE100 compliance checker

也不追求：

```text
Native English
Perfect grammar
Complex vocabulary
Beautiful prose
```

我們真正追求：

```text
Clear intent
Clear constraints
Clear technical meaning
Low communication friction
```

---

# 3. Core Design Principle

整套 system 最重要的原則：

> **Simplify the language, not the technical concepts.**

Software engineering 的 canonical terminology 應該保留，例如：

```text
context cancellation
race condition
rollback
middleware
dependency injection
eventual consistency
idempotency
goroutine
request lifecycle
serialization
graceful shutdown
```

不要為了讓 English 變簡單，而破壞 technical meaning。

例如：

```text
initialize
instantiate
invoke
dispatch
rollback
```

不能無條件全部改成：

```text
start
create
call
send
undo
```

因為 software engineering context 中可能代表不同 concepts。

---

## 專案狀態

嘗試多種 English output style
