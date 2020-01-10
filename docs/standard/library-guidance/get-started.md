---
title: 開始建立高品質的 .NET 程式庫
description: 開始建置 .NET 程式庫。
ms.date: 10/02/2018
ms.openlocfilehash: 10576219d8470a171ad0f1f347196999b2a2ee03
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706487"
---
# <a name="get-started"></a><span data-ttu-id="7f716-103">開始使用</span><span class="sxs-lookup"><span data-stu-id="7f716-103">Get started</span></span>

## <a name="cross-platform-targetingcross-platform-targetingmd"></a>[<span data-ttu-id="7f716-104">跨平台目標</span><span class="sxs-lookup"><span data-stu-id="7f716-104">Cross-platform targeting</span></span>](./cross-platform-targeting.md)

<span data-ttu-id="7f716-105">如何使用 .NET Standard 與多目標設定來建立跨平台程式庫。</span><span class="sxs-lookup"><span data-stu-id="7f716-105">How to use .NET Standard and multi-targeting to create cross-platform libraries.</span></span> <span data-ttu-id="7f716-106">.NET 可在許多地方執行，而 .NET 程式庫所支援的平台與開發人員應該越多越好。</span><span class="sxs-lookup"><span data-stu-id="7f716-106">.NET runs in many places, and good .NET libraries should strive to support as many platforms and developers as possible.</span></span>

## <a name="strong-namingstrong-namingmd"></a>[<span data-ttu-id="7f716-107">強式命名</span><span class="sxs-lookup"><span data-stu-id="7f716-107">Strong naming</span></span>](./strong-naming.md)

<span data-ttu-id="7f716-108">了解強式命名與其優缺點。</span><span class="sxs-lookup"><span data-stu-id="7f716-108">Learn about strong naming and its advantages and disadvantages.</span></span> <span data-ttu-id="7f716-109">為 .NET 程式庫提供強式命名可讓大部分的開發人員使用它，這也是建議的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="7f716-109">Strong naming a .NET library allows the most developers to use it and is a recommended best practice.</span></span>

## <a name="nuget-and-open-source-librariesnugetmd"></a>[<span data-ttu-id="7f716-110">NuGet 與開放原始碼程式庫</span><span class="sxs-lookup"><span data-stu-id="7f716-110">NuGet and open-source libraries</span></span>](./nuget.md)

<span data-ttu-id="7f716-111">針對開放原始碼 .NET 程式庫建立 NuGet 套件的最佳方式，包括適用於在 NuGet.org 上公開發佈之所有套件的建議中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7f716-111">The best way to create NuGet packages for open-source .NET libraries, including recommended metadata for all packages published publicly on NuGet.org.</span></span>

### <a name="dependenciesdependenciesmd"></a>[<span data-ttu-id="7f716-112">相依性</span><span class="sxs-lookup"><span data-stu-id="7f716-112">Dependencies</span></span>](./dependencies.md)

<span data-ttu-id="7f716-113">NuGet 可讓您在建置 .NET 程式庫時輕鬆使用現有的套件。</span><span class="sxs-lookup"><span data-stu-id="7f716-113">NuGet makes it easy to use existing packages when building a .NET library.</span></span> <span data-ttu-id="7f716-114">了解 NuGet 相依性的常見摩擦原因，以及避免它們的方法。</span><span class="sxs-lookup"><span data-stu-id="7f716-114">Learn about NuGet dependencies' common sources of friction and how to avoid them.</span></span>

### <a name="source-linksourcelinkmd"></a>[<span data-ttu-id="7f716-115">來源連結</span><span class="sxs-lookup"><span data-stu-id="7f716-115">Source Link</span></span>](./sourcelink.md)

<span data-ttu-id="7f716-116">來源連結是可讓您 .NET 程式庫的使用者在偵錯期間逐步執行其原始程式碼的絕佳工具。</span><span class="sxs-lookup"><span data-stu-id="7f716-116">Source Link is a great tool that allows users of your .NET library to step into its source code while debugging.</span></span> <span data-ttu-id="7f716-117">此文章會提供來源連結的概觀，以及您應該使用它的原因。</span><span class="sxs-lookup"><span data-stu-id="7f716-117">This article is an overview of what Source Link is and why you should use it.</span></span>

### <a name="publishingpublish-nuget-packagemd"></a>[<span data-ttu-id="7f716-118">發佈</span><span class="sxs-lookup"><span data-stu-id="7f716-118">Publishing</span></span>](./publish-nuget-package.md)

<span data-ttu-id="7f716-119">雖然 NuGet.org 是最廣為人知且最常被使用的存放庫，還有許多其他可以發佈 NuGet 套件的地方。</span><span class="sxs-lookup"><span data-stu-id="7f716-119">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages.</span></span> <span data-ttu-id="7f716-120">了解各種可供使用的 NuGet 套件存放庫，以及發佈 .NET 存放庫的安全性最佳做法。</span><span class="sxs-lookup"><span data-stu-id="7f716-120">Learn about the different NuGet package repositories available, and security best practices for publishing a .NET library.</span></span>

## <a name="versioningversioningmd"></a>[<span data-ttu-id="7f716-121">版本控制</span><span class="sxs-lookup"><span data-stu-id="7f716-121">Versioning</span></span>](./versioning.md)

<span data-ttu-id="7f716-122">良好的 .NET 程式庫會隨著時間演進，並會在後續版本中新增功能、修正錯誤 (Bug) 並改善效能。</span><span class="sxs-lookup"><span data-stu-id="7f716-122">Good .NET libraries evolve over time, adding features, fixing bugs, and improving performance in later releases.</span></span> <span data-ttu-id="7f716-123">了解各種版本號碼，以及如何與開發人員溝通中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="7f716-123">Learn about the various version numbers and how to communicate breaking changes to developers.</span></span>

### <a name="breaking-changesbreaking-changesmd"></a>[<span data-ttu-id="7f716-124">重大變更</span><span class="sxs-lookup"><span data-stu-id="7f716-124">Breaking changes</span></span>](./breaking-changes.md)

<span data-ttu-id="7f716-125">.NET 程式庫必須在針對現有使用者提供穩定性，以及針對未來取得創新之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="7f716-125">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="7f716-126">了解各種類型的中斷性變更，以及在維持回溯相容性的同時新增功能的策略。</span><span class="sxs-lookup"><span data-stu-id="7f716-126">Learn about the different kinds of breaking changes and strategies for adding new features while maintaining backwards compatibility.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7f716-127">[上一頁](index.md)
>[下一頁](cross-platform-targeting.md)</span><span class="sxs-lookup"><span data-stu-id="7f716-127">[Previous](index.md)
[Next](cross-platform-targeting.md)</span></span>
