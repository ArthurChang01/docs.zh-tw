---
title: 操作說明：使用主要畫面格建立大小變更的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344641"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="b6e8e-102">操作說明：使用主要畫面格建立大小變更的動畫</span><span class="sxs-lookup"><span data-stu-id="b6e8e-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="b6e8e-103">這個範例示範如何使用主要畫面格建立大小變更的動畫。</span><span class="sxs-lookup"><span data-stu-id="b6e8e-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e8e-104">範例</span><span class="sxs-lookup"><span data-stu-id="b6e8e-104">Example</span></span>  
 <span data-ttu-id="b6e8e-105">下面的示例使用 類<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Media.ArcSegment>設置<xref:System.Windows.Media.ArcSegment.Size%2A>動畫。</span><span class="sxs-lookup"><span data-stu-id="b6e8e-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="b6e8e-106">這個動畫會以下列方式使用三個主要畫面格：</span><span class="sxs-lookup"><span data-stu-id="b6e8e-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="b6e8e-107">在動畫的前半秒，使用<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>類的實例逐漸增加圓弧的大小。線性關鍵幀（<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>如在值之間創建平滑線性過渡）</span><span class="sxs-lookup"><span data-stu-id="b6e8e-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="b6e8e-108">在下半秒結束時，使用<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>類的實例突然增加圓弧的大小。離散的關鍵幀（<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>如在值之間創建突然跳轉），即大小更改突然發生，並且不微妙。</span><span class="sxs-lookup"><span data-stu-id="b6e8e-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="b6e8e-109">在最後兩秒鐘內<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>，使用類的實例來增加圓弧的大小。樣條線鍵幀，<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>如根據<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>屬性的值在值之間創建可變轉換。</span><span class="sxs-lookup"><span data-stu-id="b6e8e-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="b6e8e-110">在此範例中，弧線的大小一開始會緩慢增加，然後在接近時間區段結尾時以指數方式增加。</span><span class="sxs-lookup"><span data-stu-id="b6e8e-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="b6e8e-111">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="b6e8e-111">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e8e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6e8e-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="b6e8e-113">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="b6e8e-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="b6e8e-114">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="b6e8e-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
