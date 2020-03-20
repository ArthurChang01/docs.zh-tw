---
title: 在清單視圖控制項中啟用磁貼視圖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 1478ba5e4f175cd7d9ec7ab5c3c4bc9050ce02fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182158"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="207e7-102">如何：在 Windows Forms ListView 控制項中啟用並排顯示</span><span class="sxs-lookup"><span data-stu-id="207e7-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="207e7-103">使用的 <xref:System.Windows.Forms.ListView> 控制項的並排顯示檢視功能，您可以提供圖形和文字資訊之間的視覺化平衡。</span><span class="sxs-lookup"><span data-stu-id="207e7-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="207e7-104">並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。</span><span class="sxs-lookup"><span data-stu-id="207e7-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="207e7-105">並排顯示檢視與 <xref:System.Windows.Forms.ListView> 控制項中的群組或插入標記功能相配合。</span><span class="sxs-lookup"><span data-stu-id="207e7-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="207e7-106">並排顯示檢視會使用 32 x 32 像素圖示和數行的文字，如下列影像所示。</span><span class="sxs-lookup"><span data-stu-id="207e7-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="207e7-107">![在 ListView 控制項中並排顯示](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "並排顯示的圖示和文字")</span><span class="sxs-lookup"><span data-stu-id="207e7-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  

 <span data-ttu-id="207e7-108">若要啟用並排顯示檢視，請將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View.Tile>。</span><span class="sxs-lookup"><span data-stu-id="207e7-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="207e7-109">您可以藉由設定 <xref:System.Windows.Forms.ListView.TileSize%2A> 屬性調整並排顯示的大小，並藉由調整 <xref:System.Windows.Forms.ListView.Columns%2A> 集合來調整並排顯示中顯示的文字行數。</span><span class="sxs-lookup"><span data-stu-id="207e7-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="207e7-110">以程式設計方式設定並排顯示檢視</span><span class="sxs-lookup"><span data-stu-id="207e7-110">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="207e7-111">使用 <xref:System.Windows.Forms.ListView> 控制項的 <xref:System.Windows.Forms.View> 的列舉。</span><span class="sxs-lookup"><span data-stu-id="207e7-111">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="207e7-112">範例</span><span class="sxs-lookup"><span data-stu-id="207e7-112">Example</span></span>  
 <span data-ttu-id="207e7-113">下列完整的程式碼範例示範並排顯示檢視，並修改為可顯示三行文字。</span><span class="sxs-lookup"><span data-stu-id="207e7-113">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="207e7-114">已經調整並排顯示大小以避免自動換行。</span><span class="sxs-lookup"><span data-stu-id="207e7-114">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="207e7-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="207e7-115">Compiling the Code</span></span>  
 <span data-ttu-id="207e7-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="207e7-116">This example requires:</span></span>  
  
- <span data-ttu-id="207e7-117">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="207e7-117">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="207e7-118">名為 book.ico 的圖示檔，位於與可執行檔相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="207e7-118">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207e7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="207e7-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="207e7-120">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="207e7-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="207e7-121">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="207e7-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
