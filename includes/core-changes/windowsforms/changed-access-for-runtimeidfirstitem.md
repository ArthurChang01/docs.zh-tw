---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003010"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="42138-101">變更 AccessibleObject 的存取權。 RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="42138-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="42138-102">從 .NET Core 3.0 RC1 開始，`AccessibleObject.RuntimeIDFirstItem` 的存取範圍從 `protected` 變更為 `internal`。</span><span class="sxs-lookup"><span data-stu-id="42138-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="42138-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="42138-103">Change description</span></span>

<span data-ttu-id="42138-104">從 .NET Core 3.0 Preview 4 開始，`AccessibleObject.RuntimeIDFirstItem` 欄位已 `protected`。</span><span class="sxs-lookup"><span data-stu-id="42138-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="42138-105">從 .NET Core 3.0 RC1 開始，它已從 `protected` 變更為 `internal`，以配合 .NET Framework 中欄位的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="42138-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="42138-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="42138-106">Version introduced</span></span>

<span data-ttu-id="42138-107">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="42138-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="42138-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="42138-108">Recommended action</span></span>

<span data-ttu-id="42138-109">如果您開發的 .NET Core 應用程式具有衍生自 <xref:System.Windows.Forms.AccessibleObject> 的類型，並存取 `RuntimeIDFirstItem` 欄位，則變更可能會影響您。</span><span class="sxs-lookup"><span data-stu-id="42138-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="42138-110">如果是這種情況，您可以定義本機常數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="42138-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="42138-111">類別</span><span class="sxs-lookup"><span data-stu-id="42138-111">Category</span></span>

<span data-ttu-id="42138-112">Windows Form</span><span class="sxs-lookup"><span data-stu-id="42138-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="42138-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="42138-113">Affected APIs</span></span>

- <span data-ttu-id="42138-114">無法透過 API 分析來偵測。</span><span class="sxs-lookup"><span data-stu-id="42138-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
