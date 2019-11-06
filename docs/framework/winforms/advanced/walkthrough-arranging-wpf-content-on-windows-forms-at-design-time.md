---
title: 逐步解說：在設計階段排列 Windows Form 的 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9db49ae299870479a5cfa6372c25d793a92ff8f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460678"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>逐步解說：在設計階段排列 Windows Forms 上的 WPF 內容

本文說明如何使用 Windows Forms 的版面配置功能（例如錨定和對齊線）來排列 Windows Presentation Foundation （WPF）控制項。

## <a name="prerequisites"></a>Prerequisites

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="create-the-project"></a>建立專案

開啟 Visual Studio，並在 Visual Basic 或視覺效果C#中建立名為 `ArrangeElementHost`的新 Windows Forms 應用程式專案。

> [!NOTE]
> 裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。

## <a name="create-the-wpf-control"></a>建立 WPF 控制項

在將 WPF 控制項加入專案後，即可在表單上予以排列。

1. 將新的 WPF <xref:System.Windows.Controls.UserControl> 加入專案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說：在設計階段于 Windows Forms 上建立新的 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。

2. 在 [設計] 檢視中，確定已選取 `UserControl1`。

3. 在 [**屬性**] 視窗中，將 [<xref:System.Windows.FrameworkElement.Width%2A>] 和 [<xref:System.Windows.FrameworkElement.Height%2A> 屬性] 的值設定為**200**。

4. 將 [<xref:System.Windows.Controls.Control.Background%2A>] 屬性的值設定為 [**藍色**]。

5. 建置專案。

## <a name="host-wpf-controls-in-a-layout-panel"></a>在版面配置面板中裝載 WPF 控制項

您可以使用與其他 Windows Form 控制項相同的方式，在配置面板中使用 WPF 控制項。

1. 在 Windows Form 設計工具中開啟 `Form1`。

2. 在 [**工具箱**] 中，將 [<xref:System.Windows.Forms.TableLayoutPanel>] 控制項拖曳至表單上。

3. 在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的智慧標籤面板上，選取 [**移除最後一個資料列**]。

4. 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更寬且更高的大小。

5. 在 **工具箱** 中，按兩下 `UserControl1`，在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的第一個資料格中建立 `UserControl1` 的實例。

   `UserControl1` 的執行個體會裝載到名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。

6. 在 **工具箱** 中，按兩下 `UserControl1`，在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的第二個儲存格中建立另一個實例。

7. 在 [**檔大綱**] 視窗中，選取 [`tableLayoutPanel1`]。

8. 在 [**屬性**] 視窗中，將 [<xref:System.Windows.Forms.Control.Padding%2A>] 屬性的值設定為**10、10、10、10**。

   兩個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的大小會調整以配合新的配置。

## <a name="use-snaplines-to-align-wpf-controls"></a>使用對齊線來對齊 WPF 控制項

對齊線可讓您輕鬆對齊表單上的控制項。 您也可以使用對齊線來對齊 WPF 控制項。 如需詳細資訊，請參閱[逐步解說：使用對齊線排列 Windows Forms 上的控制項](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。

1. 從 [**工具箱**] 中，將 `UserControl1` 的實例拖曳至表單上，並將它放在 [<xref:System.Windows.Forms.TableLayoutPanel>] 控制項底下的空間中。

   `UserControl1` 的執行個體會裝載到名為 `elementHost3` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。

2. 使用對齊線，將 `elementHost3` 的左邊緣與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的左邊緣對齊。

3. 使用對齊線，將 `elementHost3` 的大小調整成與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項同寬。

4. 將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項方向移動，直到中央對齊線出現在兩個控制項之間為止。

5. 在 [**屬性**] 視窗中，將 [Margin] 屬性的值設定為**20、20、20、20**。

6. 將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項反方向移動，直到中央對齊線再度出現為止。 中央對齊線現在表示邊界 20。

7. 將 `elementHost3` 向右移動，直到其左邊緣與 `elementHost1`的左邊緣對齊為止。

8. 變更 `elementHost3` 的寬度，直到其右邊緣與 `elementHost2` 的右邊緣對齊為止。

## <a name="anchor-and-dock-wpf-controls"></a>錨定和停駐 WPF 控制項

裝載於表單上之 WPF 控制項的錨定和停駐行為，與其他 Windows Form 控制項相同。

1. 選取 `elementHost1`。

2. 在 [**屬性**] 視窗中，將 [<xref:System.Windows.Forms.Control.Anchor%2A>] 屬性設為 [上]、[**下]、** [向右]。

3. 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更大的大小。

   `elementHost1` 控制項會調整大小以填滿儲存格。

4. 選取 `elementHost2`。

5. 在 [**屬性**] 視窗中，將 [<xref:System.Windows.Forms.Control.Dock%2A>] 屬性的值設定為 [<xref:System.Windows.Forms.DockStyle.Fill>]。

   `elementHost2` 控制項會調整大小以填滿儲存格。

6. 選取 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。

7. 將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Top>。

8. 選取 `elementHost3`。

9. 將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Fill>。

   `elementHost3` 控制項會調整大小以填滿表單上的剩餘空間。

10. 調整表單的大小。

    這三個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項都會適當地調整大小。

    如需詳細資訊，請參閱[如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [操作說明：在設計階段將控制項對齊表單邊緣](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [逐步解說：使用對齊線排列 Windows Forms 上的控制項](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
