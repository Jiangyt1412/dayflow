<p align="center">
  <a href="https://jiangyt1412.github.io/dayflow/">
    <img src="docs/media/hero-v171.png" alt="DayFlow 1.7.1：当前像素风图标、未完成任务和关联任务的专注计时器，采用奶油白与鼠尾草绿排版。" width="100%">
  </a>
</p>

<h1 align="center">让每一天，自有节奏。</h1>

<p align="center">为任务、专注和日常生活，留一处清爽的空间。</p>
<p align="center">
  <a href="https://jiangyt1412.github.io/dayflow/"><strong>打开 DayFlow ↗</strong></a>
  &nbsp; · &nbsp;
  <a href="#看看-dayflow-如何使用">观看演示</a>
  &nbsp; · &nbsp;
  <a href="README.md">English</a>
</p>

<p align="center"><sub>无需注册 · 首次缓存后可离线使用 · 不自动云同步</sub></p>
<p align="center"><strong>版本 1.7.1</strong> · <a href="CHANGELOG.zh-CN.md">更新记录</a> · <a href="QA.md">验证报告</a></p>

## 看看 DayFlow 如何使用

完成任务、运行专注计时、进入分类的任务饼图、查看多段睡眠、保存日记。以下演示操作的是当前应用，使用虚构记录。

[![DayFlow 真实操作动图：完成任务、专注计时、分类与任务饼图。](docs/media/dayflow-demo-v171.gif)](https://github.com/Jiangyt1412/dayflow/blob/main/docs/media/dayflow-demo-v171.mp4)

<p align="center"><a href="https://github.com/Jiangyt1412/dayflow/blob/main/docs/media/dayflow-demo-v171.mp4"><strong>完整演示 · MP4 ↗</strong></a><br><sub>真实应用录屏 · 虚构演示数据 · 无音轨</sub></p>

## 从计划，到回顾

![DayFlow 1.7.1 真实界面：重要程度排序任务、关联任务的专注计时器、带引导线的分类用时饼图。](docs/media/product-showcase-v171.png)

| 安排重要的事 | 留出专注时间 | 看见时间去向 |
| --- | --- | --- |
| 分开管理 **Open（未完成）** 与 **Completed（已完成）**，设置优先级、子任务和可选时间，保护未保存的修改。 | 关联任务，开始、暂停、继续和结束；忘记开计时器时可以补录，也可修正历史记录。 | 从分类进入任务饼图，选择日期范围，查看专注时段及长期变化。 |

## 为自己的节奏留一点空间

![当前睡眠区间图：同一醒来日期保留两段睡眠和细灰色目标线；旁边展示带心情和历史列表的 Notes。](docs/media/daily-rhythm-v171.png)

每段完整睡眠都单独显示，同一天多次睡眠也能保留。清醒间隔留空，日合计不重复计算重叠时间，目标就寝时间用细灰线参考。

也可以记录饮食和个人护理。在 **Insights → Notes** 写几句话、记录心情，并回看以前的日记。

## 从今天开始

1. **[打开 DayFlow](https://jiangyt1412.github.io/dayflow/)。** 在 **Settings** 创建分类，再添加第一个任务。
2. **试一次专注计时。** 选择分类，按需关联任务后开始。删除任务后，已保存的专注记录及已有任务名称快照会保留。
3. **添加到 iPhone 主屏幕。** 在 Safari 选择 **分享 → 添加到主屏幕**。首次联网打开，等待 **Settings → Ready to work offline**。

应用界面目前为英文。通过 **Settings → Check for updates** 检查新版本，有更新时按提示操作。

## 记录保存在你的设备上

记录保存在当前浏览器或已安装网页应用中，**没有账号，也不会自动云同步**。不同设备、浏览器或主屏幕安装实例可能各有一套记录。

- **Export backup：** 完整 JSON 备份，包含已保存的 Notes；建议定期保存，更换使用入口前也先备份。
- **Import backup：** 校验 JSON 后，经确认**替换**当前记录，不会合并两套数据。
- **Export CSV：** 选定类型的表格数据，不能代替完整备份。

备份文件可直接读取，未加密，请妥善保管。清除网站数据可能移除本地记录。

<details>
<summary><strong>关于这个仓库和宣传素材</strong></summary>

本仓库通过 GitHub Pages 托管已编译的网站和项目介绍，可编辑源码另行维护。应用使用 **React、TypeScript、Vite、Dexie / IndexedDB 和 Recharts**。

以上图片用当前应用截图配合宣传排版制作；视频为真实交互录制，展示的记录均为虚构数据。像素风图标由项目所有者提供。[素材说明](docs/media/README.md)记录了来源和格式。

历次更新见[更新记录](CHANGELOG.zh-CN.md)，测试结果及真机限制见[验证报告](QA.md)。

</details>

<p align="center"><strong>找到属于自己的日常节奏。</strong><br><a href="https://jiangyt1412.github.io/dayflow/">从今天开始 ↗</a></p>
