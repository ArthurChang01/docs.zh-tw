---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803221"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="71c0e-101">分析 ASP.Net MVC4 應用程式可能會導致嚴重的執行引擎錯誤</span><span class="sxs-lookup"><span data-stu-id="71c0e-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="71c0e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="71c0e-102">Details</span></span>|<span data-ttu-id="71c0e-103">使用 NGEN /Profile 組件的分析工具可能會在啟動時損毀已分析的 ASP.NET MVC4 應用程式，並顯示「嚴重的執行引擎例外狀況」</span><span class="sxs-lookup"><span data-stu-id="71c0e-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="71c0e-104">建議</span><span class="sxs-lookup"><span data-stu-id="71c0e-104">Suggestion</span></span>|<span data-ttu-id="71c0e-105">此問題在 .NET Framework 4.5.2 中已修正。</span><span class="sxs-lookup"><span data-stu-id="71c0e-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="71c0e-106">或者，分析工具時可能會藉由在其事件遮罩中指定 <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> 來避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="71c0e-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="71c0e-107">影響範圍</span><span class="sxs-lookup"><span data-stu-id="71c0e-107">Scope</span></span>|<span data-ttu-id="71c0e-108">Edge</span><span class="sxs-lookup"><span data-stu-id="71c0e-108">Edge</span></span>|
|<span data-ttu-id="71c0e-109">版本</span><span class="sxs-lookup"><span data-stu-id="71c0e-109">Version</span></span>|<span data-ttu-id="71c0e-110">4.5</span><span class="sxs-lookup"><span data-stu-id="71c0e-110">4.5</span></span>|
|<span data-ttu-id="71c0e-111">類型</span><span class="sxs-lookup"><span data-stu-id="71c0e-111">Type</span></span>|<span data-ttu-id="71c0e-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="71c0e-112">Runtime</span></span>|
