---
title: 選取 Windows Forms 的 WPF 控制項
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19f1dfec282b025f5a1fa367ec5fa9a52472c691
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746806"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>逐步解說：在設計階段指派 Windows Forms 的 WPF 內容

本文說明如何選取您要在表單上顯示的 Windows Presentation Foundation （WPF）控制項類型。 您可以選取包含在專案中的任何 WPF 控制項類型。

## <a name="prerequisites"></a>必要條件：

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="create-the-project"></a>建立專案

開啟 Visual Studio，並在 Visual Basic 或視覺效果C#中建立名為 `SelectingWpfContent`的新 Windows Forms 應用程式專案。

> [!NOTE]
> 裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。

## <a name="create-the-wpf-control-types"></a>建立 WPF 控制項類型

當您將 WPF 控制項類型加入專案之後，即可在不同的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中裝載這些類型。

1. 將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說：在設計階段于 Windows Forms 上建立新的 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。

2. 在 [設計] 檢視中，確定已選取 `UserControl1`。

3. 在 [**屬性**] 視窗中，將 [<xref:System.Windows.FrameworkElement.Width%2A>] 和 [<xref:System.Windows.FrameworkElement.Height%2A> 屬性] 的值設定為**200**。

4. 將 <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項加入至 <xref:System.Windows.Controls.UserControl>，並將 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的值設定為 [裝載的**內容**]。

5. 將第二個 WPF <xref:System.Windows.Controls.UserControl> 加入專案。 使用控制項類型的預設名稱 `UserControl2.xaml`。

6. 在 [**屬性**] 視窗中，將 [<xref:System.Windows.FrameworkElement.Width%2A>] 和 [<xref:System.Windows.FrameworkElement.Height%2A> 屬性] 的值設定為**200**。

7. 將 <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項新增至 <xref:System.Windows.Controls.UserControl>，並將 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的值設定為 [裝載的**內容 2**]。

   > [!NOTE]
   > 一般而言，您應該裝載更複雜的 WPF 內容。 <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項在此僅供說明用途使用。

8. 建置專案。

## <a name="select-wpf-controls"></a>選取 WPF 控制項

您可以對已裝載內容的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，指派不同的 WPF 內容。

1. 在 Windows Form 設計工具中開啟 `Form1`。

2. 在 [**工具箱**] 中，按兩下 [`UserControl1`]，在表單上建立 `UserControl1` 的實例。

   `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。

3. 在 `elementHost1`的智慧標籤面板中，開啟 [**選取主控內容**] 下拉式清單。

4. 從下拉式清單方塊中選取  **usercontrol2** 。

   `elementHost1` 控制項現在會裝載 `UserControl2` 類型的執行個體。

5. 在 **屬性** 視窗中，確認 <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> 屬性已設定為  **usercontrol2**。

6. 從 [**工具箱**] 的 [ **WPF 互通性**] 群組中，將 [<xref:System.Windows.Forms.Integration.ElementHost>] 控制項拖曳至表單上。

   新控制項的預設名稱為 `elementHost2`。

7. 在 `elementHost2`的智慧標籤面板中，開啟 [**選取主控內容**] 下拉式清單。

8. 從下拉式清單中選取 [ **UserControl1** ]。

9. `elementHost2` 控制項現在會裝載 `UserControl1` 類型的執行個體。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
