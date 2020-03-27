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
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="2520e-102">操作說明：使用主要畫面格建立框線粗細的動畫</span><span class="sxs-lookup"><span data-stu-id="2520e-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="2520e-103">此示例演示如何為<xref:System.Windows.Controls.Control.BorderThickness%2A>屬性設置動畫<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="2520e-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2520e-104">範例</span><span class="sxs-lookup"><span data-stu-id="2520e-104">Example</span></span>  
 <span data-ttu-id="2520e-105">下面的示例使用 類<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Controls.Border>設置<xref:System.Windows.Controls.Control.BorderThickness%2A>動畫。</span><span class="sxs-lookup"><span data-stu-id="2520e-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="2520e-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="2520e-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="2520e-107">在上半部，使用<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>類實例逐漸增加邊框的厚度。</span><span class="sxs-lookup"><span data-stu-id="2520e-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="2520e-108">該示例用於<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>在值之間創建平滑線性增加。</span><span class="sxs-lookup"><span data-stu-id="2520e-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2. <span data-ttu-id="2520e-109">在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>類的實例突然增加邊框的厚度。</span><span class="sxs-lookup"><span data-stu-id="2520e-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="2520e-110">離散的關鍵幀，如那些派生<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>自創建值之間的突然跳轉，即動畫的運動是抖動的。</span><span class="sxs-lookup"><span data-stu-id="2520e-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3. <span data-ttu-id="2520e-111">在最後兩秒鐘內，使用<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>類的實例來減小邊框的厚度。</span><span class="sxs-lookup"><span data-stu-id="2520e-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="2520e-112">樣條線鍵幀（如從派生<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>中派生的幀）根據<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。</span><span class="sxs-lookup"><span data-stu-id="2520e-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="2520e-113">在此主要畫面格中，動畫一開始速度緩慢，然後在接近時間區段結尾時會以指數方式加速。</span><span class="sxs-lookup"><span data-stu-id="2520e-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="2520e-114">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="2520e-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2520e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2520e-115">See also</span></span>

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="2520e-116">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="2520e-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="2520e-117">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="2520e-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="2520e-118">建立 BorderThickness 值的動畫</span><span class="sxs-lookup"><span data-stu-id="2520e-118">Animate a BorderThickness Value</span></span>](../controls/how-to-animate-a-borderthickness-value.md)
