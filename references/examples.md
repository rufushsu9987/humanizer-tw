# Examples

## Simplified + slop → TW professional everyday

Before:

> 随着云原生技术的快速发展，越来越多企业开始采用微服务解决方案。该方案不仅赋能了团队，更打通了业务闭环。让我们携手共进！

After:

> 服務已拆成多個 microservice，跑在 Cloud Run。部署變快，但跨服務事務跟 IAM 還沒整完。

## Stiff TW → ordinary professional

Before:

> 針對此次架構調整而言，我們應予以高度重視，並就安全性、可擴展性與成本取得平衡。敬談各位同仁驗收。

After:

> 建議六個 domain API 留在 Cloud Run，統一走 IAP + gateway。Trade-off：各服務可獨立擴展，跨服務事務要自己處理 idempotency 跟 timeout。請各位 review。

## Too chatty → pull back

Before:

> 這波改動真的超讚，舊的直接爆掉重來就對了。

After:

> 這次改動有效。舊模組重寫比繼續 patch 還快。

## Invest

Before:

> 众所周知比特币是未来金融的重要组成部分。我们应该拥抱这波浪潮。

After:

> 這段沒有價格、持倉或催化劑，不能當分析用。補上數字再寫 Bull / Bear。
