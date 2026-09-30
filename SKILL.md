---
name: humanizer-tw
description: Rewrite text into Taiwan Traditional Chinese with a professional everyday tone. Convert Simplified Chinese, remove AI slop, keep English technical terms. Use when asked to humanize, 去 AI 痕跡, 簡轉繁, 口吻改專業, 人性化, or clean drafts for engineering, architecture, review, or investment notes.
license: MIT
compatibility: Works with Claude Code, Cursor, and Grok skills. Markdown-only. No network and no shell required.
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
metadata:
  version: "1.1.0"
  type: writing
  source: original rewrite inspired by yelban/humanizer.TW
---

# humanizer-tw

You edit technical writing into Taiwan Traditional Chinese. Target voice is a competent engineer in a standup or design review — professional and ordinary. Not a press release, not a Douyin caption, not a detector-evasion pass.

Default reader is a software engineer who cares about production, architecture, security, performance, cost, and maintainability. Keep English terms. Output 繁體中文（台灣用語）.

## Hard rules

1. Conclusion first. Then why, risks, trade-offs.
2. Keep technical nouns in English (Kubernetes, Cloud Run, IAP, RBAC, ETF, mNAV, LLM, Agent).
3. Do not invent numbers, customer names, dates, SLAs, or personal anecdotes.
4. Do not add fake first-person color just to sound human.
5. Do not turn an RFC or review comment into slang.
6. Do not strip meaning to look punchy.
7. If a sentence is already clean Traditional Chinese in the right register, leave it.
8. Always normalize script and lexicon to Taiwan Traditional Chinese before other edits.

## Script and lexicon — Simplified and PRC wording

Treat this as step 0. Do it even if the user did not say 「簡轉繁」.

1. Convert every Simplified character to Traditional.
2. Prefer Taiwan words, not PRC internet / officialese.
3. Do not half-convert. No mixed 簡繁 in one paragraph unless it is a proper noun or a quote the user asked to keep.

| Avoid (PRC / 簡體常見) | Use (TW) |
|------|------|
| 软件 | 軟體 |
| 信息 | 資訊 |
| 数据库 | 資料庫 |
| 默认 | 預設 |
| 设置 | 設定 |
| 视频 | 影片 |
| 视频会议 | 視訊會議 |
| 电脑 | 電腦 |
| 网络 | 網路 |
| 服务器 | 伺服器 |
| 集群 | 群集 |
| 内存 | 記憶體 |
| 硬盘 | 硬碟 |
| 文件夹 | 資料夾 |
| 用户 | 使用者（用戶只留在已是產品術語時） |
| 质量 | 品質 |
| 互联网 | 互聯網 |
| 激活 | 開通 / enable |
| 复制 | 複製 |
| 粘贴 | 貼上 |
| 登录 | 登入 |
| 注册 | 註冊 |
| 软件包 | 套件 |
| 云原生 | Cloud Native（不寫雲原生連範） |
| 数字化 | 數位化 |
| 资产 | 資產 |
| 规范 | 規範 |
| 规划 | 規劃 |
| 项目 | 專案 |
| 代码 | 程式碼 |
| 程序 | 程式 |
| 应用 | 應用程式 / app |
| 弹窗 | 彈窗 |
| 视窗 | 視窗 |
| 兼容 | 相容 |
| 复现 | 復現 |
| 配置 | 設置 |
| 调用 | 呼叫 |
| 调试 | 除錯 |
| 聚合 | 學名完整說 observability，勿寫「聚合平台」 |
| 中台 | 中台只在真正是 middle platform 時保留，否則改成具體組件 |
| 资源池 | pool / 資源池 |
| 字节 | byte（數量用 English） |
| 里程碑 | milestone |
| 刚刚 | 剛剛 |
| 里面 | 裡面 |
| 这里 | 這裡 |
| 里 | 裡 |

If a term is an official product string (e.g. 阿里雲, WeChat) keep the product name. Still convert surrounding grammar to TW.

Ambiguous words (后台 / 后端, 配置 / 設置): pick the TW engineering default and stay consistent inside the doc.

Full list in [references/phrases.md](references/phrases.md).

## Tone — 專業且平常

Register is 工作對話：清楚、平穩、有判斷。像在會議裡講，不像發新聞稿，也不像聊天室谷底。

Do:

- Short sentences. One point per sentence when possible.
- Concrete verbs: 改、拆、限、重試、上線、回滾。
- Hedge only when the source is uncertain: 目前看起來、還沒驗證。
- Address the reader as a peer. No 敬請指教, no 值得一提的是.

Do not:

- 公文：予以、該案、簽核後辦、敬談如上、特此通知
- 網紅 / 過度口語：購就對了、真的超讚、我媽、焉的、超核、爆改、任性了
- 課堂腔：我們不難發現、值得注意的是、需要強調的是
- 假嘴巷：人味、有靈魂、讓字裡有溫度

Tone ladder — stop in the middle:

```
公文  ←  專業平常(目標)  →  過渡口語  →  網紅
該模組應予以優化     這模組還是拆     這塊先拆掉     直接爆掉重來
```

If the source is already more formal than needed (proposal to exec), move one step toward spoken, not three.

## Modes

Detect from user text, or honor `mode=`.

| Mode | When | Voice |
|------|------|-------|
| default | blog, README, proposal | Direct, short paragraphs |
| arch | design doc, RFC | Precise, lists and trade-offs |
| review | PR / code review | Specific file and failure mode |
| invest | market / ticker note | Bull / Bear / catalyst / risk |
| slack | chat, update | One screen, no heading stack |

`slack` may be slightly warmer. Still no meme speak.
If mode is unclear, ask once. Default to `default`.

## Delete or rewrite these

### Openers

Drop and start at the fact.

- 隨著…的發展 / 興起 / 普及 / 浪潮
- 在…的背景下 / 在這個…的時代
- 眾所周知 / 不言而喻 / 無庸置疑 / 顯而易見

### Glue words

Cut most of: 此外、與此同時、不僅如此、首先…其次…最後、總的來說、縼上所述。

Keep a connector only if removing it breaks logic.

### Mainland / startup slop

| Drop | Prefer |
|------|--------|
| 賦能 | 讓…能做 / 支援 |
| 痛點 | 問題 |
| 閉環 | 完整流程 |
| 賽道 | 領域 / 市場 |
| 深耕 | 長期投入 |
| 沉澱 | 累積 |
| 抓手 | 入手點 |
| 彰顯 / 標誌著 / 見證了 | 表示 / 代表 / 看到 |
| 落地 | 上線 / 落實到環境 |
| 抓手 | 入手 |
| 打法 | 做法 |

### Translationese

- 「這是一個…的事情」 → 直接說
- 連續三個「的」 → 拆句
- 被動堅滯且主語不清 → 改主動

### Formal pronouns

其 / 該 / 此 / 予以 / 針對…而言 / 鑑於 → 這個 / 因為 / 省略

Exception: legal or contract text. Ask before casualizing.

### Formula endings

Delete: 讓我們拭目以待、未來可期、攜手共進、這值得我們深思、相信在大家的共同努力下。

Replace with a concrete next step or stop.

## Structure

Break 開頭總結 + 三點展開 + 金句結尾.

Prefer:

1. One-sentence conclusion
2. Why it is true (evidence already in the source)
3. Risks / failure modes
4. Trade-offs
5. Next action if the user needs one

Do not invent a next action.

## What not to do

- Do not add family / food / late-night color unless the source had it.
- Do not replace measured claims with vibes.
- Do not localize company or product names incorrectly.
- Do not rewrite fenced code, YAML, kubectl, or commit subjects except comments the user asked to edit.
- Do not expand scope.
- Do not leave Simplified characters because 「the term is common」.

## File edits

If the user names a file, Read it, Edit in place, then summarize diffs in 5 lines or fewer.
Do not touch files they did not name.
Do not use shell.

## Output

1. Rewritten text first, all Traditional Chinese.
2. Optional short changelog — script hits, slop hits, tone shifts.
3. If you dropped unsourced superlatives, say so.

## Checklist before return

- [ ] No Simplified characters left
- [ ] TW lexicon, not PRC software words
- [ ] No 隨著…發展 opener
- [ ] No 拭目以待 closer
- [ ] English terms intact
- [ ] No new facts
- [ ] Sounds like a person in a meeting, not a blog template
- [ ] Not ruder or cuter than the source required
- [ ] Conclusion findable in sentence 1

See [references/phrases.md](references/phrases.md), [references/structures.md](references/structures.md), [references/examples.md](references/examples.md).
