---
title: 如何：建立含陰影的文字
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186854"
---
# <a name="how-to-create-text-with-a-shadow"></a>如何：建立含陰影的文字
本節中的範例示範如何建立所顯示文字的陰影效果。  
  
## <a name="example"></a>範例  
 該<xref:System.Windows.Media.Effects.DropShadowEffect>物件允許您為[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]物件創建各種投影效果。 下列範例示範套用至文字的延伸陰影效果。 在此情況下，陰影是柔邊陰影，表示陰影色彩模糊。  
  
 ![具有柔和度&#61; 0.25 的文本陰影](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 您可以通過設置<xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>屬性來控制陰影的寬度。 的值`4.0`表示陰影寬度為 4 圖元。 您可以通過修改<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性來控制陰影的柔和度或模糊性。 的值`0.0`表示沒有模糊。 下列程式碼範例示範如何建立柔邊陰影。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> 這些陰影效果不會通過[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]文本呈現管道。 因此，使用這些效果時，會停用 ClearType。  
  
 下列範例示範套用至文字的實色延伸陰影效果。 在此情況下，陰影不會模糊。  
  
 ![具有柔和性&#61; 0 的文本陰影](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 通過將<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性設置為`0.0`（）來創建硬陰影，該屬性指示不使用模糊。 您可以通過修改<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>屬性來控制陰影的方向。 將此屬性的方向值設置為 和`0``360`之間的程度。 下圖顯示了屬性設置的方向<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>值。  
  
 ![陰影的 DropShadow 程度設定](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 下列程式碼範例示範如何建立強烈陰影。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>使用模糊效果  
 <xref:System.Windows.Media.Effects.BlurBitmapEffect>可用於創建可放置在文本物件後面的類似陰影的效果。 套用至文字的模糊點陣圖效果會讓文字所有方向都平均模糊。  
  
 下列範例示範套用至文字的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文字陰影](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 下列程式碼範例示範如何建立模糊效果。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>使用平移轉換  
 <xref:System.Windows.Media.TranslateTransform>可用於創建可放置在文本物件後面的類似陰影的效果。  
  
 以下代碼示例使用 偏移<xref:System.Windows.Media.TranslateTransform>文本。 在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。  
  
 ![使用 TranslateTransform 的文字陰影](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 下列程式碼範例示範如何建立陰影效果的轉換。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
