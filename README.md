# Codex Work Skills

[English](README.md) | [中文](README.zh-CN.md)

> Deprecated: this combined package is kept only as a correction record. Use the separate skill repositories instead:
>
> - `evidence-first`: <https://github.com/yinguangyao/evidence-first-skill>
> - `codex-dispatch`: <https://github.com/yinguangyao/codex-dispatch-skill>

A small Codex skills pack for disciplined, evidence-backed work:

- `evidence-first`: verify premises, cite evidence, and deliver with explicit verification.
- `codex-dispatch`: make a visible Direct/Single/Parallel/Sequential decision before non-trivial Codex work.

These skills are meant to compose, not merge. `codex-dispatch` decides how the work should be organized; `evidence-first` keeps the work evidence-backed and honest.

## Install With npx

List available skills:

```bash
npx skills add yinguangyao/codex-work-skills --list
```

Install both skills globally for Codex:

```bash
npx skills add yinguangyao/codex-work-skills --skill evidence-first --agent codex --global
npx skills add yinguangyao/codex-work-skills --skill codex-dispatch --agent codex --global
```

Install non-interactively:

```bash
npx skills add yinguangyao/codex-work-skills --skill evidence-first --agent codex --global --yes
npx skills add yinguangyao/codex-work-skills --skill codex-dispatch --agent codex --global --yes
```

## Included Skills

| Skill | Use when |
|---|---|
| `evidence-first` | A task needs reliable conclusions, premise checks, source-backed claims, verification, or a decision-ready deliverable. |
| `codex-dispatch` | A Codex task needs an explicit Direct vs subagent decision before repo inspection, debugging, edits, review, or high-risk work. |

## Recommended Pairing

For non-trivial Codex work, use them in this order:

1. `codex-dispatch`: choose Direct, Single, Parallel, or Sequential.
2. `evidence-first`: execute and report with verified claims.

## Repository Layout

```text
skills/
  evidence-first/
    SKILL.md
    methodology.md
    phases.md
    review.md
  codex-dispatch/
    SKILL.md
    agents/openai.yaml
```

## Maintenance Notes

- Keep `evidence-first` portable and model-neutral.
- Keep `codex-dispatch` Codex-specific and focused on execution routing.
- Do not collapse them into one `SKILL.md`; their trigger conditions and execution phases are different.
