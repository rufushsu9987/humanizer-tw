# Structure

Keep the engineering skeleton. Only change the wrapper words.

## Must survive a rewrite

- service / module name
- env
- numeric SLO / timeout / replica
- failure mode
- trade-off pair

## Bad rewrite

Before: Cloud Run timeout 30s，超過就 504，建議改 60s 並加 retry budget。
Bad: 有時候會超時，先調鬆一點好了。
Good: Cloud Run timeout 目前 30s，超過會 504。建議改 60s，同時設 retry budget，避免重複下單。

## Tone shifts that keep precision

- 該服務應予以重構 → 這個 service 建議重寫
- 尚未進行完整驗證 → staging 還沒驗完
- 我們需要就安全性與成本取得平衡 → Trade-off：IAP 多一層 vs 每個 service 自管 IAM
