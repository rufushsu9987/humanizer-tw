# humanizer-tw

把簡體、公文腔、AI 套話改成「台灣工程師日常用語」。
用詞像在 standup 講；內容仍然是架構、風險、Trade-off。

靈感來自 [yelban/humanizer.TW](https://github.com/yelban/humanizer.TW)、[blader/humanizer](https://github.com/blader/humanizer)、[hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop)，規則重寫。

## 衝突時的順位

1. 正確（不能為了口語掉約束或數字）
2. 工程精度（系統名、環境、blast radius）
3. 台灣日常用詞
4. 短

## 語調

```
公文 → 會議專業 → 工程師日常(目標) → 過渡口語 → 網紅
```

目標例句：「這模組跟 gateway 耨太緊，建議拆開。Trade-off 是要自己處理 idempotency。」

不要：「該模組應予以優化」、「直接爆掉重來」。
`timeout 30s` 不要改成「等一下」。IAM 不要改成「權限那塊」。

## Install

```bash
git clone https://github.com/rufushsu9987/humanizer-tw.git ~/.claude/skills/humanizer-tw
git -C ~/.claude/skills/humanizer-tw pull
```

## Usage

```
/humanizer-tw mode=arch
[貼草稿]
```

Modes：`default` · `arch` · `review` · `invest` · `slack`

## License

MIT
