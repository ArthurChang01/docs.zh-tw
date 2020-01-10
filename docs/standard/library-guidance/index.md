---
title: 開放原始碼 .NET 程式庫指導方針
description: 協助開發人員建立高品質 .NET 程式庫的最佳做法建議。
ms.date: 10/17/2018
ms.openlocfilehash: c1e1c302eede86fd5555a8e84630e216e96f1ce7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706448"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="d9c6d-103">開放原始碼程式庫指導方針</span><span class="sxs-lookup"><span data-stu-id="d9c6d-103">Open-source library guidance</span></span>

<span data-ttu-id="d9c6d-104">這份指導提供協助開發人員建立高品質 .NET 程式庫的最佳做法建議。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="d9c6d-105">本文件的重點在於建置 .NET 程式庫時的「內容」與「原因」，而不是「方法」。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="d9c6d-106">高品質開放原始碼 .NET 程式庫的各個層面：</span><span class="sxs-lookup"><span data-stu-id="d9c6d-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d9c6d-107">**包山包海** - 致力於支援多種平台、程式設計語言與應用程式的優質 .NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="d9c6d-108">**穩定可靠** - 優質的 .NET 程式庫可在 .NET 生態環境中共存，能在使用多種程式庫建置而成的應用程式中執行。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="d9c6d-109">**具備演進能力** - .NET 程式庫應該要隨著時間改善與演進，同時支援現有的使用者。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="d9c6d-110">**可供偵錯** - .NET 程式庫應使用最新工具來為使用者打造良好的偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="d9c6d-111">**值得信賴** - .NET 程式庫使用安全性最佳做法來發行到 NuGet，以獲得開發人員的信任。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d9c6d-112">開始使用</span><span class="sxs-lookup"><span data-stu-id="d9c6d-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="d9c6d-113">建議類型</span><span class="sxs-lookup"><span data-stu-id="d9c6d-113">Types of recommendations</span></span>

<span data-ttu-id="d9c6d-114">每篇文章都呈現四種類型的建議：**優先**、**考慮**、**避免**與**禁止**。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="d9c6d-115">建議類型指出應遵循的程度。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="d9c6d-116">您應該一律遵循**優先**類型的建議。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="d9c6d-117">例如：</span><span class="sxs-lookup"><span data-stu-id="d9c6d-117">For example:</span></span>

<span data-ttu-id="d9c6d-118">**✔️ 優先**使用 NuGet 套件散發您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-118">**✔️ DO** distribute your library using a NuGet package.</span></span>

<span data-ttu-id="d9c6d-119">至於**考慮**建議則通常應該遵循，但也會有不符合規則的例外，而您不必因為沒有遵循指導而感到自責：</span><span class="sxs-lookup"><span data-stu-id="d9c6d-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="d9c6d-120">**✔️ 考慮**使用 [SemVer 2.0.0](https://semver.org/) 來設定 NuGet 套件的版本。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-120">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="d9c6d-121">**避免**建議指的是通常不建議採行的建議，但有時違反規則尚屬合理情況：</span><span class="sxs-lookup"><span data-stu-id="d9c6d-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="d9c6d-122">**❌ 避免**需要確切版本的 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-122">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="d9c6d-123">最後，**禁止**類型的建議表示在多數情況下都不應採取的動作：</span><span class="sxs-lookup"><span data-stu-id="d9c6d-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="d9c6d-124">**❌ 不要**發佈程式庫的強式名稱和非強式名稱版本。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-124">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="d9c6d-125">例如，`Contoso.Api` 和 `Contoso.Api.StrongNamed`。</span><span class="sxs-lookup"><span data-stu-id="d9c6d-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d9c6d-126">下一步</span><span class="sxs-lookup"><span data-stu-id="d9c6d-126">Next</span></span>](get-started.md)
