---
title: 控制項中的邊界和填補
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 02cabccd0d51a3501a8aafb8733a5273deef6c49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728567"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a>Windows Form 控制項的邊界和邊框距離
對許多應用程式而言，控制項在表單上的精確位置是高優先順序。 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間提供您許多版面配置功能來完成這項作業。 最重要的兩項是 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> 屬性可定義控制項周圍的空間，使其他控制項與該控制項的邊框保持指定的距離。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> 屬性可定義控制項的內部空間，使控制項的內容 (例如，其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值) 與控制項的邊框保持指定的距離。  
  
 下圖顯示控制項上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。  
  
 ![Windows Forms 控制項的填補和邊界](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 Visual Studio 中有針對此功能提供的設計階段支援。 另請參閱[逐步解說：使用填補、邊界和 AutoSize 屬性配置 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
