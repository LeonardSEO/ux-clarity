# Worked example: a crowded operational sales application

This fictionalized scenario demonstrates the expected level of judgment. It is not a universal dashboard template and should never be output verbatim for a different product.

## Context

An internal sales application contains a work queue, proposals, follow-up reminders, message templates, reporting, and date-based appointments. A marketing stakeholder reports that key actions are hard to find and recommends adding tabs or accordions throughout. The primary sales role prepares and sends proposals; marketing occasionally edits email templates; managers monitor outcomes.

## Input observations

1. An insights page displays multiple rows that look like duplicate configuration versions. Users want period filters and consolidated results.
2. On the proposals page, "Sent" appears before "Draft / Preparation" although salespeople normally work on drafts first. The overview omits some useful context such as estimated amount.
3. On follow-up, an expanded email-history panel pushes "Schedule a reminder" and "Automatic reminders" below the fold.
4. On communications, the template editor is far down the page; all automation settings are expanded.
5. A selected template remains expanded when the user returns and there is no clear cancel/clear action.
6. An appointment date picker accepts dates before the allowed scheduling window.

## A good analysis differentiates three things

- **Confirmed functional issues:** Missing cancellation, invalid new appointment selection, and unexpected persistence are candidates for verification and targeted fixes.
- **Task-priority issues:** Draft work and template editing should be more prominent **for the roles that do that work**; another role may reasonably want another default view.
- **Unsettled pattern decisions:** Consolidating versions, adding three tabs, or collapsing every group are proposed solutions, not established requirements. First determine the object model and tasks.

## Example recommendation table

| Area | User problem | Suggested structural change | Reason / qualification | Test |
| --- | --- | --- | --- | --- |
| Insights | Duplicates make results hard to interpret | Use a consolidated summary with date-range filter and version drill-down | Preserve versions if their identity or metrics differ; clarify aggregate definition | Can users tell aggregate results from version history? |
| Proposals | Daily work competes with history | Default the sales role to "Needs action" or "Draft / Preparation"; keep Sent reachable | A role-specific queue may be clearer than reversing a global order for everyone | Can a salesperson resume the next quote? |
| Proposals | Users cannot judge priority from the list | Add only the high-value decision columns (e.g., amount, region) | Confirm users actually use the fields and permission allows them | Can users select the correct item without opening each record? |
| Follow-up | Main actions pushed out of sight | Surface reminder actions first; move history to secondary section or accordion | Use tabs only if activities are genuine peer workflows, not simply because there are three sections | Are reminder actions immediately discoverable? |
| Communications | Template editing is obscured | Put the editor's entry point near the top for the marketing role; group automated settings compactly | Do not make every setting collapsed if frequent editing requires repeated disclosure | Can marketing find and edit a template unaided? |
| Template editing | User cannot escape selected state | Provide Cancel/Clear with consistent state reset or explicit draft persistence | Ensure unsaved edits cannot silently disappear | Select, cancel, return, and verify state |
| Appointments | Invalid dates can be entered | Constrain new appointments by business rules; validate on server too | Preserve legitimate viewing/editing of past appointments | Test today, yesterday, timezone boundary, historical edit |

## Pattern selection example

Consider the follow-up page. Three proposed tabs are not automatically better than three titled sections:

- If these are independent frequent tasks with distinct UI and long bodies, named peer tabs can reduce clutter.
- If all three require shared controls or comparisons, keep them on one page with visible task shortcuts.
- If the third area is historical context only, a labelled collapsed detail section is more appropriate than a peer tab.

A good recommendation names the most likely pattern **and** states the user behavior that would confirm or overturn it. Avoid "just add three tabs" as a substitute for diagnosis.

## Example acceptance checks

- A new sales session opens on a task-relevant queue without hiding other statuses.
- Follow-up scheduling is discoverable without opening unrelated communication history.
- Relevant table fields are scannable at normal desktop and narrow viewport widths.
- A template edit can be abandoned without saving or carrying stale UI state to another page.
- Any aggregation of versions preserves meaning and avoids double counting.
- No role acquires access to newly surfaced actions it lacked before.

## Example concise conclusion

"Reorder and group the work by task priority before adding more navigation. Give active sales work the first position, keep reports separate from workflow controls, and allow temporary selections to be cancelled. Validate the proposal/status model before combining rows. Tabs may help only where the user is choosing among peer workflows; accordions are better for secondary details."
