---
title: 實作 UI 自動化 Toggle 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: c25f2d3b73e90adb3299ff8c4ff7c8a77fc5fc5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447069"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="2a06b-102">實作 UI 自動化 Toggle 控制項模式</span><span class="sxs-lookup"><span data-stu-id="2a06b-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="2a06b-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="2a06b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2a06b-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="2a06b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2a06b-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IToggleProvider>的方針和慣例，包括方法和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2a06b-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="2a06b-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="2a06b-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="2a06b-107"><xref:System.Windows.Automation.TogglePattern> 控制項模式是用來支援可循環顯示一組狀態，並在設定之後維持狀態的控制項。</span><span class="sxs-lookup"><span data-stu-id="2a06b-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="2a06b-108">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="2a06b-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="2a06b-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="2a06b-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="2a06b-110">實作切換控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="2a06b-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="2a06b-111">若控制項在啟動後不會維持狀態，如按鈕、工具列按鈕和超連結，則必須改為實作 <xref:System.Windows.Automation.Provider.IInvokeProvider> 。</span><span class="sxs-lookup"><span data-stu-id="2a06b-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="2a06b-112">控制項必須以下列順序循環其 <xref:System.Windows.Automation.ToggleState> ： <xref:System.Windows.Automation.ToggleState.On>、 <xref:System.Windows.Automation.ToggleState.Off> 以及 <xref:System.Windows.Automation.ToggleState.Indeterminate>(若支援的話)。</span><span class="sxs-lookup"><span data-stu-id="2a06b-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="2a06b-113"><xref:System.Windows.Automation.TogglePattern> 不提供 SetState(newState) 方法，因為直接設定三種狀態的核取方塊，而不依適當的 <xref:System.Windows.Automation.ToggleState> 順序循環時會發生問題。</span><span class="sxs-lookup"><span data-stu-id="2a06b-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="2a06b-114">RadioButton 控制項不會實作 <xref:System.Windows.Automation.Provider.IToggleProvider>，因為它無法循環其有效狀態。</span><span class="sxs-lookup"><span data-stu-id="2a06b-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="2a06b-115">IToggleProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="2a06b-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="2a06b-116">以下是實作 <xref:System.Windows.Automation.Provider.IToggleProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="2a06b-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="2a06b-117">必要成員</span><span class="sxs-lookup"><span data-stu-id="2a06b-117">Required member</span></span>|<span data-ttu-id="2a06b-118">成員類型</span><span class="sxs-lookup"><span data-stu-id="2a06b-118">Member type</span></span>|<span data-ttu-id="2a06b-119">備註</span><span class="sxs-lookup"><span data-stu-id="2a06b-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="2a06b-120">方法</span><span class="sxs-lookup"><span data-stu-id="2a06b-120">Method</span></span>|<span data-ttu-id="2a06b-121">None</span><span class="sxs-lookup"><span data-stu-id="2a06b-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="2a06b-122">屬性</span><span class="sxs-lookup"><span data-stu-id="2a06b-122">Property</span></span>|<span data-ttu-id="2a06b-123">None</span><span class="sxs-lookup"><span data-stu-id="2a06b-123">None</span></span>|  
  
 <span data-ttu-id="2a06b-124">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="2a06b-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="2a06b-125">例外狀況</span><span class="sxs-lookup"><span data-stu-id="2a06b-125">Exceptions</span></span>  
 <span data-ttu-id="2a06b-126">此控制項模式沒有任何相關聯的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2a06b-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a06b-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a06b-127">See also</span></span>

- [<span data-ttu-id="2a06b-128">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="2a06b-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="2a06b-129">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="2a06b-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="2a06b-130">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="2a06b-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="2a06b-131">使用 UI 自動化取得核取方塊的切換狀態</span><span class="sxs-lookup"><span data-stu-id="2a06b-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="2a06b-132">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="2a06b-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="2a06b-133">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="2a06b-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
