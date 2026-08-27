# Quality Checklist

Use this checklist before finalizing a beginner-written AI agent skill.

## Trigger

- The discovery metadata or `description` says what the skill does and when to use it.
- The discovery description names real user situations or phrases, not only broad categories.
- Each trigger branch is distinct. Remove repeated synonyms that do not add a new branch.
- The first words carry the main trigger idea.

## Structure

- The main skill file exists, usually `SKILL.md`, and includes the metadata required by the target platform.
- `name` is short, lowercase, and stable.
- `description` or equivalent discovery metadata is present when the platform supports automatic discovery.
- Optional folders are used only when they help:
  - `references/` for long details, rubrics, examples, or domain facts.
  - `scripts/` for executable code the agent can call.
  - `assets/` for templates, styles, or output resources.

## Body

- The body tells the agent what to do, not what the feature is.
- The workflow is ordered when order matters.
- Each step has a clear completion criterion.
- The output is named and judged by explicit standards.
- The skill says what good looks like and what common mistakes to avoid.
- It skips generic instructions the agent already knows.
- For complex choices, the coach gave 2-3 options with a recommendation instead of asking the beginner to decide from scratch.
- For non-trivial skills, the coach confirmed a Skill Brief before finalizing the main skill file.

## Coaching Flow

- The first question is about the user's problem or desired AI help, not skill mechanics.
- The coach asks one concrete question at a time during discovery.
- When the user says "继续", the coach moves to the next missing piece instead of restarting.
- The Skill Brief uses beginner-friendly labels and matches the user's real workflow.

## Progressive Disclosure

- Material every run needs stays in the main skill file.
- Branch-specific or long material goes into `references/`.
- Pointers to reference files explain when to read them.
- The main file remains readable without hiding the core workflow.

## Language

- Prefer positive instructions: say the target behavior.
- Use prohibitions only for hard guardrails.
- Avoid vague words like "handle", "optimize", "improve", or "process" unless the body makes them concrete.
- Keep each meaning in one place so future edits do not drift.

## Examples

- Include at least one realistic user phrase.
- Show what the agent should do next.
- Include the expected result shape.
- Prefer one strong example over several shallow examples.

## Final Test

The skill is ready when a new agent can answer these questions after reading it:

1. When should I use this skill?
2. What steps do I follow?
3. What output should I produce?
4. What mistakes should I watch for?
5. What extra files should I read only when needed?
6. What should stay outside the generated skill files as notes?
