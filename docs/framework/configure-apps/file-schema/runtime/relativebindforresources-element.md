---
title: <relativeBindForResources> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153902"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="5215d-102">\<相對綁定資源>元素</span><span class="sxs-lookup"><span data-stu-id="5215d-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="5215d-103">最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="5215d-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="5215d-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5215d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5215d-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5215d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5215d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<相對綁定資源>**</span><span class="sxs-lookup"><span data-stu-id="5215d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5215d-107">語法</span><span class="sxs-lookup"><span data-stu-id="5215d-107">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5215d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5215d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5215d-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5215d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5215d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5215d-110">Attributes</span></span>  
  
|<span data-ttu-id="5215d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5215d-111">Attribute</span></span>|<span data-ttu-id="5215d-112">描述</span><span class="sxs-lookup"><span data-stu-id="5215d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5215d-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5215d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5215d-114">指定通用語言運行時是否優化了附屬程式集的探測。</span><span class="sxs-lookup"><span data-stu-id="5215d-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5215d-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="5215d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5215d-116">值</span><span class="sxs-lookup"><span data-stu-id="5215d-116">Value</span></span>|<span data-ttu-id="5215d-117">描述</span><span class="sxs-lookup"><span data-stu-id="5215d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5215d-118">運行時不優化衛星元件的探測。</span><span class="sxs-lookup"><span data-stu-id="5215d-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="5215d-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="5215d-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="5215d-120">運行時優化了衛星元件的探測。</span><span class="sxs-lookup"><span data-stu-id="5215d-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5215d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="5215d-121">Child Elements</span></span>  
 <span data-ttu-id="5215d-122">無。</span><span class="sxs-lookup"><span data-stu-id="5215d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5215d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="5215d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5215d-124">元素</span><span class="sxs-lookup"><span data-stu-id="5215d-124">Element</span></span>|<span data-ttu-id="5215d-125">描述</span><span class="sxs-lookup"><span data-stu-id="5215d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5215d-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5215d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5215d-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="5215d-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5215d-128">備註</span><span class="sxs-lookup"><span data-stu-id="5215d-128">Remarks</span></span>  
 <span data-ttu-id="5215d-129">通常，資源管理器會調查資源，如["打包和部署資源](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)"主題中所述。</span><span class="sxs-lookup"><span data-stu-id="5215d-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="5215d-130">這意味著，當資源管理器探測資源的特定當地語系化版本時，它可能會查看全域組件快取、在應用程式代碼庫中查看特定于區域性的資料夾、查詢 Windows 安裝程式以查找附屬程式集以及引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="5215d-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="5215d-131">該`<relativeBindForResources>`元素優化了資源管理器探測附屬程式集的方式。</span><span class="sxs-lookup"><span data-stu-id="5215d-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="5215d-132">在以下條件下探測資源時，它可以提高性能：</span><span class="sxs-lookup"><span data-stu-id="5215d-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="5215d-133">當附屬程式集部署在同一位置的代碼程式集時。</span><span class="sxs-lookup"><span data-stu-id="5215d-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="5215d-134">換句話說，如果代碼程式集安裝在全域組件快取中，則還必須在那裡安裝附屬程式集。</span><span class="sxs-lookup"><span data-stu-id="5215d-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="5215d-135">如果代碼程式集安裝在應用程式的代碼庫中，則附屬程式集也必須安裝在代碼庫中特定于區域性的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5215d-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="5215d-136">當不使用 Windows 安裝程式或很少用於按需安裝附屬程式集時。</span><span class="sxs-lookup"><span data-stu-id="5215d-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="5215d-137">當應用程式代碼不處理事件<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>時。</span><span class="sxs-lookup"><span data-stu-id="5215d-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="5215d-138">設置`enabled``<relativeBindForResources>`元素的屬性以`true`優化資源管理器對附屬程式集的探測，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5215d-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="5215d-139">它使用父代碼程式集的位置來探測附屬程式集。</span><span class="sxs-lookup"><span data-stu-id="5215d-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="5215d-140">它不查詢 Windows 安裝程式的附屬程式集。</span><span class="sxs-lookup"><span data-stu-id="5215d-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="5215d-141">它不引發事件<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5215d-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5215d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5215d-142">See also</span></span>

- [<span data-ttu-id="5215d-143">封裝和部署資源</span><span class="sxs-lookup"><span data-stu-id="5215d-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="5215d-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5215d-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5215d-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5215d-145">Configuration File Schema</span></span>](../index.md)
