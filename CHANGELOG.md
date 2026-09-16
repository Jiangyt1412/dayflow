# Changelog

[简体中文](CHANGELOG.zh-CN.md) · [Open DayFlow](https://jiangyt1412.github.io/dayflow/)

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
