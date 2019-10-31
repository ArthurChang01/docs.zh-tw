---
title: .NET Standard 的新功能
description: 本文摘要說明 .NET Standard 的每個新版本中的新功能和增強功能。
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: ebf656c4a5499fff54cb5a70a93c4e8cc9c82d0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101761"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="65a2b-103">.NET Standard 的新功能</span><span class="sxs-lookup"><span data-stu-id="65a2b-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="65a2b-104">.NET Standard 是定義 API 的版本集正式規格，必須能在遵守該版本標準的 .NET 實作中取得。</span><span class="sxs-lookup"><span data-stu-id="65a2b-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="65a2b-105">.NET Standard 是以程式庫開發人員為目標。</span><span class="sxs-lookup"><span data-stu-id="65a2b-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="65a2b-106">以 .NET Standard 版本為目標的程式庫可以用於任何支援該標準的版本之 .NET Framework、.NET Core 或 Xamarin 實作。</span><span class="sxs-lookup"><span data-stu-id="65a2b-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="65a2b-107">.NET Standard 的最新版本為 2.0。</span><span class="sxs-lookup"><span data-stu-id="65a2b-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="65a2b-108">它隨附于 .NET Core 2.0 SDK，以及已安裝 .NET Core 工作負載的 Visual Studio 2017 15.3 版。</span><span class="sxs-lookup"><span data-stu-id="65a2b-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="65a2b-109">支援的 .NET 實作</span><span class="sxs-lookup"><span data-stu-id="65a2b-109">Supported .NET implementations</span></span>

<span data-ttu-id="65a2b-110">.NET Standard 2.0 支援下列.NET 實作：</span><span class="sxs-lookup"><span data-stu-id="65a2b-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="65a2b-111">.NET Core 2.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="65a2b-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="65a2b-112">.NET Framework 4.6.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="65a2b-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="65a2b-113">Mono 5.4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="65a2b-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="65a2b-114">Xamarin.iOS 10.14 或更新版本</span><span class="sxs-lookup"><span data-stu-id="65a2b-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="65a2b-115">Xamarin.Mac 3.8 或更新版本</span><span class="sxs-lookup"><span data-stu-id="65a2b-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="65a2b-116">Xamarin.Android 8.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="65a2b-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="65a2b-117">通用 Windows 平台 10.0.16299 或更新版本</span><span class="sxs-lookup"><span data-stu-id="65a2b-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="65a2b-118">.NET Standard 2.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="65a2b-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="65a2b-119">.NET Standard 2.0 包含下列新功能：</span><span class="sxs-lookup"><span data-stu-id="65a2b-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="65a2b-120">一組大幅擴充的 API</span><span class="sxs-lookup"><span data-stu-id="65a2b-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="65a2b-121">透過 1.6 版，.NET Standard 包含相較小的 API 子集。</span><span class="sxs-lookup"><span data-stu-id="65a2b-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="65a2b-122">其中排除那些經常用於 .NET Framework 或 Xamarin 的許多 API。</span><span class="sxs-lookup"><span data-stu-id="65a2b-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="65a2b-123">這讓開發變得複雜，因為當開發人員開發以多個 .NET 實作為目標的應用程式和程式庫時，他們必須尋找熟悉的 API 之合適替代方案。</span><span class="sxs-lookup"><span data-stu-id="65a2b-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="65a2b-124">.NET Standard 2.0 藉由新增比在 .NET Standard 1.6 (前一版本) 中還多 20,000 多個 API 來解決此限制。</span><span class="sxs-lookup"><span data-stu-id="65a2b-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="65a2b-125">如需新增到 .NET Standard 2.0 的 API 清單，請參閱 [.NET Standard 2.0 與 1.6 的差異](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="65a2b-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="65a2b-126">一些新增到 .NET Standard 2.0 中 <xref:System> 命名空間的項目包括：</span><span class="sxs-lookup"><span data-stu-id="65a2b-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="65a2b-127"><xref:System.AppDomain> 類別的支援。</span><span class="sxs-lookup"><span data-stu-id="65a2b-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="65a2b-128">從 <xref:System.Array> 類別中其他成員使用陣列的更好之支援。</span><span class="sxs-lookup"><span data-stu-id="65a2b-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="65a2b-129">從 <xref:System.Attribute> 類別中其他成員使用屬性的更好之支援。</span><span class="sxs-lookup"><span data-stu-id="65a2b-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="65a2b-130"><xref:System.DateTime> 值的更好之行事曆支援和其他格式選項。</span><span class="sxs-lookup"><span data-stu-id="65a2b-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="65a2b-131">其他 <xref:System.Decimal> 四捨五入功能。</span><span class="sxs-lookup"><span data-stu-id="65a2b-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="65a2b-132"><xref:System.Environment> 類別中的其他功能。</span><span class="sxs-lookup"><span data-stu-id="65a2b-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="65a2b-133">增強透過 <xref:System.GC> 類別的記憶體回收行程的控制。</span><span class="sxs-lookup"><span data-stu-id="65a2b-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="65a2b-134">增強 <xref:System.String> 類別中字串比較、列舉和正規化的支援。</span><span class="sxs-lookup"><span data-stu-id="65a2b-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="65a2b-135">支援日光節約調整和 <xref:System.TimeZoneInfo.AdjustmentRule> 與 <xref:System.TimeZoneInfo.TransitionTime> 類別中的轉換時間。</span><span class="sxs-lookup"><span data-stu-id="65a2b-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="65a2b-136">大幅增強 <xref:System.Type> 類別中的功能。</span><span class="sxs-lookup"><span data-stu-id="65a2b-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="65a2b-137">藉由新增包含 <xref:System.Runtime.Serialization.SerializationInfo> 和 <xref:System.Runtime.Serialization.StreamingContext> 參數的例外狀況建構函式，提供例外狀況物件還原序列化更好的支援。</span><span class="sxs-lookup"><span data-stu-id="65a2b-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="65a2b-138">針對 .NET Framework 程式庫的支援</span><span class="sxs-lookup"><span data-stu-id="65a2b-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="65a2b-139">絕大多數的程式庫都是以 .NET Framework 為目標而不是 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="65a2b-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="65a2b-140">不過，那些程式庫中的大部分呼叫都是呼叫 .NET Standard 2.0 中包含的 API。</span><span class="sxs-lookup"><span data-stu-id="65a2b-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="65a2b-141">從 .NET Standard 2.0 開始，您可以使用[相容性填充碼](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification) \(英文\) 從 .NET Standard 程式庫存取 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="65a2b-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="65a2b-142">此相容性層級對開發人員是透明的，您不需要執行任何動作就能利用.NET Framework 程式庫。</span><span class="sxs-lookup"><span data-stu-id="65a2b-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="65a2b-143">唯一的要求是由 .NET Framework Class Library 呼叫的 API 必須包含在 .NET Standard 2.0 中。</span><span class="sxs-lookup"><span data-stu-id="65a2b-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="65a2b-144">Visual Basic 的支援</span><span class="sxs-lookup"><span data-stu-id="65a2b-144">Support for Visual Basic</span></span>

<span data-ttu-id="65a2b-145">您現在可以在 Visual Basic 中開發 .NET Standard 程式庫。</span><span class="sxs-lookup"><span data-stu-id="65a2b-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="65a2b-146">針對使用已安裝 .NET Core 工作負載之 Visual Studio 2017 15.3 版或更新版本的 Visual Basic 開發人員，Visual Studio 現在包含 .NET Standard 類別庫範本。</span><span class="sxs-lookup"><span data-stu-id="65a2b-146">For Visual Basic developers using Visual Studio 2017 version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="65a2b-147">對於使用其他開發工具和環境的 Visual Basic 開發人員，您可以使用 [dotnet new](../../core/tools/dotnet-new.md) 命令來建立 .NET Standard 程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="65a2b-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="65a2b-148">如需詳細資訊，請參閱 [.NET Standard 程式庫的工具支援](#tooling-support-for-net-standard-libraries)。</span><span class="sxs-lookup"><span data-stu-id="65a2b-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="65a2b-149">.NET Standard 程式庫的工具支援</span><span class="sxs-lookup"><span data-stu-id="65a2b-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="65a2b-150">隨 .NET Core 2.0 和 .NET Standard 2.0 的發行，Visual Studio 2017 和 [.NET Core 命令列介面 (CLI)](../../core/tools/index.md) 也都包含建立 .NET Standard 程式庫的工具支援。</span><span class="sxs-lookup"><span data-stu-id="65a2b-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="65a2b-151">如果您安裝包含 **.NET Core 跨平台開發**工作負載的 Visual Studio，就可以使用專案範本來建立 .NET Standard 2.0 程式庫專案，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="65a2b-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="65a2b-152">C#</span><span class="sxs-lookup"><span data-stu-id="65a2b-152">C#</span></span>](#tab/csharp)

![新增 .NET Standard 程式庫專案](./media/std-project-cs.png)

<span data-ttu-id="65a2b-154">如果您是使用 .NET Core CLI，下列 [dotnet new](../../core/tools/dotnet-new.md) 命令會建立以 .NET Standard 2.0 為目標的類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="65a2b-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="65a2b-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65a2b-155">Visual Basic</span></span>](#tab/vb)

![新增 .NET Standard 程式庫專案](./media/std-project-vb.png)

<span data-ttu-id="65a2b-157">如果您是使用 .NET Core CLI，下列 [dotnet new](../../core/tools/dotnet-new.md) 命令會建立以 .NET Standard 2.0 為目標的類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="65a2b-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="65a2b-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="65a2b-158">See also</span></span>

- [<span data-ttu-id="65a2b-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="65a2b-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="65a2b-160">.NET Standard 簡介</span><span class="sxs-lookup"><span data-stu-id="65a2b-160">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
