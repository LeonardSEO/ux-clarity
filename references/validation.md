# Validate structural UX decisions

Use this reference when proposing a major information-architecture change, comparing ambiguous organizational patterns, or verifying an implementation. Prefer observing real task completion over counting clicks or declaring a design attractive.

## Contents

1. Match method to uncertainty
2. Task-based acceptance criteria
3. Lightweight test designs
4. Evidence and reporting
5. Implementation regression checklist

## 1. Match method to uncertainty

| Uncertainty | Useful method | Evidence to collect |
| --- | --- | --- |
| Users do not recognize category labels | Card sort, label prediction, short interview | Terms participants choose and where they expect each item |
| Users cannot find a feature | Tree test or first-click task | Success and wrong paths, backtracking, hesitation |
| New page hierarchy feels overwhelming | Moderated task walkthrough | Whether people locate the next action and finish unaided |
| Tabs versus sections | Task comparison with both prototypes | Completion errors, time, switching behavior, comparisons missed |
| Priority differs by role | Observe representative role-specific workflows | Most frequent next actions, urgent exceptions, consequences |
| Filters are confusing | Test initial state, combined filters, and reset | Whether users understand active constraints and result counts |
| Changing code may break behavior | Browser or component interaction test | Normal, failure, cancel, keyboard, responsive, and permission states |

A small number of moderated participants can reveal important usability issues; larger samples are needed when estimating population-level success rates. Do not prescribe a fixed participant count as universally sufficient or statistically conclusive.

## 2. Task-based acceptance criteria

Write criteria around a user-visible outcome, not implementation details. Good examples:

- From the main work page, a sales user can locate a pending proposal and reopen it without searching unrelated sent proposals.
- A user can compare two relevant values in the same view without toggling back and forth or memorizing one value.
- A user who selects an email template can cancel editing and return to a neutral state without a page reload.
- A user filtering by time period can see the active range and reset it to the default.
- A user cannot create a new appointment before the allowed date, but can still inspect historical appointments.
- A keyboard user can operate tabs, disclosures, filters, and cancellation controls with visible focus.
- A role without access to an action cannot reach it through a new shortcut or route.

Each check should identify the start state, action, expected UI state, and whether it was tested.

## 3. Lightweight test designs

**First-click check:** Start a user on a representative landing page. Ask for a concrete outcome without naming the target control ("Find the proposal that needs to be sent next"). Record first click and whether they arrive correctly. An incorrect first click can indicate grouping, labeling, or prominence issues.

**Tree test:** Show a text-only navigation tree and give realistic findability tasks. Test the structure separately from visual design. Note success, detours, and ambiguous categories.

**Card sort:** Ask target users to group real tasks or content items and name the groups. Compare outcomes with the proposed taxonomy. A handful of sessions is exploratory evidence, not a statistically precise claim.

**Operational walkthrough:** Observe a representative user as they find their next task, decide which item matters, complete the action, recover from an error, and return to their work queue. Avoid teaching the new navigation during the trial.

**Before/after check:** Use equivalent tasks, devices, and starting states when comparing designs. If data is too sparse, report qualitative observations, not fabricated percentages.

## 4. Evidence and reporting

Use three evidence levels:

- **Observed/reproduced:** Actual browser, recorded test, or direct UI interaction.
- **Reported:** Stakeholder or user feedback, not independently tested.
- **Hypothesized:** Proposed from code inspection, screenshots, or best practices.

For each proposed change, record the problem it solves, the alternative considered, any risk of hiding required content, and the validation condition. Do not treat a stakeholder's preferred layout ("use three tabs") as proof that tabs are the correct pattern; test the underlying problem ("my primary actions are hard to find").

If user behavior is not measured, avoid specific claims such as "30% faster" or "guaranteed 10/10 usability." If only code was reviewed, say so. Distinguish a successful unit test from demonstrated user comprehension.

## 5. Implementation regression checklist

Check only applicable items. Do not invent dependencies or tasks unrelated to the change.

- Primary actions remain reachable and clearly labeled.
- Visible copy contributes to the task rather than repeating headings or obvious controls. Decision-critical information stays visible at the relevant action; secondary explanations remain discoverable and operable by keyboard and touch.
- Global and local navigation names remain consistent.
- Active tab, selected filter, and disclosure state are visible.
- Important comparisons are not split across mutually exclusive views.
- Data identity, versioning, event definitions, and calculations remain correct.
- Role permissions and protected routes are unchanged.
- Direct URLs, refresh, and browser back lead to understandable states, including invalid or unavailable destinations. Shareable view state is restored where appropriate.
- Valid input and drafts survive failed saves or submissions; retry does not duplicate the operation. Discard, cancel, and warnings about unsaved work match what will actually be lost.
- No surprise state survives page transitions without an obvious indicator or clear action.
- Selection, focus, saving, saved, and completion remain distinct; navigation or preview does not trigger business completion.
- Empty data, no matches, load failure, and denied access have distinct, honest recovery paths. Background refresh preserves usable context when safe.
- Returning from detail restores useful filters, sorting, list position, selection, and focus without reviving invalid state.
- Keyboard, focus, touch, zoom, and small-screen order remain usable; dragging has a non-drag alternative.
- Long labels, translations, large values, and dense controls do not clip essential content or create unintended page overflow; scroll ownership is clear.
- For reusable builders or templates, create a fresh item, configure it, save, reopen, and complete its public flow in a safe test context. A copied item or editor screenshot alone does not establish reuse. Do not send real submissions or trigger external effects without authorization.
- Existing design tokens, typography, and components are reused unless an exception is justified. Where an approved product reference exists, compare applicable normal, empty, and narrow views, including long labels, for hierarchy, surfaces, and text density without forcing different tasks into the same layout. A successful build does not establish visual agreement.
- Automated checks are run when available; limitations are disclosed.

Conclude with: **verified**, **not verified**, and **requires user observation**. Never collapse these categories into one claim that UX has been proven better.
