---
title: 逐步解說：在設計階段建立 Windows Form 的新 WPF 內容
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fc6f988d6ffd270eba4abe277ca34fa2eeec56fd
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197433"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="f0e5c-102">逐步解說：在設計階段于 Windows Forms 上建立新的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="f0e5c-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="f0e5c-103">本文說明如何建立 Windows Presentation Foundation （WPF）控制項，以便在您的 Windows Forms 架構應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f0e5c-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f0e5c-104">Prerequisites</span></span>

<span data-ttu-id="f0e5c-105">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="f0e5c-106">建立專案</span><span class="sxs-lookup"><span data-stu-id="f0e5c-106">Create the project</span></span>

<span data-ttu-id="f0e5c-107">開啟 Visual Studio，並在名為 `HostingWpf`的 Visual Basic 或視覺效果C#中建立新的**Windows Forms 應用程式（.NET Framework）** 專案。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-107">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="f0e5c-108">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="f0e5c-109">建立新的 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="f0e5c-109">Create a new WPF control</span></span>

<span data-ttu-id="f0e5c-110">建立新的 WPF 控制項並將其加入專案中，就像是將其他任何項目加入專案中一樣容易。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-110">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="f0e5c-111">Windows Form 設計工具適用于特定類型的控制項，稱為*複合控制項*或*使用者控制項*。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-111">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="f0e5c-112">如需 WPF 使用者控制項的詳細資訊，請參閱 <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-112">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="f0e5c-113">WPF 的 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> 類型不同於 Windows Form 所提供的使用者控制項類型 (又稱為 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-113">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f0e5c-114">若要建立新的 WPF 控制項：</span><span class="sxs-lookup"><span data-stu-id="f0e5c-114">To create a new WPF control:</span></span>

1. <span data-ttu-id="f0e5c-115">在**方案總管**中，將新的**WPF 使用者控制項程式庫（.NET Framework）** 專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-115">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="f0e5c-116">使用控制項程式庫的預設名稱 `WpfControlLibrary1`。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-116">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="f0e5c-117">預設控制項名稱為 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-117">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="f0e5c-118">加入新控制項的效果如下：</span><span class="sxs-lookup"><span data-stu-id="f0e5c-118">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="f0e5c-119">會加入 UserControl1.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-119">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="f0e5c-120">已新增檔案 UserControl1.xaml.cs （或 UserControl1）。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-120">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="f0e5c-121">這個檔案包含事件處理常式和其他實作的程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-121">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="f0e5c-122">會加入 WPF 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-122">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="f0e5c-123">[檔案 UserControl1] 會在 WPF 設計工具中開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-123">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="f0e5c-124">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-124">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="f0e5c-125">在 [**屬性**] 視窗中，將 [<xref:System.Windows.FrameworkElement.Width%2A>] 和 [<xref:System.Windows.FrameworkElement.Height%2A> 屬性] 的值設定為**200**。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-125">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="f0e5c-126">從 [**工具箱**] 中，將 [<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>] 控制項拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-126">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="f0e5c-127">在 [**屬性**] 視窗中，將 [<xref:System.Windows.Controls.TextBox.Text%2A>] 屬性的值設定為 [裝載的**內容**]。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-127">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f0e5c-128">一般而言，您應該裝載更複雜的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-128">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="f0e5c-129"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項在此僅供說明用途使用。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="f0e5c-130">建置專案。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-130">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="f0e5c-131">將 WPF 控制項加入至 Windows Form</span><span class="sxs-lookup"><span data-stu-id="f0e5c-131">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="f0e5c-132">您的新 WPF 控制項已經準備好在表單上使用。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-132">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="f0e5c-133">Windows Forms 使用 <xref:System.Windows.Forms.Integration.ElementHost> 控制項來裝載 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-133">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="f0e5c-134">若要將 WPF 控制項加入至 Windows Form：</span><span class="sxs-lookup"><span data-stu-id="f0e5c-134">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="f0e5c-135">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-135">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="f0e5c-136">在 [**工具箱**] 中，尋找標示為 [ **WPFUserControlLibrary WPF 使用者控制項**] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-136">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="f0e5c-137">將 `UserControl1` 的執行個體拖曳到表單上。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-137">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="f0e5c-138"><xref:System.Windows.Forms.Integration.ElementHost> 控制項會在表單上自動建立，以裝載 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-138">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="f0e5c-139"><xref:System.Windows.Forms.Integration.ElementHost> 控制項的名稱為 `elementHost1`，而在 [**屬性**] 視窗中，您可以看到其 <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> 屬性設定為**UserControl1**。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-139">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="f0e5c-140">WPF 組件的參考會加入專案中。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-140">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="f0e5c-141">`elementHost1` 控制項具有智慧標籤面板，這個面板會顯示可用的裝載選項。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-141">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="f0e5c-142">在 [ **ElementHost Tasks** ] 智慧標籤面板中，選取 [停**駐于父容器中**]。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-142">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="f0e5c-143">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-143">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f0e5c-144">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f0e5c-144">Next steps</span></span>

<span data-ttu-id="f0e5c-145">Windows Form 和 WPF 是不同的技術，不過可以藉由設計密切地相互操作。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-145">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="f0e5c-146">若要在您的應用程式中提供更豐富的外觀和行為，請嘗試下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f0e5c-146">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="f0e5c-147">將 Windows Form 控制項裝載到 WPF 頁面中。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-147">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="f0e5c-148">如需詳細資訊，請參閱[逐步解說：在 WPF 中裝載 Windows Forms 控制項](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-148">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="f0e5c-149">將 Windows Form 視覺化樣式套用至 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-149">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="f0e5c-150">如需詳細資訊，請參閱[如何：在混合應用程式中啟用視覺化樣式](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-150">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="f0e5c-151">變更 WPF 內容的樣式。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-151">Change the style of your WPF content.</span></span> <span data-ttu-id="f0e5c-152">如需詳細資訊，請參閱[逐步解說：設定 WPF 內容的樣式](walkthrough-styling-wpf-content.md)。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-152">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f0e5c-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0e5c-153">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f0e5c-154">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="f0e5c-154">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="f0e5c-155">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="f0e5c-155">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="f0e5c-156">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="f0e5c-156">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
