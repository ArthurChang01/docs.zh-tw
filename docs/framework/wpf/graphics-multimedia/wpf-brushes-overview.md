---
title: WPF 筆刷概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 8a1d05ad48ce75ce67d21d5a4d508015fea879b2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458633"
---
# <a name="wpf-brushes-overview"></a><span data-ttu-id="5dbc5-102">WPF 筆刷概觀</span><span class="sxs-lookup"><span data-stu-id="5dbc5-102">WPF Brushes Overview</span></span>
<span data-ttu-id="5dbc5-103">螢幕上顯示的所有專案都是可見的，因為它是由筆刷繪製。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-103">Everything visible on your screen is visible because it was painted by a brush.</span></span> <span data-ttu-id="5dbc5-104">例如，筆刷是用來描述按鈕的背景、文字的前景，以及圖形的填滿。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-104">For example, a brush is used to describe the background of a button, the foreground of text, and the fill of a shape.</span></span> <span data-ttu-id="5dbc5-105">本主題介紹使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 筆刷繪製的概念，並提供範例。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-105">This topic introduces the concepts of painting with [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] brushes and provides examples.</span></span> <span data-ttu-id="5dbc5-106">筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-106">Brushes enable you to paint [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objects with anything from simple, solid colors to complex sets of patterns and images.</span></span>  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a><span data-ttu-id="5dbc5-107">使用筆刷繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-107">Painting with a Brush</span></span>  
 <span data-ttu-id="5dbc5-108"><xref:System.Windows.Media.Brush> 「繪製」含有其輸出的區域。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-108">A <xref:System.Windows.Media.Brush> "paints" an area with its output.</span></span> <span data-ttu-id="5dbc5-109">不同的筆刷具有不同類型的輸出。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-109">Different brushes have different types of output.</span></span> <span data-ttu-id="5dbc5-110">有些筆刷會以純色繪製區域，其他則具有漸層、圖樣、影像或繪圖。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-110">Some brushes paint an area with a solid color, others with a gradient, pattern, image, or drawing.</span></span> <span data-ttu-id="5dbc5-111">下圖顯示每個不同 <xref:System.Windows.Media.Brush> 類型的範例。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-111">The following illustration shows examples of each of the different <xref:System.Windows.Media.Brush> types.</span></span>  
  
 <span data-ttu-id="5dbc5-112">![筆刷類型](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span><span class="sxs-lookup"><span data-stu-id="5dbc5-112">![Brush types](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span></span>  
<span data-ttu-id="5dbc5-113">筆刷範例</span><span class="sxs-lookup"><span data-stu-id="5dbc5-113">Brush examples</span></span>  
  
 <span data-ttu-id="5dbc5-114">大部分的視覺物件都可讓您指定其繪製方式。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-114">Most visual objects enable you to specify how they are painted.</span></span> <span data-ttu-id="5dbc5-115">下表列出一些常用的物件和屬性，您可以使用 <xref:System.Windows.Media.Brush>。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-115">The following table lists some common objects and properties with which you can use a <xref:System.Windows.Media.Brush>.</span></span>  
  
|<span data-ttu-id="5dbc5-116">執行個體</span><span class="sxs-lookup"><span data-stu-id="5dbc5-116">Class</span></span>|<span data-ttu-id="5dbc5-117">筆刷屬性</span><span class="sxs-lookup"><span data-stu-id="5dbc5-117">Brush properties</span></span>|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<span data-ttu-id="5dbc5-118"><xref:System.Windows.Controls.Border.BorderBrush%2A>、 <xref:System.Windows.Controls.Border.Background%2A></span><span class="sxs-lookup"><span data-stu-id="5dbc5-118"><xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A></span></span>|  
|<xref:System.Windows.Controls.Control>|<span data-ttu-id="5dbc5-119"><xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A></span><span class="sxs-lookup"><span data-stu-id="5dbc5-119"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span></span>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<span data-ttu-id="5dbc5-120"><xref:System.Windows.Shapes.Shape.Fill%2A>、 <xref:System.Windows.Shapes.Shape.Stroke%2A></span><span class="sxs-lookup"><span data-stu-id="5dbc5-120"><xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A></span></span>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 <span data-ttu-id="5dbc5-121">下列各節說明不同的 <xref:System.Windows.Media.Brush> 型別，並提供每個類型的範例。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-121">The following sections describe the different <xref:System.Windows.Media.Brush> types and provide an example of each.</span></span>  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a><span data-ttu-id="5dbc5-122">以純色繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-122">Paint with a Solid Color</span></span>  
 <span data-ttu-id="5dbc5-123"><xref:System.Windows.Media.SolidColorBrush> 繪製具有純色 <xref:System.Windows.Media.Color>的區域。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-123">A <xref:System.Windows.Media.SolidColorBrush> paints an area with a solid <xref:System.Windows.Media.Color>.</span></span> <span data-ttu-id="5dbc5-124">有各種方式可以指定 <xref:System.Windows.Media.SolidColorBrush>的 <xref:System.Windows.Media.SolidColorBrush.Color%2A>：例如，您可以指定其 Alpha、紅色、藍色和綠色的通道，或使用 <xref:System.Windows.Media.Colors> 類別所提供的其中一個預先定義色彩。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-124">There are a variety of ways to specify the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush>: for example, you can specify its alpha, red, blue, and green channels or use one of the predefined color provided by the <xref:System.Windows.Media.Colors> class.</span></span>  
  
 <span data-ttu-id="5dbc5-125">下列範例會使用 <xref:System.Windows.Media.SolidColorBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-125">The following example uses a <xref:System.Windows.Media.SolidColorBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5dbc5-126">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-126">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="5dbc5-127">![使用 SolidColorBrush 繪製的矩形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="5dbc5-127">![A rectangle painted using a SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span></span>  
<span data-ttu-id="5dbc5-128">使用 SolidColorBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="5dbc5-128">A Rectangle painted using a SolidColorBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <span data-ttu-id="5dbc5-129">如需有關 <xref:System.Windows.Media.SolidColorBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的色彩總覽](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-129">For more information about the <xref:System.Windows.Media.SolidColorBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a><span data-ttu-id="5dbc5-130">以線性漸層繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-130">Paint with a Linear Gradient</span></span>  
 <span data-ttu-id="5dbc5-131"><xref:System.Windows.Media.LinearGradientBrush> 會以線性漸層繪製區域。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-131">A <xref:System.Windows.Media.LinearGradientBrush> paints an area with a linear gradient.</span></span> <span data-ttu-id="5dbc5-132">線性漸層會將兩個或多個色彩橫跨一條線，也就是梯度軸。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-132">A linear gradient blends two or more colors across a line, the gradient axis.</span></span> <span data-ttu-id="5dbc5-133">您可以使用 <xref:System.Windows.Media.GradientStop> 物件來指定漸層中的色彩和其位置。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-133">You use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="5dbc5-134">下列範例會使用 <xref:System.Windows.Media.LinearGradientBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-134">The following example uses a <xref:System.Windows.Media.LinearGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5dbc5-135">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-135">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="5dbc5-136">![使用 LinearGradientBrush 繪製的矩形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span><span class="sxs-lookup"><span data-stu-id="5dbc5-136">![A rectangle painted using a LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span></span>  
<span data-ttu-id="5dbc5-137">使用 LinearGradientBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="5dbc5-137">A Rectangle painted using a LinearGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <span data-ttu-id="5dbc5-138">如需有關 <xref:System.Windows.Media.LinearGradientBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的色彩總覽](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-138">For more information about the <xref:System.Windows.Media.LinearGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a><span data-ttu-id="5dbc5-139">使用放射狀漸層繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-139">Paint with a Radial Gradient</span></span>  
 <span data-ttu-id="5dbc5-140"><xref:System.Windows.Media.RadialGradientBrush> 繪製具有放射漸層的區域。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-140">A <xref:System.Windows.Media.RadialGradientBrush> paints an area with a radial gradient.</span></span> <span data-ttu-id="5dbc5-141">放射狀漸層會將兩個或多個色彩混合在一個圓形上。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-141">A radial gradient blends two or more colors across a circle.</span></span> <span data-ttu-id="5dbc5-142">如同 <xref:System.Windows.Media.LinearGradientBrush> 類別，您可以使用 <xref:System.Windows.Media.GradientStop> 物件來指定漸層中的色彩和其位置。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-142">As with the <xref:System.Windows.Media.LinearGradientBrush> class, you use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="5dbc5-143">下列範例會使用 <xref:System.Windows.Media.RadialGradientBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-143">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5dbc5-144">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-144">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="5dbc5-145">![使用 RadialGradientBrush 繪製的矩形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span><span class="sxs-lookup"><span data-stu-id="5dbc5-145">![A rectangle painted using a RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span></span>  
<span data-ttu-id="5dbc5-146">使用 RadialGradientBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="5dbc5-146">A Rectangle painted using a RadialGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <span data-ttu-id="5dbc5-147">如需有關 <xref:System.Windows.Media.RadialGradientBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的色彩總覽](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-147">For more information about the <xref:System.Windows.Media.RadialGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a><span data-ttu-id="5dbc5-148">使用影像繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-148">Paint with an Image</span></span>  
 <span data-ttu-id="5dbc5-149"><xref:System.Windows.Media.ImageBrush> 繪製具有 <xref:System.Windows.Media.ImageSource>的區域。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-149">An <xref:System.Windows.Media.ImageBrush> paints an area with a <xref:System.Windows.Media.ImageSource>.</span></span>  
  
 <span data-ttu-id="5dbc5-150">下列範例會使用 <xref:System.Windows.Media.ImageBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-150">The following example uses an <xref:System.Windows.Media.ImageBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5dbc5-151">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-151">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="5dbc5-152">![由 ImageBrush 繪製的矩形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span><span class="sxs-lookup"><span data-stu-id="5dbc5-152">![A Rectangle painted by an ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span></span>  
<span data-ttu-id="5dbc5-153">使用影像繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="5dbc5-153">A Rectangle painted using a Image</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <span data-ttu-id="5dbc5-154">如需 <xref:System.Windows.Media.ImageBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-154">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a><span data-ttu-id="5dbc5-155">使用繪圖繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-155">Paint with a Drawing</span></span>  
 <span data-ttu-id="5dbc5-156"><xref:System.Windows.Media.DrawingBrush> 繪製具有 <xref:System.Windows.Media.Drawing>的區域。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-156">A <xref:System.Windows.Media.DrawingBrush> paints an area with a <xref:System.Windows.Media.Drawing>.</span></span> <span data-ttu-id="5dbc5-157"><xref:System.Windows.Media.Drawing> 可以包含圖形、影像、文字和媒體。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-157">A <xref:System.Windows.Media.Drawing> can contain shapes, images, text, and media.</span></span>  
  
 <span data-ttu-id="5dbc5-158">下列範例會使用 <xref:System.Windows.Media.DrawingBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-158">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5dbc5-159">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-159">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="5dbc5-160">![使用 DrawingBrush 繪製的矩形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span><span class="sxs-lookup"><span data-stu-id="5dbc5-160">![A rectangle painted using a DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span></span>  
<span data-ttu-id="5dbc5-161">使用 DrawingBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="5dbc5-161">A Rectangle painted using a DrawingBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <span data-ttu-id="5dbc5-162">如需 <xref:System.Windows.Media.DrawingBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-162">For more information about the <xref:System.Windows.Media.DrawingBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a><span data-ttu-id="5dbc5-163">使用視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-163">Paint with a Visual</span></span>  
 <span data-ttu-id="5dbc5-164"><xref:System.Windows.Media.VisualBrush> 使用 <xref:System.Windows.Media.Visual> 物件繪製區域。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-164">A <xref:System.Windows.Media.VisualBrush> paints an area with a <xref:System.Windows.Media.Visual> object.</span></span> <span data-ttu-id="5dbc5-165">視覺物件的範例包括 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Page>和 <xref:System.Windows.Controls.MediaElement>。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-165">Examples of Visual objects include <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, and <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="5dbc5-166"><xref:System.Windows.Media.VisualBrush> 也可讓您從應用程式的某個部分將內容投影到另一個區域;它非常適合用來建立反映效果和螢幕的放大鏡部分。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-166">A <xref:System.Windows.Media.VisualBrush> also enables you to project content from one portion of your application into another area; it's very useful for creating reflection effects and magnifying portions of the screen.</span></span>  
  
 <span data-ttu-id="5dbc5-167">下列範例會使用 <xref:System.Windows.Media.VisualBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-167">The following example uses a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5dbc5-168">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-168">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="5dbc5-169">![使用 VisualBrush 繪製的矩形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span><span class="sxs-lookup"><span data-stu-id="5dbc5-169">![A rectangle painted using a VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span></span>  
<span data-ttu-id="5dbc5-170">使用 VisualBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="5dbc5-170">A Rectangle painted using a VisualBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <span data-ttu-id="5dbc5-171">如需 <xref:System.Windows.Media.VisualBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-171">For more information about the <xref:System.Windows.Media.VisualBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a><span data-ttu-id="5dbc5-172">使用預先定義和系統筆刷繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-172">Paint using Predefined and System Brushes</span></span>  
 <span data-ttu-id="5dbc5-173">為了方便起見，Windows Presentation Foundation （WPF）提供一組預先定義和可用來繪製物件的系統筆刷。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-173">For convenience, Windows Presentation Foundation (WPF) provides a set of predefined and system brushes that you can use to paint objects.</span></span>  
  
- <span data-ttu-id="5dbc5-174">如需可用預先定義的筆刷清單，請參閱 <xref:System.Windows.Media.Brushes> 類別。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-174">For a list of available predefined brushes, see the <xref:System.Windows.Media.Brushes> class.</span></span> <span data-ttu-id="5dbc5-175">如需顯示如何使用預先定義筆刷的範例，請參閱[使用純色繪製區域](how-to-paint-an-area-with-a-solid-color.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-175">For an example showing how to use a predefined brush, see [Paint an Area with a Solid Color](how-to-paint-an-area-with-a-solid-color.md).</span></span>  
  
- <span data-ttu-id="5dbc5-176">如需可用系統筆刷的清單，請參閱 <xref:System.Windows.SystemColors> 類別。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-176">For a list of available system brushes, see the <xref:System.Windows.SystemColors> class.</span></span> <span data-ttu-id="5dbc5-177">如需範例，請參閱[使用系統筆刷繪製區域](how-to-paint-an-area-with-a-system-brush.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-177">For an example, see [Paint an Area with a System Brush](how-to-paint-an-area-with-a-system-brush.md).</span></span>  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a><span data-ttu-id="5dbc5-178">一般筆刷功能</span><span class="sxs-lookup"><span data-stu-id="5dbc5-178">Common Brush Features</span></span>  
 <span data-ttu-id="5dbc5-179"><xref:System.Windows.Media.Brush> 物件會提供可用來將筆刷透明化或部分透明的 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-179"><xref:System.Windows.Media.Brush> objects provide an <xref:System.Windows.Media.Brush.Opacity%2A> property that can be used to make a brush transparent or partially transparent.</span></span> <span data-ttu-id="5dbc5-180"><xref:System.Windows.Media.Brush.Opacity%2A> 值0會使筆刷完全透明，而 <xref:System.Windows.Media.Brush.Opacity%2A> 值1則會使筆刷完全不透明。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-180">An <xref:System.Windows.Media.Brush.Opacity%2A> value of 0 makes a brush completely transparent, while an <xref:System.Windows.Media.Brush.Opacity%2A> value of 1 makes a brush completely opaque.</span></span> <span data-ttu-id="5dbc5-181">下列範例會使用 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性，使 <xref:System.Windows.Media.SolidColorBrush> 25% 不透明。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-181">The following example uses the <xref:System.Windows.Media.Brush.Opacity%2A> property to make a <xref:System.Windows.Media.SolidColorBrush> 25 percent opaque.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 <span data-ttu-id="5dbc5-182">如果筆刷包含部分透明的色彩，則色彩的不透明度值會透過乘法與筆刷的不透明度值結合。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-182">If the brush contains colors that are partially transparent, the opacity value of the color is combined through multiplication with the opacity value of the brush.</span></span> <span data-ttu-id="5dbc5-183">例如，如果筆刷的不透明度值為0.5，而筆刷中使用的色彩也具有不透明度值0.5，則輸出色彩會有不透明度值0.25。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-183">For example, if a brush has an opacity value of 0.5 and a color used in the brush also has an opacity value of 0.5, the output color has an opacity value of 0.25.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5dbc5-184">變更筆刷的不透明度值會比較有效率，而不是使用其 <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> 屬性來變更整個專案的不透明度。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-184">It's more efficient to change the opacity value of a brush than it is to change the opacity of an entire element using its <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="5dbc5-185">您可以使用其 <xref:System.Windows.Media.Brush.Transform%2A> 或 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性來旋轉、縮放、扭曲和轉譯筆刷的內容。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-185">You can rotate, scale, skew, and translate a brush's content by using its <xref:System.Windows.Media.Brush.Transform%2A> or <xref:System.Windows.Media.Brush.RelativeTransform%2A> properties.</span></span> <span data-ttu-id="5dbc5-186">如需詳細資訊，請參閱[筆刷轉換總覽](brush-transformation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-186">For more information, see [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="5dbc5-187">因為它們是 <xref:System.Windows.Media.Animation.Animatable> 物件，<xref:System.Windows.Media.Brush> 物件可以進行動畫。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-187">Because they are <xref:System.Windows.Media.Animation.Animatable> objects, <xref:System.Windows.Media.Brush> objects can be animated.</span></span> <span data-ttu-id="5dbc5-188">如需詳細資訊，請參閱 [動畫概觀](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-188">For more information, see [Animation Overview](animation-overview.md).</span></span>  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a><span data-ttu-id="5dbc5-189">Freezable 功能</span><span class="sxs-lookup"><span data-stu-id="5dbc5-189">Freezable Features</span></span>  
 <span data-ttu-id="5dbc5-190">因為它繼承自 <xref:System.Windows.Freezable> 類別，所以 <xref:System.Windows.Media.Brush> 類別提供數個特殊功能： <xref:System.Windows.Media.Brush> 物件可以宣告為[資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)、在多個物件之間共用，以及複製。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-190">Because it inherits from the <xref:System.Windows.Freezable> class, the <xref:System.Windows.Media.Brush> class provides several special features: <xref:System.Windows.Media.Brush> objects can be declared as [resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), shared among multiple objects, and cloned.</span></span> <span data-ttu-id="5dbc5-191">此外，除了 <xref:System.Windows.Media.VisualBrush> 以外的所有 <xref:System.Windows.Media.Brush> 類型都可以設為唯讀，以改善效能並使其成為安全線程。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-191">In addition, all the <xref:System.Windows.Media.Brush> types except <xref:System.Windows.Media.VisualBrush> can be made read-only to improve performance and made thread-safe.</span></span>  
  
 <span data-ttu-id="5dbc5-192">如需 <xref:System.Windows.Freezable> 物件所提供之不同功能的詳細資訊，請參閱可[凍結物件總覽](../advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-192">For more information about the different features provided by <xref:System.Windows.Freezable> objects, see [Freezable Objects Overview](../advanced/freezable-objects-overview.md).</span></span>  
  
 <span data-ttu-id="5dbc5-193">如需為何無法凍結 <xref:System.Windows.Media.VisualBrush> 物件的詳細資訊，請參閱 <xref:System.Windows.Media.VisualBrush> 類型 頁面。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-193">For more information on why <xref:System.Windows.Media.VisualBrush> objects cannot be frozen, see the <xref:System.Windows.Media.VisualBrush> type page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dbc5-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="5dbc5-194">See also</span></span>

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [<span data-ttu-id="5dbc5-195">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="5dbc5-195">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="5dbc5-196">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="5dbc5-196">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="5dbc5-197">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="5dbc5-197">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="5dbc5-198">筆刷範例</span><span class="sxs-lookup"><span data-stu-id="5dbc5-198">Brushes Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159973)
- [<span data-ttu-id="5dbc5-199">ImageBrush 範例</span><span class="sxs-lookup"><span data-stu-id="5dbc5-199">ImageBrush Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160005)
- [<span data-ttu-id="5dbc5-200">VisualBrush 範例</span><span class="sxs-lookup"><span data-stu-id="5dbc5-200">VisualBrush Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160049)
- [<span data-ttu-id="5dbc5-201">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="5dbc5-201">How-to Topics</span></span>](brushes-how-to-topics.md)
- [<span data-ttu-id="5dbc5-202">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="5dbc5-202">Other Performance Recommendations</span></span>](../advanced/optimizing-performance-other-recommendations.md)
