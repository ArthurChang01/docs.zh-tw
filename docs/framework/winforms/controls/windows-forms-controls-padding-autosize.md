---
title: 配置具有填補、邊界和 AutoSize 屬性的控制項
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca7942c04434592f2541252c47ac3dd17e03dbac
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742380"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a><span data-ttu-id="7afb7-102">逐步解說：使用填補、邊界和 AutoSize 屬性配置控制項</span><span class="sxs-lookup"><span data-stu-id="7afb7-102">Walkthrough: Lay out controls with padding, margins, and the AutoSize property</span></span>

<span data-ttu-id="7afb7-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="7afb7-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="7afb7-104">Visual Studio 中的**Windows Form 設計工具**提供您許多版面組態工具來完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="7afb7-104">The **Windows Forms Designer** in Visual Studio gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="7afb7-105">其中三個最重要的是 <xref:System.Windows.Forms.Control.Margin%2A>、<xref:System.Windows.Forms.Control.Padding%2A>和 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性，它們都存在於所有 Windows Forms 控制項上。</span><span class="sxs-lookup"><span data-stu-id="7afb7-105">Three of the most important are the <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, and <xref:System.Windows.Forms.Control.AutoSize%2A> properties, which are present on all Windows Forms controls.</span></span>

<span data-ttu-id="7afb7-106"><xref:System.Windows.Forms.Control.Margin%2A> 屬性可定義控制項周圍的空間，使其他控制項與該控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="7afb7-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>

<span data-ttu-id="7afb7-107"><xref:System.Windows.Forms.Control.Padding%2A> 屬性可定義控制項的內部空間，使控制項的內容 (例如，其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值) 與控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="7afb7-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>

<span data-ttu-id="7afb7-108">下圖顯示控制項上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>

![Windows Form 控制項的邊框距離和邊界](./media/vs-winformpadmargin.gif)

<span data-ttu-id="7afb7-110"><xref:System.Windows.Forms.Control.AutoSize%2A> 屬性會告知控制項自動將本身的大小調整為其內容。</span><span class="sxs-lookup"><span data-stu-id="7afb7-110">The <xref:System.Windows.Forms.Control.AutoSize%2A> property tells a control to automatically size itself to its contents.</span></span> <span data-ttu-id="7afb7-111">它不會將其大小調整為小於其原始 <xref:System.Windows.Forms.Control.Size%2A> 屬性的值，而且將會考慮其 <xref:System.Windows.Forms.Control.Padding%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7afb7-111">It will not resize itself to be smaller than the value of its original <xref:System.Windows.Forms.Control.Size%2A> property, and it will account for the value of its <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7afb7-112">必要條件：</span><span class="sxs-lookup"><span data-stu-id="7afb7-112">Prerequisites</span></span>

<span data-ttu-id="7afb7-113">您將需要 Visual Studio 才能完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="7afb7-113">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="7afb7-114">建立專案</span><span class="sxs-lookup"><span data-stu-id="7afb7-114">Create the project</span></span>

1. <span data-ttu-id="7afb7-115">在 Visual Studio 中，建立名為 `LayoutExample`的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="7afb7-115">In Visual Studio, create a **Windows Application** project called `LayoutExample`.</span></span>

2. <span data-ttu-id="7afb7-116">在  **Windows Form 設計工具**中選取表單。</span><span class="sxs-lookup"><span data-stu-id="7afb7-116">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="set-margins-for-controls"></a><span data-ttu-id="7afb7-117">設定控制項的邊界</span><span class="sxs-lookup"><span data-stu-id="7afb7-117">Set margins for controls</span></span>

<span data-ttu-id="7afb7-118">您可以使用 <xref:System.Windows.Forms.Control.Margin%2A> 屬性來設定控制項之間的預設距離。</span><span class="sxs-lookup"><span data-stu-id="7afb7-118">You can set the default distance between your controls using the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span> <span data-ttu-id="7afb7-119">當您將控制項向右移動到另一個控制項時，您會看到對齊線，其中顯示兩個控制項的邊界。</span><span class="sxs-lookup"><span data-stu-id="7afb7-119">When you move a control close enough to another control, you will see a snapline that shows the margins for the two controls.</span></span> <span data-ttu-id="7afb7-120">您要移動的控制項也會貼齊邊界所定義的距離。</span><span class="sxs-lookup"><span data-stu-id="7afb7-120">The control you are moving will also snap to the distance defined by the margins.</span></span>

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a><span data-ttu-id="7afb7-121">使用 Margin 屬性排列表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="7afb7-121">Arrange controls on your form using the Margin property</span></span>

1. <span data-ttu-id="7afb7-122">將兩個 <xref:System.Windows.Forms.Button> 控制項從 [**工具箱**] 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="7afb7-122">Drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="7afb7-123">選取其中一個 <xref:System.Windows.Forms.Button> 控制項，然後將其移到另一個，直到幾乎觸及為止。</span><span class="sxs-lookup"><span data-stu-id="7afb7-123">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span>

   <span data-ttu-id="7afb7-124">觀察出現在其間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="7afb7-124">Observe the snapline that appears between them.</span></span> <span data-ttu-id="7afb7-125">這個距離是兩個控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 值的總和。</span><span class="sxs-lookup"><span data-stu-id="7afb7-125">This distance is the sum of the two controls' <xref:System.Windows.Forms.Control.Margin%2A> values.</span></span> <span data-ttu-id="7afb7-126">您要移動的控制項會貼齊到此距離。</span><span class="sxs-lookup"><span data-stu-id="7afb7-126">The control you are moving snaps to this distance.</span></span> <span data-ttu-id="7afb7-127">如需詳細資訊，請參閱[逐步解說：使用對齊線排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。</span><span class="sxs-lookup"><span data-stu-id="7afb7-127">For details, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

3. <span data-ttu-id="7afb7-128">在 [**屬性**] 視窗中展開 [<xref:System.Windows.Forms.Control.Margin%2A>] 專案，並將 <xref:System.Windows.Forms.Padding.All%2A> 屬性設定為**20**，以變更其中一個控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-128">Change the <xref:System.Windows.Forms.Control.Margin%2A> property of one of the controls by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to **20**.</span></span>

4. <span data-ttu-id="7afb7-129">選取其中一個 <xref:System.Windows.Forms.Button> 控制項，然後將它移到另一個控制項附近。</span><span class="sxs-lookup"><span data-stu-id="7afb7-129">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other.</span></span>

   <span data-ttu-id="7afb7-130">定義邊界值總和的對齊線會較長，且控制項會與其他控制項的距離相較之下。</span><span class="sxs-lookup"><span data-stu-id="7afb7-130">The snapline defining the sum of the margin values is longer and that the control snaps to a greater distance from the other control.</span></span>

5. <span data-ttu-id="7afb7-131">藉由展開 [**屬性**] 視窗中的 [<xref:System.Windows.Forms.Control.Margin%2A>] 專案，並將 [<xref:System.Windows.Forms.Padding.Top%2A>] 屬性設定為 [ **5**]，變更所選控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-131">Change the <xref:System.Windows.Forms.Control.Margin%2A> property of the selected control by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.Top%2A> property to **5**.</span></span>

6. <span data-ttu-id="7afb7-132">將選取的控制項移到另一個控制項底下，並觀察對齊線是否較短。</span><span class="sxs-lookup"><span data-stu-id="7afb7-132">Move the selected control below the other control and observe that the snapline is shorter.</span></span> <span data-ttu-id="7afb7-133">將選取的控制項移至另一個控制項的左邊，並觀察對齊線會保留步驟4中觀察到的值。</span><span class="sxs-lookup"><span data-stu-id="7afb7-133">Move the selected control to the left of the other control and observe that the snapline retains the value observed in step 4.</span></span>

7. <span data-ttu-id="7afb7-134">您可以將 <xref:System.Windows.Forms.Control.Margin%2A> 屬性的每個層面、<xref:System.Windows.Forms.Padding.Left%2A>、<xref:System.Windows.Forms.Padding.Top%2A>、<xref:System.Windows.Forms.Padding.Right%2A>、<xref:System.Windows.Forms.Padding.Bottom%2A>設定為不同的值，也可以使用 <xref:System.Windows.Forms.Padding.All%2A> 屬性將它們全部設定為相同的值。</span><span class="sxs-lookup"><span data-stu-id="7afb7-134">You can set each of the aspects of the <xref:System.Windows.Forms.Control.Margin%2A> property, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, to different values, or you can set them all to the same value with the <xref:System.Windows.Forms.Padding.All%2A> property.</span></span>

## <a name="set-padding-for-controls"></a><span data-ttu-id="7afb7-135">設定控制項的填補</span><span class="sxs-lookup"><span data-stu-id="7afb7-135">Set padding for controls</span></span>

<span data-ttu-id="7afb7-136">若要達到應用程式所需的精確版面配置，您的控制項通常會包含子控制項。</span><span class="sxs-lookup"><span data-stu-id="7afb7-136">To achieve the precise layout required for your application, your controls will often contain child controls.</span></span> <span data-ttu-id="7afb7-137">當您想要指定子控制項的框線與父控制項框線的鄰近處時，請使用父控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性搭配子控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-137">When you want to specify the proximity of the child control's border to the parent control's border, use the parent control's <xref:System.Windows.Forms.Control.Padding%2A> property in conjunction with the child control's <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span> <span data-ttu-id="7afb7-138"><xref:System.Windows.Forms.Control.Padding%2A> 屬性也可用來控制控制項內容的鄰近程度（例如，<xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性）到其框線。</span><span class="sxs-lookup"><span data-stu-id="7afb7-138">The <xref:System.Windows.Forms.Control.Padding%2A> property is also used to control the proximity of a control's content (for example, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property) to its borders.</span></span>

### <a name="arrange-controls-on-your-form-using-padding"></a><span data-ttu-id="7afb7-139">使用填補排列表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="7afb7-139">Arrange controls on your form using padding</span></span>

1. <span data-ttu-id="7afb7-140">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="7afb7-140">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="7afb7-141">將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值變更為**true**。</span><span class="sxs-lookup"><span data-stu-id="7afb7-141">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to **true**.</span></span>

3. <span data-ttu-id="7afb7-142">藉由展開 [**屬性**] 視窗中的 [<xref:System.Windows.Forms.Control.Padding%2A>] 專案，並將 [<xref:System.Windows.Forms.Padding.All%2A>] 屬性設定為 [ **5**]，來變更 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-142">Change the <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to **5**.</span></span>

   <span data-ttu-id="7afb7-143">控制項會展開以提供空間給新的填補。</span><span class="sxs-lookup"><span data-stu-id="7afb7-143">The control expands to provide room for the new padding.</span></span>

4. <span data-ttu-id="7afb7-144">從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="7afb7-144">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="7afb7-145">將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至 [<xref:System.Windows.Forms.GroupBox>] 控制項。</span><span class="sxs-lookup"><span data-stu-id="7afb7-145">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="7afb7-146">將 <xref:System.Windows.Forms.Button> 控制項定位，使其與 <xref:System.Windows.Forms.GroupBox> 控制項的右下角進行排清。</span><span class="sxs-lookup"><span data-stu-id="7afb7-146">Position the <xref:System.Windows.Forms.Button> control so it is flush with the lower-right corner of the <xref:System.Windows.Forms.GroupBox> control.</span></span>

   <span data-ttu-id="7afb7-147">觀察顯示為 <xref:System.Windows.Forms.Button> 控制項的對齊線會接近 <xref:System.Windows.Forms.GroupBox> 控制項的底和右框線。</span><span class="sxs-lookup"><span data-stu-id="7afb7-147">Observe the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="7afb7-148">這些對齊線會對應至 <xref:System.Windows.Forms.Button>的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-148">These snaplines correspond to the <xref:System.Windows.Forms.Control.Margin%2A> property of the <xref:System.Windows.Forms.Button>.</span></span>

5. <span data-ttu-id="7afb7-149">在 [**屬性**] 視窗中展開 <xref:System.Windows.Forms.Control.Padding%2A> 專案，並將 <xref:System.Windows.Forms.Padding.All%2A> 屬性設定為**20**，以變更 <xref:System.Windows.Forms.GroupBox> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-149">Change the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to **20**.</span></span>

6. <span data-ttu-id="7afb7-150">選取 <xref:System.Windows.Forms.GroupBox> 控制項內的 [<xref:System.Windows.Forms.Button>] 控制項，並將其移至 <xref:System.Windows.Forms.GroupBox>的中央。</span><span class="sxs-lookup"><span data-stu-id="7afb7-150">Select the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and move it toward the center of the <xref:System.Windows.Forms.GroupBox>.</span></span>

   <span data-ttu-id="7afb7-151">對齊線會與 <xref:System.Windows.Forms.GroupBox> 控制項的框線距離更遠。</span><span class="sxs-lookup"><span data-stu-id="7afb7-151">The snaplines appear at a greater distance from the borders of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="7afb7-152">這個距離是 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性和 <xref:System.Windows.Forms.GroupBox> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性的總和。</span><span class="sxs-lookup"><span data-stu-id="7afb7-152">This distance is the sum of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property and the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>

## <a name="size-controls-automatically"></a><span data-ttu-id="7afb7-153">自動調整控制項的大小</span><span class="sxs-lookup"><span data-stu-id="7afb7-153">Size controls automatically</span></span>

<span data-ttu-id="7afb7-154">在某些應用程式中，控制項的大小在執行時間不會與設計階段相同。</span><span class="sxs-lookup"><span data-stu-id="7afb7-154">In some applications, the size of a control will not be the same at run time as it was at design time.</span></span> <span data-ttu-id="7afb7-155">例如，可以從資料庫取得 <xref:System.Windows.Forms.Button> 控制項的文字，而且其長度不是事先知道的。</span><span class="sxs-lookup"><span data-stu-id="7afb7-155">The text of a <xref:System.Windows.Forms.Button> control, for example, may be taken from a database, and its length are not known in advance.</span></span>

<span data-ttu-id="7afb7-156">當 [<xref:System.Windows.Forms.Control.AutoSize%2A>] 屬性設定為 [`true`] 時，控制項本身的大小會調整為其內容。</span><span class="sxs-lookup"><span data-stu-id="7afb7-156">When the <xref:System.Windows.Forms.Control.AutoSize%2A> property is set to `true`, the control will size itself to its content.</span></span> <span data-ttu-id="7afb7-157">如需詳細資訊，請參閱[AutoSize 屬性總覽](autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7afb7-157">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a><span data-ttu-id="7afb7-158">使用 AutoSize 屬性排列表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="7afb7-158">Arrange controls on your form using the AutoSize property</span></span>

1. <span data-ttu-id="7afb7-159">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="7afb7-159">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="7afb7-160">將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值變更為**true**。</span><span class="sxs-lookup"><span data-stu-id="7afb7-160">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to **true**.</span></span>

3. <span data-ttu-id="7afb7-161">將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性變更為**此按鈕，其 Text 屬性會有一個長字串**。</span><span class="sxs-lookup"><span data-stu-id="7afb7-161">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to **This button has a long string for its Text property**.</span></span>

   <span data-ttu-id="7afb7-162">當您認可變更時，<xref:System.Windows.Forms.Button> 控制項會調整自己的大小，以符合新的文字。</span><span class="sxs-lookup"><span data-stu-id="7afb7-162">When you commit the change, the <xref:System.Windows.Forms.Button> control resizes itself to fit the new text.</span></span>

4. <span data-ttu-id="7afb7-163">將另一個 <xref:System.Windows.Forms.Button> 控制項從 [**工具箱**] 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="7afb7-163">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="7afb7-164">將 <xref:System.Windows.Forms.Button> 控制項的 [<xref:System.Windows.Forms.Control.Text%2A>] 屬性變更為 [**此按鈕的 Text 屬性具有長字串]。**</span><span class="sxs-lookup"><span data-stu-id="7afb7-164">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property.**"</span></span>

   <span data-ttu-id="7afb7-165">當您認可變更時，<xref:System.Windows.Forms.Button> 控制項不會自行調整大小，而是由控制項的右邊緣裁剪文字。</span><span class="sxs-lookup"><span data-stu-id="7afb7-165">When you commit the change, the <xref:System.Windows.Forms.Button> control does not resize itself, and the text is clipped by the right edge of the control.</span></span>

6. <span data-ttu-id="7afb7-166">藉由展開 [**屬性**] 視窗中的 [<xref:System.Windows.Forms.Control.Padding%2A>] 專案，並將 [<xref:System.Windows.Forms.Padding.All%2A>] 屬性設定為 [ **5**]，來變更 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-166">Change the <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to **5**.</span></span>

   <span data-ttu-id="7afb7-167">控制項內部的文字會在所有四側裁剪。</span><span class="sxs-lookup"><span data-stu-id="7afb7-167">The text in the control's interior is clipped on all four sides.</span></span>

7. <span data-ttu-id="7afb7-168">將 <xref:System.Windows.Forms.Button> 控制項的 [<xref:System.Windows.Forms.Control.AutoSize%2A>] 屬性變更為 [ **true**]。</span><span class="sxs-lookup"><span data-stu-id="7afb7-168">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to **true**.</span></span>

   <span data-ttu-id="7afb7-169"><xref:System.Windows.Forms.Button> 控制項會調整自己的大小，以包含整個字串。</span><span class="sxs-lookup"><span data-stu-id="7afb7-169">The <xref:System.Windows.Forms.Button> control resizes itself to encompass the entire string.</span></span> <span data-ttu-id="7afb7-170">此外，文字周圍已加入填補，導致 <xref:System.Windows.Forms.Button> 控制項展開四個方向。</span><span class="sxs-lookup"><span data-stu-id="7afb7-170">Also, padding has been added around the text, causing the <xref:System.Windows.Forms.Button> control to expand in all four directions.</span></span>

8. <span data-ttu-id="7afb7-171">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="7afb7-171">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="7afb7-172">將它放在表單右下角附近。</span><span class="sxs-lookup"><span data-stu-id="7afb7-172">Position it near the lower-right corner of the form.</span></span>

9. <span data-ttu-id="7afb7-173">將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值變更為**true**。</span><span class="sxs-lookup"><span data-stu-id="7afb7-173">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to **true**.</span></span>

10. <span data-ttu-id="7afb7-174">將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設定為 <xref:System.Windows.Forms.AnchorStyles.Right>、<xref:System.Windows.Forms.AnchorStyles.Bottom>。</span><span class="sxs-lookup"><span data-stu-id="7afb7-174">Set the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.</span></span>

11. <span data-ttu-id="7afb7-175">將 <xref:System.Windows.Forms.Button> 控制項的 [<xref:System.Windows.Forms.Control.Text%2A>] 屬性變更為 [**此按鈕的 Text 屬性具有長字串]。**</span><span class="sxs-lookup"><span data-stu-id="7afb7-175">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property.**"</span></span>

   <span data-ttu-id="7afb7-176">當您認可變更時，<xref:System.Windows.Forms.Button> 控制項會向左調整其本身的大小。</span><span class="sxs-lookup"><span data-stu-id="7afb7-176">When you commit the change, the <xref:System.Windows.Forms.Button> control resizes itself toward the left.</span></span> <span data-ttu-id="7afb7-177">一般來說，自動調整大小會增加控制項的大小，而其 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設定的方向相反。</span><span class="sxs-lookup"><span data-stu-id="7afb7-177">In general, automatic sizing will increase the size of a control in the direction opposite its <xref:System.Windows.Forms.Control.Anchor%2A> property setting.</span></span>

## <a name="autosize-and-autosizemode-properties"></a><span data-ttu-id="7afb7-178">AutoSize 和 AutoSizeMode 屬性</span><span class="sxs-lookup"><span data-stu-id="7afb7-178">AutoSize and AutoSizeMode properties</span></span>

 <span data-ttu-id="7afb7-179">某些控制項支援 `AutoSizeMode` 屬性，可讓您更精細地控制控制項的自動調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="7afb7-179">Some controls support the `AutoSizeMode` property, which gives you more fine-grained control over the automatic sizing behavior of a control.</span></span>

### <a name="use-the-autosizemode-property"></a><span data-ttu-id="7afb7-180">使用 AutoSizeMode 屬性</span><span class="sxs-lookup"><span data-stu-id="7afb7-180">Use the AutoSizeMode property</span></span>

1. <span data-ttu-id="7afb7-181">從 [工具箱] <xref:System.Windows.Forms.Panel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="7afb7-181">Drag a <xref:System.Windows.Forms.Panel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="7afb7-182">將 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值設定為**true**。</span><span class="sxs-lookup"><span data-stu-id="7afb7-182">Set the value of the <xref:System.Windows.Forms.Panel> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to **true**.</span></span>

3. <span data-ttu-id="7afb7-183">將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至 [<xref:System.Windows.Forms.Panel>] 控制項。</span><span class="sxs-lookup"><span data-stu-id="7afb7-183">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.Panel> control.</span></span>

4. <span data-ttu-id="7afb7-184">將 <xref:System.Windows.Forms.Button> 控制項放在 <xref:System.Windows.Forms.Panel> 控制項的右下角附近。</span><span class="sxs-lookup"><span data-stu-id="7afb7-184">Place the <xref:System.Windows.Forms.Button> control near the lower-right corner of the <xref:System.Windows.Forms.Panel> control.</span></span>

5. <span data-ttu-id="7afb7-185">選取 <xref:System.Windows.Forms.Panel> 控制項，並抓取右下角的調整大小控點。</span><span class="sxs-lookup"><span data-stu-id="7afb7-185">Select the <xref:System.Windows.Forms.Panel> control and grab the lower-right sizing handle.</span></span> <span data-ttu-id="7afb7-186">將 <xref:System.Windows.Forms.Panel> 控制項的大小調整為較大且較小。</span><span class="sxs-lookup"><span data-stu-id="7afb7-186">Resize the <xref:System.Windows.Forms.Panel> control to be larger and smaller.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7afb7-187">您可以自由地調整 <xref:System.Windows.Forms.Panel> 控制項的大小，但無法將其調整成小於 <xref:System.Windows.Forms.Button> 控制項右下角的位置。</span><span class="sxs-lookup"><span data-stu-id="7afb7-187">You can freely resize the <xref:System.Windows.Forms.Panel> control, but you cannot size it smaller than the position of the <xref:System.Windows.Forms.Button> control's lower-right corner.</span></span> <span data-ttu-id="7afb7-188">這個行為是由 `AutoSizeMode` 屬性的預設值所指定，這是 <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>。</span><span class="sxs-lookup"><span data-stu-id="7afb7-188">This behavior is specified by the default value of the `AutoSizeMode` property, which is <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.</span></span>

6. <span data-ttu-id="7afb7-189">將 <xref:System.Windows.Forms.Panel> 控制項的 `AutoSizeMode` 屬性值設定為 [<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>]。</span><span class="sxs-lookup"><span data-stu-id="7afb7-189">Set the value of the <xref:System.Windows.Forms.Panel> control's `AutoSizeMode` property to <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.</span></span>

   <span data-ttu-id="7afb7-190"><xref:System.Windows.Forms.Panel> 控制項的大小本身會包圍 <xref:System.Windows.Forms.Button> 控制項。</span><span class="sxs-lookup"><span data-stu-id="7afb7-190">The <xref:System.Windows.Forms.Panel> control sizes itself to surround the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="7afb7-191">您無法調整 <xref:System.Windows.Forms.Panel> 控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="7afb7-191">You cannot resize the <xref:System.Windows.Forms.Panel> control.</span></span>

7. <span data-ttu-id="7afb7-192">將 [<xref:System.Windows.Forms.Button>] 控制項拖曳至 [<xref:System.Windows.Forms.Panel>] 控制項的左上角。</span><span class="sxs-lookup"><span data-stu-id="7afb7-192">Drag the <xref:System.Windows.Forms.Button> control toward the upper-left corner of the <xref:System.Windows.Forms.Panel> control.</span></span>

   <span data-ttu-id="7afb7-193"><xref:System.Windows.Forms.Panel> 控制項會調整大小為 <xref:System.Windows.Forms.Button> 控制項的新位置。</span><span class="sxs-lookup"><span data-stu-id="7afb7-193">The <xref:System.Windows.Forms.Panel> control resizes to the <xref:System.Windows.Forms.Button> control's new position.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7afb7-194">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7afb7-194">Next steps</span></span>

<span data-ttu-id="7afb7-195">還有許多其他的版面配置功能，可讓您在 Windows Forms 應用程式中排列控制項。</span><span class="sxs-lookup"><span data-stu-id="7afb7-195">There are many other layout features for arranging controls in your Windows Forms applications.</span></span> <span data-ttu-id="7afb7-196">以下是一些您可能會嘗試的組合：</span><span class="sxs-lookup"><span data-stu-id="7afb7-196">Here are some combinations you might try:</span></span>

- <span data-ttu-id="7afb7-197">使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來建立表單。</span><span class="sxs-lookup"><span data-stu-id="7afb7-197">Build a form using a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="7afb7-198">如需詳細資訊，請參閱[逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="7afb7-198">For details, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span> <span data-ttu-id="7afb7-199">請嘗試變更 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值，以及其子控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7afb7-199">Try changing the values of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.Control.Padding%2A> property, as well as the <xref:System.Windows.Forms.Control.Margin%2A> property on its child controls.</span></span>

- <span data-ttu-id="7afb7-200">使用 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項嘗試相同的實驗。</span><span class="sxs-lookup"><span data-stu-id="7afb7-200">Try the same experiment using a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="7afb7-201">如需詳細資訊，請參閱[逐步解說：使用 FlowLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="7afb7-201">For details, see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).</span></span>

- <span data-ttu-id="7afb7-202">實驗在 <xref:System.Windows.Forms.Panel> 控制項中停駐子控制項。</span><span class="sxs-lookup"><span data-stu-id="7afb7-202">Experiment with docking child controls in a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="7afb7-203"><xref:System.Windows.Forms.Control.Padding%2A> 屬性是 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> 屬性的一般實現，而且您可以藉由將子控制項放在 <xref:System.Windows.Forms.Panel> 控制項中，並將子控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 [<xref:System.Windows.Forms.DockStyle.Fill>]，來滿足這種情況。</span><span class="sxs-lookup"><span data-stu-id="7afb7-203">The <xref:System.Windows.Forms.Control.Padding%2A> property is a more general realization of the <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> property, and you can satisfy yourself that this is the case by putting a child control in a <xref:System.Windows.Forms.Panel> control and setting the child control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="7afb7-204">將 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性設定為不同的值，並記下效果。</span><span class="sxs-lookup"><span data-stu-id="7afb7-204">Set the <xref:System.Windows.Forms.Panel> control's <xref:System.Windows.Forms.Control.Padding%2A> property to various values and note the effect.</span></span>

## <a name="see-also"></a><span data-ttu-id="7afb7-205">請參閱</span><span class="sxs-lookup"><span data-stu-id="7afb7-205">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [<span data-ttu-id="7afb7-206">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="7afb7-206">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="7afb7-207">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="7afb7-207">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="7afb7-208">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="7afb7-208">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="7afb7-209">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="7afb7-209">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
