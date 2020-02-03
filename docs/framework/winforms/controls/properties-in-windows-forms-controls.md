---
title: 控制項的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 82bfab15cef4946661a37d2d88fbe1b797f3d816
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741176"
---
# <a name="properties-in-windows-forms-controls"></a>Windows Form 控制項中的屬性
Windows Forms 控制項繼承了許多屬性，形成基類 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>。 其中包括 <xref:System.Windows.Forms.Control.Font%2A>、<xref:System.Windows.Forms.Control.ForeColor%2A>、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.Bounds%2A>、<xref:System.Windows.Forms.Control.ClientRectangle%2A>、<xref:System.Windows.Forms.Control.DisplayRectangle%2A>、<xref:System.Windows.Forms.Control.Enabled%2A>、<xref:System.Windows.Forms.Control.Focused%2A>、<xref:System.Windows.Forms.Control.Height%2A>、<xref:System.Windows.Forms.Control.Width%2A>、<xref:System.Windows.Forms.Control.Visible%2A>、<xref:System.Windows.Forms.Control.AutoSize%2A>和其他許多屬性。 如需繼承屬性的詳細資訊，請參閱 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>。  
  
 您可以在控制項中覆寫繼承的屬性，以及定義新的屬性。  
  
## <a name="in-this-section"></a>本節內容  
 [定義屬性](defining-a-property-in-windows-forms-controls.md)  
 示範如何實作自訂控制項或元件的屬性，並且示範如何將屬性整合至設計環境。  
  
 [使用 ShouldSerialize 和 Reset 方法定義預設值](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 示範如何定義自訂控制項或元件的預設屬性值。  
  
 [屬性變更事件](property-changed-events.md)  
 描述如何在屬性值變更時，啟用屬性變更通知。  
  
 [如何：公開組成控制項的屬性](how-to-expose-properties-of-constituent-controls.md)  
 示範如何在自訂複合控制項中公開組成控制項的屬性。  
  
 [自訂控制項中的方法實作](method-implementation-in-custom-controls.md)  
 描述如何在自訂控制項和元件中實作方法。  
  
## <a name="reference"></a>參考  
 <xref:System.Windows.Forms.UserControl>  
 記錄基底類別以實作複合控制項。  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 記載屬性，指定要用於自訂屬性類型的 <xref:System.ComponentModel.TypeConverter>。  
  
 <xref:System.ComponentModel.EditorAttribute>  
 記載屬性，指定要用於自訂屬性的 <xref:System.Drawing.Design.UITypeEditor>。  
  
## <a name="related-sections"></a>相關章節  
 [Windows Forms 控制項中的屬性](attributes-in-windows-forms-controls.md)  
 描述可以套用至屬性 (Property) 或您的自訂控制項和元件之其他成員的屬性 (Attribute)。  
  
 [元件的設計階段屬性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))  
 列出要套用至元件和控制項的中繼資料屬性，以便在設計階段於視覺設計工具中正確顯示這些屬性。  
  
 [擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))  
 描述如何實作類別，例如提供設計階段支援的編輯器和設計工具。
