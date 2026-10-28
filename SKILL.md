---
name: ux-clarity
description: Audit, design, or improve the logical organization of websites, dashboards, and apps. Use for information architecture, task-first screen hierarchy, navigation, confusing labels, crowded dashboards, tabs versus accordions, progressive disclosure, settings, forms, tables, discoverability, UX heuristics, or requests to make a UI clearer and easier to use. Diagnose the user's tasks before rearranging UI; preserve functionality, permissions, and the existing design system.
---

# UX Clarity

Make interfaces easy to understand, navigate, and act on. Organize for users' actual tasks, not the database schema, developer architecture, stakeholder org chart, or the amount of available data. Improve task success and decision confidence rather than optimizing for fewer clicks, fewer elements, or visual minimalism by themselves.

## Choose the right mode

- **Audit:** The user asks for a review, critique, UX heuristics, or why a layout is confusing. Inspect available screens and flows; produce prioritized findings. Do not change code unless requested.
- **Structure:** The user asks how content, navigation, sections, dashboards, or workflows should be organized. Design a proposed hierarchy and justify key choices; do not invent a visual brand.
- **Implement:** The user explicitly asks to fix, reorganize, or build UI. Inspect the existing app, make scoped changes, and verify behavior. Do not stop at a report when implementation is authorized.

Use the current task's scope. A request about one page is not permission to redesign the entire product. When no UI or code is accessible, label findings as hypotheses and identify the smallest evidence needed to validate them. Do not claim that a static screenshot proves an interaction works.

## Workflow

### 1. Establish the user's job and available evidence

Inspect project files, routes, screenshots, component hierarchy, actual rendered screens, product documentation, user feedback, role/permission logic, and analytics when available. Prefer direct observation to assumptions. Identify:

- **Actor:** Who uses this screen? Separate roles when their tasks genuinely differ.
- **Job:** What are they trying to find, decide, create, update, approve, or monitor?
- **Situation:** How often, how urgently, and with what consequence if they miss something?
- **Entry and exit:** Where do they arrive from and what counts as successful completion?
- **Constraints:** Existing design system, terminology, routes, permissions, responsive targets, and dependencies.

Ask only when a missing answer would reverse a meaningful design choice. Otherwise proceed with explicit assumptions. Separate **observed facts**, **stakeholder reports**, and **untested inferences**.

### 2. Inventory the actual information and actions

For the affected scope, map each route, section, dataset, action, filter, and state to a user task. Note repetition, hidden actions, ambiguous labels, dead ends, misplaced settings, missing recovery paths, and information users must compare side by side.

Classify elements as:

- **Primary:** Needed to complete the current user's principal task or urgent next action.
- **Supporting:** Needed to understand, compare, or confidently complete that task.
- **Secondary:** Useful but not typically needed in the current task state.
- **Administrative:** Configuration, historical reporting, and maintenance outside the active workflow.

This is a per-role, per-context classification, not a universal ranking. Preserve essential status, safety, consent, price, and error information even if visually secondary.

### 3. Fix structure before decoration

Organize around user mental models and lifecycle stages. Give each concept a clear canonical location, while providing contextual links when several entry points are useful. Avoid displaying duplicate-looking items without explaining their distinct identity, version, or scope. Use labels users recognize; explain what a destination contains or what an action does.

Determine separately:

1. **Global IA:** Major destinations and their relationships.
2. **Local IA:** Sections, subtasks, and views within a destination.
3. **Task hierarchy:** What should users see and do first, next, and optionally.
4. **Visual hierarchy:** Reading order, alignment, headings, whitespace, density, and action emphasis using the existing visual language.
5. **Interaction states:** Default, selected, loading, saved, empty, invalid, cancelled, and recovered.

Give the most important task or coherent group of tasks clear priority. Allocate useful space and attention while keeping the context needed for correct decisions visible alongside the work. Do not assume every page must have exactly one action or focal point; keep independent urgent actions discoverable when the workflow requires them.

### 4. Choose the least confusing interaction pattern

Read [Pattern selection](references/pattern-selection.md) when deciding between pages, tabs, segmented controls, accordions, filters, tables, cards, summaries, and drill-downs. State *why* a pattern fits and *when it would be worse* than the alternative.

Core guardrails:

- **Tabs:** Use for peer views or modes within the same context. Do not hide information users need to compare simultaneously; make active state and labels clear.
- **Accordions:** Use for optional detail and settings, not to bury important actions or conceal a page's purpose.
- **Filters:** Narrow a collection; do not substitute filters for workflow statuses or use hidden defaults that surprise users.
- **Dedicated pages:** Use for genuinely distinct destinations, deep tasks, or complex forms; maintain orientation and an easy return path.
- **Dashboards:** Lead with the decisions, exceptions, and next actions of the actual role, not every metric available. Read [Dashboards, tables, and forms](references/dashboards-tables-forms.md) for operational workflows.
- **Progressive disclosure:** Reveal complexity at the time it becomes relevant, but keep critical tasks, comparison information, and recoverability accessible.

Do not add tabs, accordions, modals, or cards merely to make the page look organized. Often clearer grouping, simpler labels, or reordered sections are enough.

### 5. Run a heuristic evaluation

Apply [Heuristic audit](references/heuristic-audit.md) to the actual task path. Check orientation, matching labels, user control, consistency, prevention, recognition, appropriate disclosure, system feedback, accessibility, and recovery.

For each *real* finding provide:

- **Location and affected task** (screen, role, scenario).
- **Evidence** (what was observed or reported) and **confidence** (verified, reported, inferred).
- **Failure mode** (why the user may be delayed, confused, misled, or blocked).
- **Severity 0-4** (0 no issue, 1 cosmetic, 2 minor, 3 major, 4 task blocking), based on frequency, impact, persistence, and affected roles.
- **Smallest effective fix**, its main trade-off, and a concrete way to test it.

Do not manufacture a single 10/10 UX score or count findings as if they were performance metrics. Do not elevate a stylistic preference into a usability defect without a plausible task consequence.

### 6. Recommend or implement, then verify

Prioritize changes by task impact, severity, reach, confidence, implementation effort, and regression risk. Prefer small structural fixes before large redesigns. Preserve existing routes, data, permissions, keyboard access, and actions unless changing them is explicitly in scope. Never hide or remove a required capability just to make a screen cleaner.

For implementation:

1. Record the affected task and its current behavior.
2. Change the minimum necessary structure, labels, hierarchy, and interaction behavior using established components and styles.
3. Check the normal path and relevant edge cases using [Validation](references/validation.md): honest state feedback, preserved input and navigation context, failure recovery, direct entry, keyboard access, mobile, and role differences. Selection or navigation must not imply saving or completion.
4. Compare the resulting UI with the task inventory. Confirm previously available functions remain reachable.
5. Report what was actually verified; identify untested behavior and any required user study.

For research or low-confidence choices, choose a lightweight validation method from [Validation](references/validation.md). Avoid inventing user-test results, conversion impact, or measured task-speed improvements.

## Deliverable

Match output to the user's request. For a focused question, give one recommended change and its rationale, not a giant audit. For a substantial review or reorganization, use this compact format:

1. **Goal and current user task:** Role, desired outcome, and relevant assumptions.
2. **Key findings:** An issue table with task, severity, evidence, impact, and fix, in priority order.
3. **Proposed structure:** Before/after section order or navigation tree; primary, supporting, and secondary content.
4. **Pattern decisions:** Explain tabs versus accordions versus filters versus separate pages only where the choice is material.
5. **Acceptance checks:** Testable tasks, important interaction states, and any unknowns requiring evidence.

In implementation mode, include changed files and checks performed, rather than repeating the whole proposal. Use a diagram or wireframe only when it makes the proposed structure clearer or the user requests one.

## Non-goals and boundaries

- Do not turn a structure audit into a brand refresh, SEO campaign, animation pass, or performance project.
- Do not use aesthetic uniformity to erase necessary distinctions between task states or risk levels.
- Do not use arbitrary rules such as "three clicks," "seven menu items," or "one button per page" as pass/fail thresholds.
- Do not optimize a dashboard by hiding information that must be compared together.
- Do not silently alter permissions, business rules, calculations, analytics semantics, or destructive actions.
- Do not force speculative hooks, browser dependencies, or new UI libraries. Use available tools when they genuinely help.

## Reference routing

- **Choosing a UI organizational pattern:** [Pattern selection](references/pattern-selection.md)
- **Severity, Nielsen-style review, usability checks:** [Heuristic audit](references/heuristic-audit.md)
- **Task-first operational dashboards, tables, filters, forms:** [Dashboards, tables, and forms](references/dashboards-tables-forms.md)
- **Testing assumptions, acceptance criteria, confidence:** [Validation](references/validation.md)
- **Worked example of conflicting stakeholder requests:** [Worked example](references/worked-example.md)
- **Source attribution and deliberate adaptations:** [Source notes](references/source-notes.md)
