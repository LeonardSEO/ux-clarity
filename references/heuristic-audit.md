# Practical usability heuristics and issue triage

Apply this reference when diagnosing confusing interfaces, validating a proposed hierarchy, or reviewing an implemented change. A heuristic is a lens for finding possible problems, not proof of a usability failure. Anchor findings to a real task, interface state, or observed user difficulty.

## Contents

1. Ten usability lenses
2. Fast orientation check
3. Severity and evidence
4. Common trade-offs
5. Audit reporting
6. Interaction and accessibility checks

## 1. Ten usability lenses

The ten lenses are based on widely used Nielsen usability heuristics. Rephrase and apply them to the observed interface rather than copying a generic checklist into a report.

| Lens | Questions to check | Example problem | Example direction |
| --- | --- | --- | --- |
| 1. System feedback | Does an action visibly change the UI? Can the user tell pending from saved or failed? | A selected template stays open without indicating its current state | Show selection, allow cancellation, confirm persistence and errors |
| 2. User language | Do labels reflect concepts users recognize? Is information ordered like the underlying task? | "Configuration version analytics" means nothing to a salesperson | Label views for the decisions they support |
| 3. User control | Can users undo, cancel, navigate back, or reverse a temporary selection? | An editor cannot be dismissed without reloading | Add clear cancel/close and restore the prior state |
| 4. Consistency | Do repeated controls, terms, lists, and navigation behave predictably? | A "Draft" chip filters on one page but opens a modal on another | Reuse the established meaning or make the difference explicit |
| 5. Error prevention | Can the interface prevent routine slips and invalid choices? | New appointments permit a past date | Constrain new appointments; handle edits to historical records separately |
| 6. Recognition over recall | Are available options, status, context, and history visible when needed? | Users must remember a quote's stage to know where it is | Display its status and relevant context in the list |
| 7. Flexibility | Can both common and advanced workflows be efficient without clutter? | Experts repeat five steps for every item | Provide safe shortcuts, bulk actions, and contextual detail where justified |
| 8. Relevance and focus | Does displayed information support the present task? Is content grouped and scannable? | Every metric and email setting is expanded on the same page | Emphasize active work and progressively reveal secondary detail |
| 9. Recovery | If something fails, can users understand it and continue without losing work? | Error message removes unsent draft text | Preserve input, explain what happened, offer retry or recovery |
| 10. Available help | Is task-specific guidance discoverable at the point of uncertainty? | Unexplained metric or irreversible business operation | Add precise labels, inline explanation or linked documentation |

Treat information architecture as cross-cutting: a misplaced feature can violate multiple lenses. Do not count the same root problem as five independent issues; group its consequences under one actionable finding.

## 2. Fast orientation check

For any important landing page or deep link, inspect whether a first-time or returning user can answer:

- What product or workspace am I in?
- What page and task context am I in?
- What is the most relevant action available here?
- Where does each main option lead?
- How do I navigate to related work or back to a known place?
- Can I find a specific record or feature through a clear route or search when appropriate?

This is an adapted orientation check, not a demand to place search or breadcrumbs on every screen. Use predictable headings and selected navigation states; test ambiguous labels rather than declaring them self-explanatory.

## 3. Severity and evidence

Assign each finding a severity based on likely task consequences, not the aesthetic strength of the reviewer's opinion.

| Severity | Meaning | Typical action |
| --- | --- | --- |
| **0** | Not a substantiated usability issue | Do not list as a defect |
| **1** | Cosmetic inconsistency with negligible task impact | Optional cleanup |
| **2** | Noticeable effort, hesitation, or recoverable error | Schedule improvement |
| **3** | Repeated confusion, major delay, or frequent task failure | High-priority fix |
| **4** | Task blocked, dangerous misrepresentation, or no viable recovery | Resolve before further rollout |

Weight impact, frequency, persistence, affected roles, and severity of mistakes. A rare but irreversible destructive action can outrank frequently annoying spacing. Show confidence:

- **Verified:** Reproduced in the actual interface, test, or direct observation.
- **Reported:** User or stakeholder described behavior, not yet reproduced.
- **Inferred:** Potential issue predicted from code, screenshots, or structural reasoning.

Do not convert these labels into invented percentages. Do not present a single aggregate UX grade or a measured success claim without collected data.

### Suggested finding template

```text
Location: Quotes > Drafts, sales role
User task: Prepare the next quote for sending
Evidence: Reported that Drafts is hidden behind a different default tab
Heuristic: Recognition / task relevance
Severity: 2 (provisional; frequency unknown)
Recommendation: Default sales users to the actionable queue; preserve named views
Alternative considered: Global tab reorder (would affect other roles)
Check: Ask sales users to locate and resume their next pending quote
```

## 4. Common trade-offs

| Tension | Resolve by |
| --- | --- |
| Simplicity versus discoverability | Keep high-value actions visible; collapse optional detail only |
| Role priority versus global consistency | Keep stable navigation labels and structure; customize default view or shortcuts by role when justified |
| Efficiency versus error prevention | Use constraints and reversible actions; confirm high-consequence operations rather than every small edit |
| Minimalism versus required data | Keep necessary comparisons and disclosures; reorganize instead of deleting |
| Progressive disclosure versus excessive clicks | Reveal complexity at the right point; do not force repeated opening for frequent work |
| Familiarity versus innovation | Follow known interaction conventions unless a tested benefit justifies deviation |
| Speed versus accurate feedback | Acknowledge promptly, but do not announce server success before it occurs |
| Compactness versus accessibility | Use readable labels, keyboard navigation, focus states, and content adaptable to zoom and small screens |

Do not invoke arbitrary numerical rules such as a mandatory three-click maximum or a strict seven-item menu threshold. They are weak substitutes for testing actual tasks.

## 5. Audit reporting

For each issue provide a screen, job, observable symptom, evidence level, severity, fix, trade-off, and acceptance check. Consolidate related symptoms into a root cause where possible. Prioritize three to five changes for an ordinary single-page review, more only when the user asks for a thorough audit.

For conflicting stakeholder requests, distinguish:

1. An observable usability defect (e.g., no cancel control).
2. A plausible priority preference (e.g., Drafts should be first for one role).
3. A product decision needing evidence (e.g., whether three workflows deserve separate top-level routes).

Do not mechanically implement every requested tab, accordion, or new page. Preserve the stakeholder's actual problem and choose the pattern that solves it.

## 6. Interaction and accessibility checks

Check applicable states, including first load, empty results, filtered results, validation failure, save pending/success/error, navigation away, and re-entry. When changing structure or visibility, test:

- Every primary action remains reachable by mouse, touch, and keyboard.
- Focus is visible, logical, and returned appropriately after temporary UI closes.
- Labels and selected/current state are perceivable without color alone.
- Semantics for tabs, accordions, links, buttons, and tables match behavior.
- Text can reflow at narrow widths; comparisons remain possible.
- Error feedback identifies the problem and recovery without discarding inputs.
- A user can reverse or cancel a temporary edit and knows whether changes were saved.
- Navigation preserves expected history and does not silently lose critical input.
- Selected, focused, available, editable, saved, and completed states remain distinct. Navigation or preview selection must not advance a business process; success feedback and enabled actions follow the authoritative state.
- Empty data, no filter matches, loading failure, and denied access are distinguishable. A failure must not appear to be a successful empty result or silently substitute misleading data.
- Pending actions acknowledge input and prevent duplicate submission without blocking unrelated work. Announce important asynchronous changes accessibly without repeating routine status.
- Dragging and essential hover interactions have discoverable keyboard and touch alternatives.

This review flags likely issues; use platform guidelines and actual accessibility testing for compliance claims. Do not claim WCAG conformance from code inspection alone.
