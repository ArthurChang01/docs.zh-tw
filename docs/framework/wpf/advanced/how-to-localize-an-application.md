---
title: 如何：將應用程式當地語系化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174208"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="d575d-102">如何：將應用程式當地語系化</span><span class="sxs-lookup"><span data-stu-id="d575d-102">How to: Localize an Application</span></span>
<span data-ttu-id="d575d-103">本教學課程說明如何使用 LocBaml 工具來建立當地語系化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d575d-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d575d-104">LocBaml 工具不是可實際執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d575d-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="d575d-105">這只是個範例，示範如何使用一些當地語系化的 API，並說明如何撰寫當地語系化工具。</span><span class="sxs-lookup"><span data-stu-id="d575d-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>
## <a name="overview"></a><span data-ttu-id="d575d-106">概觀</span><span class="sxs-lookup"><span data-stu-id="d575d-106">Overview</span></span>  
 <span data-ttu-id="d575d-107">此討論提供將應用程式當地語系化的逐步方法。</span><span class="sxs-lookup"><span data-stu-id="d575d-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="d575d-108">首先，您要準備您的應用程式，以便從中擷取要轉譯的文字。</span><span class="sxs-lookup"><span data-stu-id="d575d-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="d575d-109">轉譯文字之後，您要轉譯的文字合併至原始應用程式的新複本中。</span><span class="sxs-lookup"><span data-stu-id="d575d-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>
## <a name="requirements"></a><span data-ttu-id="d575d-110">需求</span><span class="sxs-lookup"><span data-stu-id="d575d-110">Requirements</span></span>  
 <span data-ttu-id="d575d-111">在討論過程中，您將使用 Microsoft 生成引擎 （MSBuild），該引擎是從命令列運行的編譯器。</span><span class="sxs-lookup"><span data-stu-id="d575d-111">Over the course of this discussion, you will use Microsoft build engine (MSBuild), which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="d575d-112">此外，也會指引您使用專案檔。</span><span class="sxs-lookup"><span data-stu-id="d575d-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="d575d-113">有關如何使用 MSBuild 和專案檔案的說明，請參閱[生成和部署](../app-development/building-and-deploying-wpf-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="d575d-113">For instructions on how to use MSBuild and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="d575d-114">此討論中的所有範例都是使用 en-US (美式英文) 做為文化特性。</span><span class="sxs-lookup"><span data-stu-id="d575d-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="d575d-115">這可讓您逐步執行範例中的所有步驟，而不需要安裝不同的語言。</span><span class="sxs-lookup"><span data-stu-id="d575d-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a><span data-ttu-id="d575d-116">建立範例應用程式</span><span class="sxs-lookup"><span data-stu-id="d575d-116">Create a Sample Application</span></span>  
 <span data-ttu-id="d575d-117">在此步驟中，您將準備要當地語系化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d575d-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="d575d-118">在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 範例中有提供一個 HelloApp 範例，將用於此討論中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="d575d-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="d575d-119">如果要使用此示例，請從[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)][LocBaml 工具示例](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)下載檔案。</span><span class="sxs-lookup"><span data-stu-id="d575d-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="d575d-120">將您的應用程式開發至您要當地語系化的開始點。</span><span class="sxs-lookup"><span data-stu-id="d575d-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="d575d-121">在專案檔案中指定開發語言，以便 MSBuild 生成主程式集和附屬程式集（具有 .resources.dll 副檔名的檔）以包含中性語言資源。</span><span class="sxs-lookup"><span data-stu-id="d575d-121">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="d575d-122">HelloApp 範例中的專案檔是 HelloApp.csproj。</span><span class="sxs-lookup"><span data-stu-id="d575d-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="d575d-123">在該檔案中，您會發現識別如下的開發語言：</span><span class="sxs-lookup"><span data-stu-id="d575d-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="d575d-124">將 UID 加入您的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案。</span><span class="sxs-lookup"><span data-stu-id="d575d-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="d575d-125">UID 可用來追蹤對檔案的變更，以及識別必須轉譯的項目。</span><span class="sxs-lookup"><span data-stu-id="d575d-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="d575d-126">要將 Uid 添加到檔，請在專案檔案上運行**更新：**</span><span class="sxs-lookup"><span data-stu-id="d575d-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="d575d-127">**msbuild -t：更新helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="d575d-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="d575d-128">要驗證您沒有丟失或重複的 Uid，請運行**checkuid**：</span><span class="sxs-lookup"><span data-stu-id="d575d-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="d575d-129">**msbuild -t：checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="d575d-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="d575d-130">運行**updateuid**後，您的檔應包含 Uids。</span><span class="sxs-lookup"><span data-stu-id="d575d-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="d575d-131">例如，在 HelloApp 的 Pane1.xaml 檔案中，您應該會發現下列項目：</span><span class="sxs-lookup"><span data-stu-id="d575d-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="d575d-132">建立中性語言資源附屬組件</span><span class="sxs-lookup"><span data-stu-id="d575d-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="d575d-133">設定應用程式來產生中性語言資源附屬組件之後，您要建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="d575d-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="d575d-134">這會產生主應用程式組件，以及 LocBaml 進行當地語系化所需的中性語言資源附屬組件。</span><span class="sxs-lookup"><span data-stu-id="d575d-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="d575d-135">若要建置應用程式：</span><span class="sxs-lookup"><span data-stu-id="d575d-135">To build the application:</span></span>  
  
1. <span data-ttu-id="d575d-136">編譯 HelloApp 以創建動態連結程式庫 （DLL）：</span><span class="sxs-lookup"><span data-stu-id="d575d-136">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
     <span data-ttu-id="d575d-137">**msbuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="d575d-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="d575d-138">新建立的主應用程式組件 HelloApp.exe 會建立在下列資料夾中：</span><span class="sxs-lookup"><span data-stu-id="d575d-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="d575d-139">新建立的中性語言資源附屬組件 HelloApp.resources.dll 會建立下列資料夾中：</span><span class="sxs-lookup"><span data-stu-id="d575d-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="d575d-140">建置 LocBaml 工具</span><span class="sxs-lookup"><span data-stu-id="d575d-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="d575d-141">建置 LocBaml 時所需的所有檔案都位在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 範例中。</span><span class="sxs-lookup"><span data-stu-id="d575d-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="d575d-142">從[LocBaml 工具示例](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)下載 C# 檔。</span><span class="sxs-lookup"><span data-stu-id="d575d-142">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="d575d-143">從命令列執行專案檔 (locbaml.csproj)，以建置工具：</span><span class="sxs-lookup"><span data-stu-id="d575d-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="d575d-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="d575d-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="d575d-145">移至 Bin\Release 目錄，尋找新建立的可執行檔 (locbaml.exe)。</span><span class="sxs-lookup"><span data-stu-id="d575d-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="d575d-146">範例：C:\LocBaml\Bin\Release\locbaml.exe。</span><span class="sxs-lookup"><span data-stu-id="d575d-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="d575d-147">當您執行 LocBaml 時，可指定的選項如下：</span><span class="sxs-lookup"><span data-stu-id="d575d-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="d575d-148">**解析**或 **-p：** 分析 Baml、資源或 DLL 檔以生成 .csv 或 .txt 檔。</span><span class="sxs-lookup"><span data-stu-id="d575d-148">**parse** or **-p:** Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="d575d-149">**生成**或 **-g：** 使用已翻譯的檔生成當地語系化的二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="d575d-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="d575d-150">**輸出**或 **-o** [*檔目錄*] **：** 輸出檔案名。</span><span class="sxs-lookup"><span data-stu-id="d575d-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="d575d-151">**區域性**或 **-cul** =*區域性*= **：** 輸出程式集的局部性。</span><span class="sxs-lookup"><span data-stu-id="d575d-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="d575d-152">**翻譯**或 **-轉**式 [*翻譯.csv*] **：** 翻譯或當地語系化檔。</span><span class="sxs-lookup"><span data-stu-id="d575d-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="d575d-153">**asmpath**或 **-asmpath：** [*檔目錄*] **：** 如果[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]代碼包含自訂控制項，則必須向自訂控制項程式集提供**asmpath。**</span><span class="sxs-lookup"><span data-stu-id="d575d-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="d575d-154">**nologo：** 顯示無標誌或著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="d575d-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="d575d-155">**verbose：** 顯示詳細模式資訊。</span><span class="sxs-lookup"><span data-stu-id="d575d-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d575d-156">如果您在運行該工具時需要選項清單，請鍵入**LocBaml.exe**並按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="d575d-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="d575d-157">使用 LocBaml 來剖析檔案</span><span class="sxs-lookup"><span data-stu-id="d575d-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="d575d-158">現在您已經建立 LocBaml 工具，就準備好用它來剖析 HelloApp.resources.dll，以擷取要當地語系化的文字內容。</span><span class="sxs-lookup"><span data-stu-id="d575d-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="d575d-159">將 LocBaml.exe 複製到應用程式的 bin\debug 資料夾，這是建立主要應用程式組件的位置。</span><span class="sxs-lookup"><span data-stu-id="d575d-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="d575d-160">若要剖析附屬組件檔案，並將輸出儲存成 .csv 檔案，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="d575d-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="d575d-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="d575d-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d575d-162">如果輸入檔 HelloApp.resources.dll 不是在與 LocBaml.exe 相同的目錄中，請移動其中一個檔案，讓這兩個檔案都在相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="d575d-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="d575d-163">當您執行 LocBaml 來剖析檔案時，輸出中會包含以逗號 (.csv 檔案) 或定位點 (.txt 檔) 分隔的七個欄位。</span><span class="sxs-lookup"><span data-stu-id="d575d-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="d575d-164">下面顯示針對 HelloApp.resources.dll 所剖析的 .csv 檔案：</span><span class="sxs-lookup"><span data-stu-id="d575d-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="d575d-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="d575d-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="d575d-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="d575d-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="d575d-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="d575d-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="d575d-168">這七個欄位為：</span><span class="sxs-lookup"><span data-stu-id="d575d-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="d575d-169">**BAML 名稱**。</span><span class="sxs-lookup"><span data-stu-id="d575d-169">**BAML Name**.</span></span> <span data-ttu-id="d575d-170">有關來源語言附屬組件的 BAML 資源名稱。</span><span class="sxs-lookup"><span data-stu-id="d575d-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="d575d-171">**資源金鑰**。</span><span class="sxs-lookup"><span data-stu-id="d575d-171">**Resource Key**.</span></span> <span data-ttu-id="d575d-172">當地語系化的資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="d575d-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="d575d-173">**類別**。</span><span class="sxs-lookup"><span data-stu-id="d575d-173">**Category**.</span></span> <span data-ttu-id="d575d-174">值型別。</span><span class="sxs-lookup"><span data-stu-id="d575d-174">The value type.</span></span> <span data-ttu-id="d575d-175">請參閱[當地語系化屬性和注釋](localization-attributes-and-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="d575d-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="d575d-176">**可讀性**。</span><span class="sxs-lookup"><span data-stu-id="d575d-176">**Readability**.</span></span> <span data-ttu-id="d575d-177">當地語系化工具是否能夠讀取該值。</span><span class="sxs-lookup"><span data-stu-id="d575d-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="d575d-178">請參閱[當地語系化屬性和注釋](localization-attributes-and-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="d575d-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="d575d-179">**可修改性**。</span><span class="sxs-lookup"><span data-stu-id="d575d-179">**Modifiability**.</span></span> <span data-ttu-id="d575d-180">當地語系化工具是否能夠修改該值。</span><span class="sxs-lookup"><span data-stu-id="d575d-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="d575d-181">請參閱[當地語系化屬性和注釋](localization-attributes-and-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="d575d-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="d575d-182">**評論**.</span><span class="sxs-lookup"><span data-stu-id="d575d-182">**Comments**.</span></span> <span data-ttu-id="d575d-183">該值的其他說明，有助於判斷某值當地語系化的方式。</span><span class="sxs-lookup"><span data-stu-id="d575d-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="d575d-184">請參閱[當地語系化屬性和注釋](localization-attributes-and-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="d575d-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="d575d-185">**值**。</span><span class="sxs-lookup"><span data-stu-id="d575d-185">**Value**.</span></span> <span data-ttu-id="d575d-186">要轉譯成所需文化特性的文字值。</span><span class="sxs-lookup"><span data-stu-id="d575d-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="d575d-187">下表顯示這些欄位如何對應至 .csv 檔案的分隔值：</span><span class="sxs-lookup"><span data-stu-id="d575d-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="d575d-188">BAML 名稱</span><span class="sxs-lookup"><span data-stu-id="d575d-188">BAML name</span></span>|<span data-ttu-id="d575d-189">資源索引鍵</span><span class="sxs-lookup"><span data-stu-id="d575d-189">Resource key</span></span>|<span data-ttu-id="d575d-190">類別</span><span class="sxs-lookup"><span data-stu-id="d575d-190">Category</span></span>|<span data-ttu-id="d575d-191">可讀性</span><span class="sxs-lookup"><span data-stu-id="d575d-191">Readability</span></span>|<span data-ttu-id="d575d-192">可修改性</span><span class="sxs-lookup"><span data-stu-id="d575d-192">Modifiability</span></span>|<span data-ttu-id="d575d-193">註解</span><span class="sxs-lookup"><span data-stu-id="d575d-193">Comments</span></span>|<span data-ttu-id="d575d-194">值</span><span class="sxs-lookup"><span data-stu-id="d575d-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="d575d-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="d575d-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="d575d-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="d575d-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="d575d-197">略過</span><span class="sxs-lookup"><span data-stu-id="d575d-197">Ignore</span></span>|<span data-ttu-id="d575d-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="d575d-198">FALSE</span></span>|<span data-ttu-id="d575d-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="d575d-199">FALSE</span></span>||<span data-ttu-id="d575d-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="d575d-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="d575d-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="d575d-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="d575d-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="d575d-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="d575d-203">None</span><span class="sxs-lookup"><span data-stu-id="d575d-203">None</span></span>|<span data-ttu-id="d575d-204">TRUE</span><span class="sxs-lookup"><span data-stu-id="d575d-204">TRUE</span></span>|<span data-ttu-id="d575d-205">TRUE</span><span class="sxs-lookup"><span data-stu-id="d575d-205">TRUE</span></span>||<span data-ttu-id="d575d-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="d575d-206">Hello World</span></span>|
   |<span data-ttu-id="d575d-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="d575d-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="d575d-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="d575d-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="d575d-209">None</span><span class="sxs-lookup"><span data-stu-id="d575d-209">None</span></span>|<span data-ttu-id="d575d-210">TRUE</span><span class="sxs-lookup"><span data-stu-id="d575d-210">TRUE</span></span>|<span data-ttu-id="d575d-211">TRUE</span><span class="sxs-lookup"><span data-stu-id="d575d-211">TRUE</span></span>||<span data-ttu-id="d575d-212">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="d575d-212">Goodbye World</span></span>|
  
   <span data-ttu-id="d575d-213">請注意，"注釋"欄位的所有值不包含任何值;因此，注釋欄位的所有值都不包含"**注釋"** 欄位的所有值。如果欄位沒有值，則該欄位為空。</span><span class="sxs-lookup"><span data-stu-id="d575d-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="d575d-214">另請注意，第一行中的項既不可讀，也不可修改，並且具有"忽略"作為其**類別**值，所有這些都指示該值不可當地語系化。</span><span class="sxs-lookup"><span data-stu-id="d575d-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="d575d-215">為了便於在解析檔中（特別是在大型檔中）發現可當地語系化項，您可以按**類別**、**可讀性和\*\*\*\*可修改性**對項進行排序或篩選。</span><span class="sxs-lookup"><span data-stu-id="d575d-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="d575d-216">例如，您可以篩選出無法讀取及無法修改的值。</span><span class="sxs-lookup"><span data-stu-id="d575d-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a><span data-ttu-id="d575d-217">轉譯可當地語系化的內容</span><span class="sxs-lookup"><span data-stu-id="d575d-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="d575d-218">使用您可以用來轉譯擷取內容的任何工具。</span><span class="sxs-lookup"><span data-stu-id="d575d-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="d575d-219">執行此操作的一個好方法是將資源寫入 .csv 檔並在 Microsoft Excel 中查看它們，對最後一列（值）進行翻譯更改。</span><span class="sxs-lookup"><span data-stu-id="d575d-219">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="d575d-220">使用 LocBaml 來產生新的 .resources.dll 檔案</span><span class="sxs-lookup"><span data-stu-id="d575d-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="d575d-221">藉由使用 LocBaml 來剖析 HelloApp.resources.dll 而識別的內容已轉譯，且必須合併回原始應用程式。</span><span class="sxs-lookup"><span data-stu-id="d575d-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="d575d-222">使用**生成**或 **-g**選項生成新的 .resources.DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="d575d-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="d575d-223">使用下列語法來產生新的 HelloApp.resources.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="d575d-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="d575d-224">將文化特性標示為 en-US (/cul:en-US)。</span><span class="sxs-lookup"><span data-stu-id="d575d-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="d575d-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="d575d-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d575d-226">如果輸入檔 Hello.csv 不是在與可執行檔 LocBaml.exe 相同的目錄中，請移動其中一個檔案，讓這兩個檔案都在相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="d575d-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="d575d-227">以新建立的 HelloApp.resources.dll 檔案，取代 C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll 目錄中舊的 HelloApp.resources.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="d575d-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="d575d-228">"Hello World" 和 "Goodbye World" 現在應該已在您的應用程式中轉譯。</span><span class="sxs-lookup"><span data-stu-id="d575d-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="d575d-229">若要轉譯為不同的文化特性，請使用您想要轉譯之語言的文化特性。</span><span class="sxs-lookup"><span data-stu-id="d575d-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="d575d-230">下列範例示範如何轉譯成加拿大法文：</span><span class="sxs-lookup"><span data-stu-id="d575d-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="d575d-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="d575d-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="d575d-232">在與主應用程式組件相同的組件中，建立新的特定文化特性資料夾，以存放新的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="d575d-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="d575d-233">針對加拿大法文，資料夾會是 fr-CA。</span><span class="sxs-lookup"><span data-stu-id="d575d-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="d575d-234">將所產生的附屬組件複製到新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d575d-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="d575d-235">若要測試新的附屬組件，您需要變更您的應用程式用來執行的文化特性。</span><span class="sxs-lookup"><span data-stu-id="d575d-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="d575d-236">您可以使用下列其中一種作法：</span><span class="sxs-lookup"><span data-stu-id="d575d-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="d575d-237">更改作業系統的地區設定 （**開始**&#124;**控制台**&#124;**區域和語言選項**）。</span><span class="sxs-lookup"><span data-stu-id="d575d-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="d575d-238">在您的應用程式中，將下列程式碼加入 App.xaml.cs：</span><span class="sxs-lookup"><span data-stu-id="d575d-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="d575d-239">使用 LocBaml 的一些秘訣</span><span class="sxs-lookup"><span data-stu-id="d575d-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="d575d-240">用來定義自訂控制項的所有相依組件，都必須複製到 LocBaml 的本機目錄中，或安裝至 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="d575d-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="d575d-241">這是必需的，因為當地語系化 API 在讀取二進位 XAML （BAML） 時必須有權訪問依存性程式集。</span><span class="sxs-lookup"><span data-stu-id="d575d-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="d575d-242">如果主要組件已簽署，所產生的資源 DLL 也必須簽署，才能將其載入。</span><span class="sxs-lookup"><span data-stu-id="d575d-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="d575d-243">當地語系化資源 DLL 的版本必須與主要組件同步處理。</span><span class="sxs-lookup"><span data-stu-id="d575d-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a><span data-ttu-id="d575d-244">接下來</span><span class="sxs-lookup"><span data-stu-id="d575d-244">What's Next</span></span>  
 <span data-ttu-id="d575d-245">您現在對於如何使用 LocBaml 工具，應該有基本的了解。</span><span class="sxs-lookup"><span data-stu-id="d575d-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="d575d-246">您應該能夠建立包含 UID 的檔案。</span><span class="sxs-lookup"><span data-stu-id="d575d-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="d575d-247">藉由使用 LocBaml 工具，您應該能夠剖析檔案來擷取可當地語系化的內容，而在內容轉譯之後，您應該能夠產生將轉譯內容合併的 .resources.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="d575d-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="d575d-248">本主題可能無法顧及所有細節，但是您現在已經有了使用 LocBaml 將應用程式當地語系化所需的知識。</span><span class="sxs-lookup"><span data-stu-id="d575d-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d575d-249">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d575d-249">See also</span></span>

- [<span data-ttu-id="d575d-250">WPF 的全球化</span><span class="sxs-lookup"><span data-stu-id="d575d-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="d575d-251">使用自動配置概觀</span><span class="sxs-lookup"><span data-stu-id="d575d-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
