---
title: 設定 DataGridView 控制項的替代資料列樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: b87ad50ef7e5118a95998949bc62299955856b27
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747130"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="85f8d-102">如何：設定 Windows Form DataGridView 控制項的替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="85f8d-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="85f8d-103">表格式資料通常會以類似 Ledger 的格式呈現給使用者，在這種格式中，交替資料列會有不同的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="85f8d-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="85f8d-104">這種格式可讓使用者輕鬆地指出每個資料列中有哪些儲存格，特別是具有許多資料行的寬資料表。</span><span class="sxs-lookup"><span data-stu-id="85f8d-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="85f8d-105">利用 <xref:System.Windows.Forms.DataGridView> 控制項，您可以指定替代資料列的完整樣式資訊。</span><span class="sxs-lookup"><span data-stu-id="85f8d-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="85f8d-106">這個控制項可讓您使用背景色彩以外的樣式特性 (例如前景色彩和字型)，來區分替代資料列。</span><span class="sxs-lookup"><span data-stu-id="85f8d-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="85f8d-107">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="85f8d-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="85f8d-108">另請參閱[如何：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="85f8d-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="85f8d-109">以程式設計方式設定替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="85f8d-109">To set alternating row styles programmatically</span></span>  
  
- <span data-ttu-id="85f8d-110">設定由 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> 屬性所傳回之 <xref:System.Windows.Forms.DataGridView> 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="85f8d-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > <span data-ttu-id="85f8d-111">使用 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> 屬性所指定的樣式，會覆寫在資料行和 <xref:System.Windows.Forms.DataGridView> 層級上所指定的樣式，但會由在個別資料列和儲存格層級設定的樣式所覆寫。</span><span class="sxs-lookup"><span data-stu-id="85f8d-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="85f8d-112">如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="85f8d-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85f8d-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="85f8d-113">Compiling the Code</span></span>  
 <span data-ttu-id="85f8d-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="85f8d-114">This example requires:</span></span>  
  
- <span data-ttu-id="85f8d-115">名為 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控制項。</span><span class="sxs-lookup"><span data-stu-id="85f8d-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="85f8d-116"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="85f8d-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="85f8d-117">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="85f8d-117">Robust Programming</span></span>  
 <span data-ttu-id="85f8d-118">若要達到最大延展性，您應該在使用相同樣式的多個資料列、資料行或儲存格之間共用 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是分別設定每個項目的樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="85f8d-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="85f8d-119">如需詳細資訊，請參閱 [縮放 Windows Form DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="85f8d-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f8d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85f8d-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="85f8d-121">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="85f8d-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="85f8d-122">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="85f8d-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="85f8d-123">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="85f8d-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="85f8d-124">操作說明：設定 Windows Forms DataGridView 控制項的字型和色彩樣式</span><span class="sxs-lookup"><span data-stu-id="85f8d-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
