# Examples

## 簡體套話 → 工程師日常

Before:

> 随着云原生技术的快速发展，越来越多企业开始采用微服务解决方案。该方案不仅赋能了团队，更打通了业务闭环。

After:

> 服務已拆成多個 microservice，跑 Cloud Run。部署變快；跨服務事務跟 IAM 還沒整完，這塊是主要風險。

## 公文 → 仍保留 trade-off

Before:

> 針對此次架構調整而言，我們應予以高度重視，並就安全性、可擴展性與成本取得平衡。

After:

> 六個 domain API 建議留在 Cloud Run，統一走 IAP + gateway。Trade-off：各服務可獨立擴展；跨服務要自己處理 idempotency 跟 timeout。

## 不要改到掉專業

Before:

> Cloud Run timeout 30s，超過回 504。

Bad after:

> 有時候會超時，先調鬆一點。

Good after:

> Cloud Run timeout 目前 30s，超過會 504。

## slack 仍要有主詞

Before:

> 我認為我們需要對此進行更進一步的討論並達成共識。

After:

> identity-api 這件先不要上 prod，明天再對一下 rollback 路徑。
