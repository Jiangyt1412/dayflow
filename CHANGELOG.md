# Changelog

[简体中文](CHANGELOG.zh-CN.md) · [Open DayFlow](https://jiangyt1412.github.io/dayflow/)

## 1.4.0 — 2026-09-24

- Insights now opens on **Focus**, followed by **Sleep, Meals, Hygiene, Tasks and Notes**. Swipe left/right over ordinary content to switch sections, or keep using the tabs. Section filters and unsaved Notes drafts survive these switches. Controls, charts, horizontal scrolling and browser screen-edge gestures retain their own interactions; section animation respects Reduced Motion.
- Added **Focus → Recent sessions → Add record** for missed sessions. Open any saved record to edit its start date/time, active hours/minutes/seconds, category, task and note. Completed tasks are available for linking. Tap the header **Save** to commit; closing does not save, and record notes no longer save on blur.
- Manual entries and timing corrections use one continuous active interval. Changing a saved start time or duration removes the original pauses, with a warning in the editor. Metadata-only edits retain the exact original intervals, pauses and milliseconds. New or corrected timing must have positive duration and finish at or before the current time.
- Saved task-name snapshots are retained when available. Saving or deleting an out-of-date record is rejected if another tab changed or deleted it. Record changes update task totals and Insights without changing the active timer.

### Verification

148 unit/integration tests across 15 files and all 32 production browser tests passed. Checks cover manual focus records, timing corrections, metadata-only precision, stale save/delete protection, active-timer isolation, swipe navigation, retained drafts and filters, gesture exclusions and narrow layouts. TypeScript, the root production build and the `/dayflow/` deployment build passed; the deployment build includes 35 precache entries. A separate development-demo preview was inspected at 390px and 320px; desktop checks do not establish physical iPhone behavior. No database identity or backup schema change. See [QA.md](QA.md).

## 1.3.1 — 2026-09-17

- Tap a Focus category slice or connected label to open a new pie showing that category's tasks, with a short fade and slide transition. Each task keeps a connected label with its time and share of the category total. This replaces the selected-slice highlight and the task list below the chart.
- Return with **All categories** or Escape. Keyboard navigation restores focus to the original category label; Reduced Motion skips the transition. Changing the date range or category filter returns to the category pie.
- Focus chart labels, axes, tooltips and data tables show hours and minutes for durations of at least one hour, such as **3h 40m**. Shorter durations use whole minutes; positive durations below one minute show **<1 min**. Partial minutes are omitted only from display. Saved timestamps, chart proportions and numeric CSV values retain their precision; minute-based inputs remain unchanged.
- Fixed an aggregation boundary where adding several short focus intervals as fractional minutes could display a full minute as less than one minute. Category and task totals now add milliseconds before converting to minutes.
- Removed the gray divider above the first task in the Tasks list. Separators between tasks remain, including after deleting or restoring the first task with Undo.

### Verification

119 unit/integration tests across 14 files and all 25 production browser tests passed. Coverage includes the task pie and return navigation, connected labels and proportions, range changes, reduced motion, duration boundaries and first-row styling after Delete/Undo. TypeScript and the production build passed. A separate development-demo preview was inspected at 390px and 320px; these desktop checks do not establish physical iPhone behavior. No database identity or backup schema change. See [QA.md](QA.md).

## 1.3.0 — 2026-09-17

- Added a sliding, pale-green selection indicator to mobile bottom navigation.
- Added Saving / Saved feedback to task, record, category and note saves. Focus controls now show pending actions and a brief play/pause icon transition. Success appears only after the write succeeds.
- Added short enter/exit animations to editor dialogs. Reduced Motion disables these animations and the moving navigation indicator.
- Tap a Focus pie slice or its connected label to highlight the slice, leader and label together. The list below shows each task's active minutes in that category for the selected date range, plus category time and percentage. Tap blank chart space, Clear selection or Escape to return to all categories.
- Added a 10-second Undo for the latest task completion, reopening or deletion. Undo remains available while navigating within the open app. Restoring a deleted task also restores its schedule and eligible focus links without replacing session times or notes. Importing or clearing data invalidates pending undo; refreshing does not retain the Undo prompt.
- Swipe a task left to reveal Delete. Even a full swipe only reveals the button; deletion requires a separate tap. Vertical scrolling remains available, and the existing editor Delete action is retained.

### Data details

Pie task minutes use completed active intervals clipped to the same date range as the pie; pauses are excluded. Sessions with no linked task have a separate row. Deleted tasks retain their saved names when available. Records that have only a saved name and no task ID are grouped by that name, so identical names cannot reliably identify different deleted tasks. No database or backup schema migration is required; transient undo tokens are excluded from JSON exports.

### Verification

95 unit/integration tests and all 24 production browser tests passed. Checks cover persistence before animation ends, native validation, navigation and reduced motion, cross-page undo, preserved schedules/focus, swipe-to-reveal, category selection, date-range task totals, keyboard reset and narrow layouts. TypeScript and production builds passed. Browser checks and desktop phone-width previews do not verify physical iPhone gestures or vibration. See [QA.md](QA.md).

## 1.2.1 — 2026-09-16

- Removed the browser's blue outline when tapping or clicking chart surfaces and internal SVG layers. Keyboard focus indicators and arrow-key chart navigation remain available.
- Sleep and meal clock axes now progress from earlier at the top to later at the bottom. Overnight sleep stays on a continuous timeline across midnight; duration and count axes keep their normal direction.
- Increased the gap between date and value labels in Sleep, Meals, Hygiene and Tasks charts.
- Added an independent date range to the Focus category pie: Last 7 days (default), Last 30 days, Last 90 days, All time and Custom range. Custom dates include both endpoints. Category filtering and connected slice labels remain available.
- Monthly hourly/daily charts, yearly trends and the four focus totals retain their existing periods. The pie's date range changes only the pie.

### Verification

87 unit/integration tests and all 19 production browser tests passed, including touch versus keyboard chart focus, overnight order, axis spacing at 320/390/768px, range totals, invalid dates and narrow-screen date fields. TypeScript and production builds passed. Desktop browser checks do not replace confirmation on a physical iPhone. No database or backup format change. See [QA.md](QA.md).

## 1.2.0 — 2026-09-16

- Added Notes in Insights for a daily journal, optional mood and personal status. Entries stay on the device and are included in JSON backups.
- Moved Focus to the second Insights tab. Replaced the overview with Notes.
- Redesigned Focus insights: today, this week, this month and all-time totals; category pie chart; scrollable hourly distribution; daily and January–December line charts.
- Focus charts use saved active intervals, split at local calendar boundaries. Pauses are excluded; the current unfinished timer is not included. Hourly data no longer requires a minimum session count.
- Show task names in focus history and session details. New sessions retain a task-name snapshot; deleting an existing task preserves names on its historical records.
- Clarified meal totals versus averages over all calendar days in the selected period, including days with no records.
- Removed the browser focus outline on the non-interactive page container and made disclosure tap highlights transparent. Interactive keyboard focus indicators remain visible. The exact source of the reported intermittent iPhone blue line has not been reproduced.
- Added versioned release notes, accessible from Settings → What’s new.

### Backup compatibility

JSON backups now use schema version 2 to include journal entries. Version 1 backups can still be imported. Import is a complete replacement: an old backup without journal entries also replaces current notes with an empty journal. Keep a copy of a backup before replacing local records; importing replaces the current dataset.

### Verification

74 unit/integration tests and all 17 production browser tests passed. TypeScript and the production build passed. See [QA.md](QA.md) for checks and device limitations. Browser automation does not verify physical iPhone vibration. Task switch haptics were confirmed by the user on the preceding release; ordinary Safari buttons still use visual press feedback.

## 1.1.1 — 2026-09-15

- Unified visual press feedback across navigation, action buttons, disclosure controls and selectable inputs. Optional vibration is enabled where the browser supports it.
- Reused the native task checkbox control for subtask haptics on supported iPhones.
- Added update checks on foreground and network recovery, a manual Check for updates button, and a visible version number.
- Validation: 52 unit tests passed; targeted browser checks passed. The user’s 14 passing browser tests covered the preceding task-animation release, not this subsequent update.

Earlier deployments did not display a version number and are not assigned retrospective version numbers here.
