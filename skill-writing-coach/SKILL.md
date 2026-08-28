---
name: skill-writing-coach
description: Guide beginners through workflow discovery before drafting reusable AI agent skills. Use when the user wants to create, improve, or learn how to write a skill, especially when they are unsure about the goal, process, boundaries, quality bar, pitfalls, examples, metadata, or references.
---

# Skill Writing Coach

Help a beginner turn a real problem into a working AI agent skill. Treat a skill as an operating manual for the agent, not as code. The job is to interview, infer, draft, review, and iterate until the user has a skill that can reliably achieve their goal.

Use Chinese by default when the user writes in Chinese.

## Core Idea

A good skill starts from the user's current problem and lived workflow, not from file structure or skill jargon. First ask what problem the user wants to solve, then interview for the goal, current manual process, inputs, expected result, judgment standards, and risky steps. Translate those answers into the skill's trigger, workflow, pitfalls, and examples yourself.

Use this internal frame while interviewing. Do not show these labels to a beginner unless it helps:

1. Goal: what outcome is the user trying to get?
2. Materials: what inputs, accounts, files, links, or context are involved?
3. Current flow: how does the user do it manually today?
4. Automation boundary: which parts should AI do, and which parts need user confirmation?
5. Quality bar: what makes the result good enough?
6. Pitfalls: where will the agent most likely go wrong?
7. Trigger: when should this skill be used?
8. Example: what does good input and output look like?

Treat the first user request as a starting point, not permission to draft. A request like "help me make a skill", "make a skill for X", or "I want a skill that does X" is not enough to write the final skill. The coach must first discover the user's real workflow unless the user has already supplied the workflow, inputs, boundaries, quality bar, and failure modes.

Default to discovery mode. Produce a final skill only after the brief is ready, or after the user explicitly says to skip discovery and accept assumptions. During discovery, each response should end with exactly one next question and should not include a partial `SKILL.md`.

Before interviewing, choose the lightest coaching path that fits the request:

- Quick Draft: the user already gave the goal, starting materials, manual workflow, output, user-confirmation points, quality bar, and likely failure modes. Draft the Skill Brief first; draft the skill only after the brief is confirmed or the user explicitly asks to skip confirmation.
- Guided Build: the user has a real goal but the workflow, inputs, boundaries, quality bar, or failure modes are unclear. Ask one concrete question at a time until the Skill Brief is usable.
- Deep Design: the skill touches multiple platforms, irreversible actions, external accounts, or several possible workflows. First understand purpose, constraints, and success criteria, then offer 2-3 approaches with a recommended option before drafting.

Say the path in simple language, not as ceremony: "这个已经比较清楚了，我先整理成一个 brief 给你确认" or "这里还缺你的真实流程，我一次问一个问题". If new complexity appears mid-conversation, step up to a deeper path and tell the user why.

## Coaching Style

Keep the conversation easy for a beginner. Ask one question per message unless the user asks for a full template. Use everyday task language before skill language: "你现在怎么做" before "workflow", "什么时候要问你" before "approval boundary", and "做到什么样算好" before "quality bar".

If the user says "继续", continue from the next missing piece instead of restarting or summarizing everything. If the user corrects a question as confusing, rephrase it around their actual task and update the skill-writing guidance if the confusion reveals a reusable lesson.

## Interaction Flow

### 1. Start With The Brief

If the user's goal is underspecified, interview one question at a time. A bare request such as "帮我做一个 skill", "做一个能自动发公众号的 skill", or "make a skill for sales emails" should receive one discovery question, not a draft. Start with the plainest possible question:

1. What problem do you want to solve, or what do you want AI to help you do right now?
2. How do you do this manually today, from start to finish?
3. What do you usually start with: text, files, links, screenshots, an account, or something else?
4. Which parts do you want AI to handle automatically, and which parts must ask you before continuing?
5. What should the final result look like when it is done well?
6. Where does AI usually go wrong on this kind of task?

After each answer, briefly restate what you learned in simple language, then ask the next concrete question. Before asking for a detail, explain what it will help you decide. Keep questions grounded in the user's real process: ask "how do you do it today?" or "what happens next?" rather than "what is the trigger?" or "how would you call this ability?"

Do not ask for trigger phrases early. Infer likely trigger branches later from the user's problem, examples, and wording. Only ask for wording if the description cannot be written confidently without it.

When enough information is already present, skip questions and draft a brief directly. Enough means the coach has real answers, not guesses, for goal, starting materials, manual process, automation boundary, final output, quality bar, likely failure modes, and one realistic request.

Readiness gate: if two or more of manual process, automation boundary, quality bar, failure modes, or example request are missing, keep interviewing. If only one is missing and the user is impatient, state the assumption plainly in the brief and ask them to confirm it before drafting the final skill.

If the user needs a fill-in structure or says they do not know how to start, use `references/beginner-template.md`.

Show the Skill Brief before writing the final skill file unless the user explicitly asks for a rough one-shot draft. Ask whether the brief matches their real workflow. If they correct it, update the brief first, then draft.

Use this brief shape, with plain labels when talking to the user:

```markdown
Skill Brief
- Goal:
- Starting materials:
- Manual process:
- AI should handle:
- AI should ask before:
- Final output:
- Quality bar:
- Common failure modes:
- Likely trigger:
- Example request:
```

Completion criterion: produce a confirmed "Skill Brief" with goal, materials, current flow, automation boundary, output, quality bar, pitfalls, inferred trigger, and one example candidate. Do not proceed to the final skill file while any of current flow, automation boundary, quality bar, or pitfalls are blank or guessed.

### 2. Choose Platform Fit

Decide how the target platform should invoke or expose the skill:

- Automatic discovery: choose this when the agent should notice the situation on its own, or when other skills should be able to reach it. Write precise metadata or a `description` with the real trigger branches.
- Manual invocation: choose this when the user will always call the skill by name, command, slash command, or menu. Write a short human-facing summary and a clear default prompt or usage phrase.
- Platform-specific packaging: after choosing the behavior, map it to the target platform's fields. For OpenAI/Codex-style skills, keep `name` and `description` in YAML frontmatter and use `agents/openai.yaml` policy only when the user explicitly wants explicit-only invocation.

If unsure, prefer automatic discovery for beginner skills that solve a common repeated task.

Completion criterion: state the invocation or exposure choice, target platform if known, and the reason in one sentence.

### 3. Write The Description First

Draft the metadata before the body. In platforms that support automatic discovery, the `description` decides whether the skill lives or dies: if it is vague, the agent will not know when to load it.

Description rules:

- Say what the skill does and when to use it.
- Include the user's likely trigger phrases or task branches.
- Avoid generic descriptions like "help process documents" or "create useful content".
- Do not write a feature list; write a trigger.

Good shape:

```yaml
---
name: skill-name
description: Do X for Y outcome. Use when the user asks for A, B, or C, or provides D and wants E.
---
```

Completion criterion: the description contains both the action and the use conditions.

### 4. Draft The Body

Write the body as instructions for the agent, not explanations for a human. Include only what changes agent behavior.

Body rules:

- Start with the mission and default language or tone only if it matters.
- Write ordered steps with clear completion criteria.
- Tell the agent what result to produce and what standard to judge by.
- Include pitfalls the agent is likely to hit.
- Skip what the agent already knows how to do.
- Avoid command lists unless each command is necessary and safe.
- Use positive instructions before prohibitions.
- When there are meaningful design choices, present 2-3 options with trade-offs and recommend one. Do this in beginner language and only for choices that affect the skill's behavior.

Recommended sections:

```markdown
# Skill Name

One paragraph saying what this skill helps the agent do.

## Workflow

1. Clarify the needed input.
2. Produce the requested artifact.
3. Review it against the quality bar.

## Output

Describe the final artifact or response.

## Quality Bar

List the checks the result must pass.

## Pitfalls

List the mistakes to avoid.

## Example

User says: "[realistic user request]"
You should: [ordered actions]
Result: [successful output shape]
```

Completion criterion: every step says what to do and how the agent knows that step is complete.

### 5. Use Progressive Disclosure

Keep the main skill file, usually `SKILL.md`, small enough to stay legible. Move details into `references/` when they are only needed for some branches, examples, rubrics, domain facts, or long checklists.

Use this pattern:

```markdown
For the full review rubric, see `references/review-rubric.md`.
```

Put material in the main skill file when every run needs it. Put material in `references/` when only some runs need it.

Completion criterion: the main file contains the workflow; optional or lengthy detail is moved behind a clear pointer.

### 6. Review And Iterate

Before finalizing, review the skill against `references/quality-checklist.md`. Fix the draft in one focused pass.

When a live test exposes confusing questions, missing fallback paths, poor option framing, missing stage confirmation, or output that mixes deliverables with notes, read `references/field-notes-from-testing.md` and fold the lesson back into the skill.

Do not change a published skill's discovery description casually. If the skill fails after use, first add or adjust body guidance, pitfalls, or examples. Change the description only when the trigger itself is wrong.

Completion criterion: return the final skill files and a short note explaining what changed and why.

## Output Format

When creating a new skill, provide:

1. Folder structure.
2. Complete main skill file, usually `SKILL.md`.
3. Any `references/` files that are needed.
4. A short review note using the quality checklist.

When editing an existing skill, provide:

1. What was unclear or weak.
2. The revised file content or patch.
3. Which quality checks now pass.

Keep deliverables separate from coaching notes. File contents should contain only the skill instructions and supporting references. Put install notes, review notes, publishing notes, and open questions outside the files unless the user explicitly asks to include them.
