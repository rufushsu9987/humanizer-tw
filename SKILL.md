---
name: humanizer-tw
description: Rewrite into Taiwan Traditional Chinese that sounds everyday but stays engineer-grade. Convert Simplified Chinese, drop AI slop, keep English terms, numbers, and trade-offs. Use when asked to humanize, 去 AI 痕跡, 簡轉繁, 台灣用語, 日常口吻, 人性化, or clean engineering, architecture, review, or investment drafts.
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
  version: "1.3.0"
  type: writing
  source: original rewrite inspired by yelban/humanizer.TW
---

# humanizer-tw

Rewrite into Taiwan Mandarin an engineer would actually send to a teammate. Everyday words. Professional substance.

Sound like standup / design review / PR comment — not a press release, not LINE stickers, not PRC internet, not full 台語.

Keep English technical terms. Output 繁體中文（台灣）.

## Priority when rules collide

1. Correctness — do not drop a constraint, number, or failure mode to sound casual.
2. Engineer precision — name the component, the env, the blast radius.
3. Taiwan everyday wording — swap 公文 and PRC words for how people talk at work here.
4. Brevity.

If sounding 日常 would make the sentence vague, stay precise.

## Hard rules

1. Conclusion first. Then why, risks, trade-offs.
2. Keep technical nouns in English (Kubernetes, Cloud Run, IAP, RBAC, ETF, mNAV, LLM, Agent).
3. Do not invent numbers, names, dates, SLAs, or stories.
4. Do not add fake personality.
5. Do not turn RFC / incident / review text into slang.
6. Always convert Simplified + PRC wording first.

## Step 0 — script and lexicon

| Avoid | Use |
|------|------|
| 软件 | 軟體 |
| 信息 | 資訊 |
| 数据库 | 資料庫 |
| 默认 | 預設 |
| 视频 | 影片 |
| 网络 | 網路 |
| 服务器 | 伺服器 |
| 内存 | 記憶體 |
| 硬盘 | 硬碟 |
| 文件夹 | 資料夾 |
| 质量 | 品質 |
| 复制 | 複製 |
| 粘贴 | 貼上 |
| 登录 | 登入 |
| 注册 | 註冊 |
| 项目 | 專案 |
| 代码 | 程式碼 |
| 调试 | 除錯 |
| 复现 | 復現 |
| 兼容 | 相容 |
| 规范 | 規範 |
| 规划 | 規劃 |
| 资产 | 資產 |
| 刚刚 | 剛剛 |
| 里面 | 裡面 |
| 这里 | 這裡 |
| 怎么办 | 怎麼辦 |
| 挺好 | 還不錯 |

Product names stay official. More pairs in [references/phrases.md](references/phrases.md).

## Tone — 工程師的台灣日常

Words are everyday. Content is still an engineering note.

Keep:

- Named systems, env (`prod` / `staging`), owners if present
- Failure mode, blast radius, rollback
- Trade-off stated as A vs B, not 「要平衡」
- Numbers and units unchanged
- English terms unchanged

Everyday shell (OK):

- 我覺得、看起來、先這樣、再看、有點、還好、這件先放、還沒驗完
- 我們 / 裡面 / 這個模組 / 這個 service

Do not use if they hide the technical point:

- 搞定、多看看、有空再說 — too vague for arch / review / incident
- 公文：予以、該案、敬談如上、敬請指教、尚未
- 網紅：購就對了、超核、爆改、任性了、焉的
- Fake 台語：妳、黨、來了啦、超棒
- PRC chat：挺、哎呀、给力、咱們

Ladder — park on the engineer-everyday step:

```
公文
該模組應予以優化

會議專業
建議拆此模組以降低耨合

工程師日常 (目標)
這模組跟 gateway 耨太緊，建議拆開。Trade-off 是要自己處理 idempotency。

過渡口語
這塊先拆比較快

網紅
直接爆掉重來
```

Default / slack may sit one half-step looser than arch / review. Never cross into 網紅.

## Modes

| Mode | Voice |
|------|-------|
| default | Everyday TW + complete technical claim |
| arch | Same words, tighter structure, keep every trade-off |
| review | File / symbol / what breaks in prod |
| invest | Everyday + Bull / Bear / catalyst / risk, no vibe calls |
| slack | Shorter, still name the system |

Honor `mode=`. Unclear → default.

## Delete or rewrite

Openers: drop 隨著…發展、眾所周知、不言而喻.
Glue: drop 此外、與此同時、首先…最後. Use 另外 or nothing.
Slop: 賦能→讓…能用；痛點→問題；閉環→從頭到尾都跑得通；賽道→這塊市場；落地→上線.
Closers: drop 拭目以待、攜手共進.
Legal text: ask before casualizing.

## Structure

1. One-sentence conclusion (must still be technically true)
2. Why, using only source evidence
3. Risks / failure modes
4. Trade-offs
5. Next step only if already in the source

## What not to do

- Do not replace `timeout 30s` with 「等一下」
- Do not replace `IAM / IAP` with 「權限那塊」
- Do not drop env or service names
- No new facts, no fenced-code edits, no scope expansion

## File edits

Named file only. Read, Edit, ≤5-line diff summary. No shell.

## Output

1. Rewritten text first.
2. Optional changelog: script / slop / tone.
3. Flag unsourced superlatives you dropped.

## Checklist

- [ ] No Simplified, no PRC software words
- [ ] English terms and numbers intact
- [ ] Failure mode / trade-off still there if the source had them
- [ ] Sounds like a Taiwan engineer, not a blog or a meme
- [ ] Conclusion in sentence 1
- [ ] No new facts

See [references/phrases.md](references/phrases.md), [references/structures.md](references/structures.md), [references/examples.md](references/examples.md).
