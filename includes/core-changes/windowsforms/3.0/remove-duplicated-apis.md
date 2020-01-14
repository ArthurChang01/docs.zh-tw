---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937084"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>已從 Windows Forms 移除重複的 Api

從 .NET Core 3.0 Preview 4 開始，在 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間中不小心重複的一些 Api，已在 .NET Core 3.0 RC1 中移除。

#### <a name="change-description"></a>變更描述

.NET Core 3.0 Preview 4 不小心複製 <xref:System.ComponentModel.Design?displayProperty=fullName> 命名空間中已存在的 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間中的數種類型。 從 .NET Core 3.0 RC1 開始，這些重複的類型已無法再使用。 下表顯示原始類型和其重複類型的清單：

> [!div class="mx-tdCol2BreakAll"]
> |原始類型|重複的類型|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>引進的版本

3.0 RC1

#### <a name="recommended-action"></a>建議的動作

更新程式碼以參考原始類型，如資料表的**原始類型**資料行所示。

#### <a name="category"></a>分類

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- 無法透過 API 分析來偵測。

<!--

### Affected APIs

- Not detectable via API analysis.

-->
