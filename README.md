# UX Clarity

**Help coding agents make interfaces easier to understand, navigate, and use.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/Agent_Skill-SKILL.md-111827.svg)](SKILL.md)
[![No runtime dependencies](https://img.shields.io/badge/Runtime_dependencies-none-15803d.svg)](#compatibility)

UX Clarity is a standalone, framework-independent skill for information architecture, navigation, task priority, and cognitive load. It helps agents explain **why an interface is confusing, how to organize it better, and which changes matter most**.

Use it for websites, applications, admin panels, dashboards, settings, tables, and forms. It works from the evidence available in your project: code, routes, screenshots, rendered screens, product requirements, and user feedback.

## Installation

Run this from the project where you want to use the skill:

```bash
npx skills add LeonardSEO/ux-clarity
```

The [Skills CLI](https://github.com/vercel-labs/skills) lets you choose your coding agents. Installation is project-local by default; add `-g` for installation across projects. The CLI requires Node.js 22.20 or later; the skill itself has no runtime dependencies.

Install directly for Codex and Claude Code:

```bash
npx skills add LeonardSEO/ux-clarity --skill ux-clarity --agent codex claude-code -y
```

Install globally:

```bash
npx skills add LeonardSEO/ux-clarity -g
```

<details>
<summary>Manual installation</summary>

Download or clone this repository, then copy its contents into a folder named `ux-clarity` in your agent's skill directory.

| Agent | Project installation | Global installation |
| --- | --- | --- |
| Codex | `.agents/skills/ux-clarity/` | `~/.agents/skills/ux-clarity/` |
| Claude Code | `.claude/skills/ux-clarity/` | `~/.claude/skills/ux-clarity/` |

Keep `SKILL.md`, `references/`, and `agents/` together so relative references continue to work. Other agents can use the same files if they support the `SKILL.md` format; consult their installation instructions.

</details>

## Quick start

In Codex, invoke the skill with `$ux-clarity`. In Claude Code, use `/ux-clarity`. Follow your agent's invocation convention elsewhere.

### Audit an existing interface

```text
$ux-clarity Audit the UX hierarchy of this application.
Identify confusing navigation, misplaced actions, poor information
grouping, and cognitive overload. Prioritize findings by severity
and task impact. Do not change code.
```

### Design a better structure

```text
$ux-clarity Propose a clearer structure for this admin dashboard.
Organize it around the user's main tasks. Explain which information
belongs together and whether tabs, filters, accordions, or separate
pages fit best. Preserve every existing capability.
```

### Implement focused improvements

```text
$ux-clarity Improve the quote list and template editor usability.
Make the smallest changes with the greatest usability impact.
Preserve existing functionality, permissions, routes, and styles.
Verify keyboard access, empty states, cancellation, and navigation.
```

## Three modes, one workflow

| Mode | When to use it | Expected result |
| --- | --- | --- |
| **Audit** | Understand what makes an existing interface confusing. | Prioritized findings with evidence, severity, task impact, and proposed fixes. |
| **Structure** | Decide how content, navigation, and actions should be arranged. | A proposed hierarchy with explicit pattern choices and trade-offs. |
| **Implement** | Apply explicitly requested interface improvements. | Scoped code changes, behavior checks, and a report of what was verified. |

The skill starts with the user's role and job, inventories the relevant information and actions, and addresses structure before decoration. It then evaluates interaction patterns, applies usability heuristics, and defines acceptance checks.

For substantial reviews, expect a task summary, an issue table, a before/after structure, material pattern decisions, and testable acceptance criteria. Focused questions receive focused answers.

## Design principles

- **Organize around tasks.** Navigation should reflect how users work, rather than how the database is arranged.
- **Make priority contextual.** Primary, supporting, secondary, and administrative information depend on the role and situation.
- **Explain pattern choices.** Tabs, accordions, filters, and separate pages solve different problems.
- **Use evidence and severity.** Findings distinguish observations, reports, and inferences, with severity from 0 to 4.
- **Simplify without losing capability.** Keep important information, comparisons, actions, permissions, and recovery paths accessible.
- **Protect continuity and trust.** Preserve input and return context; distinguish selection, saving, and completion, and keep failures distinct from empty results.
- **Validate honestly.** Check relevant complete task paths and report observed behavior and untested assumptions without inventing user-test results.

There are no artificial “10/10 UX” scores, fixed click limits, or mandatory maximum menu sizes. A structure review does not automatically become a brand redesign, animation pass, SEO audit, or performance project.

## Compatibility

The skill consists of English Markdown instructions and optional agent metadata. It requires no external plugins, hooks, MCP servers, UI libraries, or framework-specific tooling. The installer is optional.

Codex and Claude Code can load the skill through their skill systems. Other agents that support `SKILL.md` can use the same instruction set. Browser interaction and implementation checks depend on the tools available to the agent; a screenshot alone does not verify an interaction.

## What's included

```text
ux-clarity/
├── SKILL.md                         # Entry point and central workflow
├── agents/
│   └── openai.yaml                  # Codex display metadata
├── references/
│   ├── pattern-selection.md         # Choose patterns and explain trade-offs
│   ├── heuristic-audit.md           # Usability checks and severity
│   ├── dashboards-tables-forms.md   # Operational interface guidance
│   ├── validation.md                # Acceptance checks and research methods
│   ├── worked-example.md            # Example of competing UX requirements
│   └── source-notes.md              # Sources, adaptations, and exclusions
├── README.md
└── LICENSE
```

Start with [SKILL.md](SKILL.md), or read the [worked example](references/worked-example.md) to see the approach in context. Reference documents are loaded when relevant to the task.

## Validation status

Version 1.0 is an initial release. Structural and installer checks establish that the package can be discovered and installed; they do not establish that every agent will make good UX decisions. Real product trials and user testing are still needed to assess usability outcomes.

## Sources and attribution

UX Clarity synthesizes established UX methods and selected approaches from four sources:

| Source | Approach carried forward |
| --- | --- |
| [Organize — Design with Intent](https://github.com/ghaida/intent) | Information architecture, navigation, logical grouping, and clear labels. |
| [Dashboard — Uxcel Lab](https://github.com/Uxcel-Lab/product-skills) | Task-based priorities, information hierarchy, and focused dashboards. |
| [UX Heuristics — Wondel.ai](https://github.com/wondelai/skills) | Nielsen's ten heuristics, cognitive load, and severity-based evaluation. |
| [Distill — Impeccable](https://github.com/pbakaus/impeccable) | Removing unnecessary complexity while preserving functionality. |

Distill is part of Impeccable, rather than a separate upstream skill. These projects are references, not installation dependencies. See [source notes](references/source-notes.md) for the inspected files, license references, and deliberate adaptations.

## Contributing

Open an [issue](https://github.com/LeonardSEO/ux-clarity/issues) or pull request with a concrete interface scenario, the observed problem, and the expected improvement. Keep instructions framework-independent and distinguish evidence from assumptions. Include a way to check the outcome of proposed changes.

## License

[MIT](LICENSE). Upstream projects retain their respective licenses and attribution.
