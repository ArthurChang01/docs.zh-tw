---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803221"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>分析 ASP.Net MVC4 應用程式可能會導致嚴重的執行引擎錯誤

|   |   |
|---|---|
|詳細資料|使用 NGEN /Profile 組件的分析工具可能會在啟動時損毀已分析的 ASP.NET MVC4 應用程式，並顯示「嚴重的執行引擎例外狀況」|
|建議|此問題在 .NET Framework 4.5.2 中已修正。 或者，分析工具時可能會藉由在其事件遮罩中指定 <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> 來避免這個問題。|
|影響範圍|Edge|
|版本|4.5|
|類型|執行階段|
