---
title: 如何：建立三次方貝茲曲線
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452106"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="01fcc-102">如何：建立三次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="01fcc-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="01fcc-103">這個範例顯示如何建立三次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="01fcc-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="01fcc-104">若要建立三次方貝茲曲線，請使用 [<xref:System.Windows.Media.PathGeometry>]、[<xref:System.Windows.Media.PathFigure>] 和 [<xref:System.Windows.Media.BezierSegment>] 類別。</span><span class="sxs-lookup"><span data-stu-id="01fcc-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="01fcc-105">若要顯示產生的幾何，請使用 <xref:System.Windows.Shapes.Path> 元素，或搭配 <xref:System.Windows.Media.GeometryDrawing> 或 <xref:System.Windows.Media.DrawingContext>使用。</span><span class="sxs-lookup"><span data-stu-id="01fcc-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="01fcc-106">在下列範例中，會從（10，100）到（300，100）繪製三次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="01fcc-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="01fcc-107">曲線的控制點為（100，0）和（200，200）。</span><span class="sxs-lookup"><span data-stu-id="01fcc-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01fcc-108">範例</span><span class="sxs-lookup"><span data-stu-id="01fcc-108">Example</span></span>  
 <span data-ttu-id="01fcc-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="01fcc-109">[xaml]</span></span>  
  
 <span data-ttu-id="01fcc-110">在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，您可以使用縮寫的標記語法來描述路徑。</span><span class="sxs-lookup"><span data-stu-id="01fcc-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="01fcc-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="01fcc-111">[xaml]</span></span>  
  
 <span data-ttu-id="01fcc-112">在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，您也可以使用物件標記繪製三次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="01fcc-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="01fcc-113">下列範例相當於先前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="01fcc-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="01fcc-114">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。</span><span class="sxs-lookup"><span data-stu-id="01fcc-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01fcc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01fcc-115">See also</span></span>

- [<span data-ttu-id="01fcc-116">建立橢圓形弧線</span><span class="sxs-lookup"><span data-stu-id="01fcc-116">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="01fcc-117">在 PathGeometry 中建立 LineSegment</span><span class="sxs-lookup"><span data-stu-id="01fcc-117">Create a LineSegment in a PathGeometry</span></span>](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [<span data-ttu-id="01fcc-118">建立三次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="01fcc-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
- [<span data-ttu-id="01fcc-119">建立二次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="01fcc-119">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
