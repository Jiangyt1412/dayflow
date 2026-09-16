<p align="center">
  <a href="https://jiangyt1412.github.io/dayflow/">
    <img src="docs/media/hero-v2.jpg" alt="DayFlow — Find your daily rhythm. A cream and sage campaign illustration featuring the graduation-themed app icon." width="100%">
  </a>
</p>

<h1 align="center">A little more clarity, every day.</h1>

<p align="center">
  A calm space for your tasks, focused time, and everyday routines.<br>
  Open it in your browser. Make it part of your day.
</p>

<p align="center">
  <a href="https://jiangyt1412.github.io/dayflow/"><strong>Open DayFlow ↗</strong></a>
  &nbsp; · &nbsp;
  <a href="#make-yourself-at-home">Get started</a>
  &nbsp; · &nbsp;
  <a href="README.zh-CN.md">简体中文</a>
</p>

<p align="center"><sub>No account required · Local data storage · Offline after setup</sub></p>

<p align="center"><strong>Version 1.3.0</strong> · <a href="CHANGELOG.md">What’s new</a> · <a href="QA.md">Validation</a></p>

---

## Your day, in one place

DayFlow brings planning and daily records together in a quiet, cream-and-sage interface. Choose what matters, give it your attention, and look back on the time you have spent.

![Illustrated preview of the DayFlow task editor, sleep records and Insights, with synthetic demo data.](docs/media/product-preview-v2.jpg)

<p align="center"><sub>Illustrated product preview · Demo data</sub></p>

| Plan with intention                                                                                                                  | Make room for focus                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| Keep **Open** and **Completed** tasks separate. Sort by importance, add subtasks, and set optional dates, start times and deadlines. | Start a count-up timer, pause when you need to, and save each session. Link focused time to a task or keep it under a category. |
| **Keep life in view**                                                                                                                | **See your daily rhythm**                                                                                                       |
| Record sleep, meals and personal care alongside your plans. Edit a record when the details change.                                   | Explore **Insights** over a chosen date range, with summaries and charts drawn from your own records.                           |

**New in 1.3.0:** A moving mobile navigation highlight, clear save/timer feedback and gentle editor transitions. Tap a category slice to explore task-by-task focus time. Swipe a task left to reveal Delete, then tap to delete; Undo the latest task action within 10 seconds.

**Introduced in 1.2.1:** Choose 7, 30 or 90 days, all time or custom dates for the Focus category pie. Sleep and meal timelines now read from earlier at the top to later at the bottom, with clearer axis spacing and no blue tap outline.

**Introduced in 1.2.0:** Write a daily note and record your mood in **Insights → Notes**. In **Focus**, see four time totals, a category pie chart, a 24-hour distribution and daily/yearly trends.

Saved focus sessions show their linked task name and remain in your history when you delete the task. Names of tasks already deleted before this version cannot be recovered from missing data.

## Make yourself at home

1. **Open [DayFlow](https://jiangyt1412.github.io/dayflow/).** No account or installation is needed to use the website.
2. **Add your first task.** Create a category in **Settings**, then choose **Tasks → Add task** and **Save task**. In **Focus**, select that category to start a session; give the task the same category if you want to link it.
3. **Take it to your Home Screen.** On iPhone, open the site in Safari, choose **Share → Add to Home Screen**, and enable **Open as Web App** if that option appears. See [Apple’s guide](https://support.apple.com/en-nz/guide/iphone/iphea86e5236/ios).

Open the app online first, then check **Settings** for **Ready to work offline**. Once the app has cached, you can keep recording without a connection. The app interface is currently in English.

## Your records, on your device

DayFlow stores records locally in the browser or installed app you are using. **There is no account or automatic cloud sync.** Another device, browser, or Home Screen installation may have a separate set of records.

- **Export backup** saves a full JSON backup, including saved journal entries. Keep a copy periodically and before moving to another installation.
- **Import backup** validates that JSON file and, after confirmation, **replaces the current local data**. It does not merge two sets of records.
- **Export CSV** provides selected records for spreadsheets; it is not a full backup.

Backup files are readable, unencrypted files. Keep them somewhere you trust. Clearing website data can remove local records.

<details>
<summary><strong>About this repository</strong></summary>

This repository hosts the published DayFlow web build and its product documentation on GitHub Pages. It is not the editable application source project.

The application is built with **React, TypeScript and Vite**, with **Dexie / IndexedDB** for local storage and **Recharts** for charts.

Campaign artwork is AI-assisted. Product illustrations are based on the app with synthetic demo data; small visual details may differ from the live interface.

</details>

---

<p align="center"><strong>Find your daily rhythm.</strong><br><a href="https://jiangyt1412.github.io/dayflow/">Start with today ↗</a></p>
