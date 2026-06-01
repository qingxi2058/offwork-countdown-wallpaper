# 下班倒计时 · 动态壁纸 | offwork-countdown-wallpaper

一个零依赖的「下班倒计时动态壁纸」——实时倒计时到你的下班点，粒子动效、今日工作进度条、下班后变红 + 抖动横幅 + 弹幕、周末/发薪倒计时、摸鱼文案轮播。打工人专属，免费。

> 既是可直接打开的网页（`index.html`），也是一个 Claude Code / AI Agent 技能（`SKILL.md`）——让 AI 帮你生成「你自己的下班时间 + 风格」的专属版。

## ✨ 功能
- ⏰ 实时倒计时到下班点；过点变红 + 抖动横幅「到点了该撤了」+ 弹幕
- 🌌 粒子连线动效 + 今日工作进度条
- 🎨 3 套主题：`neon` 赛博霓虹 / `warm` 暖色治愈 / `mono` 极简黑白
- 💬 下班弹幕两版：`hard` 狠话 / `soft` 温和
- 📅 周末倒计时 + 发薪日倒计时 + 摸鱼文案轮播

## 🚀 直接用
下载 `index.html`，浏览器打开即可。改最上面 `<script>` 里的 `CONFIG`：
```js
const CONFIG = {
  offTime: "18:00",     // 你的下班时间
  name: "打工人",        // 称呼
  theme: "neon",        // neon / warm / mono
  barrageStyle: "hard", // hard 狠话 / soft 温和
  payday: 10,           // 每月发薪日，0=不显示
  weekend: true,
};
```

## 🤖 作为 AI 技能用（推荐）
把这个仓库装进你的 AI（Claude Code / Codex / 等），直接说「做个下班倒计时壁纸」，它会问你下班时间和风格，吐出你的专属版：
```bash
npx skills add qingxi2058/offwork-countdown-wallpaper
```
或把 `SKILL.md` 加载给你的 Agent。

## 🖥️ 怎么变成壁纸
HTML 是全屏网页，三种用法：
- **Mac 桌面**：装免费的 [Plash](https://apps.apple.com/app/plash/id1494023538)，把本页网址/路径粘进去
- **Windows 桌面**：装免费的 [Lively Wallpaper](https://apps.microsoft.com/detail/9ntm2qc6qws7)，添加网页
- **手机锁屏/动态壁纸**：浏览器全屏打开 → 录屏 10–15 秒 → 存成视频 → 设为动态壁纸

## License
MIT
