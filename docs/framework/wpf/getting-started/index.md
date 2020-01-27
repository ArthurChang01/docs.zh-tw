---
title: 使用者入門
ms.date: 01/26/2018
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
ms.openlocfilehash: 0c23fd3c2e0af53005e1c2c1cec6b44c09158bd6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733753"
---
# <a name="getting-started-wpf"></a><span data-ttu-id="482f2-102">使用者入門 (WPF)</span><span class="sxs-lookup"><span data-stu-id="482f2-102">Getting Started (WPF)</span></span>
<span data-ttu-id="482f2-103">Windows Presentation Foundation (WPF) 是建立桌面用戶端應用程式的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="482f2-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="482f2-104">WPF 開發平台支援一組廣泛的應用程式開發功能，包含應用程式模型、資源、控制項、圖形、版面配置、資料繫結、文件和安全性。</span><span class="sxs-lookup"><span data-stu-id="482f2-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="482f2-105">它是 .NET Framework 的子集，所以若您先前已使用 ASP.NET 或 Windows Form 以 .NET Framework 建置過應用程式，應該會對此程式設計體驗感到熟悉。</span><span class="sxs-lookup"><span data-stu-id="482f2-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="482f2-106">WPF 使用可延伸應用程式標記語言 (XAML) 來提供應用程式設計的宣告式模型。</span><span class="sxs-lookup"><span data-stu-id="482f2-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="482f2-107">本章節的主題將介紹及幫助您開始使用 WPF。</span><span class="sxs-lookup"><span data-stu-id="482f2-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="482f2-108">我該從哪裡開始？</span><span class="sxs-lookup"><span data-stu-id="482f2-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="482f2-109">我想直接開始</span><span class="sxs-lookup"><span data-stu-id="482f2-109">I want to jump right in…</span></span>|[<span data-ttu-id="482f2-110">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="482f2-110">Walkthrough: My first WPF desktop application</span></span>](walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="482f2-111">我該如何設計應用程式 UI？</span><span class="sxs-lookup"><span data-stu-id="482f2-111">How do I design the application UI?</span></span>|[<span data-ttu-id="482f2-112">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="482f2-112">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="482f2-113">剛開始使用 .NET 嗎？</span><span class="sxs-lookup"><span data-stu-id="482f2-113">New to .NET?</span></span>|[<span data-ttu-id="482f2-114">.NET Framework 概觀</span><span class="sxs-lookup"><span data-stu-id="482f2-114">Overview of the .NET Framework</span></span>](../../get-started/overview.md)<br /><br /> [<span data-ttu-id="482f2-115">.NET Framework 應用程式基本概念</span><span class="sxs-lookup"><span data-stu-id="482f2-115">.NET Framework Application Essentials</span></span>](../../../standard/application-essentials.md)<br /><br /> [<span data-ttu-id="482f2-116">Visual C# 和 Visual Basic 使用者入門</span><span class="sxs-lookup"><span data-stu-id="482f2-116">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/quickstart-visual-basic-console)|  
|<span data-ttu-id="482f2-117">WPF 的相關詳細資訊...</span><span class="sxs-lookup"><span data-stu-id="482f2-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="482f2-118">Visual Studio 中的 WPF 簡介</span><span class="sxs-lookup"><span data-stu-id="482f2-118">Introduction to WPF in Visual Studio</span></span>](introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="482f2-119">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="482f2-119">XAML Overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="482f2-120">控制項</span><span class="sxs-lookup"><span data-stu-id="482f2-120">Controls</span></span>](../controls/index.md)<br /><br /> [<span data-ttu-id="482f2-121">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="482f2-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="482f2-122">您是 Windows Form 開發人員嗎？</span><span class="sxs-lookup"><span data-stu-id="482f2-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="482f2-123">Windows Forms 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="482f2-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="482f2-124">WPF 和 Windows Forms 互通</span><span class="sxs-lookup"><span data-stu-id="482f2-124">WPF and Windows Forms Interoperation</span></span>](../advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="482f2-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="482f2-125">See also</span></span>

- [<span data-ttu-id="482f2-126">類別庫</span><span class="sxs-lookup"><span data-stu-id="482f2-126">Class Library</span></span>](../class-library-wpf.md)
- [<span data-ttu-id="482f2-127">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="482f2-127">Application Development</span></span>](../app-development/index.md)
- [<span data-ttu-id="482f2-128">.NET Framework 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="482f2-128">.NET Framework Developer Center</span></span>](https://www.microsoft.com/net)
