---
title: <TimeSpan_LegacyFormatMode> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: c835e1bcef7bbfdc990c8db177eafed4ec6bb30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115206"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="03ae5-102">\<TimeSpan_LegacyFormatMode > 元素</span><span class="sxs-lookup"><span data-stu-id="03ae5-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="03ae5-103">判斷執行時間是否會以 <xref:System.TimeSpan?displayProperty=nameWithType> 值在格式化作業中保留舊版行為。</span><span class="sxs-lookup"><span data-stu-id="03ae5-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="03ae5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="03ae5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="03ae5-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="03ae5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="03ae5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**</span><span class="sxs-lookup"><span data-stu-id="03ae5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="03ae5-107">語法</span><span class="sxs-lookup"><span data-stu-id="03ae5-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03ae5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="03ae5-108">Attributes and Elements</span></span>

<span data-ttu-id="03ae5-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="03ae5-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="03ae5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="03ae5-110">Attributes</span></span>

|<span data-ttu-id="03ae5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="03ae5-111">Attribute</span></span>|<span data-ttu-id="03ae5-112">描述</span><span class="sxs-lookup"><span data-stu-id="03ae5-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="03ae5-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="03ae5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="03ae5-114">指定執行時間是否使用具有 <xref:System.TimeSpan?displayProperty=nameWithType> 值的舊版格式行為。</span><span class="sxs-lookup"><span data-stu-id="03ae5-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="03ae5-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="03ae5-115">enabled Attribute</span></span>

|<span data-ttu-id="03ae5-116">值</span><span class="sxs-lookup"><span data-stu-id="03ae5-116">Value</span></span>|<span data-ttu-id="03ae5-117">描述</span><span class="sxs-lookup"><span data-stu-id="03ae5-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="03ae5-118">執行時間不會還原舊版格式設定行為。</span><span class="sxs-lookup"><span data-stu-id="03ae5-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="03ae5-119">執行時間會還原舊版格式設定行為。</span><span class="sxs-lookup"><span data-stu-id="03ae5-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="03ae5-120">子項目</span><span class="sxs-lookup"><span data-stu-id="03ae5-120">Child Elements</span></span>

<span data-ttu-id="03ae5-121">無。</span><span class="sxs-lookup"><span data-stu-id="03ae5-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="03ae5-122">父項目</span><span class="sxs-lookup"><span data-stu-id="03ae5-122">Parent Elements</span></span>

|<span data-ttu-id="03ae5-123">項目</span><span class="sxs-lookup"><span data-stu-id="03ae5-123">Element</span></span>|<span data-ttu-id="03ae5-124">描述</span><span class="sxs-lookup"><span data-stu-id="03ae5-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="03ae5-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="03ae5-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="03ae5-126">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="03ae5-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="03ae5-127">備註</span><span class="sxs-lookup"><span data-stu-id="03ae5-127">Remarks</span></span>

<span data-ttu-id="03ae5-128">從 .NET Framework 4 開始，<xref:System.TimeSpan?displayProperty=nameWithType> 結構會執行 <xref:System.IFormattable> 介面，並支援使用標準和自訂格式字串的格式化作業。</span><span class="sxs-lookup"><span data-stu-id="03ae5-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="03ae5-129">如果剖析方法遇到不支援的格式規範或格式字串，它會擲回 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="03ae5-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="03ae5-130">在舊版的 .NET Framework 中，<xref:System.TimeSpan> 結構不會執行 <xref:System.IFormattable> 且不支援格式字串。</span><span class="sxs-lookup"><span data-stu-id="03ae5-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="03ae5-131">不過，許多開發人員不小心認為 <xref:System.TimeSpan> 的確支援一組格式字串，並在[複合格式作業](../../../../standard/base-types/composite-formatting.md)中使用 <xref:System.String.Format%2A?displayProperty=nameWithType>之類的方法。</span><span class="sxs-lookup"><span data-stu-id="03ae5-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="03ae5-132">一般來說，如果型別會執行 <xref:System.IFormattable> 並支援格式字串，則使用不支援的格式字串呼叫格式化方法通常會擲回 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="03ae5-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="03ae5-133">不過，因為 <xref:System.TimeSpan> 不會執行 <xref:System.IFormattable>，所以執行時間會忽略格式字串，而改為呼叫 <xref:System.TimeSpan.ToString?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="03ae5-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="03ae5-134">這表示，雖然格式字串不會影響格式化作業，但它們的存在並不會導致 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="03ae5-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="03ae5-135">若是舊版程式碼傳遞複合格式化方法和不正確格式字串，而且該程式碼無法重新編譯的情況，您可以使用 `<TimeSpan_LegacyFormatMode>` 元素來還原舊版的 <xref:System.TimeSpan> 行為。</span><span class="sxs-lookup"><span data-stu-id="03ae5-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="03ae5-136">當您將這個專案的 `enabled` 屬性設定為 `true`時，複合格式方法會導致對 <xref:System.TimeSpan.ToString?displayProperty=nameWithType> 而不是 <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>的呼叫，而且不會擲回 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="03ae5-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="03ae5-137">範例</span><span class="sxs-lookup"><span data-stu-id="03ae5-137">Example</span></span>

<span data-ttu-id="03ae5-138">下列範例會具現化 <xref:System.TimeSpan> 物件，並使用不支援的標準格式字串，嘗試使用 <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> 方法來設定它的格式。</span><span class="sxs-lookup"><span data-stu-id="03ae5-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="03ae5-139">當您在 .NET Framework 3.5 或較舊版本上執行此範例時，會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="03ae5-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="03ae5-140">如果您在 .NET Framework 4 或更新版本上執行範例，則與輸出的差異明顯不同：</span><span class="sxs-lookup"><span data-stu-id="03ae5-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="03ae5-141">不過，如果您將下列設定檔新增至範例的目錄，然後在 .NET Framework 4 或更新版本上執行範例，則輸出會與範例在 .NET Framework 3.5 上執行時所產生的相同。</span><span class="sxs-lookup"><span data-stu-id="03ae5-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="03ae5-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="03ae5-142">See also</span></span>

- [<span data-ttu-id="03ae5-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="03ae5-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="03ae5-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="03ae5-144">Configuration File Schema</span></span>](../index.md)
