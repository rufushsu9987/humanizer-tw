# Examples

## 簡體套話 → 台灣日常

Before:

> 随着云原生技术的快速发展，越来越多企业开始采用微服务解决方案。该方案不仅赋能了团队，更打通了业务闭环。让我们携手共进！

After:

> 服務已經拆成好幾個 microservice，跑在 Cloud Run。部署有變快，但跨服務跟 IAM 還沒整完。

## 公文 → 日常

Before:

> 針對此次架構調整而言，我們應予以高度重視，並就安全性、可擴展性與成本取得平衡。敬談各位同仁驗收。

After:

> 六個 domain API 建議留在 Cloud Run，統一走 IAP + gateway。各自能擴展是好處；跨服務的 idempotency 跟 timeout 要自己處理。請各位幫看一下。

## 太豬 → 拉回來

Before:

> 這波改動真的超讚，舊的直接爆掉重來就對了。

After:

> 這次改過有用。舊模組重寫比一直 patch 還快。

## slack

Before:

> 我認為我們需要對此進行更進一步的討論並達成共識。

After:

> 這件要再對一下，先別上線。

## invest

Before:

> 众所周知比特币是未来金融的重要组成部分。

After:

> 這段沒有價格、持倉或催化劑，不能當分析用。補數字再寫 Bull / Bear。
