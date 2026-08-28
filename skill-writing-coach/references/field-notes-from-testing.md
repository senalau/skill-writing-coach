# Field Notes From Testing

These notes came from live-testing `skill-writing-coach` by creating and testing a WeChat article layout skill. Use them when improving this skill or when a beginner gets stuck during an interview.

## Interview The Workflow, Not The Skill

Start from the user's problem and current manual process. Do not ask beginners for skill concepts such as trigger, invocation, or workflow too early.

A user asking "帮我做一个 skill" or "make a skill for X" is not a complete brief. Treat it as permission to start discovery, not permission to write the final skill. The coach should first uncover the real task, materials, manual process, automation boundary, quality bar, and likely failure modes.

First-turn test: if the user says only "帮我做一个 skill" or "做一个能自动发公众号的 skill", the next response should ask what problem they want AI to solve or how they currently do the task. It should not contain a `SKILL.md` draft.

When the user says "直接写", "不用问", or gives a detailed first message, show a plain Skill Brief first and let the user decide whether to proceed. Keep the brief readable; do not turn it into an audit table.

Better questions:

- "你现在想解决什么问题，或者想让 AI 帮你做什么？"
- "你现在不用 AI 的时候，是怎么一步步做这件事的？"
- "你一般会从什么材料开始？"
- "你可以把相关链接、截图、文档、好例子都发来，我会帮你判断哪些能用。"
- "哪些步骤希望 AI 自动做？哪些必须先问你确认？"
- "最后做好的结果应该长什么样？"
- "AI 做这件事时最容易哪里跑偏？"

Infer trigger branches later from the user's answers. Ask for exact wording only when the description cannot be written confidently without it.

Ask the user for private, personal, or preference-heavy materials, and let them send all relevant materials if they are not sure what matters. Inspect the materials and decide which ones shape the skill. Gather public examples, current platform rules, and outside references yourself when they would materially affect the skill design.

## Ask One Concrete Question At A Time

The interview should feel like product discovery, not a form. Ask one question, restate what you learned, then ask the next question.

Avoid abstract prompts such as:

- "你会怎么叫醒这个能力？"
- "这个 skill 的触发条件是什么？"
- "给我 2-3 句原话。"

Replace them with concrete scenario prompts:

- "下一次你想做这件事时，会直接输入哪句话？"
- "从开始到结束，你现在手动怎么做？"
- "做到哪一步时必须先问你？"

## Pick The Lightest Coaching Path

Adapted from the `brainstorming` skill pattern: not every request needs the same amount of ceremony. Choose the smallest path that will produce a useful skill.

- Brief Check: use when the user already gave enough detail to make a coherent draft, or says the information is enough. Organize what they said into a plain Skill Brief and ask whether to proceed. Do not draft the final skill until the user says the brief is enough.
- Guided Build: use when the user knows the goal but not the skill shape. Interview their manual workflow one question at a time.
- Deep Design: use when the skill affects external accounts, publishing, automation, irreversible actions, or several viable workflows. Understand goals and constraints, then offer 2-3 approaches with a recommended option.

Do not expose this as a formal menu unless the user asks for choices. Phrase it naturally: "这个已经够清楚，我先整理" or "这里我需要先摸清你的流程".

## Confirm Before Finalizing

For non-trivial skills, create a checkpoint between interview and the final main skill file.

Show a short Skill Brief that includes:

- What the skill is for.
- What materials it starts from.
- What the agent should do automatically.
- Where it must ask the user.
- What a good result looks like.
- What mistakes it must avoid.

Ask whether the brief matches the user's real workflow. If the user corrects it, revise the brief before drafting the skill.

If the brief contains guessed workflow steps, guessed user-confirmation points, or guessed failure modes, keep interviewing instead of drafting.

Ask one question at a time until the coach can summarize a useful brief or the user says the information is enough. The brief is how the user checks whether the agent understood. If the core flow is too unclear to summarize and the user has not said to proceed, ask the next discovery question. If it can be summarized, show the brief and let the user decide whether to proceed or correct it.

Write the final skill after the user approves the Skill Brief or says it is good enough. If the user corrects the brief, revise the brief and ask again.

## Use Options For Real Choices

When a choice would change the skill's behavior, give 2-3 understandable options and recommend one. Good choices include:

- Whether the skill should draft only, publish automatically, or pause for confirmation.
- Whether to rely on links, screenshots, copied examples, or all available evidence.
- Whether to keep everything in the main skill file, usually `SKILL.md`, or move long rubrics and examples into `references/`.

Avoid options for tiny wording decisions. Beginners should feel guided, not tested.

## Let Tests Improve The Skill

When testing a generated skill, treat every failure as material for the skill itself.

Examples from the WeChat layout test:

- The WeChat link could not be inspected automatically, so the generated skill needed a fallback path: ask for screenshots, copied formatted samples, PDF, or a user description.
- Chrome showed the article tab but screenshots and DOM reads timed out, so the fallback should be first-class instead of treated as an error.
- The first output mixed title suggestions and summary notes into the copy-ready article body, so the skill needed a hard rule separating deliverable body from delivery notes.

## Separate Deliverable From Notes

For artifact-generating skills, define what belongs inside the artifact and what belongs outside it.

If the user needs a copy-ready body, the body should contain only intended article content and visual placeholders. Metadata, title alternatives, summary suggestions, cover notes, paste checks, and implementation comments belong outside the body.

This rule prevents the agent from polluting the user's final artifact with helper text.

## Preserve User Boundaries

User constraints from the interview become hard quality rules in the generated skill.

Examples:

- If the user says "不能改我的原文内容", the skill must explicitly preserve wording and only adjust structure or format.
- If the user says "封面图问我确认", the skill must pause before finalizing the cover.
- If the user says "不要只给建议", the skill must produce the finished artifact, not a recommendation list.

## Capture Fallbacks

If a workflow depends on external pages, accounts, links, screenshots, files, browser state, or platform behavior, include a fallback path.

A good fallback says:

1. What might fail.
2. What to ask the user for instead.
3. How to continue with partial evidence.
4. What uncertainty to disclose.

## Update Narrowly

Do not turn one observed failure into a universal rule for every skill. Add the smallest durable instruction that would have prevented the failure.
