---
title: 如何：使用不透明和半透明筆刷繪製
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142403"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>如何：使用不透明和半透明筆刷繪製
當您填滿形狀時，您必須傳遞 <xref:System.Drawing.Brush> 物件至 <xref:System.Drawing.Graphics> 類別的其中一種填滿方法。 <xref:System.Drawing.SolidBrush.%23ctor%2A> 建構函式的參數是 <xref:System.Drawing.Color> 物件。 若要填滿不透明的圖形，請設定色彩的 Alpha 元件為 255。 若要填滿半透明的圖案，請設定 Alpha 元件為從 1 到 254 的任何值。  
  
 當您填滿半透明的圖案時，圖案的色彩會與背景的色彩混合。 Alpha 元件指定如何混合圖案和背景色彩；接近於 0 的 Alpha 值給予背景色彩較多的權重，而接近 255 的 Alpha 值給予圖形色彩較多的權重。  
  
## <a name="example"></a>範例  
 下列範例會繪製點陣圖，然後填滿重疊點陣圖的三個橢圓形。 第一個橢圓形使用的 Alpha 元件為 255，所以是不透明的。 第二個和第三個橢圓形使用的 Alpha 元件為 128，因此是半透明的；您可以看到穿透橢圓形的背景影像。 設定 <xref:System.Drawing.Graphics.CompositingQuality%2A> 屬性的呼叫會讓第三個橢圓形搭配 Gamma 修正進行混色。  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 下圖顯示了以下代碼的輸出：
  
 ![顯示不透明和半透明輸出的插圖。](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 前面的示例設計用於 Windows 表單，它要求<xref:System.Windows.Forms.PaintEventArgs>`e`. <xref:System.Windows.Forms.PaintEventHandler>  
  
## <a name="see-also"></a>另請參閱

- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [Alpha 混色線條和填色](alpha-blending-lines-and-fills.md)
- [如何：為控制項提供透明背景](../controls/how-to-give-your-control-a-transparent-background.md)
- [操作說明：繪製不透明和半透明線條](how-to-draw-opaque-and-semitransparent-lines.md)
