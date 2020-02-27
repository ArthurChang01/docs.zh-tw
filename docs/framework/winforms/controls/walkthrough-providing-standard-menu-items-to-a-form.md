---
title: 逐步解說：對表單提供標準功能表項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628770"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="b9688-102">逐步解說：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="b9688-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="b9688-103">您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。</span><span class="sxs-lookup"><span data-stu-id="b9688-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="b9688-104">本逐步解說示範如何使用 <xref:System.Windows.Forms.MenuStrip> 控制項來建立標準功能表。</span><span class="sxs-lookup"><span data-stu-id="b9688-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="b9688-105">當使用者選取功能表項目時，表單會也會回應。</span><span class="sxs-lookup"><span data-stu-id="b9688-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="b9688-106">本逐步解說將說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="b9688-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="b9688-107">建立 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="b9688-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="b9688-108">建立標準功能表。</span><span class="sxs-lookup"><span data-stu-id="b9688-108">Creating a standard menu.</span></span>

- <span data-ttu-id="b9688-109">建立 <xref:System.Windows.Forms.StatusStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b9688-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="b9688-110">處理功能表項目選取專案。</span><span class="sxs-lookup"><span data-stu-id="b9688-110">Handling menu item selection.</span></span>

<span data-ttu-id="b9688-111">當您完成時，您將會有一個具有標準功能表的表單，以顯示 <xref:System.Windows.Forms.StatusStrip> 控制項中的功能表項目選取專案。</span><span class="sxs-lookup"><span data-stu-id="b9688-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="b9688-112">若要將本主題中的程式碼複製成單一清單，請參閱[如何：將標準功能表項目提供給表單](how-to-provide-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="b9688-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b9688-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b9688-113">Prerequisites</span></span>

<span data-ttu-id="b9688-114">您將需要 Visual Studio 才能完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="b9688-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="b9688-115">建立專案</span><span class="sxs-lookup"><span data-stu-id="b9688-115">Create the project</span></span>

1. <span data-ttu-id="b9688-116">在 Visual Studio 中，建立稱為**StandardMenuForm**的 Windows 應用程式專案（**檔案 > \*\* **新增** > **專案** > **Visual C#** 或**Visual Basic\*\* > **傳統桌面** > **Windows Forms 應用程式**）。</span><span class="sxs-lookup"><span data-stu-id="b9688-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="b9688-117">在 Windows Form 設計工具中，選取表單。</span><span class="sxs-lookup"><span data-stu-id="b9688-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="b9688-118">建立標準功能表</span><span class="sxs-lookup"><span data-stu-id="b9688-118">Create a standard menu</span></span>

<span data-ttu-id="b9688-119">Windows Form 設計工具可以使用標準功能表項目，自動填入 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b9688-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="b9688-120">從 [**工具箱**] 將 [<xref:System.Windows.Forms.MenuStrip>] 控制項拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="b9688-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="b9688-121">按一下 <xref:System.Windows.Forms.MenuStrip> 控制項的設計工具動作圖像（![小型黑色箭號](./media/designer-actions-glyph.gif)），然後選取 [**插入標準專案**]。</span><span class="sxs-lookup"><span data-stu-id="b9688-121">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="b9688-122">[<xref:System.Windows.Forms.MenuStrip>] 控制項會以標準功能表項目填入。</span><span class="sxs-lookup"><span data-stu-id="b9688-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="b9688-123">按一下 [檔案] 功能表**項，以**查看其預設功能表項目和對應的圖示。</span><span class="sxs-lookup"><span data-stu-id="b9688-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="b9688-124">建立 StatusStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="b9688-124">Create a StatusStrip control</span></span>

<span data-ttu-id="b9688-125">使用 [<xref:System.Windows.Forms.StatusStrip>] 控制項來顯示 Windows Forms 應用程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="b9688-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="b9688-126">在目前的範例中，使用者選取的功能表項目會顯示在 <xref:System.Windows.Forms.StatusStrip> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="b9688-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="b9688-127">從 [**工具箱**] 將 [<xref:System.Windows.Forms.StatusStrip>] 控制項拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="b9688-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="b9688-128"><xref:System.Windows.Forms.StatusStrip> 控制項會自動停駐在表單底部。</span><span class="sxs-lookup"><span data-stu-id="b9688-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="b9688-129">按一下 [<xref:System.Windows.Forms.StatusStrip>] 控制項的下拉式按鈕，然後選取 [ **StatusLabel** ] 將 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項加入至 [<xref:System.Windows.Forms.StatusStrip>] 控制項。</span><span class="sxs-lookup"><span data-stu-id="b9688-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="b9688-130">處理專案選取</span><span class="sxs-lookup"><span data-stu-id="b9688-130">Handle item selection</span></span>

<span data-ttu-id="b9688-131">處理當使用者選取功能表項目時所要回應的 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> 事件。</span><span class="sxs-lookup"><span data-stu-id="b9688-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="b9688-132">按一下您在建立標準功能表一節中建立**的 [檔案**] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="b9688-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="b9688-133">在 [屬性] 視窗中按一下 [事件]。</span><span class="sxs-lookup"><span data-stu-id="b9688-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="b9688-134">按兩下 [<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>] 事件。</span><span class="sxs-lookup"><span data-stu-id="b9688-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="b9688-135">Windows Form 設計工具會產生 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b9688-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="b9688-136">將下列程式碼插入事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b9688-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="b9688-137">將 `UpdateStatus` 公用程式方法定義插入表單中。</span><span class="sxs-lookup"><span data-stu-id="b9688-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="b9688-138">檢查點-測試您的表單</span><span class="sxs-lookup"><span data-stu-id="b9688-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="b9688-139">按**F5**以編譯並執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="b9688-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="b9688-140">按一下 [檔案 **] 功能表項目**以開啟功能表。</span><span class="sxs-lookup"><span data-stu-id="b9688-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="b9688-141">**在 [檔案] 功能表上**，按一下其中一個專案來選取它。</span><span class="sxs-lookup"><span data-stu-id="b9688-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="b9688-142"><xref:System.Windows.Forms.StatusStrip> 控制項會顯示選取的專案。</span><span class="sxs-lookup"><span data-stu-id="b9688-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b9688-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b9688-143">Next steps</span></span>

<span data-ttu-id="b9688-144">在此逐步解說中，您已建立具有標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="b9688-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="b9688-145">您可以將 <xref:System.Windows.Forms.ToolStrip> 系列控制項用於其他許多用途：</span><span class="sxs-lookup"><span data-stu-id="b9688-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="b9688-146">使用 <xref:System.Windows.Forms.ContextMenuStrip>建立控制項的快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="b9688-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="b9688-147">如需詳細資訊，請參閱[CoNtextMenu 元件總覽](contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b9688-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="b9688-148">建立具有固定 <xref:System.Windows.Forms.ToolStrip> 控制項的多重文件介面（MDI）表單。</span><span class="sxs-lookup"><span data-stu-id="b9688-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="b9688-149">如需詳細資訊，請參閱[逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="b9688-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="b9688-150">為您的 <xref:System.Windows.Forms.ToolStrip> 控制項提供專業的外觀。</span><span class="sxs-lookup"><span data-stu-id="b9688-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="b9688-151">如需詳細資訊，請參閱[如何：設定應用程式的 ToolStrip](how-to-set-the-toolstrip-renderer-for-an-application.md)轉譯器。</span><span class="sxs-lookup"><span data-stu-id="b9688-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9688-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9688-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="b9688-153">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="b9688-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
