# Skill Writing Coach

`skill-writing-coach` helps beginners create useful AI agent skills through a guided interview, drafting, review, and iteration process.

It is designed for users who do not know how to write a skill yet. The skill starts from the user's real problem and current workflow, then helps the agent infer the trigger, workflow, quality bar, pitfalls, examples, and supporting references.

The included folder is packaged in a `SKILL.md` structure that works well for OpenAI/Codex-style skill systems, but the coaching method is platform-agnostic: use it to design reusable instructions for any AI agent environment that supports skills, commands, procedures, or reusable operating manuals.

## Install For OpenAI/Codex-Style Skills

After this repository is published to GitHub:

```bash
npx skills add OWNER/REPO --skill skill-writing-coach
```

Replace `OWNER/REPO` with this GitHub repository path.

`agents/openai.yaml` is optional OpenAI/Codex UI metadata. The core skill is the main `SKILL.md` file plus the focused references.

## Contents

```text
skill-writing-coach/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── beginner-template.md
    ├── field-notes-from-testing.md
    └── quality-checklist.md
```
