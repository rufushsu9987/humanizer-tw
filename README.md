# humanizer-tw

把簡體、公文腔、AI 套話改成台灣日常用語。像在 LINE 跟同事講，不像發稿，也不像在紗紗。

靈感來自 [yelban/humanizer.TW](https://github.com/yelban/humanizer.TW)、[blader/humanizer](https://github.com/blader/humanizer)、[hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop)，規則重寫。

## 做什麼

- 簡體 → 台灣繁體（字形 + 用詞）
- 語調停在「台灣日常」：我覺得、先這樣、再看、有點、還好
- 技術名詞留 English
- 先結論，再原因 / 風險 / Trade-off
- 不造假、不騙 detector

## 語調

```
公文 → 會議腔 → 台灣日常(目標) → 過渡豬友 → 網紅
```

「該模組應予以優化」→「這塊先拆比較快」  
不要變「直接爆掉重來啦」。

## Install

```bash
git clone https://github.com/rufushsu9987/humanizer-tw.git ~/.claude/skills/humanizer-tw
```

```bash
git -C ~/.claude/skills/humanizer-tw pull
```

## Usage

```
/humanizer-tw

[貼簡體或繁體草稿]
```

```
/humanizer-tw mode=slack
這段改成可以直接貼群組
```

Modes：`default` · `arch` · `review` · `invest` · `slack`

## License

MIT
