---
title: 將您的 Windows 市集應用程式移轉至 .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 987669fc51eeaf7e3bdef3e91a2f1ce23164a055
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389708"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a><span data-ttu-id="503c8-102">將 Windows 應用商店應用遷移到 .NET 本機</span><span class="sxs-lookup"><span data-stu-id="503c8-102">Migrate Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="503c8-103">.NET 本機提供 Windows 應用商店或開發人員電腦上的應用的靜態編譯。</span><span class="sxs-lookup"><span data-stu-id="503c8-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="503c8-104">這不同於 just-in-time (JIT) 編譯器或裝置上的 [原生映像產生器 (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) 為 Windows 市集應用程式執行的動態編譯。</span><span class="sxs-lookup"><span data-stu-id="503c8-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="503c8-105">儘管存在差異,.NET 本機嘗試與[Windows 應用商店應用的 .NET](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)保持相容性。</span><span class="sxs-lookup"><span data-stu-id="503c8-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="503c8-106">在大多數情況下,適用於 .NET 的 Windows 應用商店應用的事項也適用於 .NET 本機應用。</span><span class="sxs-lookup"><span data-stu-id="503c8-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="503c8-107">不過，在某些情況下，您可能會遇到行為上的變更。</span><span class="sxs-lookup"><span data-stu-id="503c8-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="503c8-108">本文件討論 Windows 應用商店應用的標準 .NET 和 .NET 本機在以下區域之間的這些差異:</span><span class="sxs-lookup"><span data-stu-id="503c8-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="503c8-109">一般執行階段的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-109">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="503c8-110">動態程式設計的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-110">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="503c8-111">其他與反映相關的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-111">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="503c8-112">不支援的案例和 API</span><span class="sxs-lookup"><span data-stu-id="503c8-112">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="503c8-113">Visual Studio 的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-113">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="503c8-114">一般執行階段的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-114">General runtime differences</span></span>

- <span data-ttu-id="503c8-115"><xref:System.TypeLoadException>當應用在通用語言運行時 (CLR) 上運行時,JIT 編譯器引發的異常通常會導致 .NET 本機處理時的編譯時錯誤。</span><span class="sxs-lookup"><span data-stu-id="503c8-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="503c8-116">請勿從應用程式的 UI 執行緒呼叫 <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="503c8-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="503c8-117">這可能導致 .NET 本機上死鎖。</span><span class="sxs-lookup"><span data-stu-id="503c8-117">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="503c8-118">請不要依賴靜態類別建構函式引動過程順序。</span><span class="sxs-lookup"><span data-stu-id="503c8-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="503c8-119">在 .NET 本機中,調用順序不同於標準運行時的順序。</span><span class="sxs-lookup"><span data-stu-id="503c8-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="503c8-120">(即使是使用標準執行階段，也不應該依賴靜態類別建構函式的執行順序。)</span><span class="sxs-lookup"><span data-stu-id="503c8-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="503c8-121">在任何執行緒上無限迴圈，而不進行呼叫 (例如 `while(true);`) 可能會導致應用程式中止。</span><span class="sxs-lookup"><span data-stu-id="503c8-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="503c8-122">同樣地，長時間或無限等待可能也會導致應用程式中止。</span><span class="sxs-lookup"><span data-stu-id="503c8-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="503c8-123">某些通用初始化週期不會在 .NET 本機中引發異常。</span><span class="sxs-lookup"><span data-stu-id="503c8-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="503c8-124">例如，下列程式碼會在標準 CLR 上擲回 <xref:System.TypeLoadException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="503c8-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="503c8-125">在 .NET 本機中,它不。</span><span class="sxs-lookup"><span data-stu-id="503c8-125">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="503c8-126">在某些情況下,.NET 本機提供 .NET 框架類庫的不同實現。</span><span class="sxs-lookup"><span data-stu-id="503c8-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="503c8-127">從方法傳回的物件一律會實作傳回類型的成員。</span><span class="sxs-lookup"><span data-stu-id="503c8-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="503c8-128">不過，由於其支援實作不同，所以您可能無法將其轉換成像在其他 .NET Framework 平台上轉換的相同類型集。</span><span class="sxs-lookup"><span data-stu-id="503c8-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="503c8-129">例如，在某些情況下，您可能無法將 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> 這類方法傳回的 <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> 介面物件轉換成 `T[]`。</span><span class="sxs-lookup"><span data-stu-id="503c8-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="503c8-130">默認情況下,在 Windows 應用商店應用的 .NET 上未啟用 WinInet 緩存,但它位於 .NET 本機上。</span><span class="sxs-lookup"><span data-stu-id="503c8-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="503c8-131">這可以改善效能，但有工作集含意。</span><span class="sxs-lookup"><span data-stu-id="503c8-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="503c8-132">開發人員不需任何動作。</span><span class="sxs-lookup"><span data-stu-id="503c8-132">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="503c8-133">動態程式設計的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-133">Dynamic programming differences</span></span>

<span data-ttu-id="503c8-134">.NET 本機靜態連結在代碼從 .NET 框架,使代碼應用本地的最大性能。</span><span class="sxs-lookup"><span data-stu-id="503c8-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="503c8-135">不過，二進位大小必須維持在較小的狀態，這樣才不會將整個 .NET Framework 帶進來。</span><span class="sxs-lookup"><span data-stu-id="503c8-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="503c8-136">.NET 本機編譯器通過使用刪除對未使用代碼的引用的依賴項縮減程序來解決此限制。</span><span class="sxs-lookup"><span data-stu-id="503c8-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="503c8-137">但是,當無法在編譯時靜態推斷該資訊,而是在運行時動態檢索時,.NET Native 可能無法維護和生成某些類型資訊和代碼。</span><span class="sxs-lookup"><span data-stu-id="503c8-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="503c8-138">.NET 本機確實支援反射和動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="503c8-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="503c8-139">不過，並非所有類型都可以標記來進行反映，因為這樣會使所產生的程式碼大小過大 (尤其是因為可支援在 .NET Framework 中的公用 API 上反映)。</span><span class="sxs-lookup"><span data-stu-id="503c8-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="503c8-140">.NET 本機編譯器對哪些類型應支援反射做出明智的選擇,並且僅保留元數據並僅為這些類型生成代碼。</span><span class="sxs-lookup"><span data-stu-id="503c8-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="503c8-141">例如，資料繫結會要求應用程式能夠將屬性名稱對應至函式。</span><span class="sxs-lookup"><span data-stu-id="503c8-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="503c8-142">在適用於 Windows 市集應用程式的 .NET 中，通用語言執行平台會自動使用反映來提供這項功能給 Managed 類型和可公開取得的原生類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="503c8-143">在 .NET 本機中,編譯器會自動包含綁定數據的類型的元數據。</span><span class="sxs-lookup"><span data-stu-id="503c8-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="503c8-144">.NET 本機編譯器還可以處理常用的泛型類型,<xref:System.Collections.Generic.List%601><xref:System.Collections.Generic.Dictionary%602>如 和 ,它們無需任何提示或指令即可工作。</span><span class="sxs-lookup"><span data-stu-id="503c8-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="503c8-145">在某些限制下，也可支援 [動態](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="503c8-145">The [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="503c8-146">將應用移植到 .NET 本機時,應徹底測試所有動態代碼路徑。</span><span class="sxs-lookup"><span data-stu-id="503c8-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="503c8-147">.NET 本機的預設配置對於大多數開發人員來說已經足夠了,但一些開發人員可能希望使用運行時指令 (.rd.xml) 檔來微調其配置。</span><span class="sxs-lookup"><span data-stu-id="503c8-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="503c8-148">此外,在某些情況下,.NET 本機編譯器無法確定哪些元數據必須可供反射,並依賴於提示,尤其是在以下情況下:</span><span class="sxs-lookup"><span data-stu-id="503c8-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="503c8-149">無法以靜態方式判斷某些結構，例如 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="503c8-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="503c8-150">由於編譯器無法判斷具現化，所以必須以執行階段指示詞來指定您想要反映的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="503c8-151">這不只是因為所有的程式碼必須包含在內，也因為反映在泛型類型上會形成無限循環 (例如，在泛型類型上叫用泛型方法時)。</span><span class="sxs-lookup"><span data-stu-id="503c8-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="503c8-152">執行階段指示詞中定義在執行階段指示詞 (.rd.xml) 檔案中。</span><span class="sxs-lookup"><span data-stu-id="503c8-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="503c8-153">如需使用此檔案的一般資訊，請參閱[使用者入門](getting-started-with-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="503c8-153">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="503c8-154">如需執行階段指示詞的詳細資訊，請參閱 [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="503c8-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="503c8-155">.NET 本機還包括分析工具,可説明開發人員確定預設集之外應支援反射的類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="503c8-156">其他與反映相關的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-156">Other reflection-related differences</span></span>

<span data-ttu-id="503c8-157">Windows 應用商店應用的 .NET 和 .NET 本機應用在行為上存在許多其他與反射相關的差異。</span><span class="sxs-lookup"><span data-stu-id="503c8-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="503c8-158">在 .NET 本機中:</span><span class="sxs-lookup"><span data-stu-id="503c8-158">In .NET Native:</span></span>

- <span data-ttu-id="503c8-159">不支援 .NET Framework 類別庫中，透過類型和成員的私用反映。</span><span class="sxs-lookup"><span data-stu-id="503c8-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="503c8-160">不過，您可以透過自己的私用類型和成員，以及協力廠商程式庫中的類型和成員來進行反映。</span><span class="sxs-lookup"><span data-stu-id="503c8-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="503c8-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> 屬性針對表示傳回值的 `false` 物件，正確地傳回 <xref:System.Reflection.ParameterInfo> 。</span><span class="sxs-lookup"><span data-stu-id="503c8-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="503c8-162">在適用於 Windows 市集應用程式的 .NET 中，它會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="503c8-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="503c8-163">中繼語言 (IL) 不會直接支援此作業，而是將解譯工作留給語言。</span><span class="sxs-lookup"><span data-stu-id="503c8-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="503c8-164">不支援 <xref:System.RuntimeFieldHandle> 和 <xref:System.RuntimeMethodHandle> 結構上的公用成員。</span><span class="sxs-lookup"><span data-stu-id="503c8-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="503c8-165">只有針對 LINQ、運算式樹狀架構和靜態陣列初始設定，才會支援這些類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="503c8-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> 將隱藏的成員包含基底類別中，因此可能會在非明確覆寫的情況下被覆寫。</span><span class="sxs-lookup"><span data-stu-id="503c8-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="503c8-167">針對其他 [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) 方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="503c8-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="503c8-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>並嘗試<xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType>創建某些組合(例如`byref`, 物件陣列)時,不要失敗。</span><span class="sxs-lookup"><span data-stu-id="503c8-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of `byref` objects).</span></span>

- <span data-ttu-id="503c8-169">您不能使用反映來叫用具有指標參數的成員。</span><span class="sxs-lookup"><span data-stu-id="503c8-169">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="503c8-170">您不能使用反映來取得或設定指標欄位。</span><span class="sxs-lookup"><span data-stu-id="503c8-170">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="503c8-171">當參數計數錯誤且其中一個參數的類型不正確時,.NET Native 將<xref:System.ArgumentException>引發<xref:System.Reflection.TargetParameterCountException>而不是 。</span><span class="sxs-lookup"><span data-stu-id="503c8-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="503c8-172">通常不支援例外狀況的二進位序列化。</span><span class="sxs-lookup"><span data-stu-id="503c8-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="503c8-173">因此，可以將不可序列化的物件加入 <xref:System.Exception.Data%2A?displayProperty=nameWithType> 字典。</span><span class="sxs-lookup"><span data-stu-id="503c8-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="503c8-174">不支援的案例和 API</span><span class="sxs-lookup"><span data-stu-id="503c8-174">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="503c8-175">下列各節會針對一般開發、interop 以及 HTTPClient 和 Windows Communication Foundation (WCF) 等技術，列出不支援的案例和 API：</span><span class="sxs-lookup"><span data-stu-id="503c8-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="503c8-176">一般開發</span><span class="sxs-lookup"><span data-stu-id="503c8-176">General development</span></span>](#General)

- [<span data-ttu-id="503c8-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="503c8-177">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="503c8-178">Interop</span><span class="sxs-lookup"><span data-stu-id="503c8-178">Interop</span></span>](#Interop)

- [<span data-ttu-id="503c8-179">不支援的 API</span><span class="sxs-lookup"><span data-stu-id="503c8-179">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="503c8-180">一般開發的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-180">General development differences</span></span>

<span data-ttu-id="503c8-181">**值類型**</span><span class="sxs-lookup"><span data-stu-id="503c8-181">**Value types**</span></span>

- <span data-ttu-id="503c8-182">如果您覆寫 <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> 和 <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> 方法的值類型，請勿呼叫基底類別實作。</span><span class="sxs-lookup"><span data-stu-id="503c8-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="503c8-183">在適用於 Windows 市集應用程式的 .NET 中，這些方法會依賴反映。</span><span class="sxs-lookup"><span data-stu-id="503c8-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="503c8-184">在編譯時,.NET 本機生成不依賴於運行時反射的實現。</span><span class="sxs-lookup"><span data-stu-id="503c8-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="503c8-185">這意味著,如果不重寫這兩種方法,它們將按預期方式工作,因為 .NET Native 會在編譯時生成實現。</span><span class="sxs-lookup"><span data-stu-id="503c8-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="503c8-186">不過，覆寫這些方法，但又呼叫基底類別實作，將會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="503c8-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="503c8-187">不支援大於 1 MB 的值類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-187">Value types larger than 1 megabyte aren't supported.</span></span>

- <span data-ttu-id="503c8-188">值類型不能在 .NET 本機中具有無參數構造函數。</span><span class="sxs-lookup"><span data-stu-id="503c8-188">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="503c8-189">(C# 和 Visual Basic 禁止對值類型進行無參數建構函數。</span><span class="sxs-lookup"><span data-stu-id="503c8-189">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="503c8-190">不過，可以在 IL 中建立這些預設建構函式)。</span><span class="sxs-lookup"><span data-stu-id="503c8-190">However, these can be created in IL.)</span></span>

<span data-ttu-id="503c8-191">**陣列**</span><span class="sxs-lookup"><span data-stu-id="503c8-191">**Arrays**</span></span>

- <span data-ttu-id="503c8-192">不支援下限不是零的陣列。</span><span class="sxs-lookup"><span data-stu-id="503c8-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="503c8-193">一般而言，可以呼叫 <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> 多載來建立這些陣列。</span><span class="sxs-lookup"><span data-stu-id="503c8-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="503c8-194">不支援動態建立多維陣列。</span><span class="sxs-lookup"><span data-stu-id="503c8-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="503c8-195">這類陣列的建立，通常是藉由呼叫包含 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 參數之 `lengths` 方法的多載，或是呼叫 <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="503c8-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="503c8-196">不支援具有 4 個 (含) 以上維度的多維陣列，意即，其 <xref:System.Array.Rank%2A?displayProperty=nameWithType> 屬性值為 4 (含) 以上。</span><span class="sxs-lookup"><span data-stu-id="503c8-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="503c8-197">請改用 [不規則陣列](../../csharp/programming-guide/arrays/jagged-arrays.md) (陣列的陣列)。</span><span class="sxs-lookup"><span data-stu-id="503c8-197">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="503c8-198">例如， `array[x,y,z]` 無效，但 `array[x][y][z]` 有效。</span><span class="sxs-lookup"><span data-stu-id="503c8-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="503c8-199">不支援多維陣列的變異數，它會在執行階段導致 <xref:System.InvalidCastException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="503c8-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="503c8-200">**泛型**</span><span class="sxs-lookup"><span data-stu-id="503c8-200">**Generics**</span></span>

- <span data-ttu-id="503c8-201">無限的泛型類型擴充會導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="503c8-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="503c8-202">例如，此程式碼無法編譯：</span><span class="sxs-lookup"><span data-stu-id="503c8-202">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="503c8-203">**指標**</span><span class="sxs-lookup"><span data-stu-id="503c8-203">**Pointers**</span></span>

- <span data-ttu-id="503c8-204">不支援指標的陣列。</span><span class="sxs-lookup"><span data-stu-id="503c8-204">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="503c8-205">您不能使用反映來取得或設定指標欄位。</span><span class="sxs-lookup"><span data-stu-id="503c8-205">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="503c8-206">**序列化**</span><span class="sxs-lookup"><span data-stu-id="503c8-206">**Serialization**</span></span>

<span data-ttu-id="503c8-207">不支援 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> 屬性。</span><span class="sxs-lookup"><span data-stu-id="503c8-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="503c8-208">請改用 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> 屬性。</span><span class="sxs-lookup"><span data-stu-id="503c8-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="503c8-209">**資源**</span><span class="sxs-lookup"><span data-stu-id="503c8-209">**Resources**</span></span>

<span data-ttu-id="503c8-210">不支援將當地語系化的資源與 <xref:System.Diagnostics.Tracing.EventSource> 類別搭配使用。</span><span class="sxs-lookup"><span data-stu-id="503c8-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="503c8-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> 屬性不會定義當地語系化的資源。</span><span class="sxs-lookup"><span data-stu-id="503c8-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="503c8-212">**委派**</span><span class="sxs-lookup"><span data-stu-id="503c8-212">**Delegates**</span></span>

<span data-ttu-id="503c8-213">不支援`Delegate.BeginInvoke` 和 `Delegate.EndInvoke` 。</span><span class="sxs-lookup"><span data-stu-id="503c8-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="503c8-214">**其他 API**</span><span class="sxs-lookup"><span data-stu-id="503c8-214">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="503c8-215">如果屬性未應用於類型[,TypeInfo.GUID](xref:System.Type.GUID)<xref:System.PlatformNotSupportedException><xref:System.Runtime.InteropServices.GuidAttribute>屬性將引發異常。</span><span class="sxs-lookup"><span data-stu-id="503c8-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="503c8-216">GUID 主要用於 COM 支援。</span><span class="sxs-lookup"><span data-stu-id="503c8-216">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="503c8-217">該方法<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>正確解析在 .NET 本機中包含短日期的字串。</span><span class="sxs-lookup"><span data-stu-id="503c8-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="503c8-218">不過，它不會維護 Microsoft 知識庫文章 [KB2803771](https://support.microsoft.com/kb/2803771) 和 [KB2803755](https://support.microsoft.com/kb/2803755)中描述之日期和時間剖析變更的相容性。</span><span class="sxs-lookup"><span data-stu-id="503c8-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="503c8-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")`在 .NET 本機中正確舍入。</span><span class="sxs-lookup"><span data-stu-id="503c8-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="503c8-220">在某些版本的 CLR 中，會將結果字串無條件捨去，而不是四捨五入。</span><span class="sxs-lookup"><span data-stu-id="503c8-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="503c8-221">HttpClient 差異</span><span class="sxs-lookup"><span data-stu-id="503c8-221">HttpClient differences</span></span>

<span data-ttu-id="503c8-222">在 .NET<xref:System.Net.Http.HttpClientHandler>本機 中,類在內部使用 WinINet(<xref:System.Net.WebRequest>通過<xref:System.Net.WebResponse><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>類), 而不是 Windows 應用商店應用的標準 .NET 中使用的和 類。</span><span class="sxs-lookup"><span data-stu-id="503c8-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="503c8-223">WinINet 並未支援 <xref:System.Net.Http.HttpClientHandler> 類別支援的所有組態選項。</span><span class="sxs-lookup"><span data-stu-id="503c8-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="503c8-224">因此：</span><span class="sxs-lookup"><span data-stu-id="503c8-224">As a result:</span></span>

- <span data-ttu-id="503c8-225">返回 .NET<xref:System.Net.Http.HttpClientHandler>`false`本機 版時的某些功能屬性`true`,而它們返回 Windows 應用商店應用的標準 .NET 中。</span><span class="sxs-lookup"><span data-stu-id="503c8-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="503c8-226">某些配置屬性`get`訪問器始終返回 .NET 本機上的固定值,該值與 Windows 應用商店應用 .NET 中的預設可配置值不同。</span><span class="sxs-lookup"><span data-stu-id="503c8-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="503c8-227">下列各小節會說明一些其他的行為差異。</span><span class="sxs-lookup"><span data-stu-id="503c8-227">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="503c8-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="503c8-228">**Proxy**</span></span>

<span data-ttu-id="503c8-229">類<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>不支援基於每個請求配置或重寫代理。</span><span class="sxs-lookup"><span data-stu-id="503c8-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="503c8-230">這意味著 .NET 本機上的所有請求都使用系統配置的代理伺服器,或者不使用代理伺服器,<xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType>具體取決於 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="503c8-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="503c8-231">在適用於 Windows 市集應用程式的 .NET 中，是由 <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> 屬性來定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="503c8-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="503c8-232">在 .NET 本<xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType>機上 ,將`null`<xref:System.PlatformNotSupportedException>設置為引發 異常以外的值。</span><span class="sxs-lookup"><span data-stu-id="503c8-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="503c8-233">該<xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType>屬性`false`返回 .NET 本機`true`,而它返回在 Windows 應用商店應用的標準 .NET 框架中。</span><span class="sxs-lookup"><span data-stu-id="503c8-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="503c8-234">**自動重新導向**</span><span class="sxs-lookup"><span data-stu-id="503c8-234">**Automatic redirection**</span></span>

<span data-ttu-id="503c8-235">該<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>類不允許配置最大數量的自動重定向。</span><span class="sxs-lookup"><span data-stu-id="503c8-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="503c8-236">在適用於 Windows 市集應用程式的標準 .NET 中， <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> 屬性的值預設為 50，而且可以修改。</span><span class="sxs-lookup"><span data-stu-id="503c8-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="503c8-237">在 .NET 本機上,此屬性的值為 10,嘗試修改它<xref:System.PlatformNotSupportedException>將引發異常 。</span><span class="sxs-lookup"><span data-stu-id="503c8-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="503c8-238">該<xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType>屬性`false`返回 .NET 本機`true`,而該 屬性返回 .NET 中,用於 Windows 應用商店應用。</span><span class="sxs-lookup"><span data-stu-id="503c8-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="503c8-239">**自動解壓縮**</span><span class="sxs-lookup"><span data-stu-id="503c8-239">**Automatic decompression**</span></span>

<span data-ttu-id="503c8-240">適用於 Windows 市集應用程式的 .NET 可讓您將 <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> 屬性設為 <xref:System.Net.DecompressionMethods.Deflate>、 <xref:System.Net.DecompressionMethods.GZip>、 <xref:System.Net.DecompressionMethods.Deflate> 和 <xref:System.Net.DecompressionMethods.GZip>同時設定，或是設為 <xref:System.Net.DecompressionMethods.None>。</span><span class="sxs-lookup"><span data-stu-id="503c8-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="503c8-241">.NET 本機<xref:System.Net.DecompressionMethods.Deflate>僅<xref:System.Net.DecompressionMethods.GZip><xref:System.Net.DecompressionMethods.None>支援 與 或 。</span><span class="sxs-lookup"><span data-stu-id="503c8-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="503c8-242">嘗試以無訊息模式將 <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> 屬性單獨設為 <xref:System.Net.DecompressionMethods.Deflate> 或 <xref:System.Net.DecompressionMethods.GZip> ，會將其設為同時使用 <xref:System.Net.DecompressionMethods.Deflate> 和 <xref:System.Net.DecompressionMethods.GZip>。</span><span class="sxs-lookup"><span data-stu-id="503c8-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="503c8-243">**Cookie**</span><span class="sxs-lookup"><span data-stu-id="503c8-243">**Cookies**</span></span>

<span data-ttu-id="503c8-244"><xref:System.Net.Http.HttpClient> 和 WinINet 會同時執行 Cookie 處理作業。</span><span class="sxs-lookup"><span data-stu-id="503c8-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="503c8-245"><xref:System.Net.CookieContainer> 所產生的 Cookie 會與 WinINet Cookie 快取中的 Cookie 合併。</span><span class="sxs-lookup"><span data-stu-id="503c8-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="503c8-246">從 <xref:System.Net.CookieContainer> 移除 Cookie 會防止 <xref:System.Net.Http.HttpClient> 傳送 Cookie，但如果 WinINet 已經看到 Cookie，而且使用者沒有刪除 Cookie，WinINet 就會加以傳送。</span><span class="sxs-lookup"><span data-stu-id="503c8-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="503c8-247">若要使用 <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>或 <xref:System.Net.CookieContainer> API，以程式設計方式將 Cookie 從 WinINet 移除是不可能的。</span><span class="sxs-lookup"><span data-stu-id="503c8-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="503c8-248">將 <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> 屬性設為 `false` 只會導致 <xref:System.Net.Http.HttpClient> 停止傳送 Cookie，WinINet 還是會在要求中包含其 Cookie。</span><span class="sxs-lookup"><span data-stu-id="503c8-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="503c8-249">**認證**</span><span class="sxs-lookup"><span data-stu-id="503c8-249">**Credentials**</span></span>

<span data-ttu-id="503c8-250">在適用於 Windows 市集應用程式的 .NET 中， <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> 屬性會獨立運作。</span><span class="sxs-lookup"><span data-stu-id="503c8-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="503c8-251">此外， <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性會接受實作 <xref:System.Net.ICredentials> 介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="503c8-252">在 .NET 本<xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A>機中`true`,將<xref:System.Net.Http.HttpClientHandler.Credentials%2A>屬性設定為`null`使屬性變為 。</span><span class="sxs-lookup"><span data-stu-id="503c8-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="503c8-253">此外， <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性只能設為 `null`、 <xref:System.Net.CredentialCache.DefaultCredentials%2A>，或是 <xref:System.Net.NetworkCredential>類型的物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="503c8-254">將任何其他 <xref:System.Net.ICredentials> 物件 (最常用的是 <xref:System.Net.CredentialCache>) 指派給 <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性會擲回 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="503c8-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="503c8-255">**其他不受支援或不可設定的功能**</span><span class="sxs-lookup"><span data-stu-id="503c8-255">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="503c8-256">在 .NET 本機中:</span><span class="sxs-lookup"><span data-stu-id="503c8-256">In .NET Native:</span></span>

- <span data-ttu-id="503c8-257"><xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> 屬性的值一律為 <xref:System.Net.Http.ClientCertificateOption.Automatic>。</span><span class="sxs-lookup"><span data-stu-id="503c8-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="503c8-258">在適用於 Windows 市集應用程式的 .NET 中，預設值為 <xref:System.Net.Http.ClientCertificateOption.Manual>。</span><span class="sxs-lookup"><span data-stu-id="503c8-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="503c8-259"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> 屬性不可設定。</span><span class="sxs-lookup"><span data-stu-id="503c8-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="503c8-260"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> 屬性一律為 `true`。</span><span class="sxs-lookup"><span data-stu-id="503c8-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="503c8-261">在適用於 Windows 市集應用程式的 .NET 中，預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="503c8-261">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="503c8-262">系統會將回應中的 `SetCookie2` 標頭視為過時而將它忽略。</span><span class="sxs-lookup"><span data-stu-id="503c8-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>
### <a name="interop-differences"></a><span data-ttu-id="503c8-263">Interop 的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-263">Interop differences</span></span>
 <span data-ttu-id="503c8-264">**已被取代的 API**</span><span class="sxs-lookup"><span data-stu-id="503c8-264">**Deprecated APIs**</span></span>

 <span data-ttu-id="503c8-265">有些與 Managed 程式碼交互操作的不常用 API 已被取代。</span><span class="sxs-lookup"><span data-stu-id="503c8-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="503c8-266">當與 .NET 本機一起使用時<xref:System.NotImplementedException>,這些<xref:System.PlatformNotSupportedException>API 可能會引發或異常,或導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="503c8-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="503c8-267">在適用於 Windows 市集應用程式的 .NET 中，這些 API 會標示為已過時，但是呼叫這些 API 會產生編譯器警告，而不是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="503c8-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="503c8-268">封`VARIANT`送的已棄用 API 包括:</span><span class="sxs-lookup"><span data-stu-id="503c8-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="503c8-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>支援,但在某些情況下,例如與[IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)或`byref`變體一起使用時,它會引發異常。</span><span class="sxs-lookup"><span data-stu-id="503c8-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or `byref` variants.</span></span>

 <span data-ttu-id="503c8-270">[IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)支援的已棄用 API 包括:</span><span class="sxs-lookup"><span data-stu-id="503c8-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="503c8-271">以經典 COM 事件的棄用 API 包括:</span><span class="sxs-lookup"><span data-stu-id="503c8-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="503c8-272">介面中<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>未支援的已棄用 API(在 .NET 本機中不受支援)包括:</span><span class="sxs-lookup"><span data-stu-id="503c8-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="503c8-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(所有成員)</span><span class="sxs-lookup"><span data-stu-id="503c8-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="503c8-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(所有成員)</span><span class="sxs-lookup"><span data-stu-id="503c8-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="503c8-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(所有成員)</span><span class="sxs-lookup"><span data-stu-id="503c8-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="503c8-276">其他不支援的互通功能包括:</span><span class="sxs-lookup"><span data-stu-id="503c8-276">Other unsupported interop features include:</span></span>

- <span data-ttu-id="503c8-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(所有成員)</span><span class="sxs-lookup"><span data-stu-id="503c8-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="503c8-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(所有成員)</span><span class="sxs-lookup"><span data-stu-id="503c8-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="503c8-279">很少使用封送 API:</span><span class="sxs-lookup"><span data-stu-id="503c8-279">Rarely used marshaling APIs:</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 <span data-ttu-id="503c8-280">**平台叫用和 COM interop 相容性**</span><span class="sxs-lookup"><span data-stu-id="503c8-280">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="503c8-281">大多數平台調用和 COM 互通方案在 .NET 本機中仍然受支援。</span><span class="sxs-lookup"><span data-stu-id="503c8-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="503c8-282">特別是仍支援與 Windows 執行階段 (WinRT) API 的所有交互操作性，以及 Windows 執行階段需要的所有封送處理。</span><span class="sxs-lookup"><span data-stu-id="503c8-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="503c8-283">其中包括對下列項目的封送處理支援：</span><span class="sxs-lookup"><span data-stu-id="503c8-283">This includes marshaling support for:</span></span>

- <span data-ttu-id="503c8-284">陣列 (包括 <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="503c8-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="503c8-285">委派</span><span class="sxs-lookup"><span data-stu-id="503c8-285">Delegates</span></span>

- <span data-ttu-id="503c8-286">字串 (Unicode、Ansi 和 HSTRING)</span><span class="sxs-lookup"><span data-stu-id="503c8-286">Strings (Unicode, Ansi, and HSTRING)</span></span>

- <span data-ttu-id="503c8-287">結構 (`byref` 和 `byval`)</span><span class="sxs-lookup"><span data-stu-id="503c8-287">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="503c8-288">等位</span><span class="sxs-lookup"><span data-stu-id="503c8-288">Unions</span></span>

- <span data-ttu-id="503c8-289">Win32 控制代碼</span><span class="sxs-lookup"><span data-stu-id="503c8-289">Win32 handles</span></span>

- <span data-ttu-id="503c8-290">所有 WinRT 結構</span><span class="sxs-lookup"><span data-stu-id="503c8-290">All WinRT constructs</span></span>

- <span data-ttu-id="503c8-291">部分支援封送處理變異數類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="503c8-292">支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="503c8-292">The following are supported:</span></span>

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [<span data-ttu-id="503c8-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="503c8-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="503c8-294">但是,.NET 本機不支援以下內容:</span><span class="sxs-lookup"><span data-stu-id="503c8-294">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="503c8-295">使用傳統 COM 事件</span><span class="sxs-lookup"><span data-stu-id="503c8-295">Using classic COM events</span></span>

- <span data-ttu-id="503c8-296">在 Managed 類型上實作 <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> 介面</span><span class="sxs-lookup"><span data-stu-id="503c8-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="503c8-297">透過 [屬性，在 Managed 類型上實作](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) IDispatch <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="503c8-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="503c8-298">但是,不能透過`IDispatch`呼叫 COM 物件,並且託管物件無法`IDispatch`實現 。</span><span class="sxs-lookup"><span data-stu-id="503c8-298">However, you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="503c8-299">不支援使用反映來叫用平台叫用方法。</span><span class="sxs-lookup"><span data-stu-id="503c8-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="503c8-300">若要解除決這項限制，您可以將此方法呼叫包裝在另一個方法中，並改用反映來呼叫包裝函式。</span><span class="sxs-lookup"><span data-stu-id="503c8-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="503c8-301">其他與適用於 Windows 市集應用程式的 .NET API 的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-301">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="503c8-302">本節列出了 .NET 本機中不支援的剩餘 API。</span><span class="sxs-lookup"><span data-stu-id="503c8-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="503c8-303">最大的一組不支援的 API 是 Windows 通訊基礎 (WCF) API。</span><span class="sxs-lookup"><span data-stu-id="503c8-303">The largest set of the unsupported APIs is the Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="503c8-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="503c8-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="503c8-305">.NET 本<xref:System.ComponentModel.DataAnnotations>機<xref:System.ComponentModel.DataAnnotations.Schema>中 不支援和 命名空間中的類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="503c8-306">這些類型包括 Windows 8 Windows 應用商店應用的 .NET 中存在的以下類型:</span><span class="sxs-lookup"><span data-stu-id="503c8-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 <span data-ttu-id="503c8-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="503c8-307">**Visual Basic**</span></span>

<span data-ttu-id="503c8-308">視覺基本版當前不受 .NET 本機版的支援。</span><span class="sxs-lookup"><span data-stu-id="503c8-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="503c8-309"><xref:Microsoft.VisualBasic>與<xref:Microsoft.VisualBasic.CompilerServices>命名空間中的以下型態在 .NET 本機中無法用:</span><span class="sxs-lookup"><span data-stu-id="503c8-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

<span data-ttu-id="503c8-310">**反映內容 (System.Reflection.Context 命名空間)**</span><span class="sxs-lookup"><span data-stu-id="503c8-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="503c8-311">在<xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType>.NET 本機中不支援該類。</span><span class="sxs-lookup"><span data-stu-id="503c8-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="503c8-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="503c8-312">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="503c8-313">在`System.Net.Http.RtcRequestFactory`.NET 本機中不支援該類。</span><span class="sxs-lookup"><span data-stu-id="503c8-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="503c8-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="503c8-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="503c8-315">.NET 本機中不支援[System.ServiceModel.\* 命名空間](xref:System.ServiceModel)中的類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="503c8-316">這些類型包括以下類型:</span><span class="sxs-lookup"><span data-stu-id="503c8-316">These include the following types:</span></span>

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a><span data-ttu-id="503c8-317">序列化程式的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-317">Differences in serializers</span></span>

<span data-ttu-id="503c8-318">下列差異與使用 <xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和 <xref:System.Xml.Serialization.XmlSerializer> 類別來進行序列化和還原序列化有關。</span><span class="sxs-lookup"><span data-stu-id="503c8-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="503c8-319">在 .NET<xref:System.Runtime.Serialization.DataContractSerializer><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>本機 中,無法序列化或去序列化具有其類型不是根序列化類型的基類成員的派生類。</span><span class="sxs-lookup"><span data-stu-id="503c8-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="503c8-320">例如，在下列程式碼中，嘗試序列化或還原序列化 `Y` 會產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="503c8-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="503c8-321">序列化程式無法識別 `InnerType` 類型，因為在序列化期間，並未周遊基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="503c8-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="503c8-322"><xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 無法將實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的類別或結構序列化。</span><span class="sxs-lookup"><span data-stu-id="503c8-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="503c8-323">例如，下列的類型無法序列化或還原序列化：</span><span class="sxs-lookup"><span data-stu-id="503c8-323">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="503c8-324"><xref:System.Xml.Serialization.XmlSerializer> 無法將下列物件值序列化，因為它不知道要序列化之物件的確切類型：</span><span class="sxs-lookup"><span data-stu-id="503c8-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="503c8-325">如果已序列化物件的類型是<xref:System.Xml.Serialization.XmlSerializer> ，則 <xref:System.Xml.XmlQualifiedName>無法序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="503c8-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="503c8-326">所有序列化程式 (<xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和 <xref:System.Xml.Serialization.XmlSerializer>) 都無法為 <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> 類型或是包含 <xref:System.Xml.Linq.XElement>的類型產生序列化程式碼，</span><span class="sxs-lookup"><span data-stu-id="503c8-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="503c8-327">而會顯示建置時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="503c8-327">They display build-time errors instead.</span></span>

- <span data-ttu-id="503c8-328">無法保證序列化類型的下列建構函式能夠如預期般運作：</span><span class="sxs-lookup"><span data-stu-id="503c8-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <span data-ttu-id="503c8-329">如果類型中有使用下列任何屬性的方法，則<xref:System.Xml.Serialization.XmlSerializer> 無法為該類型產生程式碼：</span><span class="sxs-lookup"><span data-stu-id="503c8-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="503c8-330"><xref:System.Xml.Serialization.XmlSerializer> 不接受 <xref:System.Xml.Serialization.IXmlSerializable> 自訂序列化介面。</span><span class="sxs-lookup"><span data-stu-id="503c8-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="503c8-331">如果您有實作這個介面的類別， <xref:System.Xml.Serialization.XmlSerializer> 會將該類型視為簡單的 CLR 物件 (POCO) 類型，並且只將其公開屬性序列化。</span><span class="sxs-lookup"><span data-stu-id="503c8-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="503c8-332">序列化一<xref:System.Exception>般 物件不能很好<xref:System.Runtime.Serialization.DataContractSerializer>地<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>使用 與 。</span><span class="sxs-lookup"><span data-stu-id="503c8-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="503c8-333">Visual Studio 的差異</span><span class="sxs-lookup"><span data-stu-id="503c8-333">Visual Studio differences</span></span>

<span data-ttu-id="503c8-334">**例外狀況和偵錯**</span><span class="sxs-lookup"><span data-stu-id="503c8-334">**Exceptions and debugging**</span></span>

<span data-ttu-id="503c8-335">當您在除錯器執行使用 .NET 本機編譯的應用程式時,為以下異常類型啟用第一次異常:</span><span class="sxs-lookup"><span data-stu-id="503c8-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="503c8-336">**建置應用程式**</span><span class="sxs-lookup"><span data-stu-id="503c8-336">**Building apps**</span></span>

<span data-ttu-id="503c8-337">使用 Visual Studio 預設使用的 x86 建置工具。</span><span class="sxs-lookup"><span data-stu-id="503c8-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="503c8-338">我們不建議使用 AMD64 MSBuild 工具 (可以在 C:\Program Files (x86)\MSBuild\12.0\bin\amd64 中找到)；這些工具可能會造成組建問題。</span><span class="sxs-lookup"><span data-stu-id="503c8-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="503c8-339">**分析工具**</span><span class="sxs-lookup"><span data-stu-id="503c8-339">**Profilers**</span></span>

- <span data-ttu-id="503c8-340">Visual Studio CPU 分析工具和 XAML 記憶體分析工具不會正確顯示 Just-My-Code。</span><span class="sxs-lookup"><span data-stu-id="503c8-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="503c8-341">XAML 記憶體分析工具不會準確地顯示 Managed 堆積資料。</span><span class="sxs-lookup"><span data-stu-id="503c8-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="503c8-342">CPU 分析工具不會正確地識別模組，並且會顯示具有前置詞的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="503c8-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="503c8-343">**單元測試程式庫專案**</span><span class="sxs-lookup"><span data-stu-id="503c8-343">**Unit Test Library projects**</span></span>

<span data-ttu-id="503c8-344">不支援在 Windows 應用商店應用專案的單位測試庫中啟用 .NET 本機,並導致專案無法生成。</span><span class="sxs-lookup"><span data-stu-id="503c8-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="503c8-345">另請參閱</span><span class="sxs-lookup"><span data-stu-id="503c8-345">See also</span></span>

- [<span data-ttu-id="503c8-346">快速入門</span><span class="sxs-lookup"><span data-stu-id="503c8-346">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="503c8-347">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="503c8-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="503c8-348">.NET 用於 Windows 應用商店應用概述</span><span class="sxs-lookup"><span data-stu-id="503c8-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="503c8-349">適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援</span><span class="sxs-lookup"><span data-stu-id="503c8-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
