# Pattern selection for clear information architecture

Use this reference when the user asks how a page or application should be arranged, or when a reviewer proposes tabs, accordions, filters, or a new route. Choose patterns based on the actual task and content relationship. Do not select patterns from personal style preference.

## Contents

1. Decision sequence
2. Pattern comparison
3. Information grouping and labels
4. Navigation, discovery, and orientation
5. Visibility and density
6. Responsive adaptation
7. Failure cases and reversibility

## 1. Decision sequence

1. Name the user's current task in a short verb phrase: "prepare a quote," "follow up a lead," "compare revenue," "edit email templates." Different jobs may belong in different places.
2. Decide whether the content is a **destination**, **view of one destination**, **attribute of a collection**, **optional detail**, **step in a process**, or **action**.
3. Identify what must remain visible together for comparison, safety, or a correct decision.
4. Consider count, complexity, user frequency, persistence, mobile space, and permissions.
5. Select the least complex pattern that preserves discoverability and orientation.
6. State the rejected alternative and why it loses in this case.
7. Define states: current/active, empty, filtered, cancelled, error, return, and responsive layout.

## 2. Pattern comparison

| Pattern | Choose when | Avoid when | Required usability behavior |
| --- | --- | --- | --- |
| **Separate page or route** | Distinct user job, complex workflow, deep navigation, linkable destination | Tiny option that belongs alongside its parent task | Descriptive title, context, clear entry/return, preserved work when navigating |
| **Tabs** | Small set of peer modes or mutually exclusive workflow views in one context | Users compare views side by side; unrelated destinations; too many or unstable tabs | Descriptive labels, obvious selected state, stable switching, accessible keyboard behavior |
| **Segmented control** | 2-4 tightly related display modes or compact mutually exclusive state | Larger navigation or complex content with separate identities | Immediate selection feedback, clear label and selected state |
| **Accordion** | Optional or secondary detail within a page; groups of infrequently changed settings | Primary action, critical status, mandatory instructions, or major navigation | Recognizable header, disclosure state, keyboard access, predictable reset/persistence |
| **Filter / facet** | Narrow a collection by independent attributes, date range, owner, province, status | Separating fundamentally different workflows; hiding high-priority actionable items behind unknown defaults | Visible applied filters, clear reset, result count, sensible default, URL/state persistence as appropriate |
| **Search** | Known-item retrieval among many records or topics | Covering up poor categories for common tasks | Useful labels, accessible results, no-results recovery, filter compatibility |
| **Summary + drill-down** | Overview decisions require detail only after an anomaly or selection | All detail is needed simultaneously for live operational decisions | Clear relationship between summary and detail, unambiguous navigation back |
| **Table** | Users scan, sort, compare, and act on many records with repeated attributes | Few rich items where visual recognition matters more than attribute comparison | Scannable labels, meaningful sort/filter, stable row actions, mobile fallback |
| **Card/list** | Small or variable items with distinct content; previews support recognition | Dense repetitive records needing column comparisons | Predictable hierarchy and action placement, avoid cards within cards |
| **Step-by-step form** | Inputs have real dependencies or a complex linear journey | Experienced users need to revisit and compare steps; arbitrary splitting increases friction | Progress, back, preserved values, clear validation, accessible recovery |
| **Inline edit** | Small reversible update in the current context | Destructive, high-consequence, or complex operation | Edit/save/cancel states, feedback, keyboard support, error preservation |
| **Modal** | Short, contextual interruption needed to finish the current task | A separate full workflow, long multi-step form, or navigational destination | Clear purpose, dismiss/cancel, focus management, return to trigger |

Never add a modal solely to hide clutter. Avoid nested tabs and nested accordions when clearer section grouping or a dedicated route can do the job.

### Tabs versus accordions: the decisive difference

- Tabs answer **"which peer view or mode am I using?"** and usually show one view at a time.
- Accordions answer **"do I need this supporting detail now?"** and reveal optional detail within the current view.
- If users must compare two contents, prefer the same view or side-by-side presentation, not separate tabs.
- If users repeatedly need hidden content to finish a frequent task, it is probably not secondary; show it by default.
- If a page has three distinct user jobs, consider separate routes or tabs depending on workflow depth and how often users move between them. Never assume "three items means three tabs."

### Tabs versus filters

A small number of named, stable workflow phases (e.g., "Needs action," "Sent," "Closed") can justify tabs. When statuses are numerous, combinable, or vary by project, use filters instead. If a role primarily works the pending queue, that view may be the default for that role; it should not silently replace the saved selection of another user.

### Sections versus new pages

Use sections when users need simultaneous context, short scanning, and frequent back-and-forth. Use a dedicated page when the subtask has its own state, deep workflow, many controls, or needs a shareable URL. Prefer contextual links over duplicating the same functionality in several sections.

## 3. Information grouping and labels

Group by the users' mental model and task lifecycle; do not mirror the codebase or internal organization. Common coherent groupings include:

- **Workflow stage:** Create -> review -> send -> follow up -> complete.
- **Object:** Quotes, customers, appointments, communications, each with its own coherent detail views.
- **Responsibility:** My assigned work, team's queue, reporting, administration, when roles differ.
- **Frequency:** Daily operational actions before occasional settings for the same actor.

Do not split a concept simply because it is stored in different tables. Do not merge records with different version identities or legal meanings merely because labels look duplicated.

For every label, ask whether the user can predict the destination before clicking. Prefer "Email templates" to "Configuration" when the content is email templates. Test ambiguous terms with users rather than assuming team terminology is universal.

Taxonomy health check:

- Clear home for each item and task.
- Important cross-links without duplicate actions or conflicting source of truth.
- No near-synonymous adjacent headings that make destination choice arbitrary.
- A structure that scales as records and categories grow.
- Meaningful depth instead of flattening everything into one enormous menu.

## 4. Navigation, discovery, and orientation

On each entry point, the user should be able to recognize:

- Where they are and the purpose of this page.
- What they can do now and which action is most relevant to their current job.
- What alternatives exist and where to find them.
- How to return to a familiar place without losing necessary work.

Use stable global navigation for significant destinations and local navigation for in-page modes. Show the current section and a descriptive page title; use breadcrumbs when hierarchy depth makes them useful, not automatically on every one-level screen. Preserve expected browser history and deep links.

Use search when collections are large or users commonly know what they want. Provide browse options to new users who do not know search terms. A zero-results state should guide correction rather than merely announce failure.

## 5. Visibility and density

Before hiding or removing an element, ask:

1. Does it contribute to the current decision or task?
2. Is it necessary to interpret another element, avoid an error, or compare options?
3. Is it needed rarely but hard to find elsewhere?
4. Would a different role or state require it immediately?
5. Is it a required disclosure, recovery action, or permission boundary?

Only hide after checking those questions. Use compact grouping, headings, alignment, and consistent spacing before assuming more containers improve clarity. The number of visible choices is not a scientific quality threshold; clear labels and coherent groups can make a richer screen usable.

Never force critical controls into an overflow menu without a reason. Multiple important actions can coexist when they have distinct labels and predictable hierarchy.

## 6. Responsive adaptation

Preserve the task order when moving from desktop to mobile. Stack secondary regions beneath the primary work; keep primary controls and context reachable. For data-heavy tables, prefer a tested horizontal-scroll table, a compact adaptive row, or a dedicated detail view based on comparison needs. Do not collapse so much content that users must open every record to compare one field.

Maintain keyboard and screen reader orientation, visible focus and selected states, and touch-accessible controls. Do not rely on hover for critical help or actions.

## 7. Failure cases and reversibility

- Show the user what is currently selected, including visible active filters and tabs.
- Provide clear **Cancel**, **Clear selection**, or **Undo** when an edit or selection can be dismissed.
- Decide intentionally whether navigation preserves a draft, resets a local disclosure, or retains a filter; apply the rule consistently.
- Prevent invalid choices where appropriate (e.g., new appointments cannot be scheduled in the past) while retaining legitimate historical edit/view states.
- Distinguish uncommitted local changes from saved server state. Do not claim "Saved" until confirmed.
- Do not count or display activity in a way that misleads the user; explain metric definitions when they affect decisions.
