<p align="center">
  <a href="https://jiangyt1412.github.io/dayflow/">
    <img src="docs/media/hero-v171.png" alt="DayFlow 1.7.1: current pixel-art icon, Open tasks and a task-linked Focus timer, in a cream and sage layout." width="100%">
  </a>
</p>

<h1 align="center">A little more clarity, every day.</h1>

<p align="center">A calm, local-first space for your tasks, focused time and everyday rhythms.</p>

<p align="center">
  <a href="https://jiangyt1412.github.io/dayflow/"><strong>Open DayFlow ↗</strong></a>
  &nbsp; · &nbsp;
  <a href="#see-dayflow-in-motion">Watch the demo</a>
  &nbsp; · &nbsp;
  <a href="README.zh-CN.md">简体中文</a>
</p>

<p align="center"><sub>No account required · Offline after setup · No automatic cloud sync</sub></p>
<p align="center"><strong>Version 1.7.1</strong> · <a href="CHANGELOG.md">What’s new</a> · <a href="QA.md">Validation</a></p>

## See DayFlow in motion

Complete a task, run a Focus session, explore a category’s tasks, review split sleep and save a note. This is the current application being operated with synthetic records.

[![Animated preview of real DayFlow operations: task completion, focus timer and category-to-task pie.](docs/media/dayflow-demo-v171.gif)](https://github.com/Jiangyt1412/dayflow/blob/main/docs/media/dayflow-demo-v171.mp4)

<p align="center"><a href="https://github.com/Jiangyt1412/dayflow/blob/main/docs/media/dayflow-demo-v171.mp4"><strong>Full demo · MP4 ↗</strong></a><br><sub>Actual app recording · Synthetic demo records · No audio</sub></p>

## From plans to perspective

![Actual DayFlow 1.7.1 screens: prioritized tasks, a running task-linked timer and a category pie with connected time labels.](docs/media/product-showcase-v171.png)

| Plan what matters | Give it your focus | See where time goes |
| --- | --- | --- |
| Separate **Open** and **Completed** tasks. Set priorities, subtasks and optional dates. Keep unsaved edits safe. | Link a task, start, pause, resume and finish. Add missed sessions or correct saved records. | Explore categories and task pies, time-of-day patterns and longer trends over your chosen range. |

## Leave room for your rhythm

![Current sleep interval chart with two separate periods on one wake date and a subtle target line, beside Notes with mood and journal history.](docs/media/daily-rhythm-v171.png)

Every completed sleep period has its own interval, including multiple sleeps on one wake date. Awake gaps stay visible, overlapping time is counted once in daily totals, and your target bedtime is a quiet gray reference.

Record meals and personal care too. In **Insights → Notes**, write a few words, record your mood and return to earlier entries.

## Make yourself at home

1. **[Open DayFlow](https://jiangyt1412.github.io/dayflow/).** Create a category in **Settings**, then add your first task.
2. **Try a Focus session.** Choose a category, optionally link a task, and start. Saved sessions keep the task name even after its task is deleted.
3. **Add it to your iPhone Home Screen.** In Safari, choose **Share → Add to Home Screen**. Open it online and wait for **Settings → Ready to work offline**.

The interface is in English. **Settings → Check for updates** checks for a newer app; follow the update prompt when one is available.

## Your records stay on your device

Records are stored locally in the browser or installed app you use. **There is no account or automatic cloud sync.** Different devices, browsers or Home Screen installations may hold separate records.

- **Export backup:** a complete JSON backup, including saved Notes. Keep a copy periodically and before moving to another installation.
- **Import backup:** validates that JSON and, after confirmation, **replaces** current local records. It does not merge two sets of data.
- **Export CSV:** selected records for spreadsheets; it is not a full backup.

Backups are readable, unencrypted files. Clearing website data can remove local records.

<details>
<summary><strong>About this repository and media</strong></summary>

This repository hosts the published static web build and product documentation on GitHub Pages. The editable source project is maintained separately. The application uses **React, TypeScript, Vite, Dexie / IndexedDB and Recharts**.

The images above combine current application screenshots with a designed layout. The video records actual interactions; all illustrated records are synthetic. The pixel-art icon was supplied by the project owner. See [media notes](docs/media/README.md) for provenance and formats.

Release history belongs in the [changelog](CHANGELOG.md). The latest validation and physical-device limits are documented in [QA.md](QA.md).

</details>

<p align="center"><strong>Find your daily rhythm.</strong><br><a href="https://jiangyt1412.github.io/dayflow/">Start with today ↗</a></p>
