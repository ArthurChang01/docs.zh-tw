---
title: 如何：使用設計工具群組 Windows Form ListView 控制項中的項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 03958109d4daa3fc369660de66973bb659e29c60
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960175"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>如何：使用設計工具群組 Windows Form ListView 控制項中的項目

[<xref:System.Windows.Forms.ListView>] 控制項的 [群組] 功能可讓您在群組中顯示相關的專案集合。 這些群組會以包含群組標題的水準群組標頭分隔在畫面上。 您可以使用 <xref:System.Windows.Forms.ListView> 群組，讓您更輕鬆地流覽大型清單，方法是依字母順序、依日期或任何其他邏輯群組來分組專案。 下圖顯示一些群組專案：

![以奇數和偶數群組分隔的數位。](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

下列程式需要具有包含 <xref:System.Windows.Forms.ListView> 控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。

若要啟用群組，您必須先在設計師或以程式設計方式建立一或多個 <xref:System.Windows.Forms.ListViewGroup> 物件。 定義群組之後，您就可以將專案指派給它。

## <a name="to-add-or-remove-groups-in-the-designer"></a>若要在設計工具中新增或移除群組

1. 在 **屬性** 視窗中<xref:System.Windows.Forms.ListView.Groups%2A> ，按一下屬性 (![旁邊的**省略號**Visual Studio](./media/visual-studio-ellipsis-button.png)) 的屬性視窗中的省略號按鈕（...） 按鈕。

     [ **ListViewGroup 集合編輯器**] 隨即出現。

2. 若要新增群組，請按一下 [**新增**] 按鈕。 接著，您可以設定新群組的屬性，例如 [<xref:System.Windows.Forms.ListViewGroup.Header%2A>] 和 [<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> 屬性]。 若要移除群組，請選取它，然後按一下 [**移除**] 按鈕。

## <a name="to-assign-items-to-groups-in-the-designer"></a>若要在設計工具中將專案指派給群組

1. 在 **屬性** 視窗中<xref:System.Windows.Forms.ListView.Items%2A> ，按一下屬性 (![旁邊的**省略號**Visual Studio](./media/visual-studio-ellipsis-button.png)) 的屬性視窗中的省略號按鈕（...） 按鈕。

     [ **ListViewItem 集合編輯器**] 隨即出現。

2. 若要加入新專案，請按一下 **[新增**] 按鈕。 接著，您可以設定新專案的屬性，例如 [<xref:System.Windows.Forms.ListViewItem.Text%2A>] 和 [<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> 屬性]。

3. 選取 [<xref:System.Windows.Forms.ListViewItem.Group%2A>] 屬性，並從下拉式清單中選擇一個群組。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView 控制項](listview-control-windows-forms.md)
- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
