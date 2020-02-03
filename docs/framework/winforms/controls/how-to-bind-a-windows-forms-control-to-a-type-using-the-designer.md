---
title: 使用設計工具將控制項系結至類型
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 2257489e123ceeea819ad3538952db51b726c7e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742025"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>如何：使用設計工具將 Windows Forms 控制項繫結至型別

當您在建立與資料互動的控制項時，有時需要將控制項繫結至類型，而非物件。 您在設計階段通常需要將控制項繫結至類型，當時資料可能無法使用，但您仍希望資料繫結的控制項顯示類型公用介面中的資料。 下列程式示範如何建立系結至類型的新 <xref:System.Windows.Forms.BindingSource>，以及如何將其中一個類型的屬性系結至 <xref:System.Windows.Forms.TextBox>的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性。

### <a name="to-bind-the-bindingsource-to-a-type"></a>將 BindingSource 繫結至類型

1. 建立 Windows Forms**專案（檔案** > **新** > **專案** > **Visual C#** 或**Visual Basic** > **傳統桌面** > Windows Forms**應用程式**）。

2. 在**設計**視圖中，將 [<xref:System.Windows.Forms.BindingSource>] 元件拖曳至表單上。

3. 在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.BindingSource.DataSource%2A>] 屬性的箭號。

4. 在 [DataSource UI 類型編輯器] 中，按一下 [新增專案資料來源]。

5. 在 [選擇資料來源類型] 頁面中，選取 [物件]，再按 [下一步]。

6. 選取要繫結的類型︰

    - 如果您想要繫結的類型是在目前專案中，或包含此類型的組件已新增為參考，請展開節點以找出您想要的類型，然後選取它。

      \-或-

    - 如果您要系結的類型是在另一個元件中，而目前不在參考清單中，請按一下 [**加入參考**]，然後按一下 [**專案**] 索引標籤。選取包含所需商務物件的專案，然後按一下 **[確定**]。 此專案會出現在組件清單中，所以您可展開節點以找出您想要的類型，然後選取它。

      > [!NOTE]
      > 如果您想要繫結至架構或 Microsoft 組件中的類型，請清除 [隱藏以 Microsoft 或 System 開頭的組件] 核取方塊。

7. 按 **[下一步]** ，再按一下 **[完成]** 。

### <a name="to-bind-the-control-to-the-bindingsource"></a>將控制項繫結至 BindingSource

1. 將 <xref:System.Windows.Forms.TextBox> 加入表單。

2. 在 [屬性] 視窗中，展開 [(DataBindings)] 節點。

3. 按一下 [<xref:System.Windows.Forms.TextBox.Text%2A>] 屬性旁的箭號。

4. 在 [ **DATASOURCE UI 類型編輯器**] 中，展開先前加入之 <xref:System.Windows.Forms.BindingSource> 的節點，然後選取您想要系結至 <xref:System.Windows.Forms.TextBox>之 [<xref:System.Windows.Forms.TextBox.Text%2A>] 屬性的系結型別屬性。

## <a name="see-also"></a>另請參閱

- [BindingSource 元件](bindingsource-component.md)
- [如何：將 Windows Forms 控制項繫結至型別](how-to-bind-a-windows-forms-control-to-a-type.md)
- [將控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
