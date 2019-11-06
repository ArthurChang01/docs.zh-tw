---
title: 如何：將控制項停駐在 Windows Form 上
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 82aef0ae9abacad33b21920f88591c0e4c33dfcb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460557"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>如何：將控制項停駐在 Windows Forms

您可以將控制項停駐在表單的邊緣，或讓它們填滿控制項的容器（表單或容器控制項）。 例如，Windows Explorer 會將其 <xref:System.Windows.Forms.TreeView> 控制項停駐于視窗的左邊，並將其 <xref:System.Windows.Forms.ListView> 控制項放到視窗右側。 使用所有可見 Windows Forms 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性來定義停駐模式。

> [!NOTE]
> 控制項停駐在反向迭置順序中。

<xref:System.Windows.Forms.Control.Dock%2A> 屬性會與 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性互動。 如需詳細資訊，請參閱[AutoSize 屬性總覽](autosize-property-overview.md)。

## <a name="to-dock-a-control"></a>若要停駐控制項

1. 在 Visual Studio 中，選取您要停駐的控制項。

2. 在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.Control.Dock%2A>] 屬性右邊的箭號。

   隨即顯示編輯器，其中會顯示一系列代表表單邊緣和中心的方塊。

3. 按一下代表您要停駐控制項之表單邊緣的按鈕。 若要填滿控制項表單或容器控制項的內容，請按一下 [中央] 方塊。 按一下 **[（無）** ] 以停用銜接。

   控制項會自動調整大小，以符合停駐邊緣的界限。

   > [!NOTE]
   > 繼承的控制項必須 `Protected`，才能夠停駐。 若要變更控制項的存取層級，請在 [**屬性**] 視窗中設定其 [**修飾**詞] 屬性。

## <a name="see-also"></a>請參閱

- [Windows Forms 控制項](index.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
- [操作說明：錨定和停駐 FlowLayoutPanel 控制項中的子控制項](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize 屬性概觀](autosize-property-overview.md)
- [操作說明：錨定 Windows Forms 上的控制項](how-to-anchor-controls-on-windows-forms.md)
