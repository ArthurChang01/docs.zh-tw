---
title: 如何：建立 MDI 子表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: b49d43e0e1123921cb3800f0d60193d0ea7b3924
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338587"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="d0c7e-102">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="d0c7e-102">How to: Create MDI child forms</span></span>

<span data-ttu-id="d0c7e-103">MDI 子表單是[多重文件介面（MDI）應用程式](multiple-document-interface-mdi-applications.md)的重要元素，因為這些形式是使用者互動的中心。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="d0c7e-104">在下列程式中，您將使用 Visual Studio 來建立顯示 <xref:System.Windows.Forms.RichTextBox> 控制項的 MDI 子表單，類似于大部分的文字處理應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-104">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="d0c7e-105">藉由將 <xref:System.Windows.Forms> 控制項替換為其他控制項（例如 <xref:System.Windows.Forms.DataGridView> 控制項）或控制項的混合，您就可以建立具有各種可能性的 MDI 子視窗（以及擴充功能、MDI 應用程式）。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-105">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="d0c7e-106">建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="d0c7e-106">Create MDI child forms</span></span>

1. <span data-ttu-id="d0c7e-107">在 Visual Studio 中建立新的 Windows Forms 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-107">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="d0c7e-108">在表單的 **屬性** 視窗中，將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`，並將其 `WindowsState` 屬性設為 `Maximized`</span><span class="sxs-lookup"><span data-stu-id="d0c7e-108">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="d0c7e-109">如此即可將表單指定為子視窗的 MDI 容器。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-109">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="d0c7e-110">將 <xref:System.Windows.Forms.MenuStrip> 控制項從 [`Toolbox`] 拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-110">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="d0c7e-111">將其 [`Text`] 屬性**設定為 [** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-111">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="d0c7e-112">按一下 [**專案**] 屬性旁的省略號（...），然後按一下 [**新增**] 以加入兩個子工具區域的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-112">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="d0c7e-113">將這些專案的 `Text` 屬性設定為 [**新增**] 和 [**視窗]** 。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-113">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="d0c7e-114">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-114">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="d0c7e-115">在 [**加入新專案**] 對話方塊中，從 [**範本**] 窗格選取 [ **Windows Form** ] （在 Visual Basic 或 Visual C#中）或 [ **Windows Forms 應用程式（.net）** ] （在 visual C++中）。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-115">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="d0c7e-116">在 [**名稱**] 方塊中，將表單命名為**Form2**。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-116">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="d0c7e-117">選取 [**開啟**]，將表單新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-117">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d0c7e-118">您在這個步驟中所建立的 MDI 子表單是標準的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-118">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="d0c7e-119">因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性，可讓您控制表單的透明度。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-119">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="d0c7e-120">然而，<xref:System.Windows.Forms.Form.Opacity%2A> 屬性是專為最上層視窗而設計的。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-120">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="d0c7e-121">請勿搭配 MDI 子表單使用這個屬性，這樣做可能會發生繪製問題。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-121">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="d0c7e-122">這個表單將是您的 MDI 子表單範本。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-122">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="d0c7e-123">**Windows Form 設計工具**隨即開啟，並顯示**Form2**。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-123">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="d0c7e-124">從 [**工具箱**] 將 [ **RichTextBox** ] 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-124">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="d0c7e-125">在 [**屬性**] 視窗中，將 [`Anchor`] 屬性設為 [ **Top]、[Left** ] 和 [`Dock`] 屬性以**填入**。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-125">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="d0c7e-126">如此一來，<xref:System.Windows.Forms.RichTextBox> 控制項就會完全填滿 MDI 子表單區域，即使表單大小重新調整過亦可。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-126">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="d0c7e-127">按兩下 [**新增**] 功能表項目，為其建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-127">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="d0c7e-128">插入與下列類似的程式碼，以便在使用者按一下 [**新增**] 功能表項目時建立新的 MDI 子表單。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-128">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d0c7e-129">在下列範例中，事件處理常式會處理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-129">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="d0c7e-130">請注意，視應用程式架構的細節而定，您的**新**功能表項目可能不會 `MenuItem2`。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-130">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   <span data-ttu-id="d0c7e-131">在C++中，將下列 `#include` 指示詞新增至 Form1. h 的頂端：</span><span class="sxs-lookup"><span data-stu-id="d0c7e-131">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="d0c7e-132">在 [**屬性**] 視窗頂端的下拉式清單中，選取對應至 [檔案 **] 功能表區域的功能表區域**，並將 [<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>] 屬性設定為 [<xref:System.Windows.Forms.ToolStripMenuItem>視窗]。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-132">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="d0c7e-133">這可讓 [**視窗]** 功能表使用作用中子視窗旁的核取記號，維護開啟的 MDI 子視窗清單。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-133">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="d0c7e-134">按 **F5** 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-134">Press **F5** to run the application.</span></span> <span data-ttu-id="d0c7e-135">藉由從 [檔案] 功能表選取 [**新增**]，您可以建立新的 MDI 子表單，其會在 [**視窗]** **功能表項目**中保持追蹤。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-135">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d0c7e-136">在 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 父表單中，開啟同樣具有 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 子表單時，如果您已設定 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性 (並選擇性地設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性)，則功能表項目會自動合併。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-136">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="d0c7e-137">將上述兩個 <xref:System.Windows.Forms.MainMenu> 的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性和子表單的所有功能表項目設定為 <xref:System.Windows.Forms.MenuMerge.MergeItems>。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-137">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="d0c7e-138">接著再設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性，如此一來，來自兩個功能表的功能表項目即可依指定順序出現。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-138">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="d0c7e-139">再者，請記住，在關閉 MDI 父表單時，每個 MDI 子表單都會在 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件引發前，先引發 <xref:System.Windows.Forms.Form.Closing> 事件。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-139">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="d0c7e-140">只取消 MDI 子表單的 <xref:System.Windows.Forms.Form.Closing> 事件並無法避免引發 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件；不過，MDI 父表單之 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 引數現在會設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-140">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="d0c7e-141">您可以將 <xref:System.ComponentModel.CancelEventArgs> 引數設定為 `false`，以強制關閉 MDI 父表單和所有 MDI 子表單。</span><span class="sxs-lookup"><span data-stu-id="d0c7e-141">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0c7e-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0c7e-142">See also</span></span>

- [<span data-ttu-id="d0c7e-143">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="d0c7e-143">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="d0c7e-144">操作說明：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="d0c7e-144">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="d0c7e-145">操作說明：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="d0c7e-145">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="d0c7e-146">操作說明：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="d0c7e-146">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="d0c7e-147">如何：安排 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="d0c7e-147">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
