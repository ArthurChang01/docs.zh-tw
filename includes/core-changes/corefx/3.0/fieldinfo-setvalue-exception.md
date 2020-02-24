---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449545"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="3a99f-101">FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況</span><span class="sxs-lookup"><span data-stu-id="3a99f-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="3a99f-102">從 .NET Core 3.0 開始，當您嘗試藉由呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>來設定靜態、<xref:System.Reflection.FieldAttributes.InitOnly> 欄位的值時，就會擲回例外狀況（exception）。</span><span class="sxs-lookup"><span data-stu-id="3a99f-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a99f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="3a99f-103">Change description</span></span>

<span data-ttu-id="3a99f-104">在3.0 之前的 .net Core .NET Framework 和版本中，您可以藉由呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>，設定靜態欄位在初始化後為常數的值（[在C#中為 readonly ](~/docs/csharp/language-reference/keywords/readonly.md)）。</span><span class="sxs-lookup"><span data-stu-id="3a99f-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="3a99f-105">不過，以這種方式設定這類欄位，會根據目標 framework 和優化設定導致無法預期的行為。</span><span class="sxs-lookup"><span data-stu-id="3a99f-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="3a99f-106">在 .NET Core 3.0 和更新版本中，當您在靜態 <xref:System.Reflection.FieldAttributes.InitOnly> 欄位上呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A> 時，會擲回 <xref:System.FieldAccessException?displayProperty=nameWithType> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3a99f-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="3a99f-107"><xref:System.Reflection.FieldAttributes.InitOnly> 欄位只能在宣告時或在包含類別的函式中進行設定。</span><span class="sxs-lookup"><span data-stu-id="3a99f-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="3a99f-108">換句話說，它會在初始化後保持不變。</span><span class="sxs-lookup"><span data-stu-id="3a99f-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a99f-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a99f-109">Version introduced</span></span>

<span data-ttu-id="3a99f-110">3.0</span><span class="sxs-lookup"><span data-stu-id="3a99f-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a99f-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3a99f-111">Recommended action</span></span>

<span data-ttu-id="3a99f-112">在靜態的函式中初始化 static、<xref:System.Reflection.FieldAttributes.InitOnly> 欄位。</span><span class="sxs-lookup"><span data-stu-id="3a99f-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="3a99f-113">這同時適用于動態和非動態類型。</span><span class="sxs-lookup"><span data-stu-id="3a99f-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="3a99f-114">或者，您可以從欄位移除 <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> 屬性，然後呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3a99f-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="3a99f-115">類別</span><span class="sxs-lookup"><span data-stu-id="3a99f-115">Category</span></span>

<span data-ttu-id="3a99f-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="3a99f-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a99f-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3a99f-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->