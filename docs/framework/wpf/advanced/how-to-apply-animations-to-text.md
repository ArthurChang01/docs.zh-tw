---
title: 如何：對文字套用動畫
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174624"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="72fb0-102">如何：對文字套用動畫</span><span class="sxs-lookup"><span data-stu-id="72fb0-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="72fb0-103">動畫可以變更應用程式中文字的顯示和外觀。</span><span class="sxs-lookup"><span data-stu-id="72fb0-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="72fb0-104">以下示例使用不同類型的動畫來影響<xref:System.Windows.Controls.TextBlock>控制項中文本的顯示。</span><span class="sxs-lookup"><span data-stu-id="72fb0-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72fb0-105">範例</span><span class="sxs-lookup"><span data-stu-id="72fb0-105">Example</span></span>  
 <span data-ttu-id="72fb0-106">下面的示例使用<xref:System.Windows.Media.Animation.DoubleAnimation>為文字區塊的寬度設置動畫。</span><span class="sxs-lookup"><span data-stu-id="72fb0-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="72fb0-107">寬度值會在 10 秒的期間內從文字區塊的寬度變更為 0，然後回復寬度值並繼續進行。</span><span class="sxs-lookup"><span data-stu-id="72fb0-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="72fb0-108">這種動畫會建立擦去效果。</span><span class="sxs-lookup"><span data-stu-id="72fb0-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="72fb0-109">下面的示例使用 動畫<xref:System.Windows.Media.Animation.DoubleAnimation>處理文字區塊的不動性。</span><span class="sxs-lookup"><span data-stu-id="72fb0-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="72fb0-110">不透明度值會在 5 秒的期間內從 1.0 變更為 0，然後回復不透明度值並繼續進行。</span><span class="sxs-lookup"><span data-stu-id="72fb0-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="72fb0-111">下圖顯示了<xref:System.Windows.Controls.TextBlock>控制項在 定義的 5 秒間隔`1.00``0.00`內將其不恰當性更改為的效果。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A></span><span class="sxs-lookup"><span data-stu-id="72fb0-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![文本將不一性從 1.00 更改為 0.00。](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 <span data-ttu-id="72fb0-113">下面的示例使用<xref:System.Windows.Media.Animation.ColorAnimation>為文字區塊的前景顏色設置動畫。</span><span class="sxs-lookup"><span data-stu-id="72fb0-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="72fb0-114">前景色彩值會在 5 秒的期間內從某種色彩變更為第二種色彩，然後回復色彩值並繼續進行。</span><span class="sxs-lookup"><span data-stu-id="72fb0-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="72fb0-115">下面的示例使用 旋轉<xref:System.Windows.Media.Animation.DoubleAnimation>文字區塊。</span><span class="sxs-lookup"><span data-stu-id="72fb0-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="72fb0-116">文字區塊會在 20 秒的期間內執行完整旋轉，然後繼續重複進行旋轉。</span><span class="sxs-lookup"><span data-stu-id="72fb0-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="72fb0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72fb0-117">See also</span></span>

- [<span data-ttu-id="72fb0-118">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="72fb0-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
