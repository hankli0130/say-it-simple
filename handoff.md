# Language Assistance System — Handoff

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

# 4. Language Model

整套 workflow 採用以下架構：

```text
┌──────────────────────────────────────────────┐
│               Your Thinking                  │
│ Chinese / English / Chinglish                │
└──────────────────────┬───────────────────────┘
                       ↓
            ┌─────────────────────┐
            │  Input Assistance   │
            │                     │
            │ /en                 │
            │ /en-review          │
            │ prompt patterns     │
            └──────────┬──────────┘
                       ↓
┌──────────────────────────────────────────────┐
│            English Working Layer             │
│                                              │
│ CLI                                          │
│ CLAUDE.md                                    │
│ AGENTS.md                                    │
│ SKILL.md                                     │
│ spec.md                                      │
│ architecture.md                              │
│ GitHub Issue / PR                            │
│ AI conversation                              │
└──────────────────────┬───────────────────────┘
                       ↓
            ┌─────────────────────┐
            │ Output Assistance   │
            │                     │
            │ /zh                 │
            │ explain selection   │
            │ glossary support    │
            └──────────┬──────────┘
                       ↓
┌──────────────────────────────────────────────┐
│              Your Understanding              │
└──────────────────────────────────────────────┘
```

---

# 5. ASD-STE100 Strategy

## 5.1 Decision

採用 **ASD-STE100 inspired principles**，但不追求 strict ASD-STE100 compliance。

這套 system 不應宣稱：

```text
ASD-STE100 compliant
```

而應該描述為：

```text
Inspired by ASD-STE100 principles.
Adapted for software engineering and AI communication.
```

---

## 5.2 Why Use STE100 Principles

ASD-STE100 解決的核心問題與本 project 類似：

```text
Technical information
+
Non-native English users
+
Need for precise communication
=
Need for simpler, consistent, less ambiguous language
```

值得借用的 ideas：

- short sentences
- one topic per sentence
- explicit wording
- active voice
- consistent terminology
- reduced ambiguity
- controlled use of synonyms
- clear instruction structure

---

## 5.3 Why Not Use Strict STE100

Software engineering 有大量 domain-specific canonical terminology。

例如：

```text
initialize
hydrate
commit
rollback
dispatch
resolve
serialize
invalidate
reconcile
```

strict simplification 可能破壞 technical precision。

因此我們建立自己的：

> **STE-inspired Software Technical English**

它不是 ASD-STE100 extension，也不是正式 standard。

它是一套適合 AI-assisted software engineering 的 controlled writing guideline。

---

# 6. STE-inspired Software Technical English

第一版只採少量高價值 principles。

## Principle 1 — Use short sentences

Avoid:

```text
Could you perhaps take a closer look at this issue and try to determine
what may potentially be causing it before making any changes?
```

Prefer:

```text
Investigate this issue.

Find the root cause.

Do not modify the code yet.
```

---

## Principle 2 — One idea per sentence

Avoid：

```text
Check the handler and see whether the timeout is related to context
cancellation and fix it if necessary.
```

Prefer：

```text
Check the handler.

Verify whether context cancellation causes the timeout.

Do not modify the code yet.
```

---

## Principle 3 — Prefer explicit actions

Prefer verbs such as：

```text
analyze
check
compare
confirm
explain
find
identify
implement
investigate
review
run
trace
update
validate
verify
```

Avoid vague wording：

```text
take a look
see what happens
do something about
check this out
```

---

## Principle 4 — Prefer active voice

Prefer：

```text
Run the tests.
```

Over：

```text
The tests should be run.
```

---

## Principle 5 — Use consistent terminology

If a component is called：

```text
handler
```

do not randomly switch between：

```text
handler
controller
endpoint component
request processor
```

unless these concepts are actually different.

---

## Principle 6 — Avoid ambiguous references

Avoid：

```text
Check it and see whether this causes that.
```

Prefer：

```text
Check the retry logic.

Verify whether the retry logic delays context cancellation.
```

---

## Principle 7 — Keep canonical engineering terminology

Do not simplify：

```text
race condition
rollback
idempotency
dependency injection
eventual consistency
context cancellation
```

into vague general English.

---

## Principle 8 — Optimize for AI communication

Priority：

```text
clear intent
clear constraints
clear expected output
```

Grammar perfection is secondary.

For example：

```text
Check why timeout happen.
Do not change code.
```

is imperfect English but still usable.

A better version is：

```text
Investigate why the timeout occurs.

Do not modify the code yet.
```

---

# 7. Core Tools

The long-term system may contain：

```text
/en
/zh
/en-review
/learn
Technical English Output Style
Personal Technical English Profile
Engineering Phrasebook
```

但這些不應一次全部實作。

Tooling 必須跟著 rollout phase 漸進增加。

---

# 8. Phase Model

這個 project 採用：

```text
Phase 0 → Phase 1 → Phase 2 → Phase 3 → Phase 4 → Phase 5
```

但這不是 rigid progression。

Phase 代表：

> **Current assistance mode**

而不是：

> English level

使用者可以依照 task complexity 暫時提高或降低 assistance。

---

# 9. Phase 0 — Baseline / Observe

## Goal

找出真正造成 language friction 的地方。

這個階段不改變目前工作方式，也不要求刻意使用 English。

核心問題：

> English 到底在哪些地方妨礙 software engineering workflow？

---

## Observe Input Friction

可能包含：

```text
不知道怎麼開始 sentence
想不到 action verb
不知道 technical term
怕 grammar 錯
中文 sentence 不知道怎麼拆
可以寫 English 但速度太慢
不知道 constraint 怎麼表達
```

---

## Observe Output Friction

可能包含：

```text
unknown vocabulary
long sentence
abstract sentence
technical concept unclear
sentence structure difficult
reading speed too slow
understand words but not main idea
```

---

## Lightweight Tracking

不建立複雜 analytics。

只需要簡單觀察，例如：

```text
/en needed: 6
/zh needed: 4

Hard:
- rollback semantics
- provided that
- how to say "先不要修改"
```

---

## Validation

Phase 0 完成的條件：

能明確列出：

```text
Top 3–5 Input Frictions
Top 3–5 Output Frictions
```

---

## Move to Phase 1 When

當我們已經知道：

> 使用 English workflow 最大的 friction 是什麼。

不要依照時間決定。

---

# 10. Phase 1 — Assisted English

## Goal

讓 English-first workflow 變得舒服。

此階段不要求使用者主動使用 English。

Workflow：

```text
Chinese / Chinglish / English
        ↓
       /en
        ↓
Simple Technical English
        ↓
        AI
```

Output：

```text
AI English output
        ↓
看得懂 → continue
        ↓
看不懂
        ↓
       /zh
```

---

## Tools

Phase 1 只建立：

```text
/en
/zh
Technical English Output Style
```

不要建立：

```text
/en-review
/learn
flashcards
vocabulary database
analytics dashboard
```

---

## `/en`

Purpose：

> Rewrite the user's intent into clear AI-ready Technical English.

不是 literal translation。

Example：

Input：

```text
我覺得 timeout 可能跟 context cancel 有關，
先查原因，不要修改 code。
```

Output：

```text
Investigate the timeout issue.

Check whether context cancellation causes the issue.

Do not modify the code yet.
Identify the root cause first.
```

---

## `/zh`

Purpose：

> Explain difficult English in Traditional Chinese while preserving technical terminology.

不是 line-by-line translation。

Example：

Input：

```text
The retry mechanism can mask transient failures and delay propagation
of the cancellation signal.
```

Expected explanation：

```text
這段主要是在說：

retry mechanism 可能會讓暫時性的 failure 不容易被發現，
也可能讓 cancellation signal 比預期更晚傳遞。

關鍵概念：

- transient failure：短時間發生、之後可能恢復的 failure
- mask：讓問題變得不明顯
- propagation：訊號往其他 component 傳遞
```

---

## Validation

觀察三件事情。

### A. English artifacts 不再造成抗拒

例如願意保留：

```text
CLAUDE.md
AGENTS.md
SKILL.md
spec.md
architecture.md
Issue
PR
```

為 English。

### B. `/en` 不造成額外 workflow burden

理想：

```text
想到東西
→ /en
→ English
→ continue
```

不是：

```text
整理中文
→ 修中文
→ /en
→ 修 English
→ continue
```

### C. `/zh` 可以解除大部分 reading blockage

---

## Move to Phase 2 When

當使用者自然開始覺得：

> 「這句我自己直接打 English 比 `/en` 快。」

例如直接寫：

```text
Do not change the public API.
```

而不是先使用 `/en`。

---

# 11. Phase 2 — Simple English Input

## Goal

讓：

```text
/en = default
```

逐漸變成：

```text
English = default
/en = fallback
```

只要求 **Simple Technical English**。

不追求 native English。

---

## Core Action Vocabulary

第一版大約 30–50 個 reusable verbs。

例如：

```text
analyze
check
compare
confirm
create
describe
explain
find
identify
implement
investigate
keep
remove
replace
review
run
trace
update
validate
verify
```

進階：

```text
benchmark
deprecate
isolate
migrate
refactor
reproduce
rollback
```

---

## Sentence Patterns

比 vocabulary 更重要。

### Investigation

```text
Investigate why ...
Find the root cause of ...
Check whether ...
Verify that ...
Reproduce the issue.
Trace the request flow.
```

### Constraints

```text
Do not ...
Only change ...
Keep ... unchanged.
Avoid ...
Do not introduce ...
```

### Implementation

```text
Implement ...
Add support for ...
Replace ... with ...
Refactor ... to ...
Remove ...
Update ...
```

### Explanation

```text
Explain how ...
Explain why ...
Give me an overview of ...
Walk me through ...
```

### Review

```text
Review the implementation.
Check for ...
Look for potential ...
Compare ... with ...
Verify against ...
```

---

## Add `/en-review`

`/en-review` 同時完成工作與少量 learning。

Example：

Input：

```text
Check why API cannot response after timeout.
```

Output：

```text
Better:

Check why the API does not respond after the timeout.

Key point:

response = noun
respond = verb
```

Teaching 必須保持 minimal。

不能讓每一次 interaction 都變成 English lesson。

---

## Validation

觀察：

```text
English input ratio ↑
/en dependency ↓
```

以及是否可以不靠 `/en` 完成常見操作：

```text
Explain something
Investigate a bug
Ask for implementation
Set constraints
Ask for verification
```

Example：

```text
Explain how this middleware works.

Investigate why the request times out.

Implement support for X.

Do not change the existing API.

Run the tests and verify the behavior.
```

---

## Move to Phase 3 When

當使用者已能用 Simple Technical English 完成大部分日常 AI interaction。

Grammar 不需要 perfect。

Intent 必須 clear。

---

# 12. Phase 3 — English Working Environment

## Goal

從：

> I can speak English with AI.

進入：

> My engineering environment is English-first.

---

## English-first Artifacts

預設使用 English：

```text
CLI conversation
CLAUDE.md
AGENTS.md
SKILL.md
spec.md
architecture.md
README
GitHub Issue
Pull Request
commit message
code comment
```

Chinese 的角色改成：

```text
comprehension language
```

---

## Technical English Output Style

AI output should follow：

```text
Use clear Technical English.

Prefer:
- short sentences
- explicit instructions
- common engineering vocabulary
- consistent terminology

Avoid:
- idioms
- unnecessarily advanced words
- long sentences
- vague references

Keep canonical software engineering terminology.

Simplify the language, not the technical concepts.
```

---

## Validation

拿一個 real engineering task：

```text
GitHub Issue
↓
investigation
↓
implementation
↓
review
↓
test
↓
PR
```

整段流程使用 English-first。

觀察：

```text
How often does English interrupt engineering thinking?
```

理想狀態不是 `/zh = 0`。

而是：

> English 不再頻繁阻斷工作。

另一個測試：

隔天重新閱讀：

```text
spec.md
architecture.md
Issue
PR
```

不靠完整中文 translation，仍可理解主要內容。

---

## Move to Phase 4 When

當主要思考焦點變成：

```text
architecture
bug
code
trade-off
test
behavior
```

而不是：

```text
這句 English 對不對？
這個 grammar 怎麼寫？
```

---

# 13. Phase 4 — Technical English Independence

## Goal

```text
/en = exception
/zh = exception
```

大部分 interaction：

```text
Thinking
   ↓
Simple Technical English
   ↓
AI
```

---

## Important Rule

這不是 English-only mode。

遇到 unfamiliar concept，例如：

```text
distributed consistency
memory ordering
database isolation
OAuth security semantics
```

仍然可以大量使用 `/zh`。

這時 `/zh` 必須分辨：

```text
language problem
```

與：

```text
concept problem
```

例如：

```text
/zh linearizability
```

不應只回答：

```text
linearizability = 線性一致性
```

而應解釋 concept。

---

## Validation

找一份沒讀過的 English technical material：

```text
GitHub Skill
library documentation
RFC
architecture proposal
```

確認是否能：

```text
read original
↓
understand main idea
↓
identify key constraints
↓
ask English follow-up questions
```

不要求 100%。

目標大約：

```text
80% original comprehension
20% assisted comprehension
```

這不是硬性數字，只是 practical reference。

---

## Move to Phase 5 When

當 assistance 主要是處理：

```text
new concepts
advanced terminology
unusual writing
```

而不是 basic communication。

---

# 14. Phase 5 — Continuous Learning

## Goal

利用真實工作資料持續改善 Technical English。

這時才建立：

```text
Personal Technical English Profile
```

---

## Profile Structure

```text
Technical English Profile

├── Core Actions
├── Sentence Patterns
│   ├── Investigation
│   ├── Implementation
│   ├── Review
│   ├── Constraints
│   └── Explanation
├── Engineering Vocabulary
└── Common Mistakes
```

---

## `/learn`

`/learn` 不應該變成 generic English lesson。

它只整理最近實際使用過的內容。

Example：

```text
This week's Technical English

Useful patterns:

1. verify whether ...
2. keep ... unchanged
3. introduce a regression

Common mistake:

response / respond

New engineering terms:

idempotent
backpressure
graceful shutdown
```

一次只挑少量 high-value items，例如：

```text
3–5 items
```

---

## Learning Philosophy

採：

> **Just-in-time learning**

而不是：

> Just-in-case learning

不要先背：

```text
1000 Technical English words
```

應該先工作，再從實際 friction 找出值得學的東西。

---

# 15. Engineering Phrasebook

未來可以自然累積一份 reusable Phrasebook。

Example：

```text
# Investigation

Investigate why ...
Find the root cause of ...
Check whether ...
Verify that ...
Reproduce the issue.
Trace the request flow.

# Constraints

Do not ...
Only change ...
Keep ... unchanged.
Avoid ...
Do not introduce ...

# Implementation

Implement ...
Add support for ...
Replace ... with ...
Refactor ... to ...
Remove ...
Update ...

# Review

Review the implementation.
Look for ...
Check for potential ...
Compare ... with ...
Verify against ...

# Explanation

Explain how ...
Explain why ...
Give me an overview of ...
Walk me through ...
```

Phrasebook 的目的是：

```text
想法
 ↓
pattern
 ↓
English
```

而不是：

```text
想法
 ↓
中文
 ↓
逐字翻譯
 ↓
English
```

---

# 16. Adaptive System

Phase 不應該是單向 progression。

應該是：

```text
            ┌──────────────┐
            │   Observe    │
            └──────┬───────┘
                   ↓
┌──────────┐  ┌──────────┐  ┌──────────┐
│ Easier   │← │ Current  │ →│ Harder   │
│ Support  │  │  Mode    │  │  Mode    │
└──────────┘  └──────────┘  └──────────┘
```

例如使用者已經進入 Phase 3。

如果開始研究：

```text
distributed systems
```

可以暫時增加 `/zh` usage。

這不是 regression。

這是：

> **context-dependent assistance**

---

# 17. Three Adaptive Controls

未來 system 可以有三個 independent controls。

---

## 17.1 Input Assistance

```text
High

Chinese allowed
/en frequently
```

```text
Medium

English-first
/en fallback
```

```text
Low

English directly
/en only when necessary
```

---

## 17.2 Output Complexity

```text
Level 1

Very simple Technical English
```

```text
Level 2

Normal software engineering English
```

```text
Level 3

Native-level technical documentation
```

---

## 17.3 Learning Intensity

```text
Off

Do not teach English.
```

```text
Light

Only point out important mistakes.
```

```text
Learning

Provide patterns and brief explanation.
```

---

## Example Configurations

Early stage：

```text
Input Assistance: Medium
Output Complexity: Level 1
Learning: Light
```

Later：

```text
Input Assistance: Low
Output Complexity: Level 2
Learning: Light
```

When researching a difficult new domain：

```text
Input Assistance: Low
Output Complexity: Level 1
Learning: Off
```

---

# 18. Success Metrics

不要使用：

```text
learned vocabulary count
grammar score
daily word target
```

主要 metrics：

| Metric | Desired Direction |
|---|---|
| `/en` dependency | ↓ |
| `/zh` dependency | ↓ overall |
| English input ratio | ↑ |
| Reading interruption | ↓ |
| Task completion friction | ↓ |
| English artifact comfort | ↑ |

注意：

`/zh` usage 在 unfamiliar technical domain 中暫時上升是正常的。

---

## Ultimate Success Metric

最重要的問題：

> **Do I forget that I am working in English?**

當 debug 時，你主要在想：

```text
context
timeout
race condition
request lifecycle
rollback
```

而不是：

```text
這句 grammar 對嗎？
這個 English 怎麼講？
```

代表 system 正在成功。

---

# 19. Anti-patterns

整個 project 應避免以下情況。

## 19.1 Full bilingual output

Avoid：

```text
English paragraph
Chinese paragraph
English paragraph
Chinese paragraph
```

問題：

- output 過長
- reading fatigue
- token waste
- 依賴 translation

---

## 19.2 Automatic full translation

不要把所有 English 自動變成 Chinese。

目標應該是：

> **English-first + Chinese-on-demand**

---

## 19.3 Grammar perfection

不要因為：

```text
Check why timeout happen.
```

grammar 不完美就阻止工作。

只要 AI 正確理解 intent，就具有 practical value。

---

## 19.4 Premature learning system

不要一開始就建立：

```text
flashcards
1000-word vocabulary
daily quizzes
learning dashboard
```

先取得 real usage data。

---

## 19.5 Premature tooling

不要一開始就建立複雜 standalone CLI。

先用 Claude Code / Codex skills 驗證 workflow。

之後再考慮抽象成 vendor-neutral：

```text
Language Assistance Layer
        │
        ├── Claude Code
        ├── Codex
        ├── GitHub
        ├── Markdown
        └── Browser documentation
```

---

# 20. Recommended Implementation Order

## Step 1 — Run Phase 0

先觀察數次真實 software engineering interaction。

建立：

```text
Top Input Frictions
Top Output Frictions
```

不要先 coding。

---

## Step 2 — Define Phase 1 Specification

正式定義：

```text
/en
/zh
Technical English Output Style
```

包含：

- purpose
- input
- output
- behavior
- non-goals
- examples
- edge cases

---

## Step 3 — Define First STE-inspired Rules

第一版保持少量：

```text
6–10 rules
```

不要複製整套 ASD-STE100。

---

## Step 4 — Implement Claude Code Version

可考慮：

```text
Claude Skill
Output Style
CLAUDE.md
```

目的是快速驗證 interaction。

---

## Step 5 — Implement Codex Version

對應：

```text
Codex Skill
AGENTS.md
```

保持 core behavior 一致。

---

## Step 6 — Use in Real Engineering Tasks

例如：

```text
bug investigation
code review
spec reading
architecture discussion
GitHub Skill research
```

記錄 friction，而不是只做 artificial test cases。

---

## Step 7 — Adjust Before Phase 2

根據真實 data 決定：

```text
/en behavior
/zh explanation depth
output complexity
terminology handling
```

不要因原本 roadmap 而硬進 Phase 2。

---

# 21. Immediate Next Milestone

目前最合理的下一個 milestone：

> **完成 Phase 0 + Phase 1 specification**

應包含：

```text
1. Phase 0 observation method

2. /en specification
   - what it does
   - what it does not do
   - output style
   - examples

3. /zh specification
   - explanation behavior
   - technical terminology handling
   - concept vs language handling
   - examples

4. Technical English Output Style
   - STE-inspired rules
   - software terminology rules
   - complexity level

5. Initial validation checklist
```

這些完成之後，再開始寫 Claude Code / Codex Skill。

---

# 22. Long-term Vision

最終可能形成：

```text
                     ┌─ Claude Code
                     │
Language Assistance ─┼─ Codex
                     │
                     ├─ GitHub
                     │
                     ├─ CLI
                     │
                     └─ Markdown / Docs
```

System components：

```text
Writing Standard
│
├── STE-inspired Software Technical English
│
Work Tools
│
├── /en
├── /zh
└── Output Style
│
Learning Tools
│
├── /en-review
├── /learn
├── Engineering Phrasebook
└── Personal Technical English Profile
```

但最終 success 不應該是「system 功能很多」。

真正的 success 是：

```text
/en usage ↓
/zh usage ↓
English confidence ↑
Technical comprehension ↑
Workflow friction ↓
```

也就是：

> **Language Assistance System 逐漸變得不重要，但使用者處理 English technical communication 的能力持續提升。**
