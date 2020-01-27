---
title: 設定 DataGridView 控制項的調整大小模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738399"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="43ce1-102">如何：設定 Windows Forms DataGridView 控制項的縮放模式</span><span class="sxs-lookup"><span data-stu-id="43ce1-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="43ce1-103">下列程序示範一些常見的情況，這些自訂或結合可用的調整大小選項以供 <xref:System.Windows.Forms.DataGridView> 控制項以及控制項中的特定資料行使用。</span><span class="sxs-lookup"><span data-stu-id="43ce1-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="43ce1-104">建立固定寬度資料行</span><span class="sxs-lookup"><span data-stu-id="43ce1-104">To create a fixed-width column</span></span>  
  
- <span data-ttu-id="43ce1-105">將 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性設為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> 、 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> 屬性設為 <xref:System.Windows.Forms.DataGridViewTriState.False> 、 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> 屬性設為 `true` 和 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> 屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="43ce1-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="43ce1-106">建立會自動調整其大小以符合其內容的資料行</span><span class="sxs-lookup"><span data-stu-id="43ce1-106">To create a column that adjusts its size to fit its content</span></span>  
  
- <span data-ttu-id="43ce1-107">將 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性設定為以內容為基礎的大小調整模式。</span><span class="sxs-lookup"><span data-stu-id="43ce1-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="43ce1-108">建立不同的大小和重要性的值填滿模式資料行</span><span class="sxs-lookup"><span data-stu-id="43ce1-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
- <span data-ttu-id="43ce1-109">設定 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> 屬性為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>來為所有不會覆寫此值的資料行設定大小調整模式。</span><span class="sxs-lookup"><span data-stu-id="43ce1-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="43ce1-110">將資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性，依照它們的平均內容寬度找出適當比例，做為設定值。</span><span class="sxs-lookup"><span data-stu-id="43ce1-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="43ce1-111">設定重要性資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 屬性，以確保會顯示部分內容。</span><span class="sxs-lookup"><span data-stu-id="43ce1-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="43ce1-112">範例</span><span class="sxs-lookup"><span data-stu-id="43ce1-112">Example</span></span>  
 <span data-ttu-id="43ce1-113">下列的完整程式碼範例提供示範用應用程式，可以協助您了解本主題中所述的大小調整選項。</span><span class="sxs-lookup"><span data-stu-id="43ce1-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="43ce1-114">若要使用這個示範應用程式：</span><span class="sxs-lookup"><span data-stu-id="43ce1-114">To use this demonstration application:</span></span>  
  
- <span data-ttu-id="43ce1-115">變更表單的大小</span><span class="sxs-lookup"><span data-stu-id="43ce1-115">Change the size of the form.</span></span> <span data-ttu-id="43ce1-116">觀察填滿模式資料行在由 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性值指定並保留比例時如何變更其寬度。</span><span class="sxs-lookup"><span data-stu-id="43ce1-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="43ce1-117">觀察資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 如何在表單太小時防止其變更。</span><span class="sxs-lookup"><span data-stu-id="43ce1-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
- <span data-ttu-id="43ce1-118">使用滑鼠拖曳資料行分隔線來變更資料行大小。</span><span class="sxs-lookup"><span data-stu-id="43ce1-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="43ce1-119">觀察某些資料行為何不能調整大小，以及可調整大小的資料行為何不能設定成比最小寬度還窄。</span><span class="sxs-lookup"><span data-stu-id="43ce1-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43ce1-120">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="43ce1-120">Compiling the Code</span></span>  
 <span data-ttu-id="43ce1-121">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="43ce1-121">This example requires:</span></span>  
  
- <span data-ttu-id="43ce1-122">本系統和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="43ce1-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ce1-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="43ce1-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
