---
title: 逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 297a7080b0c34fa10f976cbbbfb48d8c35786aca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458087"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a><span data-ttu-id="16a2e-102">逐步解說：序列化標準類型的集合</span><span class="sxs-lookup"><span data-stu-id="16a2e-102">Walkthrough: Serialize collections of standard types</span></span>

<span data-ttu-id="16a2e-103">您的自訂控制項有時會將集合公開為屬性。</span><span class="sxs-lookup"><span data-stu-id="16a2e-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="16a2e-104">本逐步解說示範如何使用 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> 類別，控制如何在設計階段序列化集合。</span><span class="sxs-lookup"><span data-stu-id="16a2e-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="16a2e-105">將 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> 值套用至集合屬性，可確保將會序列化屬性。</span><span class="sxs-lookup"><span data-stu-id="16a2e-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="16a2e-106">若要將本主題中的程式碼複製成單一清單，請參閱[如何：使用 Designerserializationvisibilityattribute 序列化序列化標準類型的集合](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="16a2e-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16a2e-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="16a2e-107">Prerequisites</span></span>

<span data-ttu-id="16a2e-108">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="16a2e-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="16a2e-109">建立具有可序列化集合的控制項</span><span class="sxs-lookup"><span data-stu-id="16a2e-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="16a2e-110">第一個步驟是建立具有可序列化集合做為屬性的控制項。</span><span class="sxs-lookup"><span data-stu-id="16a2e-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="16a2e-111">您可以使用 [**集合編輯器**] （可從 [**屬性**] 視窗存取）來編輯此集合的內容。</span><span class="sxs-lookup"><span data-stu-id="16a2e-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="16a2e-112">在 Visual Studio 中，建立 Windows 控制項程式庫專案，並將其命名為**SerializationDemoControlLib**。</span><span class="sxs-lookup"><span data-stu-id="16a2e-112">In Visual Studio, create a Windows Control Library project, and name it **SerializationDemoControlLib**.</span></span>

2. <span data-ttu-id="16a2e-113">將 `UserControl1` 重新命名為 `SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="16a2e-113">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="16a2e-114">如需詳細資訊，請參閱[重新命名程式碼符號重構](/visualstudio/ide/reference/rename)。</span><span class="sxs-lookup"><span data-stu-id="16a2e-114">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="16a2e-115">在 [**屬性**] 視窗中，將 [<xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType>] 屬性的值設定為**10**。</span><span class="sxs-lookup"><span data-stu-id="16a2e-115">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to **10**.</span></span>

4. <span data-ttu-id="16a2e-116">將 <xref:System.Windows.Forms.TextBox> 控制項放在 `SerializationDemoControl`中。</span><span class="sxs-lookup"><span data-stu-id="16a2e-116">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="16a2e-117">選取 <xref:System.Windows.Forms.TextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="16a2e-117">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="16a2e-118">在 [**屬性**] 視窗中，設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="16a2e-118">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="16a2e-119">屬性</span><span class="sxs-lookup"><span data-stu-id="16a2e-119">Property</span></span>|<span data-ttu-id="16a2e-120">變更為</span><span class="sxs-lookup"><span data-stu-id="16a2e-120">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="16a2e-121">**多行**</span><span class="sxs-lookup"><span data-stu-id="16a2e-121">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="16a2e-122">**站**</span><span class="sxs-lookup"><span data-stu-id="16a2e-122">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="16a2e-123">[ScrollBars]</span><span class="sxs-lookup"><span data-stu-id="16a2e-123">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="16a2e-124">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="16a2e-124">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="16a2e-125">在 [程式**代碼編輯器**] 中，于 `SerializationDemoControl`中宣告名為 `stringsValue` 的字串陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="16a2e-125">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="16a2e-126">定義 `SerializationDemoControl`上的 `Strings` 屬性。</span><span class="sxs-lookup"><span data-stu-id="16a2e-126">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="16a2e-127"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> 值是用來啟用集合的序列化。</span><span class="sxs-lookup"><span data-stu-id="16a2e-127">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="16a2e-128">按**F5**以建立專案，並在**UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="16a2e-128">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="16a2e-129">在**UserControl 測試容器**的 <xref:System.Windows.Forms.PropertyGrid> 中，尋找 [**字串**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="16a2e-129">Find the **Strings** property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="16a2e-130">選取 [**字串**] 屬性，然後選取省略號（![[Visual Studio](./media/visual-studio-ellipsis-button.png)）] 按鈕屬性視窗中的省略號按鈕（...），以開啟 [**字串集合編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="16a2e-130">Select the **Strings** property, then select the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="16a2e-131">在 [**字串集合編輯器**] 中輸入數個字串。</span><span class="sxs-lookup"><span data-stu-id="16a2e-131">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="16a2e-132">請在每個字串的結尾按**enter**鍵來分隔它們。</span><span class="sxs-lookup"><span data-stu-id="16a2e-132">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="16a2e-133">完成輸入字串後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="16a2e-133">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="16a2e-134">您輸入的字串會出現在 `SerializationDemoControl`的 <xref:System.Windows.Forms.TextBox> 中。</span><span class="sxs-lookup"><span data-stu-id="16a2e-134">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serialize-a-collection-property"></a><span data-ttu-id="16a2e-135">序列化集合屬性</span><span class="sxs-lookup"><span data-stu-id="16a2e-135">Serialize a collection property</span></span>

<span data-ttu-id="16a2e-136">若要測試控制項的序列化行為，請將它放在表單上，並使用 [**集合編輯器**] 來變更集合的內容。</span><span class="sxs-lookup"><span data-stu-id="16a2e-136">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="16a2e-137">您可以查看序列化的集合狀態，方法是查看**Windows Form 設計工具**發出程式碼的特殊設計工具檔案。</span><span class="sxs-lookup"><span data-stu-id="16a2e-137">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

1. <span data-ttu-id="16a2e-138">將 Windows 應用程式專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="16a2e-138">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="16a2e-139">將專案命名為 `SerializationDemoControlTest`。</span><span class="sxs-lookup"><span data-stu-id="16a2e-139">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="16a2e-140">在 [**工具箱**] 中，尋找名為 [ **SerializationDemoControlLib 元件**] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="16a2e-140">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="16a2e-141">在此索引標籤中，您會找到 `SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="16a2e-141">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="16a2e-142">如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。</span><span class="sxs-lookup"><span data-stu-id="16a2e-142">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="16a2e-143">將 `SerializationDemoControl` 放在您的表單上。</span><span class="sxs-lookup"><span data-stu-id="16a2e-143">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="16a2e-144">在 [**屬性**] 視窗中尋找 [`Strings`] 屬性。</span><span class="sxs-lookup"><span data-stu-id="16a2e-144">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="16a2e-145">按一下 [`Strings`] 屬性，然後按一下省略號（![[屬性視窗中](./media/visual-studio-ellipsis-button.png)Visual Studio 的省略號按鈕（...）] 按鈕，以開啟 [**字串集合編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="16a2e-145">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="16a2e-146">在 [**字串集合編輯器**] 中輸入數個字串。</span><span class="sxs-lookup"><span data-stu-id="16a2e-146">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="16a2e-147">請在每個字串結尾按**enter**鍵來分隔它們。</span><span class="sxs-lookup"><span data-stu-id="16a2e-147">Separate them by pressing **Enter** at the end of each string.</span></span> <span data-ttu-id="16a2e-148">完成輸入字串後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="16a2e-148">Click **OK** when you are finished entering strings.</span></span>

    > [!NOTE]
    > <span data-ttu-id="16a2e-149">您輸入的字串會出現在 `SerializationDemoControl`的 <xref:System.Windows.Forms.TextBox> 中。</span><span class="sxs-lookup"><span data-stu-id="16a2e-149">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

6. <span data-ttu-id="16a2e-150">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="16a2e-150">In **Solution Explorer**, click the **Show All Files** button.</span></span>

7. <span data-ttu-id="16a2e-151">開啟 [ **Form1** ] 節點。</span><span class="sxs-lookup"><span data-stu-id="16a2e-151">Open the **Form1** node.</span></span> <span data-ttu-id="16a2e-152">其底下是名為**Form1.Designer.cs** **或 form1.vb 的檔案。**</span><span class="sxs-lookup"><span data-stu-id="16a2e-152">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="16a2e-153">這是**Windows Form 設計工具**發出程式碼的檔案，代表表單和其子控制項的設計階段狀態。</span><span class="sxs-lookup"><span data-stu-id="16a2e-153">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="16a2e-154">在 [程式碼編輯器] 中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="16a2e-154">Open this file in the **Code Editor**.</span></span>

8. <span data-ttu-id="16a2e-155">開啟名為 [ **Windows Form 設計工具產生**的程式碼] 的區域，然後尋找標示為**serializationDemoControl1**的區段。</span><span class="sxs-lookup"><span data-stu-id="16a2e-155">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="16a2e-156">此標籤底下的程式碼代表控制項的序列化狀態。</span><span class="sxs-lookup"><span data-stu-id="16a2e-156">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="16a2e-157">您在步驟5中輸入的字串會出現在 `Strings` 屬性的指派中。</span><span class="sxs-lookup"><span data-stu-id="16a2e-157">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="16a2e-158">下列程式碼範例C#和 Visual Basic 中，會顯示類似于您輸入 "red"、"橙色" 和 "黃色" 字串的程式碼。</span><span class="sxs-lookup"><span data-stu-id="16a2e-158">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. <span data-ttu-id="16a2e-159">在 [程式**代碼編輯器**] 中，將 [`Strings`] 屬性上 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> 的值變更為 [<xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>]。</span><span class="sxs-lookup"><span data-stu-id="16a2e-159">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. <span data-ttu-id="16a2e-160">重建方案並重複步驟3和4。</span><span class="sxs-lookup"><span data-stu-id="16a2e-160">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="16a2e-161">在此情況下， **Windows Form 設計工具**不會對 `Strings` 屬性發出任何指派。</span><span class="sxs-lookup"><span data-stu-id="16a2e-161">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="16a2e-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="16a2e-162">Next steps</span></span>

<span data-ttu-id="16a2e-163">一旦您知道如何序列化標準類型的集合，請考慮將自訂控制項更深入地整合到設計階段環境中。</span><span class="sxs-lookup"><span data-stu-id="16a2e-163">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="16a2e-164">下列主題說明如何增強自訂控制項的設計階段整合：</span><span class="sxs-lookup"><span data-stu-id="16a2e-164">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="16a2e-165">[設計階段架構](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="16a2e-165">[Design-Time Architecture](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="16a2e-166">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="16a2e-166">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="16a2e-167">[設計工具序列化總覽](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="16a2e-167">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="16a2e-168">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="16a2e-168">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="16a2e-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="16a2e-169">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [<span data-ttu-id="16a2e-170">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="16a2e-170">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
