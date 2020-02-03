---
title: ListView 控制項中的群組專案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: 45846751780f433c29b186fe8b9a908f5d295ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736622"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>如何：在 Windows Form ListView 控制項中群組項目
有了 <xref:System.Windows.Forms.ListView> 控制項的群組功能，您就可以在群組中顯示相關的專案集合。 這些群組會以包含群組標題的水準群組標頭分隔在畫面上。 您可以使用 <xref:System.Windows.Forms.ListView> 群組，讓您更輕鬆地流覽大型清單，方法是依字母順序、依日期或任何其他邏輯群組來分組專案。 下圖顯示一些群組的專案。  
  
 ![奇數和偶數 ListView 群組的螢幕擷取畫面。](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 若要啟用群組，您必須先在設計工具或以程式設計方式建立一或多個群組。 定義群組之後，您可以將 <xref:System.Windows.Forms.ListView> 專案指派給群組。 您也可以透過程式設計的方式，將專案從一個群組移至另一個。  
  
### <a name="to-add-groups"></a>新增群組  
  
1. 使用 <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> 集合的 <xref:System.Windows.Forms.ListView.Groups%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>移除群組  
  
1. 使用 <xref:System.Windows.Forms.ListView.Groups%2A> 集合的 <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> 或 <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> 方法。  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> 方法會移除單一群組;<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> 方法會從清單中移除所有群組。  
  
    > [!NOTE]
    > 移除群組並不會移除該群組內的專案。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>將專案指派給群組或在群組之間移動專案  
  
1. 設定個別專案的 <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> 屬性。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView 控制項](listview-control-windows-forms.md)
- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
