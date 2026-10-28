# Task-first dashboards, data tables, forms, and settings

Use when an interface mixes operational work, reporting, data records, and configuration. An overview is useful only if users can identify what requires attention and reach the work without searching through unrelated controls.

## Contents

1. Classify the dashboard
2. Operational task hierarchy
3. Metric and activity design
4. Tables and lists
5. Forms and date constraints
6. Settings and template editing
7. Role differences and responsive layout

## 1. Classify the dashboard

**Operational:** The user monitors live state, exceptions, deadlines, and tasks they must act on now. Prioritize actionable items, owner/status, and urgency. A compact status summary can help but should not push the work queue out of view.

**Analytical:** The user explores results across time, segments, or causes. Prioritize a clear question, appropriate comparisons, time-range controls, and drill-downs. Do not fill the page with all available measures.

**Hybrid:** Separate the action queue from analysis by clearly labeled sections or destinations. Avoid a single ambiguous "Dashboard" page that mixes every function at equal weight.

Confirm which roles use the screen and whether their intent differs. One dashboard does not need to serve every role in the same default order.

## 2. Operational task hierarchy

A sensible starting order for an operational page is:

1. **Current work requiring a decision:** assigned items, pending approvals, due follow-ups, blockers, exceptions.
2. **Context for those decisions:** customer, amount, deadline, stage, owner, recent activity.
3. **Quick summary:** counts, trends, outcomes only when they change a user's next step.
4. **History, reporting, and settings:** reachable through clear local navigation or secondary sections.

This is a hypothesis, not a universal page template. Reverse or adapt the order for managers whose main task is monitoring trends rather than doing individual work.

Do not confuse workflow status and urgency. "Draft," "Sent," "Accepted," and "Expired" are lifecycle phases; "Needs attention" is a work queue that may draw from several phases. Show these concepts explicitly when both matter.

## 3. Metrics and activity

Before showing a metric, complete: "A user sees this in order to decide ____." If no concrete decision follows, deprioritize the metric.

- Show time range, units, definitions, and scope where they affect interpretation.
- Avoid duplicate-looking metrics from different versions unless version comparison is a deliberate user task; prefer a clear aggregate with drill-down.
- For activity history, distinguish **sent**, **first viewed**, **most recently viewed**, and **view count** only when events can actually be tracked reliably.
- If reporting quote opens, define whether the count means unique sessions, unique recipients, or raw events; don't present refreshes as unique interest without qualification.
- Never imply that a metric or notification exists when there is no supported underlying event source.
- Keep data needed for comparison together rather than segregating comparable numbers into separate tabs.
- Use visualizations for a question (trend, category comparison, composition); a table may be better for exact values and individual action.

Avoid all-or-nothing interpretation of an analytics chart: bar charts for discrete comparisons typically need a meaningful zero baseline; line charts can use bounded axes when honestly labelled and contextually justified. Never invent data.

## 4. Tables and lists

A good operational table should let the user scan, locate, compare, and act. Check:

- **Columns:** Make high-value identifiers, status, next action, and decision context visible. Add optional attributes only when a user can use them to decide something.
- **Column order:** Reflect task sequence rather than underlying data model.
- **Default view:** Choose for the role's current job. Expose filters and let users understand the selected status and period.
- **Sort and filters:** Offer date/priority/owner/status where relevant. The default must be visible, not mysterious.
- **Actions:** Make frequent row actions discoverable; reserve overflow menus for genuinely less frequent alternatives.
- **Empty and no results:** Distinguish "no records yet" from "filters exclude every record"; offer clear next actions.
- **Pagination / density:** Preserve keyboard and screen-reader navigation, maintain stable row identity and context.
- **Mobile:** Preserve the fields users compare. Consider compact rows, a dedicated detail route, or scrollable tables depending on the job.

A table with more columns is not inherently worse. Hiding a field used to qualify leads or choose priority may increase work more than it saves space. Ask which roles need the field, and whether it belongs in the default visible set.

## 5. Forms and date constraints

Place fields in the order users naturally complete a task. Group related inputs under descriptive headings. Keep required fields and current context visible. Validate as early as useful without punishing typing-in-progress. Preserve input on failure and provide specific recovery.

For temporal rules:

- A **new** future appointment may reject dates before today, respecting the app's timezone and lead time rules.
- An **existing** past appointment must often remain viewable or editable for correction and record integrity.
- Date constraints cannot substitute for server-side checks when the business rule matters.
- Avoid silently changing user-entered dates or timezones.

Use a wizard only when steps genuinely depend on previous answers or the task would otherwise be unmanageable. Let users review and revise earlier answers when safe.

## 6. Settings and template editing

An occasional settings screen should not compete with daily work. For dense configuration pages:

- Group settings by what they control, not implementation technology.
- Put frequently edited settings at a discoverable entry point for the role that edits them.
- Keep routine grouped settings collapsed when no one needs them simultaneously.
- Avoid default-opening a large help or configuration panel that pushes primary actions out of view.
- Display selected template, draft changes, save/discard state, and a clear cancel/close path.
- Decide whether selection survives navigation. If it does, show why and how to clear it; if not, reset without losing intentionally saved work.
- Label irreversible changes distinctly, with appropriate confirmation and recovery.

One screen can contain several related tasks, but distinct high-frequency workflows may deserve peer tabs or separate routes. A set of four accordions is not automatically better than one clear page with titled sections.

## 7. Roles and responsive layouts

Consider a salesperson, manager, and marketing administrator using the same application. A salesperson may start at pending proposals; a manager at performance trends; an administrator at templates. Prefer stable shared navigation and role-specific defaults or shortcuts over unrelated products disguised as one dashboard.

For access controls, adapt only presentation. Do not assume role-specific ordering authorizes data access changes. Record which view or action is unavailable to each role and verify permission checks remain intact.
