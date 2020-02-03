---
title: 如何：存取金鑰集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 717ba9cc8605da08701de1bd13d6bc6da1c9b758
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739622"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>如何：在 Windows Form 中存取索引集合

- 您可以依索引鍵存取個別的集合專案。 這項功能已新增至許多 Windows Forms 應用程式通常使用的集合類別。 下列清單顯示一些具有可存取之金鑰集合的集合類別：  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 與集合中的專案相關聯的索引鍵通常是專案的名稱。 下列程式說明如何使用集合類別來執行一般工作。  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>尋找並將焦點提供給控制項集合中的嵌套控制項  
  
- 使用 <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> 和 <xref:System.Windows.Forms.Control.Focus%2A> 方法，指定要尋找並將焦點放在其中的控制項名稱。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>存取影像集合中的影像  
  
- 使用 [<xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>] 屬性來指定您想要存取的映射名稱。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>將索引標籤頁設定為選取的索引標籤  
  
- 使用 [<xref:System.Windows.Forms.TabControl.SelectedTab%2A>] 屬性搭配 [<xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A>] 屬性，以指定要設定為選取之索引標籤的索引標籤頁名稱。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 使用者入門](getting-started-with-windows-forms.md)
- [操作說明：使用 Windows Forms ImageList 元件加入或移除影像](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
