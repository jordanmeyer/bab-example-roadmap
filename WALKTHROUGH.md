# Launch Ledger: predict, test, explain

This is a maintainer-built simulated teaching example. The exercises below have model-derived answers, not evidence of novice learning or screen-reader usability. [Build story](BUILD-STORY.md) links the original brief and planning history.

## A five-day delay is not a five-day launch delay

Before changing anything, predict what happens if Packaging takes five extra days. Open **Load a teaching scenario**, read the replacement notice, then load the packaging-delay example. Compare changed tasks and the two controlling chains. Explain why the launch moves three days, and name one condition this answer assumes.

<details><summary>Answer and reconciliation</summary>

The original chain is Product validation5 → Supplier readiness10 → Pilot4 → Safety7 → Launch preparation1:27 days, Nov2 to Nov29. Packaging takes8 days after validation, finishing Nov15; Supplier finishes Nov17. Packaging therefore has2 days of scheduling float. Raising its duration to13 makes it finish Nov20, after Supplier. Design sign-off now gates Pilot and Sales. The controlling chain switches to Validation5 → Packaging13 → Design sign-off0 → Pilot4 → Safety7 → Launch1 → Ready0:30 days, finishing Dec2, one day after the Dec1 promise. The five-day task change consumes two days of float, then moves completion three days. The capacity warning remains a separate constraint; this date is not a resource-feasible promise.
</details>

## A management target does not release work

Predict the result of **Load supplier-release example**. Supplier readiness has an external earliest permitted start of Nov12, although Product validation ends Nov7. Find the five-day idle gap, then change the promised date to Dec10 and apply all edits. Does any task move?

<details><summary>Answer and reconciliation</summary>

Supplier occupies Nov12–21 and ends at the Nov22 boundary. Pilot then ends Nov26, Safety Dec3 and Launch/Ready Dec4:three days late against Dec1. Changing the promise to Dec10 leaves every task date unchanged and creates six days of buffer. The earliest permitted start constrains the schedule; the promise is a management comparison. The model assumes an external date is firm and counts weekends/holidays as calendar days.
</details>

## Repair a resource conflict without buying capacity

Restore the original example. Predict whether moving Sales materials to Nov21 will fix the six overloaded days without moving completion. Select Sales in the table or task dropdown, set earliest permitted start Nov21, and apply. Next load the resource-repair example, which moves Sales to Nov28 with capacities unchanged. Compare both date buffer and daily overload, not just the headline finish.

<details><summary>Answer and reconciliation</summary>

Nov21 is six days after Sales' original Nov15 start, within its seven days of float. Launch stays Nov29, but Sales0.6 overlaps Safety0.5 for six days:1.1 people needed against1. The first move is dependency-feasible and still not staff-feasible. Starting Sales Nov28 waits until Safety finishes. Sales ends Dec4 and Launch/Ready Dec5. All overload clears with unchanged capacities, at the cost of a launch six days later and four days after the promise. The app diagnoses this hand-worked repair; it does not search for an optimal allocation, split tasks or model overtime.
</details>

## Sign-off must actually gate work

Restore the example. Predict the effect of setting Design sign-off's earliest permitted start to Dec4. Apply, compare Pilot, Sales, Ready and the headline. Then restore and delay only Ready to Dec4. Explain the difference.

<details><summary>Answer and reconciliation</summary>

Delayed Design sign-off releases Pilot and Sales on Dec4. Pilot ends Dec8, Safety Dec15, Launch/Ready Dec16. Every task is an ancestor of Ready in the supplied example, so Ready and all-work completion agree. Delaying only terminal Ready instead leaves Launch ending Nov29 and changes overall completion to Dec4. Imported/custom dependency edits can create different terminal work: the headline always means all tasks and milestones complete. A task name alone never creates a dependency.
</details>

## Complete editing and recovery task

Use only keyboard controls: follow View dates and capacity, open the exact table, activate Packaging design, and confirm focus enters its task-name editor. Make Product validation depend on Launch preparation, apply, read the cycle error, and recover the last valid schedule. Change capacity to1.6 and verify dates stay unchanged while overload clears. Export the applied plan, reload, and import the file; compare name, dates, capacities and dependencies. Export contains the current plan, not the comparison baseline. Keep the file before leaving this tab.

For an actual screen-reader check, repeat those steps with the reader running, announce the paused/error and recovery states, read the exact task table and changed-task list, and verify focus after table-to-editor selection. Record reader/browser/version, what was announced and any confusion. Keyboard inspection alone is not a screen-reader pass.

For an actual novice walkthrough, ask a person who has not used the app to interpret the default, predict the packaging delay, recover from the cycle and state one limitation without coaching. Record their answer and any revision needed. No completed novice session is claimed here.

## Optional extension: working-day calendars

Before writing code, choose which weekends and holiday jurisdiction to exclude, whether milestones can fall on non-working dates, and how resource capacity behaves then. Derive tests across a weekend, holiday and year boundary. Keep the current calendar-day model unchanged until those rules are explicitly agreed. This is a student extension, not a hidden change to this example.
