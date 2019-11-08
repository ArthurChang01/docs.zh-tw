---
title: 組件名稱
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 7a1a4d2512ebb002a3153fe2d51f47157136744d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733096"
---
# <a name="assembly-names"></a><span data-ttu-id="09807-102">組件名稱</span><span class="sxs-lookup"><span data-stu-id="09807-102">Assembly names</span></span>
<span data-ttu-id="09807-103">組件的名稱儲存在中繼資料內，而且對組件範圍具有重大影響，並供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="09807-103">An assembly's name is stored in metadata and has a significant impact on the assembly's scope and use by an application.</span></span> <span data-ttu-id="09807-104">強式名稱組件的完整名稱包括組件的名稱、文化特性、公開金鑰和版本號碼。</span><span class="sxs-lookup"><span data-stu-id="09807-104">A strong-named assembly has a fully qualified name that includes the assembly's name, culture, public key, and version number.</span></span> <span data-ttu-id="09807-105">這通常稱為顯示名稱，以及可以使用 <xref:System.Reflection.Assembly.FullName%2A> 屬性取得載入的組件。</span><span class="sxs-lookup"><span data-stu-id="09807-105">This is frequently referred to as the display name, and for loaded assemblies can be obtained by using the <xref:System.Reflection.Assembly.FullName%2A> property.</span></span>

 <span data-ttu-id="09807-106">執行階段會使用這項資訊來尋找組件，並區別它與其他同名的組件。</span><span class="sxs-lookup"><span data-stu-id="09807-106">The runtime uses this information to locate the assembly and differentiate it from other assemblies with the same name.</span></span> <span data-ttu-id="09807-107">例如，稱為 `myTypes` 的強式名稱組件的完整名稱可能如下：</span><span class="sxs-lookup"><span data-stu-id="09807-107">For example, a strong-named assembly called `myTypes` could have the following fully qualified name:</span></span>

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> <span data-ttu-id="09807-108">處理器架構會新增至 .NET Framework 2.0 版中的組件身分識別，以允許組件的處理器特定版本。</span><span class="sxs-lookup"><span data-stu-id="09807-108">Processor architecture is added to the assembly identity in the .NET Framework version 2.0, to allow processor-specific versions of assemblies.</span></span> <span data-ttu-id="09807-109">您可以建立組件的版本，其身分識別只有處理器架構不同，例如 32 位元和 64 位元處理器特定版本。</span><span class="sxs-lookup"><span data-stu-id="09807-109">You can create versions of an assembly whose identity differs only by processor architecture, for example 32-bit and 64-bit processor-specific versions.</span></span> <span data-ttu-id="09807-110">強式名稱不需要處理器架構。</span><span class="sxs-lookup"><span data-stu-id="09807-110">Processor architecture is not required for strong names.</span></span> <span data-ttu-id="09807-111">如需詳細資訊，請參閱<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="09807-111">For more information, see <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="09807-112">在此範例中，完整名稱指出 `myTypes` 組件具有含公開金鑰權杖的強式名稱、具有文化特性值「美式英文」，以及具有版本號碼 1.0.1234.0。</span><span class="sxs-lookup"><span data-stu-id="09807-112">In this example, the fully qualified name indicates that the `myTypes` assembly has a strong name with a public key token, has the culture value for US English, and has a version number of 1.0.1234.0.</span></span> <span data-ttu-id="09807-113">它的處理器架構為 "msil"，表示它將是根據作業系統和處理器編譯成 32 位元程式碼或 64 位元程式碼的 Just-In-Time (JIT)。</span><span class="sxs-lookup"><span data-stu-id="09807-113">Its processor architecture is "msil", which means that it will be just-in-time (JIT)-compiled to 32-bit code or 64-bit code depending on the operating system and processor.</span></span>

 <span data-ttu-id="09807-114">要求組件中類型的程式碼必須使用完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="09807-114">Code that requests types in an assembly must use a fully qualified assembly name.</span></span> <span data-ttu-id="09807-115">這稱為完整繫結。</span><span class="sxs-lookup"><span data-stu-id="09807-115">This is called fully qualified binding.</span></span> <span data-ttu-id="09807-116">在 .NET Framework 中參考組件時，不允許只指定組件名稱的部分繫結。</span><span class="sxs-lookup"><span data-stu-id="09807-116">Partial binding, which specifies only an assembly name, is not permitted when referencing assemblies in the .NET Framework.</span></span>

 <span data-ttu-id="09807-117">組成 .NET Framework 之元件的所有元件參考，也必須包含元件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="09807-117">All assembly references to assemblies that make up the .NET Framework must also contain the fully qualified name of the assembly.</span></span> <span data-ttu-id="09807-118">例如，1.0 版的 Data .NET Framework 元件的參考會包含：</span><span class="sxs-lookup"><span data-stu-id="09807-118">For example, a reference to the System.Data .NET Framework assembly for version 1.0 would include:</span></span>

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 <span data-ttu-id="09807-119">請注意，版本會對應到 .NET Framework 1.0 版隨附之所有 .NET Framework 組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="09807-119">Note that the version corresponds to the version number of all .NET Framework assemblies that shipped with .NET Framework version 1.0.</span></span> <span data-ttu-id="09807-120">針對 .NET Framework 組件，文化特性值一律為中性，而且公開金鑰與上述範例所示相同。</span><span class="sxs-lookup"><span data-stu-id="09807-120">For .NET Framework assemblies, the culture value is always neutral, and the public key is the same as shown in the above example.</span></span>

 <span data-ttu-id="09807-121">例如，若要在組態檔中新增組件參考來設定追蹤接聽程式，您將包括系統 .NET Framework 組件的完整名稱：</span><span class="sxs-lookup"><span data-stu-id="09807-121">For example, to add an assembly reference in a configuration file to set up a trace listener, you would include the fully qualified name of the system .NET Framework assembly:</span></span>

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> <span data-ttu-id="09807-122">繫結至組件時，執行階段會將組件名稱視為不區分大小寫，但會保留組件名稱中所使用的大小寫。</span><span class="sxs-lookup"><span data-stu-id="09807-122">The runtime treats assembly names as case-insensitive when binding to an assembly, but preserves whatever case is used in an assembly name.</span></span> <span data-ttu-id="09807-123">Windows SDK 中的數個工具會以區分大小寫的方式處理組件名稱。</span><span class="sxs-lookup"><span data-stu-id="09807-123">Several tools in the Windows SDK handle assembly names as case-sensitive.</span></span> <span data-ttu-id="09807-124">為了獲得最佳結果，請如同其區分大小寫一樣地管理組件名稱。</span><span class="sxs-lookup"><span data-stu-id="09807-124">For best results, manage assembly names as though they were case-sensitive.</span></span>

## <a name="name-application-components"></a><span data-ttu-id="09807-125">命名應用程式元件</span><span class="sxs-lookup"><span data-stu-id="09807-125">Name application components</span></span>
 <span data-ttu-id="09807-126">判斷組件的身分識別時，執行階段不會考慮檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="09807-126">The runtime does not consider the file name when determining an assembly's identity.</span></span> <span data-ttu-id="09807-127">執行階段必須知道包含組件名稱、版本、文化特性和強式名稱的組件身分識別。</span><span class="sxs-lookup"><span data-stu-id="09807-127">The assembly identity, which consists of the assembly name, version, culture, and strong name, must be clear to the runtime.</span></span>

 <span data-ttu-id="09807-128">例如，如果您有一個名為*myAssembly*的元件參考名為*myAssembly*的元件，則在執行*myAssembly*時，會正確地進行系結。</span><span class="sxs-lookup"><span data-stu-id="09807-128">For example, if you have an assembly called *myAssembly.exe* that references an assembly called *myAssembly.dll*, binding occurs correctly if you execute *myAssembly.exe*.</span></span> <span data-ttu-id="09807-129">不過，如果有另一個應用程式使用 <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>的方法執行*myAssembly* ，則執行時間會決定當 myAssembly 要求系結至 `myAssembly`時，已載入 `myAssembly` *。*</span><span class="sxs-lookup"><span data-stu-id="09807-129">However, if another application executes *myAssembly.exe* using the method <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, the runtime determines that `myAssembly` is already loaded when *myAssembly.exe* requests binding to `myAssembly`.</span></span> <span data-ttu-id="09807-130">在此情況下，絕對不會載入*myAssembly* 。</span><span class="sxs-lookup"><span data-stu-id="09807-130">In this case, *myAssembly.dll* is never loaded.</span></span> <span data-ttu-id="09807-131">因為*myAssembly*不包含要求的型別，所以會發生 <xref:System.TypeLoadException>。</span><span class="sxs-lookup"><span data-stu-id="09807-131">Because *myAssembly.exe* does not contain the requested type, a <xref:System.TypeLoadException> occurs.</span></span>

 <span data-ttu-id="09807-132">若要避免這個問題，請確定構成應用程式的組件沒有相同的組件名稱，或將同名的組件放在不同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="09807-132">To avoid this problem, make sure the assemblies that make up your application do not have the same assembly name or place assemblies with the same name in different directories.</span></span>

> [!NOTE]
> <span data-ttu-id="09807-133">在 .NET Framework 中，如果您將強式名稱的元件放在全域組件快取中，則元件的檔案名必須符合元件名稱，不包括副檔名，例如 *.exe*或 *.dll*。</span><span class="sxs-lookup"><span data-stu-id="09807-133">In the .NET Framework, if you put a strong-named assembly in the global assembly cache, the assembly's file name must match the assembly name, not including the file name extension, such as *.exe* or *.dll*.</span></span> <span data-ttu-id="09807-134">例如，如果元件的檔案名是*myAssembly*，則元件名稱必須 `myAssembly`。</span><span class="sxs-lookup"><span data-stu-id="09807-134">For example, if the file name of an assembly is *myAssembly.dll*, the assembly name must be `myAssembly`.</span></span> <span data-ttu-id="09807-135">只有在根應用程式目錄中部署的私用組件才能具有與檔案名稱不同的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="09807-135">Private assemblies deployed only in the root application directory can have an assembly name that is different from the file name.</span></span>

## <a name="see-also"></a><span data-ttu-id="09807-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="09807-136">See also</span></span>

- [<span data-ttu-id="09807-137">如何：判斷元件的完整名稱</span><span class="sxs-lookup"><span data-stu-id="09807-137">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)
- [<span data-ttu-id="09807-138">建立元件</span><span class="sxs-lookup"><span data-stu-id="09807-138">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="09807-139">強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="09807-139">Strong-named assemblies</span></span>](strong-named.md)
- [<span data-ttu-id="09807-140">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="09807-140">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="09807-141">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="09807-141">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
