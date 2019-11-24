---
title: 實作 UI 自動化 RangeValue 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 04db9f97ccea10cf8c65df0f0117c272a5e868dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435111"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="8c9a5-102">實作 UI 自動化 RangeValue 控制項模式</span><span class="sxs-lookup"><span data-stu-id="8c9a5-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="8c9a5-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8c9a5-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8c9a5-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IRangeValueProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="8c9a5-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8c9a5-107"><xref:System.Windows.Automation.RangeValuePattern> 控制項模式用來支援可以設定為某範圍內的值之控制項。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="8c9a5-108">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8c9a5-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="8c9a5-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8c9a5-110">實作範圍值控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="8c9a5-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="8c9a5-111">控制項可以根據地區設定或使用者偏好設定，重新劃分所支援屬性的刻度。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="8c9a5-112">例如，溫度計控制項可以設為顯示華氏或攝氏溫度。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="8c9a5-113">範圍值不明確的控制項 (如進度列或滑桿) 應將這些值正規化。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="8c9a5-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="8c9a5-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="8c9a5-115">進度列範例，其中的值屬於整數類型，而最小值和最大值的屬性值分別正規化為 0 和 100。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="8c9a5-116">IRangeValueProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="8c9a5-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="8c9a5-117">必要成員</span><span class="sxs-lookup"><span data-stu-id="8c9a5-117">Required member</span></span>|<span data-ttu-id="8c9a5-118">成員類型</span><span class="sxs-lookup"><span data-stu-id="8c9a5-118">Member type</span></span>|<span data-ttu-id="8c9a5-119">備註</span><span class="sxs-lookup"><span data-stu-id="8c9a5-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="8c9a5-120">屬性</span><span class="sxs-lookup"><span data-stu-id="8c9a5-120">Property</span></span>|<span data-ttu-id="8c9a5-121">None</span><span class="sxs-lookup"><span data-stu-id="8c9a5-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="8c9a5-122">屬性</span><span class="sxs-lookup"><span data-stu-id="8c9a5-122">Property</span></span>|<span data-ttu-id="8c9a5-123">None</span><span class="sxs-lookup"><span data-stu-id="8c9a5-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="8c9a5-124">屬性</span><span class="sxs-lookup"><span data-stu-id="8c9a5-124">Property</span></span>|<span data-ttu-id="8c9a5-125">None</span><span class="sxs-lookup"><span data-stu-id="8c9a5-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="8c9a5-126">屬性</span><span class="sxs-lookup"><span data-stu-id="8c9a5-126">Property</span></span>|<span data-ttu-id="8c9a5-127">None</span><span class="sxs-lookup"><span data-stu-id="8c9a5-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="8c9a5-128">屬性</span><span class="sxs-lookup"><span data-stu-id="8c9a5-128">Property</span></span>|<span data-ttu-id="8c9a5-129">None</span><span class="sxs-lookup"><span data-stu-id="8c9a5-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="8c9a5-130">屬性</span><span class="sxs-lookup"><span data-stu-id="8c9a5-130">Property</span></span>|<span data-ttu-id="8c9a5-131">None</span><span class="sxs-lookup"><span data-stu-id="8c9a5-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="8c9a5-132">方法</span><span class="sxs-lookup"><span data-stu-id="8c9a5-132">Methods</span></span>|<span data-ttu-id="8c9a5-133">None</span><span class="sxs-lookup"><span data-stu-id="8c9a5-133">None</span></span>|  
  
 <span data-ttu-id="8c9a5-134">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8c9a5-135">例外狀況</span><span class="sxs-lookup"><span data-stu-id="8c9a5-135">Exceptions</span></span>  
 <span data-ttu-id="8c9a5-136">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8c9a5-137">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="8c9a5-137">Exception type</span></span>|<span data-ttu-id="8c9a5-138">條件</span><span class="sxs-lookup"><span data-stu-id="8c9a5-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="8c9a5-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> 以大於 <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> 或小於 <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>的值呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c9a5-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c9a5-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c9a5-140">See also</span></span>

- [<span data-ttu-id="8c9a5-141">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="8c9a5-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="8c9a5-142">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="8c9a5-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="8c9a5-143">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="8c9a5-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="8c9a5-144">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="8c9a5-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="8c9a5-145">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="8c9a5-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
