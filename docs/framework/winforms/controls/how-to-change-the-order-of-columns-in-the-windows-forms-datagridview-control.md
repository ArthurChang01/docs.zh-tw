---
title: 變更 DataGridView 控制項中的資料行順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 2aef196e9544a81f42a563783ce6c357869aa247
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746553"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>如何：變更 Windows Form DataGridView 控制項資料行的順序
當您使用 <xref:System.Windows.Forms.DataGridView> 顯示來自資料來源的資料時，資料來源結構描述中的資料行有時不會以您想要的順序顯示。 您可以使用 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> 類別的 <xref:System.Windows.Forms.DataGridViewColumn> 屬性來變更資料行的顯示順序。  
  
 下列程式碼範例會重新調整繫結至 Northwind 範例資料庫中的 Customers 資料表時，所自動產生之一些資料行的位置。 如需如何將 <xref:System.Windows.Forms.DataGridView> 控制項系結至資料庫資料表的詳細資訊，請參閱[如何：將資料系結至 Windows Forms DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[如何：使用設計工具變更 Windows Forms DataGridView 控制項中的資料行順序](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 <xref:System.Windows.Forms.DataGridView> 的 `customersDataGridView` 控制項，這個控制項會繫結至具有指定資料行名稱的資料表，例如 Northwind 範例資料庫中的 `Customers` 資料表。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType> 和 <xref:System.Xml?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [操作說明：將資料繫結至 Windows Forms DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
