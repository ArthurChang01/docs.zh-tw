---
title: 如何：建立橢圓弧形
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453061"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="0d7ec-102">如何：建立橢圓弧形</span><span class="sxs-lookup"><span data-stu-id="0d7ec-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="0d7ec-103">這個範例示範如何繪製橢圓形弧線。若要建立橢圓形弧線，請使用 [<xref:System.Windows.Media.PathGeometry>]、[<xref:System.Windows.Media.PathFigure>] 和 [<xref:System.Windows.Media.ArcSegment>] 類別。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d7ec-104">範例</span><span class="sxs-lookup"><span data-stu-id="0d7ec-104">Example</span></span>  
 <span data-ttu-id="0d7ec-105">在下列範例中，會從（10100）繪製橢圓形弧線到（200100）。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="0d7ec-106">弧線的 <xref:System.Windows.Media.ArcSegment.Size%2A> 為100，50與裝置無關的圖元、45度的 <xref:System.Windows.Media.ArcSegment.RotationAngle%2A>、`true`的 <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> 設定，以及 <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> <xref:System.Windows.Media.SweepDirection.Counterclockwise>。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="0d7ec-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="0d7ec-107">[xaml]</span></span>  
  
 <span data-ttu-id="0d7ec-108">在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，您可以使用屬性語法來描述路徑。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="0d7ec-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="0d7ec-109">[xaml]</span></span>  
  
 <span data-ttu-id="0d7ec-110">（請注意，此屬性語法實際上會建立 <xref:System.Windows.Media.StreamGeometry>，也就是較輕量的 <xref:System.Windows.Media.PathGeometry>版本。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="0d7ec-111">如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)頁面。)</span><span class="sxs-lookup"><span data-stu-id="0d7ec-111">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="0d7ec-112">在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，您也可以藉由明確地使用物件標記來繪製橢圓形弧線。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="0d7ec-113">下列相當於上述 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="0d7ec-114">這個範例是某完整範例的一部分。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-114">This example is part of a larger sample.</span></span> <span data-ttu-id="0d7ec-115">如需完整範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。</span><span class="sxs-lookup"><span data-stu-id="0d7ec-115">For the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7ec-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d7ec-116">See also</span></span>

- [<span data-ttu-id="0d7ec-117">建立二次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="0d7ec-117">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
- [<span data-ttu-id="0d7ec-118">建立三次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="0d7ec-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
