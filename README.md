# humanizer-tw

繁體中文技術文寫作去 AI 痕跡 skill。把簡體與公文腔改成台灣工程師在會議裡會說的話：專業、平常、不連範。

靈感來自 [yelban/humanizer.TW](https://github.com/yelban/humanizer.TW)、[blader/humanizer](https://github.com/blader/humanizer)、[hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop)，規則重寫。

## 做什麼

- 簡體 → 台灣繁體（字形 + 用詞）
- 先結論，再原因 / 風險 / Trade-off
- 技術名詞保留 English
- 語調停在「專業平常」：不公文、不網紅、不造假人格
- 不用來騙 AI detector

## Install

```bash
git clone https://github.com/rufushsu9987/humanizer-tw.git ~/.claude/skills/humanizer-tw
```

已裝過就 pull：

```bash
git -C ~/.claude/skills/humanizer-tw pull
```

## Usage

```
/humanizer-tw

[貼上簡體或繁體草稿]
```

```
/humanizer-tw mode=arch
這段架構說明改到可以直接貼進 RFC
```

Modes：`default` · `arch` · `review` · `invest` · `slack`

## Tone

```
公文  ←  專業平常(目標)  →  過渡口語  →  網紅
```

範例：「該模組應予以優化」→「這模組還是拆」。不要變「直接爆掉重來」。

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

MIT
