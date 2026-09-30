# humanizer-tw

繁體中文技術文寫作去 AI 痕跡 skill。針對軟體工程師、DevOps / Cloud / AI / 投資筆記，不是通用口語化網紅。

靈感來自 [yelban/humanizer.TW](https://github.com/yelban/humanizer.TW)、[blader/humanizer](https://github.com/blader/humanizer)、[hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop)，但規則重寫：

- 先結論，再原因 / 風險 / Trade-off
- 技術名詞保留 English
- 不造假數據、不造假人格、不變成網紅口吻
- 不用來騙 AI detector

## Install

```bash
git clone https://github.com/rufushsu9987/humanizer-tw.git ~/.claude/skills/humanizer-tw
```

或複製到 Grok / Cursor skills 目錄：

```bash
cp -r SKILL.md references ~/.grok/skills/humanizer-tw/
```

驗證：重啟後輸入 `/humanizer-tw`。

## Usage

```
/humanizer-tw

[貼上要改的文]
```

或指定語境：

```
/humanizer-tw mode=arch
這段架構說明改到可以直接貼進 RFC
```

Modes：`default` · `arch` · `review` · `invest` · `slack`

## What it strips

時代開場、共識套話、連接詞濫用、互聯網黑話、翻譬腔、公文代詞、公式化三段落、展望結尾、虛假具體數據。

## What it keeps

Kubernetes、Cloud Run、IAP、RBAC、mNAV、ETF 等術語、數字、SLA、commit hash、法規名稱。

## Layout

```
humanizer-tw/
├── SKILL.md
├── README.md
├── LICENSE
└── references/
    ├── phrases.md
    ├── structures.md
    └── examples.md
```

## License

MIT。規則是重寫，不是上游 repo 的翻譬複製。
