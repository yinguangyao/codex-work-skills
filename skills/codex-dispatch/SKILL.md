---
name: codex-dispatch
description: "Use when starting Codex work that needs an explicit Direct vs subagent choice: code edits, debugging, reviews, repo exploration, multi-file changes, ambiguous scope, high-risk judgment, or requests mentioning agents, subagents, delegation, parallel work, model choice, cost, token use, or over-delegation."
---

# Codex Dispatch

## Core rule

Make one visible dispatch decision before substantial work. Loading this skill never means “spawn”; it means decide.

Root owns requirements, shared context, file-conflict control, final synthesis, and the user-facing answer. Delegate only when a child result is independently useful enough to justify coordination overhead.

When the root model is strong (for example Sol-class) or other skills already push toward subagents, be stricter, not looser. Children are for context isolation, true parallelism, bounded implementation, hard debugging, or independent review—not confidence theater.

## Required decision

Before running repo inspection, editing files, or debugging deeply, emit exactly one decision:

```text
Dispatch: Direct | Single | Parallel | Sequential
Reason: <why this mode is sufficient>
Children: <none, or role -> bounded result>
```

No visible decision means the skill has not been used.

## Bias

Start at Direct. Stay Direct unless at least one hard delegation gate below is met.

Choose Direct when:

- the only reason to spawn is task size, confidence, model strength, or habit;
- files are tightly coupled or likely to overlap;
- the user has not authorized subagents and active runtime policy requires explicit authorization;
- the root can finish faster than it can coordinate.

## Hard delegation gates

Delegate only when one of these is true:

| Gate | Delegate when | Prefer |
|---|---|---|
| Context isolation | A large read-only search, inventory, extraction, or comparison would bloat the root context before implementation. | `luna-explorer` |
| True parallelism | Independent areas can be explored or verified without overlapping files or shared state. | `luna-explorer` / `terra-worker` |
| Bounded implementation | One clear change has acceptance criteria, expected files, and a matching test or verification command. | `terra-worker` |
| Hard debugging | Reproduction or root cause is uncertain enough that a focused investigator can return a concrete failing case or fix plan. | `terra-debugger` |
| Independent review | The result is high-risk, architectural, security-sensitive, or likely to suffer from root blind spots. | `sol-reviewer` |

## Modes

| Outcome | Selected children |
|---|---|
| Direct | No hard gate is met, or coordination would cost more than it saves. |
| Single | Exactly one bounded artifact. |
| Parallel | Two or three independent, non-overlapping artifacts. |
| Sequential | Two or three artifacts where a later child depends on an earlier child. |

Hard maximum: three child tasks per routing decision. Root synthesis does not count. If more branches exist, combine them into three bounded scopes or keep excess work with root.

Never parallelize agents writing overlapping files. Keep delegation root-to-child; children must not spawn agents. Respect active runtime policy; this skill requires a decision, not a spawn.

## Choose agents

| Agent | Route here |
|---|---|
| `luna-explorer` | Clear read-only exploration, extraction, inventory, classification, or summaries. |
| `terra-worker` | Everyday implementation, writing, straightforward debugging, and tests with clear acceptance criteria. |
| `terra-debugger` | Difficult reproduction, root-cause analysis, cross-module reasoning, or high-effort implementation. |
| `sol-reviewer` | Independent review of ambiguous, architectural, security-sensitive, or high-value results. |

Cost preference for compatible work: Luna Low -> Terra Medium -> Terra High -> Sol High. Cost never overrides role semantics. Max and Ultra require explicit user choice.

## Child contract

For every child, provide: goal, scope, completion criteria, allowed mutations, and expected return format. State the outcome, not tactics. Wait for required results, compare cited evidence, and synthesize one answer; never concatenate child responses.

Reuse an existing agent with follow-up instructions instead of spawning a duplicate for the same role and scope. Ask for concise findings, verification, and remaining risk rather than raw logs.

Direct is not a shortcut around verification. Use the task's domain skills, tests, and evidence requirements normally.

## Common mistakes

- Spawning agents merely because a task is large.
- Spawning agents because a strong model is available.
- Treating “I used the skill” as true without a visible dispatch note.
- Using Sol for clear bounded work that Luna or Terra can complete.
- Running dependent stages in parallel.
- Giving two writers ownership of the same files.
- Letting children expand scope or spawn grandchildren.
- Reporting success without waiting for required verification.
