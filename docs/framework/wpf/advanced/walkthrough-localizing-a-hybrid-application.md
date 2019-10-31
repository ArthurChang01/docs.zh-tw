---
title: 逐步解說：當地語系化混合應用程式
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: bef296d5de4735780c839af312b5d4fe7eeeb960
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197861"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="fec45-102">逐步解說：當地語系化混合應用程式</span><span class="sxs-lookup"><span data-stu-id="fec45-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="fec45-103">本逐步解說將示範如何在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]型混合式應用程式中，將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素當地語系化。</span><span class="sxs-lookup"><span data-stu-id="fec45-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>

<span data-ttu-id="fec45-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="fec45-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="fec45-105">建立 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 主專案。</span><span class="sxs-lookup"><span data-stu-id="fec45-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>

- <span data-ttu-id="fec45-106">新增可當地語系化的內容。</span><span class="sxs-lookup"><span data-stu-id="fec45-106">Adding localizable content.</span></span>

- <span data-ttu-id="fec45-107">啟用當地語系化。</span><span class="sxs-lookup"><span data-stu-id="fec45-107">Enabling localization.</span></span>

- <span data-ttu-id="fec45-108">指派資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="fec45-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="fec45-109">使用 LocBaml 工具產生附屬組件。</span><span class="sxs-lookup"><span data-stu-id="fec45-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="fec45-110">如需本逐步解說中所述工作的完整程式代碼清單，請參閱[當地語系化混合式應用程式範例](https://go.microsoft.com/fwlink/?LinkID=160015)。</span><span class="sxs-lookup"><span data-stu-id="fec45-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="fec45-111">完成之後，就會有當地語系化的混合應用程式。</span><span class="sxs-lookup"><span data-stu-id="fec45-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fec45-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="fec45-112">Prerequisites</span></span>

<span data-ttu-id="fec45-113">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="fec45-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="fec45-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fec45-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="fec45-115">建立 Windows Forms 主專案</span><span class="sxs-lookup"><span data-stu-id="fec45-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="fec45-116">第一個步驟是建立 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式專案，並新增包含您要當地語系化之內容的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素。</span><span class="sxs-lookup"><span data-stu-id="fec45-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="fec45-117">建立主專案</span><span class="sxs-lookup"><span data-stu-id="fec45-117">To create the host project</span></span>

1. <span data-ttu-id="fec45-118">建立名為 `LocalizingWpfInWf`的**WPF 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="fec45-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="fec45-119">（**檔案** > **新**的 \*\* > 專案\*\* > **Visual C#** 或**Visual Basic** > **傳統桌面** > **WPF 應用程式**）。</span><span class="sxs-lookup"><span data-stu-id="fec45-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="fec45-120">將名為 `SimpleControl` 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> 元素新增至專案。</span><span class="sxs-lookup"><span data-stu-id="fec45-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="fec45-121">使用 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，將 `SimpleControl` 元素放在表單上。</span><span class="sxs-lookup"><span data-stu-id="fec45-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="fec45-122">如需詳細資訊，請參閱[逐步解說：在 Windows Forms 中裝載立體 WPF 複合控制項](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="fec45-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="fec45-123">新增可當地語系化的內容</span><span class="sxs-lookup"><span data-stu-id="fec45-123">Adding Localizable Content</span></span>

<span data-ttu-id="fec45-124">接下來，您將加入 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 標籤控制項，並將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素的內容設定為可當地語系化的字串。</span><span class="sxs-lookup"><span data-stu-id="fec45-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="fec45-125">新增可當地語系化的內容</span><span class="sxs-lookup"><span data-stu-id="fec45-125">To add localizable content</span></span>

1. <span data-ttu-id="fec45-126">在**方案總管**中，按兩下**simplecontrol.xaml**以在 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]中開啟它。</span><span class="sxs-lookup"><span data-stu-id="fec45-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2. <span data-ttu-id="fec45-127">使用下列程式碼來設定 <xref:System.Windows.Controls.Button> 控制項的內容。</span><span class="sxs-lookup"><span data-stu-id="fec45-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="fec45-128">在**方案總管**中，按兩下 [ **Form1** ]，在 Windows Form 設計工具中將它開啟。</span><span class="sxs-lookup"><span data-stu-id="fec45-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="fec45-129">開啟 [**工具箱**] 並按兩下 [**標籤**]，將標籤控制項新增至表單。</span><span class="sxs-lookup"><span data-stu-id="fec45-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="fec45-130">將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性的值設定為 `"Hello"`。</span><span class="sxs-lookup"><span data-stu-id="fec45-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="fec45-131">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="fec45-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="fec45-132">`SimpleControl` 元素和標籤控制項都會顯示 **"Hello"** 文字。</span><span class="sxs-lookup"><span data-stu-id="fec45-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="fec45-133">啟用當地語系化</span><span class="sxs-lookup"><span data-stu-id="fec45-133">Enabling Localization</span></span>

<span data-ttu-id="fec45-134">Windows Forms 設計工具提供在附屬組件中啟用當地語系化的設定。</span><span class="sxs-lookup"><span data-stu-id="fec45-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="fec45-135">啟用當地語系化</span><span class="sxs-lookup"><span data-stu-id="fec45-135">To enable localization</span></span>

1. <span data-ttu-id="fec45-136">在**方案總管**中，按兩下**Form1.cs**以在 Windows Form 設計工具中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="fec45-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="fec45-137">在 [**屬性**] 視窗中，將表單可**當地語系化**屬性的值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fec45-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="fec45-138">在 [**屬性**] 視窗中，將 [ **Language** ] 屬性的值設定為 [**西班牙文（西班牙）** ]。</span><span class="sxs-lookup"><span data-stu-id="fec45-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="fec45-139">在 [Windows Forms 設計工具] 中，選取 Label 控制項。</span><span class="sxs-lookup"><span data-stu-id="fec45-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="fec45-140">在 [**屬性**] 視窗中，將 [<xref:System.Windows.Forms.Control.Text%2A>] 屬性的值設定為 [`"Hola"`]。</span><span class="sxs-lookup"><span data-stu-id="fec45-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="fec45-141">名為 Form1.es-ES.resx 的新資源檔會新增至專案。</span><span class="sxs-lookup"><span data-stu-id="fec45-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="fec45-142">在**方案總管**中，以滑鼠右鍵按一下**Form1.cs** ，然後按一下 [**查看程式碼**]，在程式碼編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="fec45-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="fec45-143">在呼叫 `InitializeComponent`之前，將下列程式碼複製到 `Form1` 的函式中。</span><span class="sxs-lookup"><span data-stu-id="fec45-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="fec45-144">在**方案總管**中，以滑鼠右鍵按一下**LocalizingWpfInWf** ，然後按一下 **[卸載專案**]。</span><span class="sxs-lookup"><span data-stu-id="fec45-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="fec45-145">專案名稱已標記為 **（無法使用）** 。</span><span class="sxs-lookup"><span data-stu-id="fec45-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="fec45-146">以滑鼠右鍵按一下 [ **LocalizingWpfInWf**]，然後按一下 [**編輯 LocalizingWpfInWf**]。</span><span class="sxs-lookup"><span data-stu-id="fec45-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="fec45-147">隨即在程式碼編輯器中開啟專案檔。</span><span class="sxs-lookup"><span data-stu-id="fec45-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="fec45-148">將下面這一行複製到專案檔中的第一個 `PropertyGroup`。</span><span class="sxs-lookup"><span data-stu-id="fec45-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="fec45-149">儲存並關閉專案檔。</span><span class="sxs-lookup"><span data-stu-id="fec45-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="fec45-150">在**方案總管**中，以滑鼠右鍵按一下**LocalizingWpfInWf** ，然後按一下 [**重載專案**]。</span><span class="sxs-lookup"><span data-stu-id="fec45-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="fec45-151">指派資源識別碼</span><span class="sxs-lookup"><span data-stu-id="fec45-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="fec45-152">您可以使用資源識別碼，將可當地語系化的內容對應至資源組件。</span><span class="sxs-lookup"><span data-stu-id="fec45-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="fec45-153">當您指定 `updateuid` 選項時，Msbuild.exe 應用程式會自動指派資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="fec45-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="fec45-154">指派資源識別碼</span><span class="sxs-lookup"><span data-stu-id="fec45-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="fec45-155">在 [開始] 功能表中，開啟 Visual Studio 的 [開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="fec45-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="fec45-156">使用下列命令，將資源識別碼指派給可當地語系化的內容。</span><span class="sxs-lookup"><span data-stu-id="fec45-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="fec45-157">在**方案總管**中，按兩下**simplecontrol.xaml** ，在程式碼編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="fec45-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="fec45-158">您會看到 `msbuild` 命令已將 `Uid` 屬性新增至所有元素。</span><span class="sxs-lookup"><span data-stu-id="fec45-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="fec45-159">這有助於透過資源識別碼指派進行當地語系化。</span><span class="sxs-lookup"><span data-stu-id="fec45-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="fec45-160">按**F6**以建立方案。</span><span class="sxs-lookup"><span data-stu-id="fec45-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="fec45-161">使用 LocBaml 產生附屬組件</span><span class="sxs-lookup"><span data-stu-id="fec45-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="fec45-162">您的當地語系化內容會儲存在僅限資源的*附屬元件*中。</span><span class="sxs-lookup"><span data-stu-id="fec45-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="fec45-163">使用命令列工具 LocBaml，為您的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容產生當地語系化的元件。</span><span class="sxs-lookup"><span data-stu-id="fec45-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="fec45-164">產生附屬組件</span><span class="sxs-lookup"><span data-stu-id="fec45-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="fec45-165">將 LocBaml.exe 複製至專案的 obj\Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fec45-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="fec45-166">如需詳細資訊，請參閱[將應用程式當地語系化](how-to-localize-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="fec45-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="fec45-167">在 [命令提示字元] 視窗中，使用下列命令來將資源字串擷取至暫存檔。</span><span class="sxs-lookup"><span data-stu-id="fec45-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="fec45-168">使用 Visual Studio 或其他文字編輯器開啟 temp .csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="fec45-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="fec45-169">將字串 `"Hello"` 取代為其西班牙文翻譯，`"Hola"`。</span><span class="sxs-lookup"><span data-stu-id="fec45-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="fec45-170">儲存 temp.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="fec45-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="fec45-171">使用下列命令來產生已當地語系化的資源檔。</span><span class="sxs-lookup"><span data-stu-id="fec45-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="fec45-172">LocalizingWpfInWf.g.es-ES.resources 檔案會在 obj\Debug 資料夾中建立。</span><span class="sxs-lookup"><span data-stu-id="fec45-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="fec45-173">使用下列命令來建置已當地語系化的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="fec45-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="fec45-174">LocalizingWpfInWf.resources.dll 檔案會在 obj\Debug 資料夾中建立。</span><span class="sxs-lookup"><span data-stu-id="fec45-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="fec45-175">將 LocalizingWpfInWf.resources.dll 檔案複製至專案的 bin\Debug\es-ES 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fec45-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="fec45-176">取代現有檔案。</span><span class="sxs-lookup"><span data-stu-id="fec45-176">Replace the existing file.</span></span>

8. <span data-ttu-id="fec45-177">執行 LocalizingWpfInWf.exe，其位於專案的 bin\Debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="fec45-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="fec45-178">請不要重建應用程式，否則將會覆寫附屬組件。</span><span class="sxs-lookup"><span data-stu-id="fec45-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="fec45-179">應用程式會顯示當地語系化字串，而不是英文字串。</span><span class="sxs-lookup"><span data-stu-id="fec45-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="fec45-180">請參閱</span><span class="sxs-lookup"><span data-stu-id="fec45-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="fec45-181">將應用程式當地語系化</span><span class="sxs-lookup"><span data-stu-id="fec45-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="fec45-182">[逐步解說：當地語系化 Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fec45-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="fec45-183">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="fec45-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
