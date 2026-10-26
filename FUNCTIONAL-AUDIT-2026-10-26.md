# Functional audit — 2026-10-26

## Fixed
- Grocery bulk entry now defaults to automatic per-item classification instead of assigning every record the selected default “غير مصنف”. Explicit category overrides remain optional.
- Grocery entry splits Arabic conjunctions, commas and lines in both the manual service and Smart Capture.
- Bare known product lists such as “بيض وكندر” work without a command prefix. Kinder and common pantry/snack products have categories.
- Explicit multi-task lists and independently introduced task clauses create separate tasks; each resolves its own date and work/personal category.
- Explicit tasks mentioning a grocery remain tasks. Notes and negation stay intact during command splitting.
- Existing databases receive additional category options without changing their records.

## Automated verification
263 passing tests; zero failing. Includes original 192 command examples, existing behavioral checks, regression scenarios, and fresh-store create/edit/reload/JSON restore/undo checks for all 15 record types. Tests validate stored records, categories and relationships, not just parser outcome. Failure, duplicate, ambiguous input, financial, backup-conflict and persistence protections are included.

## Actual browser UI checks, isolated databases
Started with zero records at 127.0.0.1:5181/?qa=1; second empty origin localhost:5181/?qa=1 for restore.
- Typed exact user example “بيض وكندر” in Smart Capture: two records, ألبان and حلويات وتسالي; no clarification.
- Undid the insertion; repeated exact example in grocery page with default automatic category: two records with distinct categories.
- Marked eggs purchased: eggs alone appear in purchased filter; Kinder remains open.
- Submitted two tasks in one message, with today/tomorrow dates: work report and personal haircut task, no invented time.
- Work filter, task details, edit urgent, complete, and open/urgent counters verified.
- Created doctor appointment tomorrow 10:00 and saw it in calendar beside date-only task.
- Ambiguous oil request prompted clarification; cooking choice saved and cleared pending counter.
- Exported actual six-record test backup through UI; imported through file chooser into empty second origin; reloaded and verified persistence.
- Added account 1000 via editor, entered purchase 12 via Smart Capture; UI showed balance 988 and expense 12.

## Limits
All 15 record lifecycles were checked at service level; not every field combination of every editor was exercised through browser UI. Physical iPhone installation, Safari keyboard, OS notifications and airplane-mode behavior are not verified. Local rules do not provide general language understanding: unknown products remain preserved as غير مصنف without mandatory selection; ambiguous instructions still require clarification/review. Existing user records are not automatically rewritten or split. No production user records were accessed or reset.
