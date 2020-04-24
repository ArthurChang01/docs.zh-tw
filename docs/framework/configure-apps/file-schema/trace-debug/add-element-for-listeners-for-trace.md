---
title: <add><listeners> For 的元素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153668"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="937a1-102">\<為追蹤> 的\< \<接聽程式> 加入> 元素</span><span class="sxs-lookup"><span data-stu-id="937a1-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="937a1-103">將接聽程式加入至接聽**程式集合。**</span><span class="sxs-lookup"><span data-stu-id="937a1-103">Adds a listener to the **Listeners** collection.</span></span>  

<span data-ttu-id="937a1-104">[**\<設定>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="937a1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="937a1-105">&nbsp;&nbsp;[**\<系統診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="937a1-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="937a1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<追蹤>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="937a1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="937a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<接聽程式>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="937a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="937a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<新增>**</span><span class="sxs-lookup"><span data-stu-id="937a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="937a1-109">語法</span><span class="sxs-lookup"><span data-stu-id="937a1-109">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="937a1-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="937a1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="937a1-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="937a1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="937a1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="937a1-112">Attributes</span></span>  
  
|<span data-ttu-id="937a1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="937a1-113">Attribute</span></span>|<span data-ttu-id="937a1-114">描述</span><span class="sxs-lookup"><span data-stu-id="937a1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="937a1-115">**type**</span><span class="sxs-lookup"><span data-stu-id="937a1-115">**type**</span></span>|<span data-ttu-id="937a1-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="937a1-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="937a1-117">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="937a1-117">Specifies the type of the listener.</span></span> <span data-ttu-id="937a1-118">您必須使用符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="937a1-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="937a1-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="937a1-119">**initializeData**</span></span>|<span data-ttu-id="937a1-120">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="937a1-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="937a1-121">傳遞至指定類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="937a1-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="937a1-122">**name**</span><span class="sxs-lookup"><span data-stu-id="937a1-122">**name**</span></span>|<span data-ttu-id="937a1-123">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="937a1-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="937a1-124">指定接聽程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="937a1-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="937a1-125">子元素</span><span class="sxs-lookup"><span data-stu-id="937a1-125">Child Elements</span></span>  
  
|<span data-ttu-id="937a1-126">元素</span><span class="sxs-lookup"><span data-stu-id="937a1-126">Element</span></span>|<span data-ttu-id="937a1-127">描述</span><span class="sxs-lookup"><span data-stu-id="937a1-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="937a1-128">\<篩選></span><span class="sxs-lookup"><span data-stu-id="937a1-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="937a1-129">將篩選加入至追蹤之`Listeners`集合中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="937a1-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="937a1-130">父項目</span><span class="sxs-lookup"><span data-stu-id="937a1-130">Parent Elements</span></span>  
  
|<span data-ttu-id="937a1-131">元素</span><span class="sxs-lookup"><span data-stu-id="937a1-131">Element</span></span>|<span data-ttu-id="937a1-132">描述</span><span class="sxs-lookup"><span data-stu-id="937a1-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="937a1-133">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="937a1-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="937a1-134">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="937a1-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="937a1-135">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="937a1-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="937a1-136">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="937a1-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="937a1-137">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="937a1-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="937a1-138">備註</span><span class="sxs-lookup"><span data-stu-id="937a1-138">Remarks</span></span>  
 <span data-ttu-id="937a1-139">和類別會共用相同的接聽程式集合。 **Listeners** <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace></span><span class="sxs-lookup"><span data-stu-id="937a1-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="937a1-140">如果您將接聽程式物件加入其中一個類別中的集合，另一個類別會使用相同的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="937a1-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="937a1-141">接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>。</span><span class="sxs-lookup"><span data-stu-id="937a1-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="937a1-142">如果您沒有指定追蹤接聽`name`項的屬性， <xref:System.Diagnostics.TraceListener.Name%2A>追蹤接聽程式的會預設為空字串（""）。</span><span class="sxs-lookup"><span data-stu-id="937a1-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="937a1-143">如果您的應用程式只有一個接聽程式，您可以在不指定名稱的情況下新增它，並藉由指定名稱的空字串將它移除。</span><span class="sxs-lookup"><span data-stu-id="937a1-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="937a1-144">不過，如果您的應用程式有多個接聽程式，您應該為每個追蹤接聽項指定唯一的名稱，讓您識別及管理和<xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A>集合內的個別追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="937a1-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="937a1-145">加入多個相同類型且具有相同名稱的追蹤接聽程式，只會導致該類型和名稱的一個追蹤接聽項加入至`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="937a1-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="937a1-146">不過，您可以透過程式設計的方式，將`Listeners`多個相同的接聽程式加入至集合。</span><span class="sxs-lookup"><span data-stu-id="937a1-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="937a1-147">**InitializeData**屬性的值取決於您所建立的接聽程式類型。</span><span class="sxs-lookup"><span data-stu-id="937a1-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="937a1-148">並非所有的追蹤接聽程式都需要您指定**initializeData**。</span><span class="sxs-lookup"><span data-stu-id="937a1-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="937a1-149">當您使用`initializeData`屬性時，您可能會收到編譯器警告：「' initializeData ' 屬性未宣告」。</span><span class="sxs-lookup"><span data-stu-id="937a1-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="937a1-150">之所以會發生這個警告，是因為系統會針對抽象基類驗證<xref:System.Diagnostics.TraceListener>設定值，而該類別`initializeData`無法辨識屬性。</span><span class="sxs-lookup"><span data-stu-id="937a1-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="937a1-151">一般來說，您可以忽略具有接受參數之函式的追蹤接聽程式執行的這個警告。</span><span class="sxs-lookup"><span data-stu-id="937a1-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="937a1-152">下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其**initializeData**屬性的值。</span><span class="sxs-lookup"><span data-stu-id="937a1-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="937a1-153">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="937a1-153">Trace listener class</span></span>|<span data-ttu-id="937a1-154">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="937a1-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="937a1-155">此`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>函式的值。</span><span class="sxs-lookup"><span data-stu-id="937a1-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="937a1-156">將`initializeData`屬性設定為 "`true`"，以將追蹤和調試輸出<xref:System.Console.Error%2A?displayProperty=nameWithType>寫入至;要`false`寫入的 "" <xref:System.Console.Out%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="937a1-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="937a1-157"><xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="937a1-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="937a1-158">現有事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="937a1-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="937a1-159">寫入的<xref:System.Diagnostics.EventSchemaTraceListener>檔案名。</span><span class="sxs-lookup"><span data-stu-id="937a1-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="937a1-160">寫入的<xref:System.Diagnostics.TextWriterTraceListener>檔案名。</span><span class="sxs-lookup"><span data-stu-id="937a1-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="937a1-161">寫入的<xref:System.Diagnostics.XmlWriterTraceListener>檔案名。</span><span class="sxs-lookup"><span data-stu-id="937a1-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="937a1-162">範例</span><span class="sxs-lookup"><span data-stu-id="937a1-162">Example</span></span>  
 <span data-ttu-id="937a1-163">下列範例示範如何使用\*\* \<add>\*\* 專案，將接聽`MyListener`程式和`MyEventListener`加入至接聽程式**集合。**</span><span class="sxs-lookup"><span data-stu-id="937a1-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="937a1-164">`MyListener`建立名`MyListener.log`為的檔案，並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="937a1-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="937a1-165">`MyEventListener`在事件記錄檔中建立專案。</span><span class="sxs-lookup"><span data-stu-id="937a1-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="937a1-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="937a1-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="937a1-167">追蹤和 Debug 設定架構</span><span class="sxs-lookup"><span data-stu-id="937a1-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="937a1-168">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="937a1-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
