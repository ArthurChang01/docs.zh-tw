---
title: 使用對齊線排列控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3b88f64fca8d3f11308f1cbfde97de2e6c2f22cc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740214"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a><span data-ttu-id="b1354-102">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="b1354-102">Walkthrough: Arrange controls on Windows Forms using snaplines</span></span>

<span data-ttu-id="b1354-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="b1354-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="b1354-104">Windows Form 設計工具提供您許多版面組態工具來完成此動作。</span><span class="sxs-lookup"><span data-stu-id="b1354-104">The Windows Forms Designer gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="b1354-105">其中一個最重要的是 <xref:System.Windows.Forms.Design.Behavior.SnapLine> 功能。</span><span class="sxs-lookup"><span data-stu-id="b1354-105">One of the most important is the <xref:System.Windows.Forms.Design.Behavior.SnapLine> feature.</span></span>

<span data-ttu-id="b1354-106">對齊線可讓您精確地顯示控制項與其他控制項的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-106">Snaplines show you precisely where to line up controls with other controls.</span></span> <span data-ttu-id="b1354-107">它們也會顯示控制項之間的邊界建議距離，如[Windows 使用者介面指導方針](/windows/win32/uxguide/guidelines)所指定。</span><span class="sxs-lookup"><span data-stu-id="b1354-107">They also show you the recommended distances for margins between controls, as specified by the [Windows User Interface guidelines](/windows/win32/uxguide/guidelines).</span></span>

<span data-ttu-id="b1354-108">對齊線可讓您輕鬆對齊控制項，以提供清晰、專業的外觀和行為（外觀與風格）。</span><span class="sxs-lookup"><span data-stu-id="b1354-108">Snaplines make it easy to align your controls, for crisp, professional appearance and behavior (look and feel).</span></span>

## <a name="create-the-project"></a><span data-ttu-id="b1354-109">建立專案</span><span class="sxs-lookup"><span data-stu-id="b1354-109">Create the project</span></span>

1. <span data-ttu-id="b1354-110">在 Visual Studio 中，建立名為 "SnaplineExample" 的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b1354-110">In Visual Studio, create a Windows-based application project called "SnaplineExample".</span></span>

2. <span data-ttu-id="b1354-111">選取 [表單設計工具] 中的表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-111">Select the form in the Forms Designer.</span></span>

## <a name="space-and-align-controls"></a><span data-ttu-id="b1354-112">空間和對齊控制項</span><span class="sxs-lookup"><span data-stu-id="b1354-112">Space and align controls</span></span>

<span data-ttu-id="b1354-113">對齊線可讓您以精確且直覺的方式對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-113">Snaplines give you an accurate and intuitive way to align controls on your form.</span></span> <span data-ttu-id="b1354-114">當您將選取的控制項或控制項移到靠近另一個控制項或一組控制項的位置附近時，就會顯示它們。</span><span class="sxs-lookup"><span data-stu-id="b1354-114">They appear when you are moving a selected control or controls near a position that would align with another control or set of controls.</span></span> <span data-ttu-id="b1354-115">當您將它移到其他控制項之後，您的選擇就會「貼齊」到建議的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-115">Your selection will "snap" to the suggested position as you move it past the other controls.</span></span>

### <a name="to-arrange-controls-using-snaplines"></a><span data-ttu-id="b1354-116">使用對齊線排列控制項</span><span class="sxs-lookup"><span data-stu-id="b1354-116">To arrange controls using snaplines</span></span>

1. <span data-ttu-id="b1354-117">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-117">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="b1354-118">將 [<xref:System.Windows.Forms.Button>] 控制項移到表單的右下角。</span><span class="sxs-lookup"><span data-stu-id="b1354-118">Move the <xref:System.Windows.Forms.Button> control to the lower-right corner of the form.</span></span> <span data-ttu-id="b1354-119">請注意，顯示為 <xref:System.Windows.Forms.Button> 控制項的對齊線會接近表單的底部和右側框線。</span><span class="sxs-lookup"><span data-stu-id="b1354-119">Note the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the form.</span></span> <span data-ttu-id="b1354-120">這些對齊線會顯示控制項框線與表單之間的建議距離。</span><span class="sxs-lookup"><span data-stu-id="b1354-120">These snaplines display the recommended distance between the borders of the control and the form.</span></span>

3. <span data-ttu-id="b1354-121">將 [<xref:System.Windows.Forms.Button>] 控制項移到表單的框線周圍，並記下對齊線的顯示位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-121">Move the <xref:System.Windows.Forms.Button> control around the borders of the form and note where the snaplines appear.</span></span> <span data-ttu-id="b1354-122">當您完成時，請將 [<xref:System.Windows.Forms.Button>] 控制項移到表單的中央附近。</span><span class="sxs-lookup"><span data-stu-id="b1354-122">When you are finished, move the <xref:System.Windows.Forms.Button> control near the center of the form.</span></span>

4. <span data-ttu-id="b1354-123">將另一個 <xref:System.Windows.Forms.Button> 控制項從 [**工具箱**] 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="b1354-123">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="b1354-124">移動第二個 <xref:System.Windows.Forms.Button> 控制項，直到接近第一個的層級為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-124">Move the second <xref:System.Windows.Forms.Button> control until it is nearly level with the first.</span></span> <span data-ttu-id="b1354-125">請注意這兩個按鈕的文字基線上所顯示的對齊線，並請注意，您要移動的控制項會貼齊至與其他控制項完全層級的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-125">Note the snapline that appears at the text baseline of both buttons, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>

6. <span data-ttu-id="b1354-126">移動第二個 <xref:System.Windows.Forms.Button> 控制項，直到它位於第一個位置的正上方。</span><span class="sxs-lookup"><span data-stu-id="b1354-126">Move the second <xref:System.Windows.Forms.Button> control until it is positioned directly above the first.</span></span> <span data-ttu-id="b1354-127">請注意出現在兩個按鈕左右邊緣的對齊線，並請注意，您要移動的控制項會對齊與其他控制項完全一致的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-127">Note the snaplines that appear along the left and right edges of both buttons, and note that the control you are moving snaps to a position that is exactly aligned with the other control.</span></span>

7. <span data-ttu-id="b1354-128">選取其中一個 <xref:System.Windows.Forms.Button> 控制項，然後將其移到另一個，直到幾乎觸及為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-128">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span> <span data-ttu-id="b1354-129">請記下出現在其間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="b1354-129">Note the snapline that appears between them.</span></span> <span data-ttu-id="b1354-130">這個距離是控制項框線之間的建議距離。</span><span class="sxs-lookup"><span data-stu-id="b1354-130">This distance is the recommended distance between the borders of the controls.</span></span> <span data-ttu-id="b1354-131">另請注意，您要移動的控制項會貼齊此位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-131">Also note that the control you are moving snaps to this position.</span></span>

8. <span data-ttu-id="b1354-132">將兩個 <xref:System.Windows.Forms.Panel> 控制項從 [**工具箱**] 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="b1354-132">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto your form.</span></span>

9. <span data-ttu-id="b1354-133">移動其中一個 <xref:System.Windows.Forms.Panel> 控制項，直到接近第一個的層級為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-133">Move one of the <xref:System.Windows.Forms.Panel> controls until it is nearly level with the first.</span></span> <span data-ttu-id="b1354-134">請注意顯示在這兩個控制項上下邊緣的對齊線，並請注意，您要移動的控制項會貼齊至與其他控制項完全層級的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-134">Note the snaplines that appear along the top and bottom edges of both controls, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>

## <a name="align-to-form-and-container-margins"></a><span data-ttu-id="b1354-135">對齊表單和容器邊界</span><span class="sxs-lookup"><span data-stu-id="b1354-135">Align to form and container margins</span></span>

<span data-ttu-id="b1354-136">對齊線可協助您以一致的方式讓控制項對齊表單和容器邊界。</span><span class="sxs-lookup"><span data-stu-id="b1354-136">Snaplines help you to align your controls to form and container margins in a consistent manner.</span></span>

1. <span data-ttu-id="b1354-137">選取其中一個 <xref:System.Windows.Forms.Button> 控制項，然後將它移到靠近表單的右框線，直到對齊線出現為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-137">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="b1354-138">對齊線與右框線的距離是控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性和表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值的總和。</span><span class="sxs-lookup"><span data-stu-id="b1354-138">The snapline's distance from the right border is the sum of the control's <xref:System.Windows.Forms.Control.Margin%2A> property and the form's <xref:System.Windows.Forms.Control.Padding%2A> property values.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b1354-139">如果表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性設定為0，0，0，0，則 Windows Form 設計工具會提供陰影 <xref:System.Windows.Forms.Control.Padding%2A> 值9、9、9、9。</span><span class="sxs-lookup"><span data-stu-id="b1354-139">If the form's <xref:System.Windows.Forms.Control.Padding%2A> property is set to 0,0,0,0, the Windows Forms Designer gives the form a shadowed <xref:System.Windows.Forms.Control.Padding%2A> value of 9,9,9,9.</span></span> <span data-ttu-id="b1354-140">若要覆寫此行為，請指派0、0、0、0以外的值。</span><span class="sxs-lookup"><span data-stu-id="b1354-140">To override this behavior, assign a value other than 0,0,0,0.</span></span>

2. <span data-ttu-id="b1354-141">藉由展開 [**屬性**] 視窗中的 [<xref:System.Windows.Forms.Control.Margin%2A>] 專案，並將 [<xref:System.Windows.Forms.Padding.All%2A>] 屬性設為0，來變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="b1354-141">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 0.</span></span> <span data-ttu-id="b1354-142">如需詳細資訊，請參閱[逐步解說：使用填補、邊界和 AutoSize 屬性配置 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)。</span><span class="sxs-lookup"><span data-stu-id="b1354-142">For details, see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>

3. <span data-ttu-id="b1354-143">將 [<xref:System.Windows.Forms.Button>] 控制項移到表單的右框線附近，直到對齊線出現為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-143">Move the <xref:System.Windows.Forms.Button> control close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="b1354-144">這個距離現在是由表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值所提供。</span><span class="sxs-lookup"><span data-stu-id="b1354-144">This distance is now given by the value of the form's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>

4. <span data-ttu-id="b1354-145">從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-145">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="b1354-146">藉由展開 [**屬性**] 視窗中的 [<xref:System.Windows.Forms.Control.Padding%2A>] 專案，並將 [<xref:System.Windows.Forms.Padding.All%2A>] 屬性設定為 [10]，來變更 <xref:System.Windows.Forms.GroupBox> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="b1354-146">Change the value of the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 10.</span></span>

6. <span data-ttu-id="b1354-147">將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至 [<xref:System.Windows.Forms.GroupBox>] 控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-147">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>

7. <span data-ttu-id="b1354-148">將 <xref:System.Windows.Forms.Button> 控制項移至靠近 <xref:System.Windows.Forms.GroupBox> 控制項的右框線，直到對齊線出現為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-148">Move the <xref:System.Windows.Forms.Button> control close to the right border of the <xref:System.Windows.Forms.GroupBox> control until a snapline appears.</span></span> <span data-ttu-id="b1354-149">移動 <xref:System.Windows.Forms.GroupBox> 控制項內的 <xref:System.Windows.Forms.Button> 控制項，並注意對齊線的出現位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-149">Move the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and note where the snaplines appear.</span></span>

## <a name="align-to-grouped-controls"></a><span data-ttu-id="b1354-150">對齊群組控制項</span><span class="sxs-lookup"><span data-stu-id="b1354-150">Align to grouped controls</span></span>

<span data-ttu-id="b1354-151">您可以使用對齊線來對齊群組控制項以及 <xref:System.Windows.Forms.GroupBox> 控制項內的控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-151">You can use snaplines to align grouped controls as well as controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span>

1. <span data-ttu-id="b1354-152">選取表單上的兩個控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-152">Select two of the controls on your form.</span></span> <span data-ttu-id="b1354-153">移動選取範圍，並記下您的選取範圍與其他控制項之間出現的對齊線。</span><span class="sxs-lookup"><span data-stu-id="b1354-153">Move the selection around and note the snaplines that appear between your selection and the other controls.</span></span>

2. <span data-ttu-id="b1354-154">從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-154">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>

3. <span data-ttu-id="b1354-155">將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至 [<xref:System.Windows.Forms.GroupBox>] 控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-155">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>

4. <span data-ttu-id="b1354-156">選取其中一個 <xref:System.Windows.Forms.Button> 控制項，然後將它移至 <xref:System.Windows.Forms.GroupBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-156">Select one of the <xref:System.Windows.Forms.Button> controls and move it around the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="b1354-157">請注意顯示在 <xref:System.Windows.Forms.GroupBox> 控制項邊緣的對齊線。</span><span class="sxs-lookup"><span data-stu-id="b1354-157">Note the snaplines that appear at the edges of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="b1354-158">也請注意出現在 <xref:System.Windows.Forms.GroupBox> 控制項所包含的 <xref:System.Windows.Forms.Button> 控制項邊緣的對齊線。</span><span class="sxs-lookup"><span data-stu-id="b1354-158">Also note the snaplines that appear at the edges of the <xref:System.Windows.Forms.Button> control that is contained by the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="b1354-159">屬於容器控制項子系的控制項也支援對齊線。</span><span class="sxs-lookup"><span data-stu-id="b1354-159">Controls that are children of a container control also support snaplines.</span></span>

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="b1354-160">使用對齊線來放置控制項，方法是大綱其大小</span><span class="sxs-lookup"><span data-stu-id="b1354-160">Use snaplines to place a control by outlining its size</span></span>

1. <span data-ttu-id="b1354-161">按一下 [工具箱]的 <xref:System.Windows.Forms.Button> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="b1354-161">In the **Toolbox**, click the <xref:System.Windows.Forms.Button> control icon.</span></span> <span data-ttu-id="b1354-162">請勿拖曳到表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-162">Do not drag it onto the form.</span></span>

2. <span data-ttu-id="b1354-163">將滑鼠指標移到表單的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="b1354-163">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="b1354-164">請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="b1354-164">Note that the pointer changes to a crosshair with the <xref:System.Windows.Forms.Button> control icon attached.</span></span> <span data-ttu-id="b1354-165">另請注意，顯示的對齊線會建議 <xref:System.Windows.Forms.Button> 控制項的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-165">Also note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span>

3. <span data-ttu-id="b1354-166">按住滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1354-166">Click and hold the mouse button.</span></span>

4. <span data-ttu-id="b1354-167">將滑鼠指標拖曳至表單的周圍。</span><span class="sxs-lookup"><span data-stu-id="b1354-167">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="b1354-168">請注意，會繪製外框，表示控制項的位置和大小。</span><span class="sxs-lookup"><span data-stu-id="b1354-168">Note that an outline is drawn, indicating the position and the size of the control.</span></span>

5. <span data-ttu-id="b1354-169">拖曳指標，直到它與表單上的另一個控制項對齊。</span><span class="sxs-lookup"><span data-stu-id="b1354-169">Drag the pointer until it aligns with another control on the form.</span></span> <span data-ttu-id="b1354-170">請注意，對齊線會出現以指出對齊方式。</span><span class="sxs-lookup"><span data-stu-id="b1354-170">Note that a snapline appears to indicate alignment.</span></span>

6. <span data-ttu-id="b1354-171">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1354-171">Release the mouse button.</span></span> <span data-ttu-id="b1354-172">控制項會建立在外框所指示的位置和大小。</span><span class="sxs-lookup"><span data-stu-id="b1354-172">The control is created at the position and size indicated by the outline.</span></span>

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="b1354-173">從工具箱拖曳控制項時使用對齊線</span><span class="sxs-lookup"><span data-stu-id="b1354-173">Use snaplines when dragging a control from the Toolbox</span></span>

1. <span data-ttu-id="b1354-174">將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至表單上，但不要放開滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="b1354-174">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form, but do not release the mouse button.</span></span>

2. <span data-ttu-id="b1354-175">將滑鼠指標移到表單的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="b1354-175">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="b1354-176">請注意，指標會變更以指出將建立新 <xref:System.Windows.Forms.Button> 控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-176">Note that the pointer changes to indicate the position at which the new <xref:System.Windows.Forms.Button> control will be created.</span></span>

3. <span data-ttu-id="b1354-177">將滑鼠指標拖曳至表單的周圍。</span><span class="sxs-lookup"><span data-stu-id="b1354-177">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="b1354-178">請注意，顯示的對齊線會建議 <xref:System.Windows.Forms.Button> 控制項的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-178">Note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="b1354-179">尋找與其他控制項對齊的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-179">Find a position that is aligned with other controls.</span></span>

4. <span data-ttu-id="b1354-180">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1354-180">Release the mouse button.</span></span> <span data-ttu-id="b1354-181">會在對齊線所指示的位置建立控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-181">The control is created at the position indicated by the snaplines.</span></span>

## <a name="resize-a-control-using-snaplines"></a><span data-ttu-id="b1354-182">使用對齊線調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="b1354-182">Resize a control using snaplines</span></span>

1. <span data-ttu-id="b1354-183">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-183">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="b1354-184">抓取其中一個角落調整大小控點和拖曳，以調整 <xref:System.Windows.Forms.Button> 控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="b1354-184">Resize the <xref:System.Windows.Forms.Button> control by grabbing one of the corner sizing handles and dragging.</span></span> <span data-ttu-id="b1354-185">如需詳細資訊，請參閱[如何：在 Windows Forms 上調整控制項大小](how-to-resize-controls-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b1354-185">For details, see [How to: Resize Controls on Windows Forms](how-to-resize-controls-on-windows-forms.md).</span></span>

3. <span data-ttu-id="b1354-186">拖曳調整大小控點，直到其中一個 <xref:System.Windows.Forms.Button> 控制項的框線與另一個控制項對齊為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-186">Drag the sizing handle until one of the <xref:System.Windows.Forms.Button> control's borders is aligned with another control.</span></span> <span data-ttu-id="b1354-187">請注意，對齊線隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b1354-187">Note that a snapline appears.</span></span> <span data-ttu-id="b1354-188">另請注意，調整大小控點會貼齊對齊線所指示的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-188">Also note that the sizing handle snaps to the position indicated by the snapline.</span></span>

4. <span data-ttu-id="b1354-189">以不同的方向調整 <xref:System.Windows.Forms.Button> 控制項的大小，並將調整大小控點對齊不同的控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-189">Resize the <xref:System.Windows.Forms.Button> control in different directions and align the sizing handle to different controls.</span></span> <span data-ttu-id="b1354-190">請注意對齊線如何顯示在各種方向，以表示對齊方式。</span><span class="sxs-lookup"><span data-stu-id="b1354-190">Note how the snaplines appear in various orientations to indicate alignment.</span></span>

## <a name="align-a-label-to-a-controls-text"></a><span data-ttu-id="b1354-191">將標籤對齊控制項的文字</span><span class="sxs-lookup"><span data-stu-id="b1354-191">Align a label to a control's text</span></span>

1. <span data-ttu-id="b1354-192">從 [工具箱] <xref:System.Windows.Forms.TextBox>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-192">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="b1354-193">當您將 [<xref:System.Windows.Forms.TextBox>] 控制項放到表單上時，請按一下智慧標籤圖像，然後選取 [**將文字設定為 textBox1** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="b1354-193">When you drop the <xref:System.Windows.Forms.TextBox> control onto the form, click the smart-tag glyph and select the **Set text to textBox1** option.</span></span> <span data-ttu-id="b1354-194">如需詳細資訊，請參閱[逐步解說：使用 Windows Forms 控制項上的智慧標籤執行一般](performing-common-tasks-using-smart-tags-on-wf-controls.md)工作。</span><span class="sxs-lookup"><span data-stu-id="b1354-194">For details, see [Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](performing-common-tasks-using-smart-tags-on-wf-controls.md).</span></span>

2. <span data-ttu-id="b1354-195">從 [工具箱] <xref:System.Windows.Forms.Label>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-195">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto your form.</span></span>

3. <span data-ttu-id="b1354-196">變更 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b1354-196">Change the value of the <xref:System.Windows.Forms.Label> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="b1354-197">請注意，控制項的框線會調整以符合顯示文字。</span><span class="sxs-lookup"><span data-stu-id="b1354-197">Note that the control's borders are adjusted to fit the display text.</span></span>

4. <span data-ttu-id="b1354-198">將 [<xref:System.Windows.Forms.Label>] 控制項移至 [<xref:System.Windows.Forms.TextBox>] 控制項的左側，使其與 <xref:System.Windows.Forms.TextBox> 控制項的下邊緣對齊。</span><span class="sxs-lookup"><span data-stu-id="b1354-198">Move the <xref:System.Windows.Forms.Label> control to the left of the <xref:System.Windows.Forms.TextBox> control, so it is aligned with the bottom edge of the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="b1354-199">請注意沿著兩個控制項的下邊緣顯示的對齊線。</span><span class="sxs-lookup"><span data-stu-id="b1354-199">Note the snapline that appears along the bottom edges of the two controls.</span></span>

5. <span data-ttu-id="b1354-200">將 <xref:System.Windows.Forms.Label> 控制項稍微向上移動，直到 <xref:System.Windows.Forms.Label> 文字和 <xref:System.Windows.Forms.TextBox> 文字對齊為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-200">Move the <xref:System.Windows.Forms.Label> control slightly upward, until the <xref:System.Windows.Forms.Label> text and the <xref:System.Windows.Forms.TextBox> text are aligned.</span></span> <span data-ttu-id="b1354-201">請注意出現的不同樣式對齊線，表示兩個控制項的文字欄位何時對齊。</span><span class="sxs-lookup"><span data-stu-id="b1354-201">Note the differently styled snapline that appears, indicating when the text fields of both controls are aligned.</span></span>

## <a name="use-snaplines-with-keyboard-navigation"></a><span data-ttu-id="b1354-202">搭配鍵盤導覽使用對齊線</span><span class="sxs-lookup"><span data-stu-id="b1354-202">Use snaplines with keyboard navigation</span></span>

1. <span data-ttu-id="b1354-203">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-203">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="b1354-204">將它放在表單的左上角。</span><span class="sxs-lookup"><span data-stu-id="b1354-204">Place it in the upper-left corner of the form.</span></span>

2. <span data-ttu-id="b1354-205">按**Ctrl**+**向下**鍵。</span><span class="sxs-lookup"><span data-stu-id="b1354-205">Press **Ctrl**+**down arrow**.</span></span> <span data-ttu-id="b1354-206">請注意，控制項會向下移動到第一個可用的水準對齊位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-206">Note that the control moves down the form to the first available horizontal alignment position.</span></span>

3. <span data-ttu-id="b1354-207">按**Ctrl**+**向下鍵**，直到控制項到達表單的底部為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-207">Press **Ctrl**+**down arrow** until the control reaches the bottom of the form.</span></span> <span data-ttu-id="b1354-208">請注意它在表單向下移動時所佔用的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-208">Note the positions it occupies as it moves down the form.</span></span>

4. <span data-ttu-id="b1354-209">按**Ctrl**+**向右箭**號。</span><span class="sxs-lookup"><span data-stu-id="b1354-209">Press **Ctrl**+**right arrow**.</span></span> <span data-ttu-id="b1354-210">請注意，控制項會在表單上移動到第一個可用的垂直對齊位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-210">Note that the control moves across the form to the first available vertical alignment position.</span></span>

5. <span data-ttu-id="b1354-211">按**Ctrl**+**向右箭**號，直到控制項到達表單的側邊為止。</span><span class="sxs-lookup"><span data-stu-id="b1354-211">Press **Ctrl**+**right arrow** until the control reaches the side of the form.</span></span> <span data-ttu-id="b1354-212">請注意它在表單上移動時所佔用的位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-212">Note the positions it occupies as it moves across the form.</span></span>

6. <span data-ttu-id="b1354-213">使用方向鍵的組合來移動表單周圍的控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-213">Move the control around the form with a combination of arrow keys.</span></span> <span data-ttu-id="b1354-214">請注意控制項所佔用的位置以及伴隨的對齊線。</span><span class="sxs-lookup"><span data-stu-id="b1354-214">Note the positions the control occupies and the snaplines that accompany them.</span></span>

7. <span data-ttu-id="b1354-215">按**Shift**+**方向鍵**，藉由一個圖元的遞增來調整 <xref:System.Windows.Forms.Button> 控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="b1354-215">Press **Shift**+**arrow keys** to resize the <xref:System.Windows.Forms.Button> control by increments of one pixel.</span></span>

8. <span data-ttu-id="b1354-216">按**Ctrl**+**Shift**+**方向鍵**，以調整 <xref:System.Windows.Forms.Button> 控制項的對齊方式遞增。</span><span class="sxs-lookup"><span data-stu-id="b1354-216">Press **Ctrl**+**Shift**+**arrow keys** to resize the <xref:System.Windows.Forms.Button> control in snapline increments.</span></span>

## <a name="selectively-disable-snaplines"></a><span data-ttu-id="b1354-217">選擇性停用對齊線</span><span class="sxs-lookup"><span data-stu-id="b1354-217">Selectively disable snaplines</span></span>

1. <span data-ttu-id="b1354-218">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b1354-218">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="b1354-219">在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="b1354-219">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox**.</span></span> <span data-ttu-id="b1354-220">請注意，新的按鈕控制項會出現在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的第一個儲存格。</span><span class="sxs-lookup"><span data-stu-id="b1354-220">Note that a new button control appears in the <xref:System.Windows.Forms.TableLayoutPanel> control's first cell.</span></span>

3. <span data-ttu-id="b1354-221">按兩下 [**工具箱**] 中的 [<xref:System.Windows.Forms.Button> 控制項] 圖示，再按兩次。</span><span class="sxs-lookup"><span data-stu-id="b1354-221">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox** twice more.</span></span> <span data-ttu-id="b1354-222">這會在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中留下一個空白儲存格。</span><span class="sxs-lookup"><span data-stu-id="b1354-222">This leaves one empty cell in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="b1354-223">將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至 [<xref:System.Windows.Forms.TableLayoutPanel>] 控制項的空白儲存格。</span><span class="sxs-lookup"><span data-stu-id="b1354-223">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the empty cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="b1354-224">請注意，不會顯示對齊線。</span><span class="sxs-lookup"><span data-stu-id="b1354-224">Note that no snaplines appear.</span></span>

5. <span data-ttu-id="b1354-225">將 [<xref:System.Windows.Forms.Button>] 控制項拖曳至 [<xref:System.Windows.Forms.TableLayoutPanel>] 控制項，並將它移到 [<xref:System.Windows.Forms.TableLayoutPanel>] 控制項周圍。</span><span class="sxs-lookup"><span data-stu-id="b1354-225">Drag the <xref:System.Windows.Forms.Button> control out of the <xref:System.Windows.Forms.TableLayoutPanel> control and move it around the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="b1354-226">請注意，對齊線會再次出現。</span><span class="sxs-lookup"><span data-stu-id="b1354-226">Note that snaplines appear again.</span></span>

## <a name="disable-snaplines"></a><span data-ttu-id="b1354-227">停用對齊線</span><span class="sxs-lookup"><span data-stu-id="b1354-227">Disable snaplines</span></span>

<span data-ttu-id="b1354-228">按**Alt**鍵，並在表單周圍移動控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-228">Press the **Alt** key and while moving a control around the form.</span></span>

<span data-ttu-id="b1354-229">不會顯示對齊線，而且控制項不會貼齊任何可能的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="b1354-229">No snaplines appear and the control does not snap to any potential alignment positions.</span></span>

### <a name="to-disable-snaplines-in-the-design-environment"></a><span data-ttu-id="b1354-230">停用設計環境中的對齊線</span><span class="sxs-lookup"><span data-stu-id="b1354-230">To disable snaplines in the design environment</span></span>

1. <span data-ttu-id="b1354-231">從 [**工具**] 功能表中，開啟 [**選項**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b1354-231">From the **Tools** menu, open the **Options** dialog box.</span></span> <span data-ttu-id="b1354-232">選取 [ **Windows Form 設計工具**]。</span><span class="sxs-lookup"><span data-stu-id="b1354-232">Select **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="b1354-233">選取 [**一般**] 節點。</span><span class="sxs-lookup"><span data-stu-id="b1354-233">Select the **General** node.</span></span> <span data-ttu-id="b1354-234">在 [**版面配置模式]** 區段中，將選取專案從**對齊線**變更為**對齊**。</span><span class="sxs-lookup"><span data-stu-id="b1354-234">In the **Layout Mode** section, change the selection from **SnapLines** to **SnapToGrid**.</span></span>

3. <span data-ttu-id="b1354-235">選取 **[確定]** 以套用設定。</span><span class="sxs-lookup"><span data-stu-id="b1354-235">Select **OK** to apply the setting.</span></span>

4. <span data-ttu-id="b1354-236">選取表單上的控制項，並將它移到其他控制項的周圍。</span><span class="sxs-lookup"><span data-stu-id="b1354-236">Select a control on your form and move it around the other controls.</span></span> <span data-ttu-id="b1354-237">請注意，對齊線不會出現。</span><span class="sxs-lookup"><span data-stu-id="b1354-237">Note that snaplines do not appear.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1354-238">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b1354-238">Next steps</span></span>

<span data-ttu-id="b1354-239">對齊線提供直覺的方式來對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-239">Snaplines offer an intuitive means of aligning controls on your form.</span></span> <span data-ttu-id="b1354-240">進一步的探索建議包括：</span><span class="sxs-lookup"><span data-stu-id="b1354-240">Suggestions for more exploration include:</span></span>

- <span data-ttu-id="b1354-241">嘗試在另一個 <xref:System.Windows.Forms.GroupBox> 控制項內嵌套 <xref:System.Windows.Forms.GroupBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b1354-241">Try nesting a <xref:System.Windows.Forms.GroupBox> control within another <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="b1354-242">將 <xref:System.Windows.Forms.Button> 控制項放在子 <xref:System.Windows.Forms.GroupBox> 控制項內，另一個在父 <xref:System.Windows.Forms.GroupBox> 控制項內。</span><span class="sxs-lookup"><span data-stu-id="b1354-242">Place a <xref:System.Windows.Forms.Button> control within the child <xref:System.Windows.Forms.GroupBox> control, and another within the parent <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="b1354-243">四處移動 <xref:System.Windows.Forms.Button> 控制項，以查看對齊線如何跨容器界限。</span><span class="sxs-lookup"><span data-stu-id="b1354-243">Move the <xref:System.Windows.Forms.Button> controls around to see how the snaplines cross container boundaries.</span></span>

- <span data-ttu-id="b1354-244">建立 <xref:System.Windows.Forms.TextBox> 控制項的資料行，以及 <xref:System.Windows.Forms.Label> 控制項的對應資料行。</span><span class="sxs-lookup"><span data-stu-id="b1354-244">Create a column of <xref:System.Windows.Forms.TextBox> controls and a corresponding column of <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="b1354-245">將 [<xref:System.Windows.Forms.Label> 控制項] 的 [<xref:System.Windows.Forms.Control.AutoSize%2A>] 屬性值設定為 [`true`]。</span><span class="sxs-lookup"><span data-stu-id="b1354-245">Set the value of the <xref:System.Windows.Forms.Label> controls' <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="b1354-246">使用對齊線來移動 <xref:System.Windows.Forms.Label> 控制項，使其顯示的文字與 <xref:System.Windows.Forms.TextBox> 控制項中的文字對齊。</span><span class="sxs-lookup"><span data-stu-id="b1354-246">Use snaplines to move the <xref:System.Windows.Forms.Label> controls so their displayed text is aligned with the text in the <xref:System.Windows.Forms.TextBox> controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1354-247">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1354-247">See also</span></span>

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [<span data-ttu-id="b1354-248">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="b1354-248">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="b1354-249">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="b1354-249">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="b1354-250">逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="b1354-250">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
