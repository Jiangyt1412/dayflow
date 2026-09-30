# Changelog

[简体中文](CHANGELOG.zh-CN.md) · [Open DayFlow](https://jiangyt1412.github.io/dayflow/)

## 1.5.6 — 2026-10-01

- Reduced late-bedtime and late-night meal dots from 8px to 5px in diameter. Sleep and Meals now share muted mauve, warm brown and soft burgundy accents, with pale gray night-hour bands.
- Replaced Meals' cross-date curves with individual horizontal marks for every regular meal. A thin vertical line joins each day's earliest and latest regular meal. Intermediate meals are included; a single-meal day has one mark and no connector. Night meals remain small independent dots and never extend a regular eating window.
- Marks narrow in dense date ranges. Kept the full-range layout, white background, dashed grid, forward clock axis, configurable night hours and accurate date-based touch/keyboard tooltips. The tooltip and data table now include every regular meal time.
- Sleep retains its smooth connected paths, timestamps, thresholds and calculations. No saved-data or backup migration; dependency versions and the lockfile are unchanged.

### Verification

157 unit/integration tests and all 49 production browser tests passed (2.3 minutes). TypeScript and the production builds passed. See [QA.md](QA.md).

## 1.5.5 — 2026-09-30

- Sleep's late-bedtime markers and Meals' late-night markers are now burgundy round dots (#843b4a), replacing the crosses. Regular points and their smooth connected lines keep their existing colors.
- Updated the meal legend, chart hints and calculation notes to describe the burgundy dots. Date matching, full-range width, gray night-hour bands and time thresholds remain as in 1.5.4.

### Verification

156 unit/integration tests and all 48 production browser tests passed (2.2 minutes). TypeScript and the root production build passed. See [QA.md](QA.md).

## 1.5.4 — 2026-09-30

- Meals uses the same horizontal chart margins and date-axis padding as Sleep, giving the curves and markers more width without adding horizontal scrolling.
- Fixed a real date-tooltip mismatch: a sparse night-only Scatter dataset could clamp the active date index, making later dates repeatedly show an earlier day's records. Night crosses now use reference marks on the shared full-date axis; the tooltip resolves records from that axis date.
- Date tooltips remain visible for night-only days and days with no regular meals. Night markers, regular points and empty date positions all use that day's records. Smooth curves, Sleep-matching colors, white dashed backing and gray night bands remain.

### Verification

156 unit/integration tests and all 48 production browser tests passed (2.2 minutes). TypeScript and the root production build passed. See [QA.md](QA.md).

## 1.5.3 — 2026-09-30

- Meals timing now fits the complete selected date range into the card without horizontal chart scrolling. The 7/30/90-day, all-time and custom ranges remain available; regular-meal curves remain smooth.
- Matched Sleep's purple and warm yellow-brown line colors. The chart has a white background and dashed grid; only the configured late-night hours are shaded gray, with dark-gray crosses for each night record.
- Replaced the ambiguous “Late-night × · —” tooltip row with “Late-night meals · No records” when that date has none, or the recorded times when it does. The legend and hint explain the cross and shaded hours.
- Retained plot padding so midnight, 23:59 and first/last-date crosses stay inside the chart. The standard clock axis replaces the former fixed scrolling rail.

### Verification

156 unit/integration tests and all 47 production browser tests passed (2.2 minutes). TypeScript and the root production build passed. See [QA.md](QA.md).

## 1.5.2 — 2026-09-30

- Corrected Sleep & wake: all bedtimes stay on the original smooth line, in the original color. A late bedtime changes only from a round dot to a cross. Wake times, axes and table values are unchanged. This replaces 1.5.1's separate, disconnected late-bedtime series.
- Meals now keeps only the Late-night eating summary above the chart. Removed the first/last eating time, total count and daily-average summary cards.
- Redesigned the eating-window chart with cream daytime and muted lavender night bands, smooth regular-meal curves and a horizontally scrollable date canvas with a fixed left-hand time scale. Night records remain individual crosses without connecting lines. Added horizontal and vertical plot margins so midnight, 23:59 and first/last-date crosses stay fully inside the plot. Chart swipes scroll dates instead of changing Insights sections when the chart overflows.
- Removed the native focus outline around the dialog container when returning from a record editor to Your records. Focus restoration and visible keyboard focus on controls remain.
- No saved-record, preference-threshold, database, backup, icon or haptic changes.

### Verification

156 unit/integration tests and all 47 production browser tests passed (2.1 minutes). TypeScript and the root production build passed. See [QA.md](QA.md).

## 1.5.1 — 2026-09-29

- Sleep & wake marks late bedtimes with separate crosses. These records are excluded from the bedtime connecting line; wake times keep their usual line. Tooltips, the legend and the data table identify late bedtimes separately.
- The display threshold follows Settings → Preferred bedtime, falling back to 00:00 when it is unset. Equality is not marked late. Clock comparisons use a noon-to-noon cycle, so after-midnight sleep follows the preceding evening and afternoon naps are not treated as late relative to an evening target. This is a chart convention based on a personal preference, not a medical definition of staying up late.
- Changing Preferred bedtime updates the markers; sleep timestamps, durations, averages, variability and backups remain unchanged. Meals and record-history improvements from 1.5.0 remain included.

### Verification

156 unit/integration tests and all 46 production browser tests passed. TypeScript and the production build passed. See [QA.md](QA.md).

## 1.5.0 — 2026-09-29

- Meals and Hygiene charts start on the first recorded date inside the selected range. The 7/30/90-day and custom choices remain available. Later empty dates and gaps remain visible; calendar views, summaries and average-per-day denominators still use the complete selected range. Drinks do not start the eating chart.
- Today → Your records now offers All, Sleep, Meals and Hygiene filters, plus an activity filter for Hygiene. Saving, cancelling or deleting a record returns to the same record list and filter. Opening an editor directly from Today still returns to Today.
- The eating-window chart separates regular and late-night eating: a light regular-hours band, darker late-night bands, lines for first/last regular meals, and an individual cross for each late-night record. Night records never join the regular lines. The time axis runs from 00:00 at the top to 24:00 at the bottom.
- Night classification follows Settings → late-night window (default 23:00–05:00, start included and end excluded), rather than the record's meal-type label. Custom windows also control shading. Tooltips and the data table expose regular times and every late-night time separately.
- No database, saved-record or backup-format migration; no icon or haptic changes.

### Verification

153 unit/integration tests and all 45 browser tests passed. TypeScript and the production build passed. See [QA.md](QA.md) for coverage and physical-device limits.

## 1.4.3 — 2026-09-24

- Added a 32px gutter between Insights panels during a swipe, with each panel clipping its own content so labels and cards do not run together.
- Resting and preview panels now use the same formatting and width. Hidden charts keep their measured layout and DOM nodes rather than collapsing to zero size. A long-to-short section transition includes the expected scroll-limit adjustment in the animation to avoid a separate landing snap.
- Expanded section swipes to text, cards, ordinary charts, pie charts, buttons and the page heading. Taps retain their actions; a horizontal drag does not also activate the touched button or pie slice. Native editing controls, actual horizontal data scrollers, text selection, dialogs and the screen-edge navigation area keep their own gestures.
- Removed the empty date placeholder above Focus and Notes. Date-range captions now belong to the four sections that use them.
- Task, focus-record and other shared editor dialogs now lock the background document while open, contain scroll chaining, support nested dialogs, and restore the previous page position on close. Insights swipes also stop while a modal is open.
- No changes to saved records, database identity, backup format, icons or haptics. Physical iPhone gesture feel and keyboard behavior remain unverified.

### Verification

148 unit/integration tests and all 41 production browser tests passed (1.9 minutes). TypeScript and the root production build passed. Deployment verification is recorded separately.

## 1.4.2 — 2026-09-24

- Switching between Today, Tasks, Focus, Insights and Settings now replaces the current history entry while preserving the page URL and query parameters. App navigation no longer adds a browser-back step for every section. Direct links, reloads, keyboard activation and existing browser history still work. Older history entries are not erased, and this does not disable the operating system’s edge gesture.
- Insights now moves the current and adjacent panels together in one continuous transition. Adjacent charts are prepared when a swipe starts, and movement uses one transform update per animation frame. Removed the sequential slide-out/fade and separate entrance animation; retained short-drag recovery, gesture exclusions, draft/filter persistence and Reduced Motion.
- Verified Insights section swipes while offline, without document, script or stylesheet requests. This is a local interface transition, not a page download. Physical iPhone frame rate and gesture feel remain unverified.
- No changes to saved records, database identity, backup format, app icons or haptics.

### Verification

148 unit/integration tests and all 36 production browser tests passed (1.7 minutes). TypeScript and the root production build passed. The separate `/dayflow/` build and publication are recorded in QA and deployment verification.

## 1.4.1 — 2026-09-24

- Removed the Daily / Weekly / Monthly grouping selector from Hygiene. The Insights date-range selector is now its only time control, and the Personal care chart plots daily counts within that range.
- Insights content now follows a horizontal finger drag. Short, cancelled and end-of-list drags return to rest; completed swipes use a brief outgoing slide/fade and a longer eased entrance. Motion is applied to the existing panel without rerendering charts on every touch event. Vertical scrolling, interactive charts, form controls, screen-edge gestures and Reduced Motion remain supported.
- Removed the duplicate history icon from Today’s Personal care card. The page-level Record history button still opens saved records for editing.
- No changes to stored records, backups, focus timing, app icons or vibration behavior.

### Verification

148 unit/integration tests across 15 files and all 34 production browser tests passed (1.9 minutes for the browser suite). TypeScript and the root production build passed. The `/dayflow/` deployment build passed with 35 precache entries. Real iPhone motion feel and frame rate have not been measured.

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
