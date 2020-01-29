---
title: 如何：從 MDI 下拉式功能表移除 ToolStripMenuItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735847"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="5b047-102">如何：從 MDI 下拉式功能表移除 ToolStripMenuItem (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="5b047-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="5b047-103">在某些應用程式中，多重文件介面 (MDI) 子視窗的類型可能與 MDI 父視窗不同。</span><span class="sxs-lookup"><span data-stu-id="5b047-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="5b047-104">例如，MDI 父視窗可能是試算表，而 MDI 子視窗可能是圖表。</span><span class="sxs-lookup"><span data-stu-id="5b047-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="5b047-105">在這種情況下，由於已啟動各種不同類型的 MDI 子視窗，因此您需要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容。</span><span class="sxs-lookup"><span data-stu-id="5b047-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="5b047-106">下列程式會使用 [<xref:System.Windows.Forms.Form.IsMdiContainer%2A>]、[<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>]、[<xref:System.Windows.Forms.MergeAction>] 和 [<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>] 屬性，從 MDI 父功能表的下拉式部分移除功能表項目。</span><span class="sxs-lookup"><span data-stu-id="5b047-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="5b047-107">關閉 MDI 子視窗會將已移除的功能表項目還原至 MDI 父功能表。</span><span class="sxs-lookup"><span data-stu-id="5b047-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="5b047-108">若要從 MDI 下拉式功能表移除 MenuStrip</span><span class="sxs-lookup"><span data-stu-id="5b047-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="5b047-109">建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5b047-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="5b047-110">將 <xref:System.Windows.Forms.MenuStrip> 加入 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5b047-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="5b047-111">將最上層功能表項目加入 `Form1`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `&File`。</span><span class="sxs-lookup"><span data-stu-id="5b047-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="5b047-112">將三個子功能表項目目新增至 [`&File`] 功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 [`&Open`]、[`&Import from`] 和 [`E&xit`]。</span><span class="sxs-lookup"><span data-stu-id="5b047-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="5b047-113">將兩個子功能表項目目新增至 [`&Import from`] 子功能表專案，並將其 [<xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性] 設定為 `&Word` 和 `&Excel`。</span><span class="sxs-lookup"><span data-stu-id="5b047-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="5b047-114">將表單加入專案，將 <xref:System.Windows.Forms.MenuStrip> 加入表單，並將 `Form2`<xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5b047-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="5b047-115">將最上層功能表項目加入 `Form2`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&File`。</span><span class="sxs-lookup"><span data-stu-id="5b047-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="5b047-116">將 `&Import from` 子功能表專案新增至 `Form2`的 [`&File`] 功能表，並將 [`&Word`] 子功能表專案新增至 [`&File`] 功能表。</span><span class="sxs-lookup"><span data-stu-id="5b047-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="5b047-117">設定 `Form2` 功能表項目的 <xref:System.Windows.Forms.MergeAction> 和 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="5b047-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="5b047-118">Form2 功能表項目</span><span class="sxs-lookup"><span data-stu-id="5b047-118">Form2 menu item</span></span>|<span data-ttu-id="5b047-119">MergeAction 值</span><span class="sxs-lookup"><span data-stu-id="5b047-119">MergeAction value</span></span>|<span data-ttu-id="5b047-120">MergeIndex 值</span><span class="sxs-lookup"><span data-stu-id="5b047-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="5b047-121">File</span><span class="sxs-lookup"><span data-stu-id="5b047-121">File</span></span>|<span data-ttu-id="5b047-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="5b047-122">MatchOnly</span></span>|<span data-ttu-id="5b047-123">-1</span><span class="sxs-lookup"><span data-stu-id="5b047-123">-1</span></span>|  
    |<span data-ttu-id="5b047-124">從  匯入</span><span class="sxs-lookup"><span data-stu-id="5b047-124">Import from</span></span>|<span data-ttu-id="5b047-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="5b047-125">MatchOnly</span></span>|<span data-ttu-id="5b047-126">-1</span><span class="sxs-lookup"><span data-stu-id="5b047-126">-1</span></span>|  
    |<span data-ttu-id="5b047-127">Word</span><span class="sxs-lookup"><span data-stu-id="5b047-127">Word</span></span>|<span data-ttu-id="5b047-128">Remove</span><span class="sxs-lookup"><span data-stu-id="5b047-128">Remove</span></span>|<span data-ttu-id="5b047-129">-1</span><span class="sxs-lookup"><span data-stu-id="5b047-129">-1</span></span>|  
  
10. <span data-ttu-id="5b047-130">在 `Form1`中，為 `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5b047-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="5b047-131">在事件處理常式中，插入類似下列程式碼範例的程式碼，以建立和顯示 `Form2` 的新實例，做為 `Form1`的 MDI 子系：</span><span class="sxs-lookup"><span data-stu-id="5b047-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. <span data-ttu-id="5b047-132">將類似下列程式碼範例的程式碼放入 `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> 之中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5b047-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5b047-133">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5b047-133">Compiling the Code</span></span>  
 <span data-ttu-id="5b047-134">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="5b047-134">This example requires:</span></span>  
  
- <span data-ttu-id="5b047-135">名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。</span><span class="sxs-lookup"><span data-stu-id="5b047-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="5b047-136">`Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="5b047-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="5b047-137"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="5b047-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b047-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b047-138">See also</span></span>

- [<span data-ttu-id="5b047-139">操作說明：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="5b047-139">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="5b047-140">操作說明：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="5b047-140">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="5b047-141">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="5b047-141">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
