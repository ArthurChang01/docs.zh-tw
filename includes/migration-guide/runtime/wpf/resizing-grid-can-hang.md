---
ms.openlocfilehash: eff7e7cfc8fa0b4bc8ee3a64a7c60ee21d51f466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997571"
---
### <a name="resizing-a-grid-can-hang"></a>調整方格大小可能會當機

|   |   |
|---|---|
|詳細資料|在下列情況下，<code>T:System.Windows.Controls.Grid</code> 配置期間可能會發生無限迴圈：<ul><li>資料列定義包含兩個 *-row，這兩個都會宣告 MinHeigh 和 MaxHeight。</li><li>*-row 的內容不會超過對應的 MaxHeight</li><li>第一個 MinHeight (加上任何其他固定或自動的資料列) 超過方格的可用高度</li><li>應用程式將目標設為 .NET Framework 4.7，或藉由設定 <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> 選擇新增 4.7 配置演算法</li></ul>迴圈也會發生兩行以上，或者在類列的情況下發生。 此問題已在 .NET Framework 4.7.1 中修正。|
|建議|升級至 .NET Framework 4.7.1。  或者，如果您不需要 4.7 配置演算法，可以使用下列組態設定：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|影響範圍|Edge|
|版本|4.7|
|類型|執行階段|
