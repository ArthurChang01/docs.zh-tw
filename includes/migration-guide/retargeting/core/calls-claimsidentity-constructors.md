---
ms.openlocfilehash: c10d617e07ca2fa0239298d449d93cf833b83fce
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275262"
---
### <a name="calls-to-claimsidentity-constructors"></a>呼叫 ClaimsIdentity 建構函式

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.6.2 開始，具有 <xref:System.Security.Principal.IIdentity?displayProperty=name> 參數的 <xref:System.Security.Claims.ClaimsIdentity> 建構函式如何設定 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 屬性的方法有變更。 如果 <xref:System.Security.Principal.IIdentity?displayProperty=name> 引數是 <xref:System.Security.Claims.ClaimsIdentity> 物件，而且該 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 屬性不是 <code>null</code>，則會使用 <xref:System.Security.Claims.ClaimsIdentity.Clone> 方法來附加 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 屬性。 在 Framework 4.6.1 和更早版本中，<xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 屬性會附加作為現有的參考。由於此項變更，從 .NET Framework 4.6.2 開始，新 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 屬性便不等於建構函式之 <xref:System.Security.Principal.IIdentity?displayProperty=name> 引數的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 屬性。 在 .NET Framework 4.6.1 和更早版本中，它是相等的。|
|建議|如果不想要這種行為，您可以將應用程式組態檔中的 <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> 參數設為 <code>true</code> 來還原舊版行為。 您會需要將下列內容新增至 web.config 檔案的 <code>&lt;runtime&gt;</code> 區段︰<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|影響範圍|Edge|
|版本|4.6.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)></li></ul>|
