---
title: <memoryCache> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153980"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="dcef7-102">\<記憶體緩存>元素（緩存設置）</span><span class="sxs-lookup"><span data-stu-id="dcef7-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="dcef7-103">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="dcef7-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="dcef7-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement> 類別定義可用來設定快取的 [memoryCache](memorycache-element-cache-settings.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="dcef7-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="dcef7-105">多個 <xref:System.Runtime.Caching.MemoryCache> 類別執行個體可以用於單一應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcef7-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="dcef7-106">組態檔中的每個 `memoryCache` 項目都可以包含具名 <xref:System.Runtime.Caching.MemoryCache> 執行個體的設定。</span><span class="sxs-lookup"><span data-stu-id="dcef7-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
<span data-ttu-id="dcef7-107">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dcef7-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dcef7-108">&nbsp;&nbsp;[**\<系統.運行時.緩存>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="dcef7-108">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="dcef7-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<記憶體緩存>**</span><span class="sxs-lookup"><span data-stu-id="dcef7-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcef7-110">語法</span><span class="sxs-lookup"><span data-stu-id="dcef7-110">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="dcef7-111">類型</span><span class="sxs-lookup"><span data-stu-id="dcef7-111">Type</span></span>  
 <span data-ttu-id="dcef7-112"><xref:System.Runtime.Caching.MemoryCache> 類別。</span><span class="sxs-lookup"><span data-stu-id="dcef7-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcef7-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dcef7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="dcef7-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dcef7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcef7-115">屬性</span><span class="sxs-lookup"><span data-stu-id="dcef7-115">Attributes</span></span>  
  
|<span data-ttu-id="dcef7-116">屬性</span><span class="sxs-lookup"><span data-stu-id="dcef7-116">Attribute</span></span>|<span data-ttu-id="dcef7-117">描述</span><span class="sxs-lookup"><span data-stu-id="dcef7-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="dcef7-118"><xref:System.Runtime.Caching.MemoryCache> 物件執行個體可以成長的最大記憶體大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="dcef7-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="dcef7-119">預設值為 0，表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 類別的自動調整啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="dcef7-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="dcef7-120">快取組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="dcef7-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="dcef7-121">快取可使用的實體記憶體百分比。</span><span class="sxs-lookup"><span data-stu-id="dcef7-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="dcef7-122">預設值為 0，表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 類別的自動調整啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="dcef7-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="dcef7-123">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="dcef7-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="dcef7-124">此值是以 "HH:MM:SS" 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="dcef7-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcef7-125">子元素</span><span class="sxs-lookup"><span data-stu-id="dcef7-125">Child Elements</span></span>  
  
|<span data-ttu-id="dcef7-126">元素</span><span class="sxs-lookup"><span data-stu-id="dcef7-126">Element</span></span>|<span data-ttu-id="dcef7-127">描述</span><span class="sxs-lookup"><span data-stu-id="dcef7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcef7-128">\<具名快取></span><span class="sxs-lookup"><span data-stu-id="dcef7-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="dcef7-129">包含 `namedCache` 執行個體的組態設定集合。</span><span class="sxs-lookup"><span data-stu-id="dcef7-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dcef7-130">父項目</span><span class="sxs-lookup"><span data-stu-id="dcef7-130">Parent Elements</span></span>  
  
|<span data-ttu-id="dcef7-131">元素</span><span class="sxs-lookup"><span data-stu-id="dcef7-131">Element</span></span>|<span data-ttu-id="dcef7-132">描述</span><span class="sxs-lookup"><span data-stu-id="dcef7-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcef7-133">\<配置></span><span class="sxs-lookup"><span data-stu-id="dcef7-133">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="dcef7-134">指定通用語言運行時和 .NET Framework 應用程式使用的每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="dcef7-134">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="dcef7-135">\<系統.運行時.緩存></span><span class="sxs-lookup"><span data-stu-id="dcef7-135">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="dcef7-136">包含允許您在內置於 .NET 框架中的應用程式中實現輸出緩存的類型。</span><span class="sxs-lookup"><span data-stu-id="dcef7-136">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcef7-137">備註</span><span class="sxs-lookup"><span data-stu-id="dcef7-137">Remarks</span></span>  
 <span data-ttu-id="dcef7-138"><xref:System.Runtime.Caching.MemoryCache> 類別是抽象 <xref:System.Runtime.Caching.ObjectCache> 類別的具體實作。</span><span class="sxs-lookup"><span data-stu-id="dcef7-138">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="dcef7-139"><xref:System.Runtime.Caching.MemoryCache> 類別執行個體可以與應用程式組態檔中的組態資訊一起提供。</span><span class="sxs-lookup"><span data-stu-id="dcef7-139">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="dcef7-140">[memoryCache](memorycache-element-cache-settings.md) 組態區段包含 `namedCaches` 組態集合。</span><span class="sxs-lookup"><span data-stu-id="dcef7-140">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="dcef7-141">初始化記憶體型快取物件時，會先嘗試尋找 `namedCaches` 項目，而此項目符合傳遞給記憶體快取建構函式之參數中的名稱。</span><span class="sxs-lookup"><span data-stu-id="dcef7-141">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="dcef7-142">如果找不到 `namedCaches` 項目，則會從組態檔中擷取輪詢和記憶體管理資訊。</span><span class="sxs-lookup"><span data-stu-id="dcef7-142">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="dcef7-143">初始化程序接著會判斷是否已覆寫任何組態項目，方法是在建構函式中使用組態資訊的選擇性名稱/值組集合。</span><span class="sxs-lookup"><span data-stu-id="dcef7-143">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="dcef7-144">如果您在名稱/值組集合中傳遞下列任何一個值，則這些值會覆寫從組態檔取得的資訊︰</span><span class="sxs-lookup"><span data-stu-id="dcef7-144">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="dcef7-145">範例</span><span class="sxs-lookup"><span data-stu-id="dcef7-145">Example</span></span>  
 <span data-ttu-id="dcef7-146">下面的示例演示如何通過將<xref:System.Runtime.Caching.MemoryCache>`name`屬性設置為"預設"來將物件的名稱設置為預設緩存物件名稱。</span><span class="sxs-lookup"><span data-stu-id="dcef7-146">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="dcef7-147">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryLimitPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="dcef7-147">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="dcef7-148">將這些屬性設定為零表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 自動調整啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="dcef7-148">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="dcef7-149">快取實作應該會每隔兩分鐘即比較目前的記憶體負載與絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="dcef7-149">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcef7-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcef7-150">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="dcef7-151">\<系統.運行時.緩存>元素（緩存設置）</span><span class="sxs-lookup"><span data-stu-id="dcef7-151">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="dcef7-152">\<具名快取>元素（緩存設置）</span><span class="sxs-lookup"><span data-stu-id="dcef7-152">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
