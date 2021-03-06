---
title: 操作說明：使用主要畫面格建立框線粗細的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344698"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>操作說明：使用主要畫面格建立框線粗細的動畫
此示例演示如何為<xref:System.Windows.Controls.Control.BorderThickness%2A>屬性設置動畫<xref:System.Windows.Controls.Border>。  
  
## <a name="example"></a>範例  
 下面的示例使用 類<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Controls.Border>設置<xref:System.Windows.Controls.Control.BorderThickness%2A>動畫。 這個動畫會以下列方式使用三個主要畫面格：  
  
1. 在上半部，使用<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>類實例逐漸增加邊框的厚度。 該示例用於<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>在值之間創建平滑線性增加。  
  
2. 在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>類的實例突然增加邊框的厚度。 離散的關鍵幀，如那些派生<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>自創建值之間的突然跳轉，即動畫的運動是抖動的。  
  
3. 在最後兩秒鐘內，使用<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>類的實例來減小邊框的厚度。 樣條線鍵幀（如從派生<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>中派生的幀）根據<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。 在此主要畫面格中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
- [建立 BorderThickness 值的動畫](../controls/how-to-animate-a-borderthickness-value.md)
