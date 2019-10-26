---
title: 逐步解說：使用 Microsoft Expression Blend 建立按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 10342d97abc2e3c158f93171f5fe5cd560f9b7e4
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920260"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a><span data-ttu-id="d19da-102">逐步解說：使用 Microsoft Expression Blend 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="d19da-102">Walkthrough: Create a Button by Using Microsoft Expression Blend</span></span>

<span data-ttu-id="d19da-103">本逐步解說會逐步引導您使用 Microsoft Expression Blend 建立 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-103">This walkthrough steps you through the process of creating a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] customized button using Microsoft Expression Blend.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d19da-104">Microsoft Expression Blend 的運作方式是產生 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，然後進行編譯以進行可執行檔程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-104">Microsoft Expression Blend works by generating [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is then compiled to make the executable program.</span></span> <span data-ttu-id="d19da-105">如果您想要直接使用 XAML，還有另一個逐步解說，會使用 XAML 搭配 Visual Studio 而不是 Blend 來建立與此應用程式相同的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-105">If you would rather work with XAML directly, there is another walkthrough that creates the same application as this one using XAML with Visual Studio rather than Blend.</span></span> <span data-ttu-id="d19da-106">如需詳細資訊，請參閱[使用 XAML 建立按鈕](walkthrough-create-a-button-by-using-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="d19da-106">See [Create a Button by Using XAML](walkthrough-create-a-button-by-using-xaml.md) for more information.</span></span>

<span data-ttu-id="d19da-107">下圖顯示您將建立的自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-107">The following illustration shows the customized button that you will create.</span></span>

![您將建立的自訂按鈕](./media/custom-button-blend-intro.jpg)

## <a name="convert-a-shape-to-a-button"></a><span data-ttu-id="d19da-109">將圖形轉換成按鈕</span><span class="sxs-lookup"><span data-stu-id="d19da-109">Convert a Shape to a Button</span></span>

<span data-ttu-id="d19da-110">在本逐步解說的第一個部分中，您會建立自訂的按鈕外觀。</span><span class="sxs-lookup"><span data-stu-id="d19da-110">In the first part of this walkthrough you create the custom look of the custom button.</span></span> <span data-ttu-id="d19da-111">若要這樣做，您必須先將矩形轉換成按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-111">To do this, you first convert a rectangle to a button.</span></span> <span data-ttu-id="d19da-112">接著，您可以將其他圖形新增至按鈕的範本，以建立更複雜的 [尋找] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-112">You then add additional shapes to the template of the button, creating a more complex looking button.</span></span> <span data-ttu-id="d19da-113">為什麼無法以一般按鈕開始進行自訂？</span><span class="sxs-lookup"><span data-stu-id="d19da-113">Why not start with a regular button and customize it?</span></span> <span data-ttu-id="d19da-114">因為按鈕有您不需要的內建功能，針對自訂按鈕，以矩形開頭較容易。</span><span class="sxs-lookup"><span data-stu-id="d19da-114">Because a button has built-in functionality that you do not need; for custom buttons, it is easier to start with a rectangle.</span></span>

### <a name="to-create-a-new-project-in-expression-blend"></a><span data-ttu-id="d19da-115">在 Expression Blend 中建立新的專案</span><span class="sxs-lookup"><span data-stu-id="d19da-115">To create a new project in Expression Blend</span></span>

1. <span data-ttu-id="d19da-116">開始運算式 Blend。</span><span class="sxs-lookup"><span data-stu-id="d19da-116">Start Expression Blend.</span></span> <span data-ttu-id="d19da-117">（按一下 [**開始**]，指向 [**所有程式**]，指向 [ **microsoft 運算式**]，然後按一下 [ **microsoft expression Blend**]）。</span><span class="sxs-lookup"><span data-stu-id="d19da-117">(Click **Start**, point to **All Programs**, point to **Microsoft Expression**, and then click **Microsoft Expression Blend**.)</span></span>

2. <span data-ttu-id="d19da-118">視需要將應用程式最大化。</span><span class="sxs-lookup"><span data-stu-id="d19da-118">Maximize the application if needed.</span></span>

3. <span data-ttu-id="d19da-119">按一下 [檔案] 功能表上的 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="d19da-119">On the **File** menu, click **New Project**.</span></span>

4. <span data-ttu-id="d19da-120">選取 **[標準應用程式（.exe）** ]。</span><span class="sxs-lookup"><span data-stu-id="d19da-120">Select **Standard Application (.exe)**.</span></span>

5. <span data-ttu-id="d19da-121">將專案命名為 `CustomButton`，然後按 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d19da-121">Name the project `CustomButton` and press **OK**.</span></span>

<span data-ttu-id="d19da-122">此時，您會有一個空白的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="d19da-122">At this point you have a blank [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] project.</span></span> <span data-ttu-id="d19da-123">您可以按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-123">You can press F5 to run the application.</span></span> <span data-ttu-id="d19da-124">如您所預期，應用程式只會包含一個空白視窗。</span><span class="sxs-lookup"><span data-stu-id="d19da-124">As you might expect, the application consists of only a blank window.</span></span> <span data-ttu-id="d19da-125">接下來，您要建立一個圓角矩形，並將它轉換成一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-125">Next, you create a rounded rectangle and convert it into a button.</span></span>

### <a name="to-convert-a-rectangle-to-a-button"></a><span data-ttu-id="d19da-126">將矩形轉換成按鈕</span><span class="sxs-lookup"><span data-stu-id="d19da-126">To convert a Rectangle to a Button</span></span>

1. <span data-ttu-id="d19da-127">**將視窗背景屬性設定為黑色：** 選取 [] 視窗，按一下 [**屬性]** 索引標籤，然後將 [<xref:System.Windows.Controls.Control.Background%2A>] 屬性設定為 [`Black`]。</span><span class="sxs-lookup"><span data-stu-id="d19da-127">**Set the Window Background property to black:** Select the Window, click the **Properties Tab**, and set the <xref:System.Windows.Controls.Control.Background%2A> property to `Black`.</span></span>

    ![將按鈕的背景設定為黑色的方式](./media/custom-button-blend-changebackground.png)

2. <span data-ttu-id="d19da-129">在**視窗上繪製大約按鈕大小的矩形：** 選取左側工具面板上的 [矩形] 工具，然後將矩形拖曳至視窗。</span><span class="sxs-lookup"><span data-stu-id="d19da-129">**Draw a rectangle approximately the size of a button on the Window:** Select the rectangle tool on the left-hand tool panel and drag the rectangle onto the Window.</span></span>

    ![繪製矩形的方式](./media/custom-button-blend-drawrect.png)

3. <span data-ttu-id="d19da-131">**進位矩形的角落：** 請拖曳矩形的控制點，或直接設定 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> 和 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d19da-131">**Round out the corners of the rectangle:** Either drag the control points of the rectangle or directly set the <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="d19da-132">將 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> 和 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 的值設定為20。</span><span class="sxs-lookup"><span data-stu-id="d19da-132">Set the values of <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> to 20.</span></span>

    ![將矩形的邊角設為圓角的方式](./media/custom-button-blend-roundcorners.png)

4. <span data-ttu-id="d19da-134">**將矩形變更為按鈕：** 選取矩形。</span><span class="sxs-lookup"><span data-stu-id="d19da-134">**Change the rectangle into a button:** Select the rectangle.</span></span> <span data-ttu-id="d19da-135">在 [**工具**] 功能表上，按一下 [**建立] 按鈕**。</span><span class="sxs-lookup"><span data-stu-id="d19da-135">On the **Tools** menu, click **Make Button**.</span></span>

    ![在按鈕中繪製圖案的方式](./media/custom-button-blend-makebutton.png)

5. <span data-ttu-id="d19da-137">**指定樣式/範本的範圍：** 如下所示的對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d19da-137">**Specify the scope of the style/template:** A dialog box like the following appears.</span></span>

    ![建立樣式資源對話方塊](./media/custom-button-blend-makebutton2.gif)

    <span data-ttu-id="d19da-139">針對 **[資源名稱（金鑰）** ]，選取 [**全部**套用]。</span><span class="sxs-lookup"><span data-stu-id="d19da-139">For **Resource name (Key)**, select **Apply to all**.</span></span>  <span data-ttu-id="d19da-140">這會使產生的樣式和按鈕範本適用于所有按鈕的物件。</span><span class="sxs-lookup"><span data-stu-id="d19da-140">This will make the resulting style and button template apply to all objects that are buttons.</span></span> <span data-ttu-id="d19da-141">針對 [**定義于] 中**，選取 [**應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="d19da-141">For **Define in**, select **Application**.</span></span> <span data-ttu-id="d19da-142">這會使產生的樣式和按鈕範本具有整個應用程式的範圍。</span><span class="sxs-lookup"><span data-stu-id="d19da-142">This will make the resulting style and button template have scope over the entire application.</span></span> <span data-ttu-id="d19da-143">當您設定這兩個方塊中的值時，按鈕樣式和範本會套用至整個應用程式內的所有按鈕，而且您在應用程式中建立的任何按鈕預設都會使用此範本。</span><span class="sxs-lookup"><span data-stu-id="d19da-143">When you set the values in these two boxes, the button style and template apply to all buttons within the entire application and any button you create in the application will, by default, use this template.</span></span>

## <a name="edit-the-button-template"></a><span data-ttu-id="d19da-144">編輯按鈕範本</span><span class="sxs-lookup"><span data-stu-id="d19da-144">Edit the Button Template</span></span>

<span data-ttu-id="d19da-145">您現在已有一個已變更為按鈕的矩形。</span><span class="sxs-lookup"><span data-stu-id="d19da-145">You now have a rectangle that has been changed to a button.</span></span> <span data-ttu-id="d19da-146">在本節中，您將修改按鈕的範本，並進一步自訂其外觀。</span><span class="sxs-lookup"><span data-stu-id="d19da-146">In this section, you'll modify the template of the button and further customize how it looks.</span></span>

### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a><span data-ttu-id="d19da-147">若要編輯按鈕範本以變更按鈕外觀</span><span class="sxs-lookup"><span data-stu-id="d19da-147">To edit the button template to change the button appearance</span></span>

1. <span data-ttu-id="d19da-148">**進入 [編輯範本] 視圖：** 若要進一步自訂按鈕的外觀，我們需要編輯 [按鈕] 範本。</span><span class="sxs-lookup"><span data-stu-id="d19da-148">**Go into edit template view:** To further customize the look of our button, we need to edit the button template.</span></span> <span data-ttu-id="d19da-149">當我們將矩形轉換成按鈕時，就會建立此範本。</span><span class="sxs-lookup"><span data-stu-id="d19da-149">This template was created when we converted the rectangle into a button.</span></span> <span data-ttu-id="d19da-150">若要編輯按鈕範本，請以滑鼠右鍵按一下按鈕，然後依序選取 [**編輯控制群組件（範本）** ] 和 [**編輯範本**]。</span><span class="sxs-lookup"><span data-stu-id="d19da-150">To edit the button template, right-click the button and select **Edit Control Parts (Template)** and then **Edit Template**.</span></span>

    ![編輯範本的方式](./media/custom-button-blend-edittemplate.jpg)

    <span data-ttu-id="d19da-152">在 [範本編輯器] 中，請注意，按鈕現在會分成 <xref:System.Windows.Shapes.Rectangle> 和 <xref:System.Windows.Controls.ContentPresenter>。</span><span class="sxs-lookup"><span data-stu-id="d19da-152">In the template editor, notice that the button is now separated into a <xref:System.Windows.Shapes.Rectangle> and the <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="d19da-153"><xref:System.Windows.Controls.ContentPresenter> 可用來呈現按鈕內的內容（例如，字串 "Button"）。</span><span class="sxs-lookup"><span data-stu-id="d19da-153">The <xref:System.Windows.Controls.ContentPresenter> is used to present content within the button (for example, the string "Button").</span></span> <span data-ttu-id="d19da-154">矩形和 <xref:System.Windows.Controls.ContentPresenter> 都是在 <xref:System.Windows.Controls.Grid>內進行配置。</span><span class="sxs-lookup"><span data-stu-id="d19da-154">Both the rectangle and <xref:System.Windows.Controls.ContentPresenter> are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

    ![矩形呈現外觀中的元件](./media/custom-button-blend-templatepanel.png)

2. <span data-ttu-id="d19da-156">**變更範本元件的名稱：** 以滑鼠右鍵按一下範本清查中的矩形，將 <xref:System.Windows.Shapes.Rectangle> 名稱從 "[Rectangle]" 變更為 "outerRectangle"，並將 "[ContentPresenter]" 變更為 "myContentPresenter"。</span><span class="sxs-lookup"><span data-stu-id="d19da-156">**Change the names of the template components:** Right-click the rectangle in the template inventory, change the <xref:System.Windows.Shapes.Rectangle> name from "[Rectangle]" to "outerRectangle", and change "[ContentPresenter]" to "myContentPresenter".</span></span>

    ![重新命名範本之元件的方式](./media/custom-button-blend-renamecomponents.png)

3. <span data-ttu-id="d19da-158">**修改矩形，使其在內部（例如環圈圖）為空白：** 選取 [ **outerRectangle** ]，並將 <xref:System.Windows.Shapes.Shape.Fill%2A> 設定為 [透明]，並 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 為5。</span><span class="sxs-lookup"><span data-stu-id="d19da-158">**Alter the rectangle so that it is empty inside (like a donut):** Select **outerRectangle** and set <xref:System.Windows.Shapes.Shape.Fill%2A> to "Transparent" and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> to 5.</span></span>

    ![建立矩形空白的方式](./media/custom-button-blend-changerectproperties.png)

    <span data-ttu-id="d19da-160">然後將 [<xref:System.Windows.Shapes.Shape.Stroke%2A>] 設定為範本會是任何內容的色彩。</span><span class="sxs-lookup"><span data-stu-id="d19da-160">Then set the <xref:System.Windows.Shapes.Shape.Stroke%2A> to the color of whatever the template will be.</span></span> <span data-ttu-id="d19da-161">若要這麼做，請按一下 [**筆觸**] 旁的小白色方塊，選取 [ **CustomExpression**]，然後在對話方塊中輸入 "{TemplateBinding Background}"。</span><span class="sxs-lookup"><span data-stu-id="d19da-161">To do this, click the small white box next to **Stroke**, select **CustomExpression**, and type "{TemplateBinding Background}" in the dialog box.</span></span>

    ![設定範本色彩用法的方式](./media/custom-button-blend-templatestroke.png)

4. <span data-ttu-id="d19da-163">**建立內部矩形：** 現在，建立另一個矩形（將其命名為 "innerRectangle"），並將其在**outerRectangle**內對稱放置。</span><span class="sxs-lookup"><span data-stu-id="d19da-163">**Create an inner rectangle:** Now, create another rectangle (name it "innerRectangle") and position it symmetrically on the inside of **outerRectangle** .</span></span> <span data-ttu-id="d19da-164">針對這種工作，您可能會想要縮放，使編輯區域中的按鈕變大。</span><span class="sxs-lookup"><span data-stu-id="d19da-164">For this kind of work, you will probably want to zoom to make the button larger in the editing area.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d19da-165">您的矩形看起來可能與圖中的不同（例如，它可能有圓角）。</span><span class="sxs-lookup"><span data-stu-id="d19da-165">Your rectangle might look different than the one in the figure (for example, it might have rounded corners).</span></span>

    ![在某個矩形內部建立另一個矩形的方式](./media/custom-button-blend-innerrectangleproperties.png)

5. <span data-ttu-id="d19da-167">**將 ContentPresenter 移至頂端：** 此時，可能不會再顯示文字「按鈕」。</span><span class="sxs-lookup"><span data-stu-id="d19da-167">**Move ContentPresenter to the top:** At this point, it is possible that the text "Button" will not be visible any longer.</span></span> <span data-ttu-id="d19da-168">如果這樣做，這是因為**innerRectangle**是在**myContentPresenter**的頂端。</span><span class="sxs-lookup"><span data-stu-id="d19da-168">If this is so, this is because **innerRectangle** is on top of the **myContentPresenter**.</span></span> <span data-ttu-id="d19da-169">若要修正此問題，請將**myContentPresenter**拖曳到 [ **innerRectangle**] 下方。</span><span class="sxs-lookup"><span data-stu-id="d19da-169">To fix this, drag **myContentPresenter** below **innerRectangle**.</span></span> <span data-ttu-id="d19da-170">重新置放矩形和**myContentPresenter** ，看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="d19da-170">Reposition rectangles and **myContentPresenter** to look similar to below.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d19da-171">或者，您也可以用滑鼠右鍵按一下**myContentPresenter** ，然後按 [**向前傳送**]，將它放在最上層。</span><span class="sxs-lookup"><span data-stu-id="d19da-171">Alternatively, you can also position **myContentPresenter** on top by right-clicking it and pressing **Send Forward**.</span></span>

    ![將某個按鈕移至另一個按鈕上的方式](./media/custom-button-blend-innerrectangle2.png)

6. <span data-ttu-id="d19da-173">**變更 innerRectangle 的外觀：** 將 [<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>]、[<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>] 和 [<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>] 值設定為20。</span><span class="sxs-lookup"><span data-stu-id="d19da-173">**Change the look of innerRectangle:** Set the <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> values to 20.</span></span> <span data-ttu-id="d19da-174">此外，使用自訂表格達式 "{TemplateBinding Background}" 將 <xref:System.Windows.Shapes.Shape.Fill%2A> 設定為範本的背景，並將 <xref:System.Windows.Shapes.Shape.Stroke%2A> 設定為「透明」。</span><span class="sxs-lookup"><span data-stu-id="d19da-174">In addition, set the <xref:System.Windows.Shapes.Shape.Fill%2A> to the background of the template using the custom expression "{TemplateBinding Background}" ) and set <xref:System.Windows.Shapes.Shape.Stroke%2A> to "transparent".</span></span> <span data-ttu-id="d19da-175">請注意， **innerRectangle**的 <xref:System.Windows.Shapes.Shape.Fill%2A> 和 <xref:System.Windows.Shapes.Shape.Stroke%2A> 設定與**outerRectangle**相反。</span><span class="sxs-lookup"><span data-stu-id="d19da-175">Notice that the settings for the <xref:System.Windows.Shapes.Shape.Fill%2A> and <xref:System.Windows.Shapes.Shape.Stroke%2A> of **innerRectangle** are the opposite of those for **outerRectangle**.</span></span>

    ![變更矩形外觀的方式](./media/custom-button-blend-glassrectangleproperties1.png)

7. <span data-ttu-id="d19da-177">**在頂端新增玻璃層：** 自訂按鈕外觀的最後一項是在頂端新增玻璃圖層。</span><span class="sxs-lookup"><span data-stu-id="d19da-177">**Add a glass layer on top:** The final piece of customizing the look of the button is to add a glass layer on top.</span></span> <span data-ttu-id="d19da-178">這個半透明層是由第三個矩形所組成。</span><span class="sxs-lookup"><span data-stu-id="d19da-178">This glass layer consists of a third rectangle.</span></span> <span data-ttu-id="d19da-179">因為玻璃會涵蓋整個按鈕，所以半透明矩形在**outerRectangle**的維度中類似。</span><span class="sxs-lookup"><span data-stu-id="d19da-179">Because the glass will cover the entire button, the glass rectangle is similar in dimensions to the **outerRectangle**.</span></span> <span data-ttu-id="d19da-180">因此，只要製作**outerRectangle**的複本，即可建立矩形。</span><span class="sxs-lookup"><span data-stu-id="d19da-180">Therefore, create the rectangle by simply making a copy of the **outerRectangle**.</span></span> <span data-ttu-id="d19da-181">反白顯示**outerRectangle** ，並使用 Ctrl + C 和 Ctrl + V 建立複本。</span><span class="sxs-lookup"><span data-stu-id="d19da-181">Highlight **outerRectangle** and use CTRL+C and CTRL+V to make a copy.</span></span> <span data-ttu-id="d19da-182">將此新矩形命名為 "glassCube"。</span><span class="sxs-lookup"><span data-stu-id="d19da-182">Name this new rectangle "glassCube".</span></span>

8. <span data-ttu-id="d19da-183">視**需要重新置放 glassCube：** 如果**glassCube**尚未定位，使其涵蓋整個按鈕，請將其拖曳至 [位置]。</span><span class="sxs-lookup"><span data-stu-id="d19da-183">**Reposition glassCube if necessary:** If **glassCube** is not already positioned so that it covers the entire button, drag it into position.</span></span>

9. <span data-ttu-id="d19da-184">**提供 glassCube 的圖形與 outerRectangle 稍微不同：** 變更**glassCube**的屬性。</span><span class="sxs-lookup"><span data-stu-id="d19da-184">**Give glassCube a slightly different shape than outerRectangle:** Change the properties of **glassCube**.</span></span> <span data-ttu-id="d19da-185">一開始先將 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> 和 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 屬性變更為10，並將 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 為2。</span><span class="sxs-lookup"><span data-stu-id="d19da-185">Start off by changing the <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties to 10 and the <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> to 2.</span></span>

    ![glassCube 的外觀設定](./media/custom-button-blend-glasscubeappearance.gif)

10. <span data-ttu-id="d19da-187">**讓 glassCube 看起來像玻璃：** 使用75% 不透明的線性漸層，將 <xref:System.Windows.Shapes.Shape.Fill%2A> 設定為 glassy 的外觀，並將色彩白色和透明的寬度替換為接近平均間隔的6。</span><span class="sxs-lookup"><span data-stu-id="d19da-187">**Make glassCube look like glass:** Set the <xref:System.Windows.Shapes.Shape.Fill%2A> to a glassy look by  using a linear gradient that is 75% opaque and alternates between the color White and Transparent over 6 approximately evenly spaced intervals.</span></span> <span data-ttu-id="d19da-188">這是要設定漸層停駐點的目標：</span><span class="sxs-lookup"><span data-stu-id="d19da-188">This is what to set the gradient stops to:</span></span>

    - <span data-ttu-id="d19da-189">漸層停駐點1：具有 Alpha 值75% 的白色</span><span class="sxs-lookup"><span data-stu-id="d19da-189">Gradient Stop 1: White with Alpha value of 75%</span></span>

    - <span data-ttu-id="d19da-190">梯度停駐2：透明</span><span class="sxs-lookup"><span data-stu-id="d19da-190">Gradient Stop 2: Transparent</span></span>

    - <span data-ttu-id="d19da-191">漸層停駐點3：具有 Alpha 值75% 的白色</span><span class="sxs-lookup"><span data-stu-id="d19da-191">Gradient Stop 3: White with Alpha value of 75%</span></span>

    - <span data-ttu-id="d19da-192">梯度停駐4：透明</span><span class="sxs-lookup"><span data-stu-id="d19da-192">Gradient Stop 4: Transparent</span></span>

    - <span data-ttu-id="d19da-193">漸層停駐點5：具有 Alpha 值75% 的白色</span><span class="sxs-lookup"><span data-stu-id="d19da-193">Gradient Stop 5: White with Alpha value of 75%</span></span>

    - <span data-ttu-id="d19da-194">漸層停駐點6：透明</span><span class="sxs-lookup"><span data-stu-id="d19da-194">Gradient Stop 6: Transparent</span></span>

    <span data-ttu-id="d19da-195">這會建立「波浪」玻璃外觀。</span><span class="sxs-lookup"><span data-stu-id="d19da-195">This creates a "wavy" glass look.</span></span>

    ![看起來像玻璃的矩形](./media/custom-button-blend-glassrectangleproperties2.png)

11. <span data-ttu-id="d19da-197">**隱藏半透明層：** 現在您已看到 glassy 圖層的樣子，請移至 [**屬性] 面板**的 [**外觀] 窗格**，並將不透明度設定為0% 以隱藏它。</span><span class="sxs-lookup"><span data-stu-id="d19da-197">**Hide the glass layer:** Now that you see what the glassy layer looks like, go into the **Appearance pane** of the **Properties panel** and set the Opacity to 0% to hide it.</span></span> <span data-ttu-id="d19da-198">在前面的章節中，我們將使用屬性觸發程式和事件來顯示及操作半透明層。</span><span class="sxs-lookup"><span data-stu-id="d19da-198">In the sections ahead, we'll use property triggers and events to show and manipulate the glass layer.</span></span>

    ![隱藏玻璃矩形的方式](./media/custom-button-glassrectangleproperties3.gif)

## <a name="customize-the-button-behavior"></a><span data-ttu-id="d19da-200">自訂按鈕行為</span><span class="sxs-lookup"><span data-stu-id="d19da-200">Customize the Button Behavior</span></span>

<span data-ttu-id="d19da-201">此時，您已藉由編輯範本的方式來自訂按鈕的呈現，但是按鈕不會回應使用者動作，因為一般按鈕會發生（例如，變更滑鼠停留時的外觀、接收焦點，然後按一下）。接下來的兩個程式示範如何在 [自訂] 按鈕中建立像這樣的行為。</span><span class="sxs-lookup"><span data-stu-id="d19da-201">At this point, you have customized the presentation of the button by editing its template, but the button does not react to user actions as typical buttons do (for example, changing appearance upon mouse-over, receiving focus, and clicking.) The next two procedures show how to build behaviors like these into the custom button.</span></span> <span data-ttu-id="d19da-202">我們會從簡單的屬性觸發程式開始，然後新增事件觸發程式和動畫。</span><span class="sxs-lookup"><span data-stu-id="d19da-202">We'll start with simple property triggers, and then add event triggers and animations.</span></span>

### <a name="to-set-property-triggers"></a><span data-ttu-id="d19da-203">若要設定屬性觸發程式</span><span class="sxs-lookup"><span data-stu-id="d19da-203">To set property triggers</span></span>

1. <span data-ttu-id="d19da-204">**建立新的屬性觸發程式：** 選取**glassCube**後，按一下 [**觸發**程式] 面板中的 [ **+ 屬性**] （請參閱下一個步驟後面的圖表）。</span><span class="sxs-lookup"><span data-stu-id="d19da-204">**Create a new property trigger:** With **glassCube** selected, click **+ Property** in the **Triggers** panel (see the figure that follows the next step).</span></span> <span data-ttu-id="d19da-205">這會建立具有預設屬性觸發程式的屬性觸發程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-205">This creates a property trigger with a default property trigger.</span></span>

2. <span data-ttu-id="d19da-206">將**System.windows.uielement.ismouseover 設為觸發程式所使用的屬性：** 將屬性變更為 <xref:System.Windows.UIElement.IsMouseOver%2A>。</span><span class="sxs-lookup"><span data-stu-id="d19da-206">**Make IsMouseOver the property used by the trigger:** Change the property to <xref:System.Windows.UIElement.IsMouseOver%2A>.</span></span> <span data-ttu-id="d19da-207">這會讓屬性觸發程式在 `true` <xref:System.Windows.UIElement.IsMouseOver%2A> 屬性時啟動（當使用者指向具有滑鼠的按鈕時）。</span><span class="sxs-lookup"><span data-stu-id="d19da-207">This makes the property trigger activate when the <xref:System.Windows.UIElement.IsMouseOver%2A> property is `true` (when the user points to the button with the mouse).</span></span>

    ![對屬性設定觸發程序的方式](./media/custom-button-blend-ismousedoverpropertytrigger.png)

3. <span data-ttu-id="d19da-209">**System.windows.uielement.ismouseover 會觸發 glassCube 的100% 不透明度：** 請注意，**觸發程式記錄是 on** （請參閱上圖）。</span><span class="sxs-lookup"><span data-stu-id="d19da-209">**IsMouseOver triggers opacity of 100% for glassCube:** Notice that the **Trigger recording is on** (see the preceding figure).</span></span> <span data-ttu-id="d19da-210">這表示當您在錄製時對**glassCube**的屬性值所做的任何變更，都會成為 `true`<xref:System.Windows.UIElement.IsMouseOver%2A> 時所發生的動作。</span><span class="sxs-lookup"><span data-stu-id="d19da-210">This means that any changes you make to the property values of **glassCube** while recording is on will become an action that takes place when <xref:System.Windows.UIElement.IsMouseOver%2A> is `true`.</span></span> <span data-ttu-id="d19da-211">錄製時，請將**glassCube**的 <xref:System.Windows.UIElement.Opacity%2A> 變更為100%。</span><span class="sxs-lookup"><span data-stu-id="d19da-211">While recording, change the <xref:System.Windows.UIElement.Opacity%2A> of **glassCube** to 100%.</span></span>

    ![設定按鈕不透明度的方式](./media/custom-button-blend-ismousedoverpropertytrigger2.gif)

    <span data-ttu-id="d19da-213">您現在已建立您的第一個屬性觸發程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-213">You have now created your first property trigger.</span></span> <span data-ttu-id="d19da-214">請注意，編輯器的 [觸發程式]**面板**已記錄變更為100% 的 <xref:System.Windows.UIElement.Opacity%2A>。</span><span class="sxs-lookup"><span data-stu-id="d19da-214">Notice that the **Triggers panel** of the editor has recorded the <xref:System.Windows.UIElement.Opacity%2A> being changed to 100%.</span></span>

    ![「觸發程序」面板](./media/custom-button-blend-propertytriggerinfo.png)

    <span data-ttu-id="d19da-216">按 F5 鍵執行應用程式，並將滑鼠指標移至按鈕上方或下方。</span><span class="sxs-lookup"><span data-stu-id="d19da-216">Press F5 to run the application, and move the mouse pointer over and off the button.</span></span> <span data-ttu-id="d19da-217">當您將滑鼠停留在按鈕上時，您應該會看到玻璃層出現，並在指標離開時消失。</span><span class="sxs-lookup"><span data-stu-id="d19da-217">You should see the glass layer appear when you mouse-over the button and disappear when the pointer leaves.</span></span>

4. <span data-ttu-id="d19da-218">**System.windows.uielement.ismouseover 觸發程式筆觸值變更：** 讓我們將一些其他動作與 <xref:System.Windows.UIElement.IsMouseOver%2A> 觸發程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="d19da-218">**IsMouseOver triggers stroke value change:** Let's associate some other actions with the <xref:System.Windows.UIElement.IsMouseOver%2A> trigger.</span></span> <span data-ttu-id="d19da-219">錄製繼續時，請將您的選取範圍從**glassCube**切換到**outerRectangle**。</span><span class="sxs-lookup"><span data-stu-id="d19da-219">While recording continues, switch your selection from **glassCube** to **outerRectangle**.</span></span> <span data-ttu-id="d19da-220">然後將**outerRectangle**的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 設定為 "{DynamicResource {x:Static SystemColors. HighlightBrushKey}}" 的自訂表格達式。</span><span class="sxs-lookup"><span data-stu-id="d19da-220">Then set the <xref:System.Windows.Shapes.Shape.Stroke%2A> of **outerRectangle** to the custom expression of "{DynamicResource {x:Static SystemColors.HighlightBrushKey}}".</span></span> <span data-ttu-id="d19da-221">這會將 <xref:System.Windows.Shapes.Shape.Stroke%2A> 設定為按鈕所使用的一般醒目提示色彩。</span><span class="sxs-lookup"><span data-stu-id="d19da-221">This sets the <xref:System.Windows.Shapes.Shape.Stroke%2A> to the typical highlight color used by buttons.</span></span> <span data-ttu-id="d19da-222">按 F5 鍵可查看滑鼠停留在按鈕上的效果。</span><span class="sxs-lookup"><span data-stu-id="d19da-222">Press F5 to see the effect when you mouse over the button.</span></span>

    ![將筆劃設定為醒目提示色彩的方式](./media/custom-button-blend-ismousedoverpropertytrigger3.png)

5. <span data-ttu-id="d19da-224">**System.windows.uielement.ismouseover 會觸發模糊的文字：** 讓我們將另一個動作與 <xref:System.Windows.UIElement.IsMouseOver%2A> 屬性觸發程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="d19da-224">**IsMouseOver triggers blurry text:** Let's associate one more action to the <xref:System.Windows.UIElement.IsMouseOver%2A> property trigger.</span></span> <span data-ttu-id="d19da-225">當玻璃出現在螢幕上時，讓按鈕的內容看起來有點模糊。</span><span class="sxs-lookup"><span data-stu-id="d19da-225">Make the content of the button appear a little blurry when the glass appears over it.</span></span> <span data-ttu-id="d19da-226">若要這麼做，我們可以將模糊 <xref:System.Windows.Media.Effects.BitmapEffect> 套用至 <xref:System.Windows.Controls.ContentPresenter> （**myContentPresenter**）。</span><span class="sxs-lookup"><span data-stu-id="d19da-226">To do this, we can apply a blur <xref:System.Windows.Media.Effects.BitmapEffect> to the <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).</span></span>

    ![將按鈕內容設定為模糊的方式](./media/custom-button-blend-propertytriggerwithbitmapeffect.png)

    > [!NOTE]
    > <span data-ttu-id="d19da-228">若要將 [**屬性] 面板**傳回給搜尋 <xref:System.Windows.Media.Effects.BitmapEffect>之前的內容，請清除 [**搜尋**] 方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="d19da-228">To return the **Properties panel** back to what it was before you did the search for <xref:System.Windows.Media.Effects.BitmapEffect>, clear the text from the **Search box**.</span></span>

    <span data-ttu-id="d19da-229">此時，我們使用了屬性觸發程式與數個相關聯的動作，在滑鼠指標進入和離開按鈕區域時，建立反白顯示的行為。</span><span class="sxs-lookup"><span data-stu-id="d19da-229">At this point, we have used a property trigger with several associated actions to create highlighting behavior for when the mouse pointer enters and leaves the button area.</span></span> <span data-ttu-id="d19da-230">按鈕的另一個一般行為是反白顯示焦點（如同按一下之後）。</span><span class="sxs-lookup"><span data-stu-id="d19da-230">Another typical behavior for a button is to highlight when it has focus (as after it is clicked).</span></span> <span data-ttu-id="d19da-231">我們可以新增 <xref:System.Windows.UIElement.IsFocused%2A> 屬性的另一個屬性觸發程式來加入這類行為。</span><span class="sxs-lookup"><span data-stu-id="d19da-231">We can add such behavior by adding another property trigger for the <xref:System.Windows.UIElement.IsFocused%2A> property.</span></span>

6. <span data-ttu-id="d19da-232">**建立 IsFocused 的屬性觸發程式：** 使用與 <xref:System.Windows.UIElement.IsMouseOver%2A> 相同的程式（請參閱本節的第一個步驟），為 <xref:System.Windows.UIElement.IsFocused%2A> 屬性建立另一個屬性觸發程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-232">**Create property trigger for IsFocused:** Using the same procedure as for <xref:System.Windows.UIElement.IsMouseOver%2A> (see the first step of this section), create another property trigger for the <xref:System.Windows.UIElement.IsFocused%2A> property.</span></span> <span data-ttu-id="d19da-233">當**觸發程式記錄為 on**時，請將下列動作新增至觸發程式：</span><span class="sxs-lookup"><span data-stu-id="d19da-233">While **Trigger recording is on**, add the following actions to the trigger:</span></span>

    - <span data-ttu-id="d19da-234">**glassCube**取得100% 的 <xref:System.Windows.UIElement.Opacity%2A>。</span><span class="sxs-lookup"><span data-stu-id="d19da-234">**glassCube** gets an <xref:System.Windows.UIElement.Opacity%2A> of 100%.</span></span>

    - <span data-ttu-id="d19da-235">**outerRectangle**會取得 "{DynamicResource {x:Static SystemColors. HighlightBrushKey}}" 的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 自訂表格達式值。</span><span class="sxs-lookup"><span data-stu-id="d19da-235">**outerRectangle** gets a <xref:System.Windows.Shapes.Shape.Stroke%2A> custom expression value of "{DynamicResource {x:Static SystemColors.HighlightBrushKey}}".</span></span>

<span data-ttu-id="d19da-236">在本逐步解說中的最後一個步驟中，我們會將動畫新增至按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-236">As the final step in this walkthrough, we will add animations to the button.</span></span> <span data-ttu-id="d19da-237">這些動畫將由事件觸發，具體而言，就是 <xref:System.Windows.UIElement.MouseEnter> 和 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="d19da-237">These animations will be triggered by events—specifically, the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events.</span></span>

### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a><span data-ttu-id="d19da-238">使用事件觸發程式和動畫來新增互動性</span><span class="sxs-lookup"><span data-stu-id="d19da-238">To use event triggers and animations to add interactivity</span></span>

1. <span data-ttu-id="d19da-239">**建立 MouseEnter 事件觸發程式：** 加入新的事件觸發程式，然後選取 [<xref:System.Windows.UIElement.MouseEnter>] 做為要在觸發程式中使用的事件。</span><span class="sxs-lookup"><span data-stu-id="d19da-239">**Create a MouseEnter Event Trigger:** Add a new event trigger and select <xref:System.Windows.UIElement.MouseEnter> as the event to use in the trigger.</span></span>

     ![建立 MouseEnter 事件觸發程序的方式](./media/custom-button-blend-mouseovereventtrigger.png)

2. <span data-ttu-id="d19da-241">**建立動畫時間軸：** 接下來，將動畫時間軸與 <xref:System.Windows.UIElement.MouseEnter> 事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d19da-241">**Create an animation timeline:** Next, associate an animation timeline to the <xref:System.Windows.UIElement.MouseEnter> event.</span></span>

    ![將動畫時刻表加入至事件的方式](./media/custom-button-blend-mouseovereventtrigger2.png)

    <span data-ttu-id="d19da-243">在您按下 **[確定]** 以建立新的時間軸之後，[**時間軸] 面板**會出現並顯示在設計面板中的 [時間軸錄製已開啟]。</span><span class="sxs-lookup"><span data-stu-id="d19da-243">After you press **OK** to create a new timeline, a **Timeline Panel** appears and "Timeline recording is on" is visible in the design panel.</span></span> <span data-ttu-id="d19da-244">這表示我們可以開始在時間軸中記錄屬性變更（以動畫顯示內容變更）。</span><span class="sxs-lookup"><span data-stu-id="d19da-244">This means we can start recording property changes in the timeline (animate property changes).</span></span>

    > [!NOTE]
    > <span data-ttu-id="d19da-245">您可能需要調整視窗和/或面板的大小，才能看到顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="d19da-245">You may need to resize your window and/or panels to see the display.</span></span>

    ![時刻表面板](./media/custom-button-blend-mouseovereventtrigger3.png)

3. <span data-ttu-id="d19da-247">**建立**主要畫面格：若要建立動畫，請選取您想要製作動畫的物件、在時間軸上建立兩個或更多的主要畫面格，然後針對這些主要畫面格，設定您想要讓動畫在其間插補的屬性值。</span><span class="sxs-lookup"><span data-stu-id="d19da-247">**Create a keyframe:** To create an animation, select the object you want to animate, create two or more keyframes on the timeline, and for those keyframes, set the property values you want the animation to interpolate between.</span></span> <span data-ttu-id="d19da-248">下圖會引導您完成建立主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="d19da-248">The following figure guides you through the creation of a keyframe.</span></span>

    ![建立主要畫面格的方式](./media/custom-button-blend-mouseovereventtrigger4.png)

4. <span data-ttu-id="d19da-250">**縮小此主要畫面格的 glassCube：** 選取第二個主要畫面格時，請使用**大小轉換**，將**glassCube**的大小縮減為90% 的完整大小。</span><span class="sxs-lookup"><span data-stu-id="d19da-250">**Shrink glassCube at this keyframe:** With the second keyframe selected, shrink the size of the **glassCube** to 90% of its full size using the **Size Transform**.</span></span>

    ![縮減按鈕大小的方式](./media/custom-button-blend-sizetransform.png)

    <span data-ttu-id="d19da-252">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-252">Press F5 to run the application.</span></span> <span data-ttu-id="d19da-253">將滑鼠指標移至按鈕上方。</span><span class="sxs-lookup"><span data-stu-id="d19da-253">Move the mouse pointer over the button.</span></span> <span data-ttu-id="d19da-254">請注意，玻璃層會在按鈕上方縮小。</span><span class="sxs-lookup"><span data-stu-id="d19da-254">Notice that the glass layer shrinks on top of the button.</span></span>

5. <span data-ttu-id="d19da-255">**建立另一個事件觸發程式，並將不同的動畫與它建立關聯：** 讓我們再加上一個動畫。</span><span class="sxs-lookup"><span data-stu-id="d19da-255">**Create another Event Trigger and associate a different animation with it:** Let's add one more animation.</span></span> <span data-ttu-id="d19da-256">使用您用來建立先前事件觸發程式動畫的類似程式：</span><span class="sxs-lookup"><span data-stu-id="d19da-256">Use a similar procedure to what you used to create the previous event trigger animation:</span></span>

    1. <span data-ttu-id="d19da-257">使用 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件建立新的事件觸發程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-257">Create a new event trigger using the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>

    2. <span data-ttu-id="d19da-258">將新的時間軸與 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d19da-258">Associate a new timeline with the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>

        ![建立新時刻表的方式](./media/custom-button-blend-clickeventtrigger1.png)

    3. <span data-ttu-id="d19da-260">針對此時間軸，建立兩個主要畫面格，一個在0.0 秒，第二個是0.3 秒。</span><span class="sxs-lookup"><span data-stu-id="d19da-260">For this timeline, create two keyframes, one at 0.0 seconds and the second one at 0.3 seconds.</span></span>

    4. <span data-ttu-id="d19da-261">在反白顯示0.3 秒的主要畫面格時，將 [**旋轉轉換角度**] 設定為360度。</span><span class="sxs-lookup"><span data-stu-id="d19da-261">With the keyframe at 0.3 seconds highlighted, set the **Rotate Transform Angle** to 360 degrees.</span></span>

        ![建立旋轉轉換的方式](./media/custom-button-blend-rotatetransform.gif)

    5. <span data-ttu-id="d19da-263">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-263">Press F5 to run the application.</span></span> <span data-ttu-id="d19da-264">按一下按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-264">Click the button.</span></span> <span data-ttu-id="d19da-265">請注意，玻璃層會旋轉。</span><span class="sxs-lookup"><span data-stu-id="d19da-265">Notice that the glass layer spins around.</span></span>

## <a name="conclusion"></a><span data-ttu-id="d19da-266">結論</span><span class="sxs-lookup"><span data-stu-id="d19da-266">Conclusion</span></span>

<span data-ttu-id="d19da-267">您已完成自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-267">You have completed a customized button.</span></span> <span data-ttu-id="d19da-268">您使用套用至應用程式中所有按鈕的按鈕範本來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="d19da-268">You did this using a button template that was applied to all buttons in the application.</span></span> <span data-ttu-id="d19da-269">如果您離開範本編輯模式（請參閱下圖）並建立更多按鈕，您會看到它們的外觀和行為類似于您的自訂按鈕，而不像預設按鈕。</span><span class="sxs-lookup"><span data-stu-id="d19da-269">If you leave the template editing mode (see the following figure) and create more buttons, you will see that they look and behave like your custom button rather than like the default button.</span></span>

![自訂按鈕範本](./media/custom-button-blend-scopeup.gif)

![使用相同範本的多個按鈕](./media/custom-button-blend-createmultiplebuttons.png)

<span data-ttu-id="d19da-272">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-272">Press F5 to run the application.</span></span> <span data-ttu-id="d19da-273">按一下按鈕，並留意其所有行為都相同。</span><span class="sxs-lookup"><span data-stu-id="d19da-273">Click the buttons and notice how they all behave the same.</span></span>

<span data-ttu-id="d19da-274">請記住，當您自訂範本時，您會將**innerRectangle**的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性和 <xref:System.Windows.Shapes.Shape.Stroke%2A> 屬性**outerRectangle**設定為範本背景（{TemplateBinding background}）。</span><span class="sxs-lookup"><span data-stu-id="d19da-274">Remember that while you were customizing the template, you set the <xref:System.Windows.Shapes.Shape.Fill%2A> property of **innerRectangle** and the <xref:System.Windows.Shapes.Shape.Stroke%2A> property **outerRectangle** to the template background ({TemplateBinding Background}).</span></span> <span data-ttu-id="d19da-275">因此，當您設定個別按鈕的背景色彩時，您設定的背景將會用於那些各自的屬性。</span><span class="sxs-lookup"><span data-stu-id="d19da-275">Because of this, when you set the background color of the individual buttons, the background you set will be used for those respective properties.</span></span> <span data-ttu-id="d19da-276">立即嘗試變更背景。</span><span class="sxs-lookup"><span data-stu-id="d19da-276">Try changing the backgrounds now.</span></span> <span data-ttu-id="d19da-277">在下圖中，會使用不同的漸層。</span><span class="sxs-lookup"><span data-stu-id="d19da-277">In the following figure, different gradients are used.</span></span> <span data-ttu-id="d19da-278">因此，雖然範本適用于控制項（例如按鈕）的整體自訂，但具有範本的控制項仍然可以進行修改，使其看起來不同。</span><span class="sxs-lookup"><span data-stu-id="d19da-278">Therefore, although a template is useful for overall customization of controls like button, controls with templates can still be modified to look different from each other.</span></span>

<span data-ttu-id="d19da-279">![具有相同範本且外觀不同的按鈕](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")</span><span class="sxs-lookup"><span data-stu-id="d19da-279">![Buttons with the same template that look diferent](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")</span></span>

<span data-ttu-id="d19da-280">總之，在自訂按鈕範本的過程中，您已瞭解如何在 Microsoft Expression Blend 中執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d19da-280">In conclusion, in the process of customizing a button template you have learned how to do the following in Microsoft Expression Blend:</span></span>

- <span data-ttu-id="d19da-281">自訂控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="d19da-281">Customize the look of a control.</span></span>

- <span data-ttu-id="d19da-282">設定屬性觸發程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-282">Set property triggers.</span></span> <span data-ttu-id="d19da-283">屬性觸發程式非常有用，因為它們可以用於大部分的物件，而不只是控制項。</span><span class="sxs-lookup"><span data-stu-id="d19da-283">Property triggers are very useful because they can be used on most objects, not just controls.</span></span>

- <span data-ttu-id="d19da-284">設定事件觸發程式。</span><span class="sxs-lookup"><span data-stu-id="d19da-284">Set event triggers.</span></span> <span data-ttu-id="d19da-285">事件觸發程式非常有用，因為它們可以用於大部分的物件，而不只是控制項。</span><span class="sxs-lookup"><span data-stu-id="d19da-285">Event triggers are very useful because they can be used on most objects, not just controls.</span></span>

- <span data-ttu-id="d19da-286">建立動畫。</span><span class="sxs-lookup"><span data-stu-id="d19da-286">Create animations.</span></span>

- <span data-ttu-id="d19da-287">其他：建立漸層、加入 BitmapEffects、使用轉換和設定物件的基本屬性。</span><span class="sxs-lookup"><span data-stu-id="d19da-287">Miscellaneous: create gradients, add BitmapEffects, use transforms, and set basic properties of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d19da-288">請參閱</span><span class="sxs-lookup"><span data-stu-id="d19da-288">See also</span></span>

- [<span data-ttu-id="d19da-289">使用 XAML 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="d19da-289">Create a Button by Using XAML</span></span>](walkthrough-create-a-button-by-using-xaml.md)
- [<span data-ttu-id="d19da-290">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="d19da-290">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="d19da-291">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="d19da-291">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="d19da-292">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="d19da-292">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="d19da-293">點陣圖效果概觀</span><span class="sxs-lookup"><span data-stu-id="d19da-293">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
