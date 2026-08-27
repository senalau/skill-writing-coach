# Beginner Skill Template

Copy this structure when helping a beginner draft their first AI agent skill. Adapt the metadata and file names to the target platform.

```markdown
---
name: example-skill-name
description: Do [specific action] for [specific outcome]. Use when the user asks for [trigger phrase 1], [trigger phrase 2], or provides [input] and wants [result].
---

# Skill Name

Help the agent [do the repeated task] so the user gets [desired result].

## Workflow

1. Clarify [missing input] if needed.
   Completion criterion: [what must be known before continuing].
2. Inspect or gather [materials].
   Completion criterion: [what evidence or source is available].
3. Produce [artifact/result].
   Completion criterion: [what the result contains].
4. Review against [quality bar].
   Completion criterion: [what checks must pass].

## Output

Return [format], including [required parts].

## Quality Bar

- [Concrete standard 1]
- [Concrete standard 2]
- [Concrete standard 3]

## Pitfalls

- [Likely mistake and what to do instead]
- [Likely mistake and what to do instead]

## Example

User says: "[realistic trigger phrase]"

You should:
1. [first action]
2. [second action]
3. [final response or artifact]

Result: [shape of successful output]
```

## Fill-In Prompts

Ask these when the beginner is stuck:

1. "你现在想解决什么问题，或者想让 AI 帮你做什么？"
2. "你现在不用 AI 的时候，是怎么一步步做这件事的？从开始到结束讲一遍就行。"
3. "你一般会从什么材料开始？比如文字、文件、链接、截图、账号后台，还是别的。"
4. "哪些步骤你希望 AI 自动做？哪些步骤必须先问你确认？"
5. "最后做好的结果应该长什么样？什么情况你会觉得它做得好？"
6. "AI 做这件事时最容易哪里跑偏？"
7. "有没有一次你觉得它做对了？那次输入和输出大概是什么样？"

## Skill Brief Template

Use this before drafting the main skill file, usually `SKILL.md`, for any non-trivial beginner skill:

```markdown
我先把你的需求整理成一个 brief，你看看是不是贴近你的真实流程：

- 目标：
- 起始材料：
- 你现在手动怎么做：
- 希望 AI 自动做：
- 必须先问你确认：
- 最终结果：
- 做得好的标准：
- 最容易跑偏的地方：
- 我推断的触发方式：
- 一个典型请求：
```
