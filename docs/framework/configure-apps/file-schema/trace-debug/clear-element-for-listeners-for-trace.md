---
title: 適用于 <listeners> 的 <clear> 元素 <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 049b8e7ed17633c0f34b062915afaf719927dad6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088920"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="2b140-102">\<清除 \<追蹤 > 的 \<接聽程式 > 元素 ></span><span class="sxs-lookup"><span data-stu-id="2b140-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="2b140-103">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="2b140-103">Clears the `Listeners` collection for trace.</span></span>  

<span data-ttu-id="2b140-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b140-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b140-105">&nbsp;&nbsp;[ **\<系統診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b140-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="2b140-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b140-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="2b140-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<接聽程式[ **>** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="2b140-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="2b140-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="2b140-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2b140-109">語法</span><span class="sxs-lookup"><span data-stu-id="2b140-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b140-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b140-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b140-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2b140-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b140-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2b140-112">Attributes</span></span>  
 <span data-ttu-id="2b140-113">無。</span><span class="sxs-lookup"><span data-stu-id="2b140-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b140-114">子項目</span><span class="sxs-lookup"><span data-stu-id="2b140-114">Child Elements</span></span>  
 <span data-ttu-id="2b140-115">無。</span><span class="sxs-lookup"><span data-stu-id="2b140-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b140-116">父項目</span><span class="sxs-lookup"><span data-stu-id="2b140-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2b140-117">項目</span><span class="sxs-lookup"><span data-stu-id="2b140-117">Element</span></span>|<span data-ttu-id="2b140-118">描述</span><span class="sxs-lookup"><span data-stu-id="2b140-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2b140-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2b140-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2b140-120">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="2b140-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="2b140-121">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="2b140-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="2b140-122">包含收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="2b140-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="2b140-123">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="2b140-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b140-124">備註</span><span class="sxs-lookup"><span data-stu-id="2b140-124">Remarks</span></span>  
 <span data-ttu-id="2b140-125">`<clear>` 元素會從 trace 的 `Listeners` 集合中移除所有接聽程式。</span><span class="sxs-lookup"><span data-stu-id="2b140-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="2b140-126">您可以使用 `<clear>` 專案，然後再使用 `<add>` 元素，以確保集合中沒有其他作用中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="2b140-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="2b140-127">您可以在 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> 屬性（`System.Diagnostics.Trace.Listeners.Clear()`）上呼叫 <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> 方法，以程式設計方式清除 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="2b140-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="2b140-128">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="2b140-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b140-129">`<clear>` 元素會從 `Listeners` 集合中移除 <xref:System.Diagnostics.DefaultTraceListener>、改變 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>、<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> 方法的行為。</span><span class="sxs-lookup"><span data-stu-id="2b140-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="2b140-130">呼叫 `Assert` 或 `Fail` 方法通常會導致訊息方塊的顯示。</span><span class="sxs-lookup"><span data-stu-id="2b140-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="2b140-131">不過，如果 <xref:System.Diagnostics.DefaultTraceListener> 不在 `Listeners` 集合中，則不會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="2b140-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b140-132">範例</span><span class="sxs-lookup"><span data-stu-id="2b140-132">Example</span></span>  
 <span data-ttu-id="2b140-133">下列範例示範如何使用 `<clear>` 專案，然後再使用 `<add>` 元素，將接聽程式 `console` 加入至追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="2b140-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="2b140-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="2b140-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="2b140-135">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2b140-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b140-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="2b140-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="2b140-137">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="2b140-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
