---
title: 如何：使用 ToolStrip 控制項中的工具提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: db411023ad624e4c3d60b09bdbd588c85f8e22d1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745513"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>如何：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete
下列程式會將 <xref:System.Windows.Forms.ToolStripLabel> 與可以下拉的 <xref:System.Windows.Forms.ToolStripComboBox> 結合，以顯示專案清單，例如最近造訪的網站。 如果使用者輸入的字元符合清單中其中一個專案的第一個字元，則會立即顯示該專案。  
  
> [!NOTE]
> 自動完成功能可與 `ToolStrip` 控制項搭配使用，其方式與傳統控制項（例如 <xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.TextBox>）相同。  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>若要啟用 ToolStrip 控制項中的自動完成功能  
  
1. 建立 <xref:System.Windows.Forms.ToolStrip> 控制項，並在其中新增專案。  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]   
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2. 將標籤和下拉式方塊的 [<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>] 屬性設定為 [<xref:System.Windows.Forms.ToolStripItemOverflow.Never>]，讓清單一律可供使用，不論表單的大小為何。  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3. 將文字加入至 <xref:System.Windows.Forms.ToolStripComboBox> 控制項的 Items 集合。  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. 將下拉式方塊的 [<xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>] 屬性設定為 [<xref:System.Windows.Forms.AutoCompleteMode.Append>]。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. 將下拉式方塊的 [<xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>] 屬性設定為 [<xref:System.Windows.Forms.AutoCompleteSource.ListItems>]。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
