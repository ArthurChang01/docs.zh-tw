---
title: 停駐控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02f1c26dcb322a39c41781c83d8c820bd2fd27e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745517"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="cd553-102">如何：將控制項停駐在 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd553-102">How to: Dock controls on Windows Forms</span></span>

<span data-ttu-id="cd553-103">您可以將控制項停駐在表單的邊緣，或讓它們填滿控制項的容器（表單或容器控制項）。</span><span class="sxs-lookup"><span data-stu-id="cd553-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="cd553-104">例如，Windows Explorer 會將其 <xref:System.Windows.Forms.TreeView> 控制項停駐于視窗的左邊，並將其 <xref:System.Windows.Forms.ListView> 控制項放到視窗右側。</span><span class="sxs-lookup"><span data-stu-id="cd553-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="cd553-105">使用所有可見 Windows Forms 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性來定義停駐模式。</span><span class="sxs-lookup"><span data-stu-id="cd553-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>

> [!NOTE]
> <span data-ttu-id="cd553-106">控制項停駐在反向迭置順序中。</span><span class="sxs-lookup"><span data-stu-id="cd553-106">Controls are docked in reverse z-order.</span></span>

<span data-ttu-id="cd553-107"><xref:System.Windows.Forms.Control.Dock%2A> 屬性會與 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性互動。</span><span class="sxs-lookup"><span data-stu-id="cd553-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="cd553-108">如需詳細資訊，請參閱[AutoSize 屬性總覽](autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cd553-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="to-dock-a-control"></a><span data-ttu-id="cd553-109">若要停駐控制項</span><span class="sxs-lookup"><span data-stu-id="cd553-109">To dock a control</span></span>

1. <span data-ttu-id="cd553-110">在 Visual Studio 中，選取您要停駐的控制項。</span><span class="sxs-lookup"><span data-stu-id="cd553-110">In Visual Studio, select the control that you want to dock.</span></span>

2. <span data-ttu-id="cd553-111">在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.Control.Dock%2A>] 屬性右邊的箭號。</span><span class="sxs-lookup"><span data-stu-id="cd553-111">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

   <span data-ttu-id="cd553-112">隨即顯示編輯器，其中會顯示一系列代表表單邊緣和中心的方塊。</span><span class="sxs-lookup"><span data-stu-id="cd553-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>

3. <span data-ttu-id="cd553-113">按一下代表您要停駐控制項之表單邊緣的按鈕。</span><span class="sxs-lookup"><span data-stu-id="cd553-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="cd553-114">若要填滿控制項表單或容器控制項的內容，請按一下 [中央] 方塊。</span><span class="sxs-lookup"><span data-stu-id="cd553-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="cd553-115">按一下 **[（無）** ] 以停用銜接。</span><span class="sxs-lookup"><span data-stu-id="cd553-115">Click **(none)** to disable docking.</span></span>

   <span data-ttu-id="cd553-116">控制項會自動調整大小，以符合停駐邊緣的界限。</span><span class="sxs-lookup"><span data-stu-id="cd553-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>

   > [!NOTE]
   > <span data-ttu-id="cd553-117">繼承的控制項必須 `Protected`，才能夠停駐。</span><span class="sxs-lookup"><span data-stu-id="cd553-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="cd553-118">若要變更控制項的存取層級，請在 [**屬性**] 視窗中設定其 [**修飾**詞] 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd553-118">To change the access level of a control, set its **Modifier** property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd553-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd553-119">See also</span></span>

- [<span data-ttu-id="cd553-120">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="cd553-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="cd553-121">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="cd553-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="cd553-122">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="cd553-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="cd553-123">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="cd553-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="cd553-124">操作說明：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="cd553-124">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="cd553-125">操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="cd553-125">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="cd553-126">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="cd553-126">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="cd553-127">操作說明：錨定 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="cd553-127">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
