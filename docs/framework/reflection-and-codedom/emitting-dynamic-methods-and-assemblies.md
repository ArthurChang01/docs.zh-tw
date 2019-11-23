---
title: 發出動態方法和組件
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 4578b708b10e93a7f5def5b9dc040eeb646bdc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130239"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="c2d8d-102">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="c2d8d-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="c2d8d-103">本節說明 <xref:System.Reflection.Emit> 命名空間中的一組 Managed 類型，它可讓編譯器或工具在執行階段發出中繼資料和 Microsoft 中繼語言 (MSIL)，以及選擇性地在磁碟上產生可攜式執行檔 (PE)。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="c2d8d-104">指令碼引擎和編譯器是此命名空間的主要使用者。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="c2d8d-105">在本節中，<xref:System.Reflection.Emit> 命名空間所提供的功能稱為反映發出。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="c2d8d-106">反映發出提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="c2d8d-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="c2d8d-107">使用 <xref:System.Reflection.Emit.DynamicMethod> 類別，在執行階段定義輕量型全域方法，並使用委派加以執行。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="c2d8d-108">在執行階段定義組件，然後加以執行，並/或儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="c2d8d-109">在執行階段定義組件、加以執行，然後將其卸載，並允許記憶體回收，以回收其資源。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="c2d8d-110">在執行階段定義新組件中的模組，然後加以執行，並/或儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="c2d8d-111">在執行階段定義模組中的類型、建立這些類型的執行個體，並叫用其方法。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="c2d8d-112">針對已定義的模組，定義可供工具 (例如偵錯工具和程式碼分析工具) 使用的符號資訊。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="c2d8d-113">除了 <xref:System.Reflection.Emit> 命名空間中的 Managed 類型，還有[中繼資料介面](../unmanaged-api/metadata/metadata-interfaces.md)參考文件中說明的 Unmanaged 中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="c2d8d-114">相較於 Unmanaged 中繼資料介面，Managed 反映發出提供較強的語意錯誤檢查，以及抽象層級較高的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="c2d8d-115">另一項適用於中繼資料和 MSIL 的有用資源，是通用語言基礎結構 (CLI) 文件，尤其是＜第二部分：中繼資料定義和語意＞以及＜第三部分：CIL 指令集＞。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="c2d8d-116">您可以在 [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) 以及 [Ecma 網站](https://go.microsoft.com/fwlink/?LinkId=116487)上，線上取得這份文件。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-116">The documentation is available online on [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](https://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2d8d-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="c2d8d-117">In This Section</span></span>
  
[<span data-ttu-id="c2d8d-118">反映發出中的安全性問題</span><span class="sxs-lookup"><span data-stu-id="c2d8d-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="c2d8d-119">說明有關使用反映發出來建立動態組件的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="c2d8d-120">[如何：定義和執行動態方法](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="c2d8d-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="c2d8d-121">顯示如何執行簡單的動態方法以及繫結至類別執行個體的動態方法。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="c2d8d-122">[如何：使用反映發出定義泛型型別](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="c2d8d-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="c2d8d-123">顯示如何建立具有兩個型別參數的簡單泛型型別、如何將類別、介面和特殊條件約束套用至型別參數，以及如何建立成員，以使用類別的型別參數作為參數類型及傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="c2d8d-124">[如何：使用反映發出定義泛型方法](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="c2d8d-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="c2d8d-125">顯示如何建立、發出和叫用簡單泛型方法。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="c2d8d-126">[動態類型產生的可回收組件](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="c2d8d-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="c2d8d-127">引進可回收組件，即動態組件，不需要卸載其建立所在的應用程式定義域即可予以卸載。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="c2d8d-128">參考</span><span class="sxs-lookup"><span data-stu-id="c2d8d-128">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="c2d8d-129">將可用來建置方法主體的 MSIL 指令碼編製目錄。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="c2d8d-130">包含用來發出動態方法、組件和類型的 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="c2d8d-131">說明 <xref:System.Type> 類別，其代表 Managed 反映和反映發出中的類型，且其為使用這些技術的關鍵。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="c2d8d-132">包含用來探索中繼資料和 Managed 程式碼的 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c2d8d-133">相關章節</span><span class="sxs-lookup"><span data-stu-id="c2d8d-133">Related Sections</span></span>  

[<span data-ttu-id="c2d8d-134">反映</span><span class="sxs-lookup"><span data-stu-id="c2d8d-134">Reflection</span></span>](reflection.md)  
<span data-ttu-id="c2d8d-135">說明如何探索中繼資料和 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-135">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="c2d8d-136">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="c2d8d-136">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="c2d8d-137">提供 .NET 實作中組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="c2d8d-137">Provides an overview of assemblies in .NET implementations.</span></span>
