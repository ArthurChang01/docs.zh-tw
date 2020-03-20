---
title: <runtime> 的 <assemblyBinding> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154318"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="5f015-102">\<用於\<運行時>的程式集綁定>元素</span><span class="sxs-lookup"><span data-stu-id="5f015-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="5f015-103">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f015-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
<span data-ttu-id="5f015-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5f015-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5f015-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5f015-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5f015-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<程式集綁定>**</span><span class="sxs-lookup"><span data-stu-id="5f015-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f015-107">語法</span><span class="sxs-lookup"><span data-stu-id="5f015-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f015-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f015-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5f015-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5f015-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f015-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5f015-110">Attributes</span></span>  
  
|<span data-ttu-id="5f015-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5f015-111">Attribute</span></span>|<span data-ttu-id="5f015-112">描述</span><span class="sxs-lookup"><span data-stu-id="5f015-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f015-113">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="5f015-113">**xmlns**</span></span>|<span data-ttu-id="5f015-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5f015-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="5f015-115">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="5f015-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="5f015-116">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="5f015-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="5f015-117">**適用于**</span><span class="sxs-lookup"><span data-stu-id="5f015-117">**appliesTo**</span></span>|<span data-ttu-id="5f015-118">指定 .NET Framework 組件重新導向適用的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="5f015-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="5f015-119">這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="5f015-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="5f015-120">如果未指定 **appliesTo** 屬性，則 **\<assemblyBinding>** 項目會套用至所有的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="5f015-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="5f015-121">**應用到**屬性在 .NET 框架版本 1.1 中引入;.NET 框架版本 1.0 會忽略它。</span><span class="sxs-lookup"><span data-stu-id="5f015-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="5f015-122">這意味著在使用 .NET Framework 版本 1.0 時應用所有**\<程式集綁定>** 元素，即使指定了**應用To**屬性也是如此。</span><span class="sxs-lookup"><span data-stu-id="5f015-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f015-123">子元素</span><span class="sxs-lookup"><span data-stu-id="5f015-123">Child Elements</span></span>  
  
|<span data-ttu-id="5f015-124">元素</span><span class="sxs-lookup"><span data-stu-id="5f015-124">Element</span></span>|<span data-ttu-id="5f015-125">描述</span><span class="sxs-lookup"><span data-stu-id="5f015-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f015-126">\<從屬裝配></span><span class="sxs-lookup"><span data-stu-id="5f015-126">\<dependentAssembly></span></span>](dependentassembly-element.md)|<span data-ttu-id="5f015-127">封裝組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="5f015-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="5f015-128">為每個程式集使用一個**\<依存性程式集>** 標記。</span><span class="sxs-lookup"><span data-stu-id="5f015-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="5f015-129">\<探測></span><span class="sxs-lookup"><span data-stu-id="5f015-129">\<probing></span></span>](probing-element.md)|<span data-ttu-id="5f015-130">指定載入組件時，Common Language Runtime 會搜尋的子目錄。</span><span class="sxs-lookup"><span data-stu-id="5f015-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="5f015-131">\<發行者策略></span><span class="sxs-lookup"><span data-stu-id="5f015-131">\<publisherPolicy></span></span>](publisherpolicy-element.md)|<span data-ttu-id="5f015-132">指定執行階段是否套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="5f015-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="5f015-133">\<符合條件></span><span class="sxs-lookup"><span data-stu-id="5f015-133">\<qualifyAssembly></span></span>](qualifyassembly-element.md)|<span data-ttu-id="5f015-134">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="5f015-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f015-135">父項目</span><span class="sxs-lookup"><span data-stu-id="5f015-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5f015-136">元素</span><span class="sxs-lookup"><span data-stu-id="5f015-136">Element</span></span>|<span data-ttu-id="5f015-137">描述</span><span class="sxs-lookup"><span data-stu-id="5f015-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5f015-138">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5f015-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5f015-139">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f015-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5f015-140">範例</span><span class="sxs-lookup"><span data-stu-id="5f015-140">Example</span></span>  
 <span data-ttu-id="5f015-141">下列範例將示範如何將某一個組件版本重新導向至另一個版本，並提供程式碼庫。</span><span class="sxs-lookup"><span data-stu-id="5f015-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="5f015-142">下面的示例演示如何使用**應用 To**屬性重定向 .NET 框架程式集的綁定。</span><span class="sxs-lookup"><span data-stu-id="5f015-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f015-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f015-143">See also</span></span>

- [<span data-ttu-id="5f015-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5f015-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5f015-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5f015-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5f015-146">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="5f015-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
