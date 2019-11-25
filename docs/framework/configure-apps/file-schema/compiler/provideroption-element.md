---
title: <providerOption> 項目
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: a6718173e84ecffc4ba0641f6e865e777aa6b1a4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088665"
---
# <a name="provideroption-element"></a><span data-ttu-id="d2cef-102">\<providerOption > 元素</span><span class="sxs-lookup"><span data-stu-id="d2cef-102">\<providerOption> Element</span></span>
<span data-ttu-id="d2cef-103">指定語言提供者的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="d2cef-103">Specifies the compiler version attributes for a language provider.</span></span>  

<span data-ttu-id="d2cef-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2cef-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d2cef-105">&nbsp;&nbsp;[ **\<system.object >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2cef-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="d2cef-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<編譯器 >** ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2cef-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="d2cef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**編譯器 >** ](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2cef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>\
<span data-ttu-id="d2cef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<providerOption >**</span><span class="sxs-lookup"><span data-stu-id="d2cef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d2cef-109">語法</span><span class="sxs-lookup"><span data-stu-id="d2cef-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2cef-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d2cef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d2cef-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d2cef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2cef-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d2cef-112">Attributes</span></span>  
  
|<span data-ttu-id="d2cef-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d2cef-113">Attribute</span></span>|<span data-ttu-id="d2cef-114">描述</span><span class="sxs-lookup"><span data-stu-id="d2cef-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d2cef-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d2cef-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="d2cef-116">指定選項的名稱;例如，"CompilerVersion"。</span><span class="sxs-lookup"><span data-stu-id="d2cef-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="d2cef-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d2cef-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="d2cef-118">指定選項的值。例如，"v 3.5"。</span><span class="sxs-lookup"><span data-stu-id="d2cef-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2cef-119">子項目</span><span class="sxs-lookup"><span data-stu-id="d2cef-119">Child Elements</span></span>  
 <span data-ttu-id="d2cef-120">無。</span><span class="sxs-lookup"><span data-stu-id="d2cef-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2cef-121">父項目</span><span class="sxs-lookup"><span data-stu-id="d2cef-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d2cef-122">項目</span><span class="sxs-lookup"><span data-stu-id="d2cef-122">Element</span></span>|<span data-ttu-id="d2cef-123">描述</span><span class="sxs-lookup"><span data-stu-id="d2cef-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2cef-124">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="d2cef-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="d2cef-125">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d2cef-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="d2cef-126">\<system.object > 元素</span><span class="sxs-lookup"><span data-stu-id="d2cef-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="d2cef-127">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="d2cef-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="d2cef-128">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="d2cef-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="d2cef-129">編譯器設定元素的容器;包含零個或多個 `<compiler>` 元素。</span><span class="sxs-lookup"><span data-stu-id="d2cef-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="d2cef-130">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="d2cef-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="d2cef-131">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="d2cef-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2cef-132">備註</span><span class="sxs-lookup"><span data-stu-id="d2cef-132">Remarks</span></span>  
 <span data-ttu-id="d2cef-133">在 .NET Framework 版本3.5 中，程式碼檔物件模型（CodeDOM）程式碼提供者可以使用 `<providerOption>` 元素來支援提供者特定選項。</span><span class="sxs-lookup"><span data-stu-id="d2cef-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="d2cef-134">.NET Framework 3.5 包含更新的 .NET Framework 2.0 元件，並提供新的版本3.5 元件，其中包含新的類型。</span><span class="sxs-lookup"><span data-stu-id="d2cef-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="d2cef-135">Microsoft C#和 Visual Basic 的程式碼提供者包含在 .NET Framework 2.0 元件中，但已更新為支援3.5 版編譯器。</span><span class="sxs-lookup"><span data-stu-id="d2cef-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="d2cef-136">根據預設，更新後的程式碼提供者會產生2.0 版編譯器的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d2cef-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="d2cef-137">您可以使用 `<providerOption>` 元素，將目標編譯器版本變更為3.5。</span><span class="sxs-lookup"><span data-stu-id="d2cef-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="d2cef-138">若要這麼做，請為 `name` 屬性指定 "CompilerVersion"，並針對 `value` 屬性指定 "v 3.5"。</span><span class="sxs-lookup"><span data-stu-id="d2cef-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="d2cef-139">您必須在版本號碼之前加上小寫的 "v"。</span><span class="sxs-lookup"><span data-stu-id="d2cef-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="d2cef-140">您可以將 `<providerOption>` 專案新增至 .NET Framework 2.0 Machine.config 或根 Web.config 檔案，讓版本規格成為全域。</span><span class="sxs-lookup"><span data-stu-id="d2cef-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="d2cef-141">如果您在 Machine.config 檔案中將預設的編譯器版本更新為3.5，則可以使用應用程式佈建檔中的 `<providerOption>` 專案，以每個應用程式為基礎，將它變更回2.0。</span><span class="sxs-lookup"><span data-stu-id="d2cef-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="d2cef-142">CodeDOM 程式碼提供者實作者可以藉由提供接受 <xref:System.Collections.Generic.IDictionary%602>型別之 `providerOptions` 參數的函式，來處理自訂選項。</span><span class="sxs-lookup"><span data-stu-id="d2cef-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2cef-143">範例</span><span class="sxs-lookup"><span data-stu-id="d2cef-143">Example</span></span>  
 <span data-ttu-id="d2cef-144">下列範例示範如何指定應該使用的程式C#代碼提供者版本3.5。</span><span class="sxs-lookup"><span data-stu-id="d2cef-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2cef-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="d2cef-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="d2cef-146">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d2cef-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d2cef-147">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="d2cef-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="d2cef-148">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="d2cef-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="d2cef-149">[編譯編譯器的編譯器元素（ASP.NET 設定架構）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2cef-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
