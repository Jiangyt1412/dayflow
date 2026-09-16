# Validation report

## Version 1.2.1 — 2026-09-16

- `pnpm test`: **87 tests passed**, 11 files. Added 13 Focus range cases covering preset windows, inclusive custom boundaries, invalid dates, pauses, cross-midnight sessions, all-time aggregation, categories, DST and the maximum supported calendar year.
- `pnpm test:e2e`: **19 tests passed (36.9 seconds)** against a fresh production build. Includes the entire preceding 17-test regression suite and two new interaction tests. Browser launch used execution outside the macOS sandbox.
- New browser checks: touched SVG chart surfaces and focused child layers have no outline; Tab focus retains a visible 2px ring and arrow keys show the tooltip; overnight bedtimes appear above subsequent wake times; Meals clock ticks ascend top-to-bottom; count/duration axes retain their normal direction. Axis label separation is at least 12px on one axis at 320, 390 and 768px, with no page overflow.
- Focus browser checks: all five pie date-range options produce the expected saved-active-minute totals; inclusive custom dates, empty results, invalid/reversed dates, category filtering and connected labels; monthly controls do not change the pie or fixed-period totals. New date fields reuse the iPhone DateTimeInput wrapper and fit at 320, 390 and 768px.
- Independent in-app browser inspection at 390px used the isolated development demo database. It reproduced a blue outline on a focused Recharts internal grid layer (`g[tabindex=-1]`) before the final fix, and inspected the updated chart and custom-range pie layouts. Recharts also makes its root SVG focusable for keyboard navigation. Both layers are covered by the pointer-specific outline rule.
- TypeScript and root production build passed. Deployment uses the separate `BASE_PATH=/dayflow/` production build.
- Still not physically verified: the updated app on the user's iPhone. No changes were made to stored records, database identity, backup schema, icons or haptics.

## Version 1.2.0 — 2026-09-16

- `pnpm test`: **74 tests passed**, 11 files. Includes additive Dexie v1→v2 migration, Notes save/edit/delete and stale-edit protection, v1/v2 backup compatibility, preserved focus task names after task deletion, time aggregation across pauses, midnight, months, years and DST; and pie geometry/label collision checks.
- `pnpm test:e2e`: **17 tests passed (34.0 seconds)** against a fresh production build. Browser launch required execution outside the macOS sandbox. After fixing navigation waits and a textarea label, the complete suite passed in one run. Earlier failed attempts are not counted as passes.
- Browser coverage: task animations, preferences, task/category/schedule persistence, life records, timer recovery and task deletion, JSON/CSV and invalid imports, production offline behavior, 320–1440px route bounds, sticky task editor actions, Notes draft retention across tabs and main navigation, journal reload/edit/delete/backup restore, Focus category/hour/day/year rendering and horizontal scrolling; connected pie labels with eight unequal slices and long English/Chinese names at 320, 390, 768 and 1440px.
- Independent in-app browser inspection used a separate localhost demo database: Notes drafts, save and navigation; phone-sized layout of the category pie chart and hourly chart. Test records were not added to the user's installed app.
- TypeScript and root production build passed. The final GitHub Pages build uses `BASE_PATH=/dayflow/`.
- Still not verified by automation: physical iPhone vibration, installed home-screen icon refresh, and the reported intermittent blue line. The user described the line at the bottom of an empty task list and said it no longer appeared. No intentional blue border exists there; the exact cause is unconfirmed. Only non-interactive page outlines and additional native tap highlights were normalized; keyboard focus remains visible.
- No native iOS wrapper or sound effects were added. Generic browser vibration remains unsupported on iOS Safari; system haptics for native switches are separate.
- Backup schema 2 includes journal entries. Restore is a full replacement, including an empty journal when restoring a v1 file without notes. The database identity remains `dayflow-local-v1`; the schema change only adds the journal store.

The historical records below refer to their own releases.

## iPhone date field and header layout repair — 2026-09-14

Published in commit `13d918591ce54db59350d282f6d4d9cf5526e331`. GitHub Pages run `34839171741` succeeded; all 33 release files match the repository tree. Direct HTTPS byte verification was unavailable in this follow-up after the network permission expired.

User screenshots showed Schedule and sleep datetime inputs overflowing their inner backgrounds and the Close focus ring touching Save. A matching iOS-only date-input padding bug is documented at https://bugs.webkit.org/show_bug.cgi?id=301648. A shared DateTimeInput now places border and padding on a normal wrapper; the native date/time input has zero padding and border, keeps its native picker, labels, required/disabled attributes and change handlers. All 11 date/time controls use it. Header actions now have a 12px gap and inset keyboard focus outlines. Task dialogs move padding to a body wrapper, so the sticky header sits at the actual dialog top.

TypeScript, root and /dayflow/ builds, and 34 precache entries passed. Actual desktop in-app browser measurements at 390px: all three Schedule fields equal their parent width (281px), with the inner input padding 0; after scrolling 548px the header top is one pixel below the dialog top and the button gap is 12px. At 320px the task dialog client and scroll widths both equal 279px; document width is 320px; Save fits and fields remain contained. Sleep fields match their labels at 320px (243px) and 390px (313px). Both task and sleep were visually inspected. The temporary viewport was reset; no records were saved to the user's app.

The existing browser suite now checks inner date field bounds, sleep dialog widths, a minimum 12px action gap and the sticky header top. It was collected and type-checked; the full 12 tests were not executed here. These desktop responsive checks do not prove the iOS-specific workaround; physical iPhone confirmation is still pending. Data schema, record actions, timer handling, backup format and graduate-v2 icons are unchanged.

## Icon replacement — 2026-09-14

The exact user-supplied white-background graduation illustration is preserved in `design/app-icon-source.png`. The existing Sharp pipeline resized it without cropping for the 180px iPhone icon, 192px/512px app icons and 64px favicon. Current URLs use `graduate-v2`; v1 and unversioned aliases provide the same new bytes. Original app identity, routes, database and record-handling code are unchanged.

TypeScript and both production builds passed. Icon dimensions, HTML/manifest references, v2/v1/unversioned aliases and 34 precache entries passed validation. The rendered 180px icon was visually inspected. All 30 release files match the repository tree; all 28 public runtime files match the release bytes over HTTPS with a cache-busting query. The user's installed iPhone home-screen icon appearance has not been verified. Prior browser-test status remains recorded below.

Published in commit `9e430724cf5dc9075b61f42f1f02ade155584cf1`; GitHub Pages run `34811988959` succeeded.

## User browser run and assertion correction — 2026-09-14

The user ran the 12-test suite and reported **11 passed, 1 failed** (23.3 seconds). Passing cases include status separation, sorting, clearing times, phone/tablet layout and the sticky Save button. The failing deletion/focus assertion captured the expected value with `innerText()` but compared the default `textContent`; the reported category, timestamp and duration matched, while line breaks differed. The assertion now uses `toHaveText(history, { useInnerText: true })` so both sides use rendered text. It still checks the complete prior history entry, and the subsequent assertions still require the detached running timer to finish and both history rows to survive reload. This correction passed TypeScript and test collection; its browser rerun is pending. No production application code changed.

`pnpm test:e2e` now runs `pnpm build` first to avoid testing an older production build. The user also confirmed that their existing iPhone home-screen app shows Open and Completed, which confirms this task UI update has reached that installation; it is not a complete iPhone acceptance test.

## Task status views — 2026-09-14

Published to the original URL in commit `de080a8f39bec143efd7d95fea3d88c73ee6a7d6`. GitHub Pages run `34807075215` succeeded for that commit. All 25 release files match the repository tree. Live byte verification was not completed for this follow-up because shell DNS resolution failed and the web tool rejected opening the URL.

Tasks now defaults to Open, with a separate Completed view. Completing and reopening tasks moves them between the two views. Date-based tabs and the duplicate status filter are absent. Importance/newest/deadline sorting remains available. Add task switches to Open and opens the full editor. The task database, focus data, backup format, service-worker update logic and PWA identity are unchanged.

Strict TypeScript and both production builds passed. All HTML assets, icon aliases, manifest and 25 precache entries passed delivery validation. The existing browser regression was updated to cover default Open, completion/reopen movement, sorting and adding from Completed. All 12 browser tests were collected; they were not executed for this follow-up. Earlier browser observations and the 38 passing data/unit tests below belong to the prior task-editor update.

## Earlier task editor update — 2026-09-14

Published at https://jiangyt1412.github.io/dayflow/ in commit `5b16c4ea35e33a4e5f72cac9441fa05edce8cc07`. GitHub Pages run `34791800813` succeeded. All 22 application files match the repository tree; all 20 live runtime files were fetched over verified HTTPS and match the released bytes.

Changes: one task list with importance/newest/deadline sorting, completed tasks last; full editor before creation; independent Clear buttons for planned date, start time and deadline; Save task in a sticky header to the right of Close; responsive constraints for date controls, long labels, cards and tablet layouts. Task deletion continues to preserve focus sessions and active timers. Database name, schema version, backup format and PWA identity are unchanged.

- **38 unit/database tests passed in 6 files.** New coverage verifies complete draft creation, no stored draft before Save, duplicate/stale creation guards, cleared date persistence, sorting, and deleting a task with history plus either a running or paused timer. Focus records are compared field by field, unrelated records remain intact, backup round-trip is checked, and the detached timer can finish.
- Strict TypeScript and both root and `/dayflow/` production builds passed. HTML, icon aliases, manifest, 25 precache entries and archive integrity checks passed.
- Actual in-app browser observations: Add task opens the complete editor; Cancel leaves the list empty; new low/high-priority tasks save with their priority labels; a long task title renders; a long category name saves. These used a separate local test origin.
- Actual final header check at **320 × 700**: empty title is rejected; after scrolling the dialog by 680px, Close and Save task remain fully inside it, with Save to the right. Dialog scroll width and client width are both 279px; document width equals the 320px viewport. Clicking the top Save successfully closes the editor and adds the task. A prior 390px editor check also found no horizontal dialog overflow.
- **The expanded 12-test Playwright suite was collected and type-checked, not fully executed in this agent environment.** Chromium headless launch is blocked by the macOS environment, WebKit is not installed, native date-picker interaction crashed the in-app preview, and multi-route browser batches timed out. No claim is made that the full current suite, all device sizes, or iPhone Safari passed. The older user-supplied 7/7 result below is historical, not acceptance of this release.

## Earlier release history

Historical delivery checks from 2026-09-13. This report distinguishes executable verification, browser observations and remaining device checks. The implementation is delivered; complete real-device acceptance is still pending.

## Automated verification that passed

- **32 tests passed across 5 files** using Vitest. Re-run on 2026-09-13 after the browser-test corrections; all 32 passed. Strict TypeScript also passed again. The current corrections change test code only.
- Strict TypeScript project check: `tsc -b`, no errors, including the browser test source.
- Production Vite/PWA build for `/` and `/dayflow/` completed. Service worker, manifest, icons and precached chunks generated. Two upstream Zod comments produce non-fatal Rollup annotation warnings.

| Test group     | Tests | Coverage                                                                                                                                                                                                  |
| -------------- | ----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Time           |     6 | Cross-midnight and after-midnight sleep, local days, 23/25-hour DST days, active interval splitting, wrapped late-night window                                                                            |
| Analytics      |    10 | Circular clock averages and ambiguity, clipped focus intervals, zero-day averages, multiple hygiene occurrences, weekly/monthly boundaries, sleep chart endpoint ordering, task cohorts, drinks exclusion |
| Timer          |     7 | Pause/resume elapsed time, saved-state recovery, one active session, concurrent finish idempotency, cancellation, stale-session action guard                                                              |
| Backup         |     5 | Full JSON round-trip, relationships and interval validation, invalid/versioned input, atomic rollback on write failure, CSV escaping/formula safety                                                       |
| Record actions |     4 | Deleted category/task stale references, backup-compatible text limits, merging only changed preferences into the latest settings                                                                          |

IndexedDB integration tests use `fake-indexeddb`; they exercise Dexie transactions but do not prove Safari's complete implementation or lifecycle behavior.

## Browser observations

The in-app browser was used through its supported UI controls.

- Loaded the ordinary empty-data app and the isolated development demo in earlier checks. Task capture and shared category UI were exercised. Earlier demo charts rendered from stored sample records.
- After the requested simplification, visually checked Today and Settings at **390 × 844**, Focus at **320 × 844**, and Insights at **1440 × 900**.
- Measured no horizontal document overflow for Settings at 390, Tasks at 320, Focus at 320, and Insights at 1440. A multi-route run changed the actual viewport unexpectedly; those ambiguous intermediate sizes were not counted as 320-pixel results.
- Inspected the new five-row Insights overview, shortened navigation/headings, consolidated Today and Settings layouts, and collapsed secondary controls.
- Switched the Hygiene graph from daily to weekly; the selected option updated and Recharts rendered the stored data. No user records were edited during this visual check.
- A production preview displayed “Ready to work offline” before the final UI changes. This confirms registration/readiness was observed, **not** a complete offline reload test of the final bundle.
- Browser navigation integration was available and used earlier; it exposes navigation only.
- Restored the temporary viewport override and left the preview on Insights Overview.

## Browser automation and remaining acceptance

Seven Playwright end-to-end tests are supplied in `tests/browser/app.spec.ts`.

The user ran the corrected suite in their normal terminal on 2026-09-13: **7 passed in 10.3 seconds**. This result was supplied by the user; it was not produced by the sandboxed agent runtime. All seven supplied flows passed:

| Flow                                                   | Latest user-run result |
| ------------------------------------------------------ | ---------------------- |
| Task content, plan, shared category and persistence    | Passed                 |
| Sleep, meals and hygiene                               | Passed                 |
| Running/paused timer recovery and linked task          | Passed                 |
| Backup, restore, CSV and invalid import                | Passed                 |
| Production PWA and offline record changes              | Passed                 |
| Five routes at 320/390/1440 pixels and a mobile dialog | Passed                 |
| Empty Insights without invalid numbers                 | Passed                 |

The first run's two failures were both blocked at an exact `getByLabel('Category')` selector. All three affected lookups now use the combobox role and accessible name; the user's second run passed those steps. The second run exposed missing persistence waits in the tests: clicking Save task was followed immediately by reload, and clicking Pause was followed by a one-time timer read and reload. Neither click waits for asynchronous IndexedDB work. The test now waits for the editor to close after the save transaction, and for the committed Paused/Resume state before reloading. It also verifies the persisted category, date, subtask, and that the paused timer stays frozen. No assertion was removed or test skipped to hide the failures. **The subsequent user-run suite passed all seven tests, including these strengthened checks.**

Standalone browser execution in the agent environment remains blocked: with local networking allowed, Chromium launch failed at macOS MachPortRendezvousServer registration (`Permission denied`, SIGTRAP); without that grant, the preview server fails to bind (`listen EPERM`). These infrastructure failures are distinct from the user's application-level test results.

The embedded browser also had connection interruptions and a native date-picker crash during earlier interaction checks. Refreshing once exposed stale Vite module cache; restarting the development server resolved it. That stale-cache failure is not present in the production build.

Still requiring a supported browser/device test run:

- Update-prompt behavior after redeployment; production offline reload and record changes passed in the user-run suite.
- Physical iPhone Home Screen installation, Safari/native date controls, force-close/reopen, screen lock and background operation.
- Keyboard/screen-reader review and sustained performance on large datasets. The supplied route-width checks passed; they do not constitute a full accessibility audit.

## GitHub Pages deployment verification

- Live website: https://jiangyt1412.github.io/dayflow/
- GitHub's pages build and deployment run **34733404494** completed successfully for commit **8926fa16a92de67f689e0b17c3564164fd6ee1aa**. Build, reporting and deployment jobs all succeeded.
- All 14 repository application/configuration files have matching remote Git blob hashes and sizes; the initial README was preserved.
- The live HTTPS homepage returned **200**. Downloaded all 12 application resources (HTML, both JS chunks, CSS, manifest, service worker, Workbox runtime, favicon and four PNG icons) with certificate verification enabled; every response matched the validated local release byte for byte. `.nojekyll` and `_config.yml` are deployment configuration, not runtime resources.
- This confirms deployment and resource delivery. Browser control still timed out when opening the live page, so live UI interaction and physical iPhone acceptance are not claimed as completed. The user's seven passing browser tests cover the matching local production application.

Run the supplied checks in a normal local/CI environment:

```sh
pnpm install
pnpm test
pnpm build
pnpm exec playwright install chromium
pnpm test:e2e
```

Use a deployed HTTPS address for iPhone acceptance. Back up personal records first. Local storage, wall-clock changes and timezone regrouping limits are documented in the README; none is represented as fully solved by this desktop verification.

## User-selected icon update — 2026-09-13

The user's supplied 1254 × 1254 graduation illustration is preserved in `design/app-icon-source.png`. It was scaled without cropping or generative changes into 180/192/512-pixel app icons and a 64-pixel favicon. New `graduate-v1` URLs are used in the HTML and manifest. The original icon URLs remain available for older cached pages; the follow-up compatibility fix below updates their contents to the current image.

Strict TypeScript, root and `/dayflow/` production builds, icon dimensions, HTML references, precache resources and ZIP integrity passed. The three application JS/CSS assets are byte-identical to the previous release. The earlier user-run 7/7 browser suite remains the functional baseline; it was not re-run for this asset-only update.

Commit `2ff21cb4fcbcba42f779a708140558daf6e372f0` was published successfully by GitHub Pages run `34751090828`. All 14 current repository files match local hashes/sizes, and all 12 live HTTPS application files match the new build byte for byte, including the new icon files, HTML, manifest and service worker. Physical iPhone icon refresh has not been observed and may require adding the site to the Home Screen again; export existing records first.

## Follow-up: cached pages requesting old icons

The user confirmed the canonical live URL but still saw the old icon when adding to the iPhone Home Screen. An HTTPS inspection found that the live HTML and manifest referenced the new artwork while `icons/apple-touch-icon.png` still served the previous 3,706-byte image. This server-side omission was confirmed; whether it was the only cause on the user's phone was not remotely established.

The icon generator now writes the current image to all four original PNG URLs and embeds the current favicon image in the legacy SVG. The Apple touch icon link explicitly declares 180 × 180. The generated service worker includes refreshed hashes for the legacy files. No database or application logic changed. Release verification now checks that each legacy PNG equals its current counterpart. Root and /dayflow/ builds and package verification passed. Commit `285df04d23b4c055d3ba97bcb2463c834d40bccb` was deployed successfully in GitHub Pages run `34751712622`. All 19 repository release files match the local manifest; all 17 runtime files were fetched via HTTPS and matched byte for byte, including the original icon URLs. The iPhone Add to Home Screen preview still requires user confirmation.
