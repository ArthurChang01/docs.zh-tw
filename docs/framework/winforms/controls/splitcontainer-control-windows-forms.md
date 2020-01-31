---
title: SplitContainer 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: ac04f60847aa6f77c11637f37b5ec94b6f7ef341
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742913"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="1ef13-102">SplitContainer 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="1ef13-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="1ef13-103">Windows Form `SplitContainer` 控制項可視為一個複合控制項，其中包含兩個可移動的分隔列所分隔的面板。</span><span class="sxs-lookup"><span data-stu-id="1ef13-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="1ef13-104">將滑鼠指標移到分隔列上時，指標會變更形狀，以顯示分隔列是可移動的。</span><span class="sxs-lookup"><span data-stu-id="1ef13-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ef13-105">在 [**工具箱**] 中，此控制項會取代舊版 Visual Studio 中的 <xref:System.Windows.Forms.Splitter> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1ef13-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="1ef13-106">`SplitContainer` 控制項會比 <xref:System.Windows.Forms.Splitter> 控制項合用。</span><span class="sxs-lookup"><span data-stu-id="1ef13-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="1ef13-107">.NET Framework 中仍會包含 <xref:System.Windows.Forms.Splitter> 類別，以與現有的應用程式相容，但強烈建議您在新專案中使用 `SplitContainer` 控制項。</span><span class="sxs-lookup"><span data-stu-id="1ef13-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="1ef13-108">`SplitContainer` 控制項可讓您建立複雜的使用者介面；通常，在某個面板中選取的項目會決定在另一個面板中所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="1ef13-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="1ef13-109">這種排列方式可有效地顯示及瀏覽資訊。</span><span class="sxs-lookup"><span data-stu-id="1ef13-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="1ef13-110">擁有兩個面板可讓您彙總區域中的資訊，而分隔列 (或「分隔器」) 可讓使用者輕鬆調整面板的大小。</span><span class="sxs-lookup"><span data-stu-id="1ef13-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ef13-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="1ef13-111">In This Section</span></span>  
 [<span data-ttu-id="1ef13-112">SplitContainer 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1ef13-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="1ef13-113">介紹 `SplitContainer` 控制項，並描述常用的屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="1ef13-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="1ef13-114">操作說明：定義分隔視窗的調整大小和位置行為</span><span class="sxs-lookup"><span data-stu-id="1ef13-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="1ef13-115">描述如何在 `SplitContainer` 控制項中控制分隔器。</span><span class="sxs-lookup"><span data-stu-id="1ef13-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="1ef13-116">操作說明：水平分隔視窗</span><span class="sxs-lookup"><span data-stu-id="1ef13-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="1ef13-117">描述如何在 `SplitContainer` 控制項中控制分隔器的方向。</span><span class="sxs-lookup"><span data-stu-id="1ef13-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="1ef13-118">逐步解說：利用 Windows Forms 建立多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="1ef13-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="1ef13-119">建立與 Microsoft Outlook 中所用類似的多窗格使用者介面。</span><span class="sxs-lookup"><span data-stu-id="1ef13-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="1ef13-120">另請參閱[如何：使用設計工具水準分割視窗](how-to-split-a-window-horizontally-using-the-designer.md)、[如何：在 Windows Form 上建立 windows Explorer 樣式的介面](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md)、[如何：使用設計工具建立具有 Windows Forms 的多窗格使用者介面](create-a-multipane-user-interface-with-wf-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="1ef13-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1ef13-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="1ef13-121">Reference</span></span>  
 <span data-ttu-id="1ef13-122"><xref:System.Windows.Forms.SplitContainer> 類別</span><span class="sxs-lookup"><span data-stu-id="1ef13-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="1ef13-123">說明這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="1ef13-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ef13-124">相關章節</span><span class="sxs-lookup"><span data-stu-id="1ef13-124">Related Sections</span></span>  
 [<span data-ttu-id="1ef13-125">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="1ef13-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="1ef13-126">提供專為搭配 Windows Form 使用所設計之控制項的相關主題連結。</span><span class="sxs-lookup"><span data-stu-id="1ef13-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="1ef13-127">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="1ef13-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="1ef13-128">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="1ef13-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
