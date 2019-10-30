---
title: 實作 UI 自動化 MultipleView 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: edef213c0f4d43a15b7c6842ef6c62e95544da66
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039504"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="c3310-102">實作 UI 自動化 MultipleView 控制項模式</span><span class="sxs-lookup"><span data-stu-id="c3310-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="c3310-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="c3310-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c3310-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="c3310-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c3310-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IMultipleViewProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c3310-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="c3310-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="c3310-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="c3310-107"><xref:System.Windows.Automation.MultipleViewPattern> 控制項模式可用來支援控制項，這種控制項提供相同一組資訊或子控制項的多種不同表示，而且能夠在這些表示之間切換。</span><span class="sxs-lookup"><span data-stu-id="c3310-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="c3310-108">可以顯示多個視圖的控制項範例包括 [清單] 視圖（可以將其內容顯示為縮圖、磚、圖示或詳細資料）、[!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] 圖表（圓形圖、折線圖、橫條圖、具有公式的儲存格值）、[!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] 檔（一般、Web 配置、列印版面配置、閱讀版面配置、大綱）、Microsoft Outlook 行事曆（年、月、周、日）和 Microsoft Windows 媒體播放機的外觀。</span><span class="sxs-lookup"><span data-stu-id="c3310-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="c3310-109">支援哪些檢視會由控制項的開發人員決定，而且是每個控制項所特有。</span><span class="sxs-lookup"><span data-stu-id="c3310-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c3310-110">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="c3310-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="c3310-111">實作多重檢視控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="c3310-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="c3310-112">若管理目前檢視的容器與提供目前檢視的控制項不同，則也應在容器上實作<xref:System.Windows.Automation.Provider.IMultipleViewProvider> 。</span><span class="sxs-lookup"><span data-stu-id="c3310-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="c3310-113">例如，Windows 檔案總管包含目前資料夾內容的清單控制項，而控制項的檢視則是由 Windows 檔案總管應用程式管理。</span><span class="sxs-lookup"><span data-stu-id="c3310-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="c3310-114">可以排序內容的控制項不視為支援多種檢視。</span><span class="sxs-lookup"><span data-stu-id="c3310-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="c3310-115">檢視集合在執行個體之間必須完全相同。</span><span class="sxs-lookup"><span data-stu-id="c3310-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="c3310-116">檢視名稱必須適用於文字轉換語音、點字以及其他人類看得懂的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3310-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="c3310-117">IMultipleViewProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="c3310-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="c3310-118">以下是實作 IMultipleViewProvider 的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="c3310-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="c3310-119">必要成員</span><span class="sxs-lookup"><span data-stu-id="c3310-119">Required members</span></span>|<span data-ttu-id="c3310-120">成員類型</span><span class="sxs-lookup"><span data-stu-id="c3310-120">Member type</span></span>|<span data-ttu-id="c3310-121">備註</span><span class="sxs-lookup"><span data-stu-id="c3310-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="c3310-122">屬性</span><span class="sxs-lookup"><span data-stu-id="c3310-122">Property</span></span>|<span data-ttu-id="c3310-123">None</span><span class="sxs-lookup"><span data-stu-id="c3310-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="c3310-124">方法</span><span class="sxs-lookup"><span data-stu-id="c3310-124">Method</span></span>|<span data-ttu-id="c3310-125">None</span><span class="sxs-lookup"><span data-stu-id="c3310-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="c3310-126">方法</span><span class="sxs-lookup"><span data-stu-id="c3310-126">Method</span></span>|<span data-ttu-id="c3310-127">None</span><span class="sxs-lookup"><span data-stu-id="c3310-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="c3310-128">方法</span><span class="sxs-lookup"><span data-stu-id="c3310-128">Method</span></span>|<span data-ttu-id="c3310-129">None</span><span class="sxs-lookup"><span data-stu-id="c3310-129">None</span></span>|  
  
 <span data-ttu-id="c3310-130">這個控制項模式沒有相關事件。</span><span class="sxs-lookup"><span data-stu-id="c3310-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="c3310-131">例外狀況</span><span class="sxs-lookup"><span data-stu-id="c3310-131">Exceptions</span></span>  
 <span data-ttu-id="c3310-132">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c3310-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="c3310-133">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="c3310-133">Exception type</span></span>|<span data-ttu-id="c3310-134">條件</span><span class="sxs-lookup"><span data-stu-id="c3310-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="c3310-135">呼叫 <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> 或 <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> 時使用的參數不是所支援檢視集合的成員。</span><span class="sxs-lookup"><span data-stu-id="c3310-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3310-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3310-136">See also</span></span>

- [<span data-ttu-id="c3310-137">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="c3310-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="c3310-138">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="c3310-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="c3310-139">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="c3310-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="c3310-140">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="c3310-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="c3310-141">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="c3310-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
