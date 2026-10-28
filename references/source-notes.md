# Source analysis and attribution

The UX Clarity skill is a new, standalone instruction set that synthesizes common UX methods and selected design judgment from four public source documents. It is not a bundle of, or runtime dependency on, those projects. Upstream source instructions were reviewed on 2026-10-28. Reference each upstream project when studying its method or adapting future releases.

## Sources inspected

| Source | Upstream file | Blob SHA | License |
| --- | --- | --- | --- |
| Design with Intent / Organize by ghaida | https://github.com/ghaida/intent/blob/main/skills/organize/SKILL.md | `21fbc9ea8d144e38f05fe872779c238f10aa3acf` | CC0 1.0 |
| Uxcel Lab / Dashboard | https://github.com/Uxcel-Lab/product-skills/blob/main/ux/screens/dashboard/SKILL.md | `a3a437b42f0d21e341135b1590e627fedc998ef0` | MIT, copyright Uxcel Lab 2026 |
| Wondel.ai / UX Heuristics | https://github.com/wondelai/skills/blob/main/ux-heuristics/SKILL.md | `63e6db1c88ba20d7e5ef7391d266ef6b3019a3b0` | MIT, copyright Wondel.ai sp. z o.o. 2025 |
| Impeccable / Distill by Paul Bakaus | https://github.com/pbakaus/impeccable/blob/main/skill/reference/distill.md | `cf8225ce94175f32d0b4f723f67019527ed6836f` | Apache-2.0 |

`distill` is a command/reference within the larger Impeccable skill, not a separately installable original skill. This synthesis does not use its CLI, hooks, detector rules, or scripts.

Full upstream licenses are available at:

- https://github.com/ghaida/intent/blob/main/LICENSE
- https://github.com/Uxcel-Lab/product-skills/blob/main/LICENSE
- https://github.com/wondelai/skills/blob/main/LICENSE
- https://github.com/pbakaus/impeccable/blob/main/LICENSE

## Retained strengths and changes

### Organize

**Keep:** User-centered categories, structural IA beyond menu design, known-item search versus exploratory browse, wayfinding, taxonomy clarity, and validation via card sorts/tree tests.

**Adapt:** Bring page-level prioritization and interaction states into the same skill rather than requiring other specialist agents. Require trade-off explanation for navigation patterns.

**Do not port:** Mandatory visualization prompts, fixed HTML diagram styling, dependencies on Intent agents, and absolute menu-count or research sample-size rules.

### Uxcel Dashboard

**Keep:** Start with role and decision; distinguish operational from analytical dashboards; put relevant information first; keep comparison data visible together; resist the temptation to show every metric.

**Adapt:** Extend beyond data visualization into work queues, approvals, records, and settings. Make role-based default views conditional rather than global.

**Do not port:** Automatic invocation of separately installed Uxcel audit skills; a universal chart choice or absolute zero-baseline rule for every type of visual.

### Wondel UX Heuristics

**Keep:** A structured Nielsen-informed review, scan-friendly orientation, clear labeling, cancellation and recovery, and severity 0-4 tied to task consequences.

**Adapt:** Add explicit evidence confidence, role/context, and the smallest effective change. Treat heuristics as diagnostic hypotheses rather than facts until the behavior is observed.

**Do not port:** A fabricated or mechanical 10/10 UX score, the "seven plus or minus two" count as a law, or claims that one click-count target fits all products.

### Impeccable Distill

**Keep:** Remove redundant elements, competing emphasis, excess surface noise, and unneeded steps while preserving the real task. Ensure every prominent element earns its position.

**Adapt:** Simplify the information model and task hierarchy *before* visual cleanup. Insist that necessary comparison, disclosure, safety, and capabilities remain accessible.

**Do not port:** The full design-polish system, CLI hooks, visual effects rules, arbitrary limitations on colors or font counts, or blanket bans on cards and sidebars.

## Why one skill, with references but without hooks

These problems depend on product context, roles, semantics, and user needs. A deterministic edit hook cannot reliably decide whether tabs beat accordions, whether two records should merge, or which task should appear first. Hooks would add intrusive behavior to unrelated edits. The main SKILL.md supplies the decision workflow; small reference files load only when relevant. No runtime dependency or network call is needed to apply the framework to available project files.

## Originality and distribution

UX Clarity describes established interaction-design concepts in new wording and combines them into a separate workflow. It does not embed upstream SKILL.md files, executable code, branded CSS templates, or command prompts. Original upstream rights remain with their respective owners. Link to the original files for license and future updates.
