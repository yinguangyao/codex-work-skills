# Codex Work Skills

[English](README.md) | [中文](README.zh-CN.md)

一个面向 Codex 日常工作的 skills 包：

- `evidence-first`：先核对前提，用证据支撑结论，并明确验证方式。
- `codex-dispatch`：在非琐碎 Codex 工作开始前，显式决定 Direct / Single / Parallel / Sequential。

这两个 skill 应该组合使用，而不是合成一个。`codex-dispatch` 决定工作如何组织；`evidence-first` 保证执行和交付有证据、有验证、不虚报。

## 用 npx 安装

查看仓库里可安装的 skills：

```bash
npx skills add yinguangyao/codex-work-skills --list
```

全局安装到 Codex：

```bash
npx skills add yinguangyao/codex-work-skills --skill evidence-first --agent codex --global
npx skills add yinguangyao/codex-work-skills --skill codex-dispatch --agent codex --global
```

非交互安装：

```bash
npx skills add yinguangyao/codex-work-skills --skill evidence-first --agent codex --global --yes
npx skills add yinguangyao/codex-work-skills --skill codex-dispatch --agent codex --global --yes
```

## 包含的 Skills

| Skill | 触发场景 |
|---|---|
| `evidence-first` | 任务需要可靠结论、前提核对、来源支撑、验证方式，或要交付给别人做决策。 |
| `codex-dispatch` | Codex 任务在读仓库、排查、改代码、review 或高风险判断前，需要显式决定 Direct 还是使用子 agent。 |

## 推荐组合方式

非琐碎 Codex 工作建议按这个顺序：

1. `codex-dispatch`：先决定 Direct、Single、Parallel 或 Sequential。
2. `evidence-first`：执行和交付时保证每个结论有证据、有验证。

## 仓库结构

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

## 维护约定

- `evidence-first` 保持可移植、模型无关。
- `codex-dispatch` 保持 Codex 专用，只负责执行路由。
- 不要把它们合并成一个 `SKILL.md`；它们的触发条件和执行阶段不同。
