---
title: <disableCachingBindingFailures> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
ms.openlocfilehash: 23633cb282b8e59b4df4bcc2cd38717d805a207e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117504"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="10afc-102">\<disableCachingBindingFailures > 元素</span><span class="sxs-lookup"><span data-stu-id="10afc-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="10afc-103">指定是否要停用發生的系結失敗快取，因為探查找不到元件。</span><span class="sxs-lookup"><span data-stu-id="10afc-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
<span data-ttu-id="10afc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="10afc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="10afc-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="10afc-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="10afc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCachingBindingFailures >**</span><span class="sxs-lookup"><span data-stu-id="10afc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10afc-107">語法</span><span class="sxs-lookup"><span data-stu-id="10afc-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10afc-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="10afc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="10afc-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="10afc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10afc-110">屬性</span><span class="sxs-lookup"><span data-stu-id="10afc-110">Attributes</span></span>  
  
|<span data-ttu-id="10afc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="10afc-111">Attribute</span></span>|<span data-ttu-id="10afc-112">描述</span><span class="sxs-lookup"><span data-stu-id="10afc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10afc-113">enabled</span><span class="sxs-lookup"><span data-stu-id="10afc-113">enabled</span></span>|<span data-ttu-id="10afc-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="10afc-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="10afc-115">指定是否要停用發生的系結失敗快取，因為探查找不到元件。</span><span class="sxs-lookup"><span data-stu-id="10afc-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="10afc-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="10afc-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="10afc-117">值</span><span class="sxs-lookup"><span data-stu-id="10afc-117">Value</span></span>|<span data-ttu-id="10afc-118">描述</span><span class="sxs-lookup"><span data-stu-id="10afc-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10afc-119">0</span><span class="sxs-lookup"><span data-stu-id="10afc-119">0</span></span>|<span data-ttu-id="10afc-120">請勿停用發生的系結失敗快取，因為探查找不到元件。</span><span class="sxs-lookup"><span data-stu-id="10afc-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="10afc-121">從 .NET Framework 版本2.0 開始，這是預設的系結行為。</span><span class="sxs-lookup"><span data-stu-id="10afc-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="10afc-122">1</span><span class="sxs-lookup"><span data-stu-id="10afc-122">1</span></span>|<span data-ttu-id="10afc-123">停用發生的系結失敗快取，因為探查找不到元件。</span><span class="sxs-lookup"><span data-stu-id="10afc-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="10afc-124">此設定會還原為 .NET Framework 版本1.1 的系結行為。</span><span class="sxs-lookup"><span data-stu-id="10afc-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10afc-125">子項目</span><span class="sxs-lookup"><span data-stu-id="10afc-125">Child Elements</span></span>  
 <span data-ttu-id="10afc-126">無。</span><span class="sxs-lookup"><span data-stu-id="10afc-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10afc-127">父項目</span><span class="sxs-lookup"><span data-stu-id="10afc-127">Parent Elements</span></span>  
  
|<span data-ttu-id="10afc-128">項目</span><span class="sxs-lookup"><span data-stu-id="10afc-128">Element</span></span>|<span data-ttu-id="10afc-129">描述</span><span class="sxs-lookup"><span data-stu-id="10afc-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="10afc-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="10afc-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="10afc-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="10afc-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10afc-132">備註</span><span class="sxs-lookup"><span data-stu-id="10afc-132">Remarks</span></span>  
 <span data-ttu-id="10afc-133">從 .NET Framework 版本2.0 開始，載入元件的預設行為是快取所有的系結和載入失敗。</span><span class="sxs-lookup"><span data-stu-id="10afc-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="10afc-134">也就是說，如果嘗試載入元件失敗，後續載入相同元件的要求會立即失敗，而不會嘗試找出元件。</span><span class="sxs-lookup"><span data-stu-id="10afc-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="10afc-135">這個元素會針對發生的系結失敗停用預設行為，因為在探查路徑中找不到該元件。</span><span class="sxs-lookup"><span data-stu-id="10afc-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="10afc-136">這些失敗會擲回 <xref:System.IO.FileNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="10afc-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="10afc-137">某些系結和載入失敗不會受到此元素的影響，而且一律會進行快取。</span><span class="sxs-lookup"><span data-stu-id="10afc-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="10afc-138">因為找到元件，但無法載入，所以會發生這些失敗。</span><span class="sxs-lookup"><span data-stu-id="10afc-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="10afc-139">它們會擲回 <xref:System.BadImageFormatException> 或 <xref:System.IO.FileLoadException>。</span><span class="sxs-lookup"><span data-stu-id="10afc-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="10afc-140">下列清單包含一些這類失敗的範例。</span><span class="sxs-lookup"><span data-stu-id="10afc-140">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="10afc-141">如果您嘗試載入的檔案不是有效的元件，則後續載入元件的嘗試將會失敗，即使錯誤的檔案已被正確的元件取代也一樣。</span><span class="sxs-lookup"><span data-stu-id="10afc-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="10afc-142">如果您嘗試載入由檔案系統鎖定的元件，則即使檔案系統釋放元件之後，載入元件的後續嘗試也會失敗。</span><span class="sxs-lookup"><span data-stu-id="10afc-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="10afc-143">如果您嘗試載入的一個或多個元件版本是在探查路徑中，但您要求的特定版本不在其中，則後續嘗試載入該版本的動作將會失敗，即使將正確的版本移入探查路徑也一樣。</span><span class="sxs-lookup"><span data-stu-id="10afc-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10afc-144">範例</span><span class="sxs-lookup"><span data-stu-id="10afc-144">Example</span></span>  
 <span data-ttu-id="10afc-145">下列範例示範如何停用因為探查找不到元件而發生的元件系結失敗的快取。</span><span class="sxs-lookup"><span data-stu-id="10afc-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10afc-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="10afc-146">See also</span></span>

- [<span data-ttu-id="10afc-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="10afc-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="10afc-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="10afc-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="10afc-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="10afc-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
