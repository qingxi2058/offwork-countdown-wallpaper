---
name: offwork-countdown-wallpaper
description: 下班倒计时「动态壁纸」生成器。零依赖单文件 HTML，实时倒计时到下班点、粒子动效、今日工作进度条、下班后变红+横幅+骂老板弹幕、周末/发薪/摸鱼计时、里程碑提示、周五特殊态；内置"怎么设成桌面/手机壁纸"说明。当用户要做下班倒计时、摸鱼壁纸、打工人壁纸、下班壁纸、倒计时网页、或把它做成可发布的小红书产品时使用。触发词：下班倒计时、摸鱼壁纸、下班壁纸、打工人壁纸、倒计时壁纸、倒计时网页、下班动态壁纸、offwork countdown。
---

# 下班倒计时动态壁纸生成器

> 根据用户一句话，生成一个零依赖单文件 HTML 动态壁纸。用户只改顶部 CONFIG，也可直接用生成版。可作为 Red Skill 发布（粉丝复制装进 AI 生成自己的）。

## 生成流程
1. **把用户一句话解析成参数**（见下「输入解析」），缺的用默认值。
2. **复制 `assets/wallpaper.html`**，只改顶部 `CONFIG`，其余结构别动。
3. 输出**单文件**到指定目录（默认项目内/桌面），文件名如 `下班倒计时.html`。不拆文件、不加外部依赖。
4. **可选预览**：Chrome headless 渲染 PNG（手机 1080×1920 / 桌面 1920×1080）：
   ```bash
   "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
     --window-size=1080,1920 --screenshot=preview.png "file://$(pwd)/下班倒计时.html"
   ```

## 输入解析（一句话 → 参数）
从用户话里提取，缺省用默认：
| 用户说 | 字段 | 例 |
|---|---|---|
| 下班时间（18点/6点半/18:30）| `offTime` | "18:30" |
| 暖色/霓虹/极简 | `theme` | warm/neon/mono |
| 狠一点·怼老板·发疯版 / 温和·治愈 | `barrageStyle` | hard / soft |
| 称呼（打工人/小王/产品狗）| `name` | "小王" |
| 每月几号发工资 | `payday` | 10（0=不显示）|
| 一天工作几小时 | `workHours` | 8 |

**硬规则**：用户**没明确要狠**时，`barrageStyle` 默认 `soft`；只有说"狠一点/怼老板/发疯版"才用 `hard`。

**示例**：
- 用户："我18点下班，要暖色温和版" → `{offTime:"18:00", theme:"warm", barrageStyle:"soft"}`
- 用户："6点半下班，怼老板那种，叫我产品狗" → `{offTime:"18:30", barrageStyle:"hard", name:"产品狗"}`

## 默认值
`offTime:"18:00"` ｜ `name:"打工人"` ｜ `theme:"neon"` ｜ `barrageStyle:"soft"` ｜ `payday:10` ｜ `weekend:true` ｜ `workHours:8` ｜ `fishMode/fridayMode/milestones:true`

## CONFIG 字段全集
`offTime` 下班时间 ｜ `name` 称呼 ｜ `theme` neon/warm/mono ｜ `barrageStyle` hard/soft ｜ `payday` 发薪日(0关) ｜ `weekend` 周末倒计时 ｜ `fishMode`+`fishStart` 今日摸鱼计时 ｜ `fridayMode` 周五特殊态 ｜ `milestones` 剩30/10/5/1分钟弹提示 ｜ `workHours` 进度条 ｜ `mochiu[]` 摸鱼文案。

## 内置功能
三段式布局（上状态/中巨型倒计时/下信息）｜粒子连线（页面不可见自动暂停省电）｜今日工作进度条｜下班后红色告警+抖动横幅+弹幕｜周末·发薪·摸鱼 chips｜里程碑 toast｜周五特殊态｜摸鱼文案轮播｜F11·双击全屏｜设壁纸说明弹窗。

## 怎么当壁纸（HTML 不能直接设壁纸，必须讲清）
- **Mac 桌面**：装 Plash，把 HTML 网址/路径粘进去
- **Win 桌面**：装 Lively Wallpaper，添加网页
- **手机锁屏/动态壁纸**：浏览器全屏 → 录屏 10–15 秒 → 存视频 → 设为动态壁纸
- HTML 内已内置「?」按钮弹出这套说明

## 做成小红书内容时（成果型·涨粉）
- 选题："我做了张会催我下班的壁纸"——成果前置（红屏弹幕第一秒上）。
- Red Skill 站内话术："放笔记里了，复制就能装进你的 AI，改成你自己的下班时间。"
- 合规：笔记里**别提外部域名**（站外导流红线）；弹幕保持自嘲、**别升级成骂公司/制造对立**；公开版默认 soft；发布勾「AI 辅助创作」。

## 完成标准（自检）
- [ ] 已把用户一句话解析进 CONFIG；没要狠话则默认 soft
- [ ] 单文件可直接双击打开，无外部依赖
- [ ] 倒计时态 / 超时红色态都正常
- [ ] theme 写错不白屏、mochiu 为空不报错、发薪日跨月不算错
- [ ] 给了"怎么当壁纸"的说明
- [ ] 公开发布：温和文案 + 不提外部域名
