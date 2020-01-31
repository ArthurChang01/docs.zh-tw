---
title: 逐步解說：使用 WindowsFormsHost 項目對應屬性
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: c076937d6431adf1750793d47ece88dc82edf95c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794106"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="e234d-102">逐步解說：使用 WindowsFormsHost 項目對應屬性</span><span class="sxs-lookup"><span data-stu-id="e234d-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="e234d-103">本逐步解說將示範如何使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> 屬性，將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性對應至裝載之 Windows Forms 控制項的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="e234d-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted Windows Forms control.</span></span>

<span data-ttu-id="e234d-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="e234d-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="e234d-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="e234d-105">Creating the project.</span></span>

- <span data-ttu-id="e234d-106">定義應用程式版面配置。</span><span class="sxs-lookup"><span data-stu-id="e234d-106">Defining the application layout.</span></span>

- <span data-ttu-id="e234d-107">定義新的屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-107">Defining a new property mapping.</span></span>

- <span data-ttu-id="e234d-108">移除預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-108">Removing a default property mapping.</span></span>

- <span data-ttu-id="e234d-109">取代預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-109">Replacing a default property mapping.</span></span>

- <span data-ttu-id="e234d-110">擴充預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-110">Extending a default property mapping.</span></span>

<span data-ttu-id="e234d-111">如需本逐步解說中所述工作的完整程式代碼清單，請參閱[使用 WindowsFormsHost 元素範例對應屬性](https://go.microsoft.com/fwlink/?LinkID=160019)。</span><span class="sxs-lookup"><span data-stu-id="e234d-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="e234d-112">當您完成時，您可以將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性對應至託管 Windows Forms 控制項上的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="e234d-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted Windows Forms control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e234d-113">必要條件：</span><span class="sxs-lookup"><span data-stu-id="e234d-113">Prerequisites</span></span>

<span data-ttu-id="e234d-114">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="e234d-114">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="e234d-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e234d-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="e234d-116">建立和設定專案</span><span class="sxs-lookup"><span data-stu-id="e234d-116">Create and set up the project</span></span>

1. <span data-ttu-id="e234d-117">建立名為 `PropertyMappingWithWfhSample`的**WPF 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="e234d-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="e234d-118">在**方案總管**中，加入名為 WindowsFormsIntegration 的 WindowsFormsIntegration 元件參考。</span><span class="sxs-lookup"><span data-stu-id="e234d-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="e234d-119">在**方案總管**中，新增對 System.web 和 system.web 元件的參考。</span><span class="sxs-lookup"><span data-stu-id="e234d-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="e234d-120">定義應用程式版面配置</span><span class="sxs-lookup"><span data-stu-id="e234d-120">Defining the Application Layout</span></span>

<span data-ttu-id="e234d-121">以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式會使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素來裝載 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="e234d-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a Windows Forms control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="e234d-122">定義應用程式版面配置</span><span class="sxs-lookup"><span data-stu-id="e234d-122">To define the application layout</span></span>

1. <span data-ttu-id="e234d-123">在 WPF 設計工具中開啟 Window1.xaml。</span><span class="sxs-lookup"><span data-stu-id="e234d-123">Open Window1.xaml in the WPF Designer.</span></span>

2. <span data-ttu-id="e234d-124">將現有的程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e234d-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="e234d-125">在程式碼編輯器中，開啟 Window1.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="e234d-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="e234d-126">在檔案頂端，匯入下列命名空間。</span><span class="sxs-lookup"><span data-stu-id="e234d-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="e234d-127">定義新的屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="e234d-128"><xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素提供數個預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="e234d-129">您可以藉由在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> 方法，來加入新的屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="e234d-130">定義新的屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-130">To define a new property mapping</span></span>

- <span data-ttu-id="e234d-131">將下列程式碼複製到 `Window1` 類別的定義中。</span><span class="sxs-lookup"><span data-stu-id="e234d-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="e234d-132">`AddClipMapping` 方法會加入 <xref:System.Windows.UIElement.Clip%2A> 屬性的新對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="e234d-133">`OnClipChange` 方法會將 <xref:System.Windows.UIElement.Clip%2A> 屬性轉譯為 Windows Forms 的<xref:System.Windows.Forms.Control.Region%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e234d-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the Windows Forms<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="e234d-134">`Window1_SizeChanged` 方法會處理視窗的 <xref:System.Windows.FrameworkElement.SizeChanged> 事件，並調整裁剪區域的大小以符合應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="e234d-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="e234d-135">移除預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="e234d-136">藉由在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> 方法，移除預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="e234d-137">移除預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-137">To remove a default property mapping</span></span>

- <span data-ttu-id="e234d-138">將下列程式碼複製到 `Window1` 類別的定義中。</span><span class="sxs-lookup"><span data-stu-id="e234d-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="e234d-139">`RemoveCursorMapping` 方法會刪除 <xref:System.Windows.FrameworkElement.Cursor%2A> 屬性的預設對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="e234d-140">取代預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="e234d-141">藉由移除預設的對應，並在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> 方法，來取代預設的屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="e234d-142">移除預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-142">To replace a default property mapping</span></span>

- <span data-ttu-id="e234d-143">將下列程式碼複製到 `Window1` 類別的定義中。</span><span class="sxs-lookup"><span data-stu-id="e234d-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="e234d-144">`ReplaceFlowDirectionMapping` 方法會取代 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性的預設對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="e234d-145">`OnFlowDirectionChange` 方法會將 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性轉譯為 Windows Forms 的<xref:System.Windows.Forms.Control.RightToLeft%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e234d-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the Windows Forms<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="e234d-146">`cb_CheckedChanged` 方法會處理 <xref:System.Windows.Forms.CheckBox> 控制項上的 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="e234d-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="e234d-147">它會根據 <xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性的值來指派 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="e234d-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="e234d-148">擴充預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="e234d-149">您可以使用預設屬性對應，也可以使用自己的對應來進行擴充。</span><span class="sxs-lookup"><span data-stu-id="e234d-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="e234d-150">擴充預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-150">To extend a default property mapping</span></span>

- <span data-ttu-id="e234d-151">將下列程式碼複製到 `Window1` 類別的定義中。</span><span class="sxs-lookup"><span data-stu-id="e234d-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="e234d-152">`ExtendBackgroundMapping` 方法會將自訂屬性 translator 加入至現有的 <xref:System.Windows.Controls.Control.Background%2A> 屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="e234d-153">`OnBackgroundChange` 方法會將特定的影像指派給主控控制項的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e234d-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="e234d-154">套用預設屬性對應之後，會呼叫 `OnBackgroundChange` 方法。</span><span class="sxs-lookup"><span data-stu-id="e234d-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="e234d-155">初始化屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="e234d-156">藉由呼叫 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式中先前所述的方法來設定屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="e234d-157">初始化屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="e234d-158">將下列程式碼複製到 `Window1` 類別的定義中。</span><span class="sxs-lookup"><span data-stu-id="e234d-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="e234d-159">`WindowLoaded` 方法會處理 <xref:System.Windows.FrameworkElement.Loaded> 事件，並執行下列初始化。</span><span class="sxs-lookup"><span data-stu-id="e234d-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    - <span data-ttu-id="e234d-160">建立 Windows Forms<xref:System.Windows.Forms.CheckBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e234d-160">Creates a Windows Forms<xref:System.Windows.Forms.CheckBox> control.</span></span>

    - <span data-ttu-id="e234d-161">呼叫您稍早在本逐步解說中所定義的方法來設定屬性對應。</span><span class="sxs-lookup"><span data-stu-id="e234d-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="e234d-162">將初始值指派給對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="e234d-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="e234d-163">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e234d-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="e234d-164">按一下核取方塊以查看 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 對應的效果。</span><span class="sxs-lookup"><span data-stu-id="e234d-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="e234d-165">當您按一下核取方塊時，版面配置會反轉其左右方向。</span><span class="sxs-lookup"><span data-stu-id="e234d-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e234d-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="e234d-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="e234d-167">Windows Forms 和 WPF 屬性對應</span><span class="sxs-lookup"><span data-stu-id="e234d-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="e234d-168">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="e234d-168">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="e234d-169">逐步解說：在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e234d-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
