---
title: 圖形介面的結構
ms.date: 03/30/2017
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
ms.openlocfilehash: d3b16249b6bae4a113661f5a3a47097046ba20f1
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505277"
---
# <a name="structure-of-the-graphics-interface"></a>圖形介面的結構
GDI + managed 的類別介面包含大約 60 個類別、 50 的列舉型別和 8 的結構。 <xref:System.Drawing.Graphics>類別是在 GDI + 功能的核心，它是實際繪製線條、 曲線、 圖形、 影像和文字的類別。  
  
## <a name="important-classes"></a>重要的類別  
 搭配運作的許多類別<xref:System.Drawing.Graphics>類別。 例如，<xref:System.Drawing.Graphics.DrawLine%2A>方法會接收<xref:System.Drawing.Pen>物件，包含要繪製的行的屬性 （色彩、 寬度、 虛線樣式等）。 <xref:System.Drawing.Graphics.FillRectangle%2A>方法，可以接收的指標<xref:System.Drawing.Drawing2D.LinearGradientBrush>物件，搭配<xref:System.Drawing.Graphics>逐漸變更的色彩填滿矩形的物件。 <xref:System.Drawing.Font> 並<xref:System.Drawing.StringFormat>物件影響方式<xref:System.Drawing.Graphics>物件繪製的文字。 A<xref:System.Drawing.Drawing2D.Matrix>物件可儲存及操作的自然變換<xref:System.Drawing.Graphics>物件，用來旋轉、 縮放和翻轉影像。  
  
 GDI + 提供數種結構 (例如<xref:System.Drawing.Rectangle>， <xref:System.Drawing.Point>，和<xref:System.Drawing.Size>) 來組織圖形資料。 此外，某些類別做主要是為結構化的資料類型。 比方說，<xref:System.Drawing.Imaging.BitmapData>類別是 helper<xref:System.Drawing.Bitmap>類別，而<xref:System.Drawing.Drawing2D.PathData>類別是 helper<xref:System.Drawing.Drawing2D.GraphicsPath>類別。  
  
 GDI + 會定義數個列舉型別是集合的相關常數。 例如，<xref:System.Drawing.Drawing2D.LineJoin>列舉型別包含的項目<xref:System.Drawing.Drawing2D.LineJoin.Bevel>， <xref:System.Drawing.Drawing2D.LineJoin.Miter>，和<xref:System.Drawing.Drawing2D.LineJoin.Round>，其中指定可以用來聯結兩個線條的樣式。  
  
## <a name="see-also"></a>另請參閱

- [圖形概觀](graphics-overview-windows-forms.md)
- [關於 GDI+ Managed 程式碼](about-gdi-managed-code.md)
- [使用 Managed 圖形類別](using-managed-graphics-classes.md)
