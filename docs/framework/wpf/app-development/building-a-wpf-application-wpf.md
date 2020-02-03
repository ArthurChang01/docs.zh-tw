---
title: 編譯應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: 00c76dfcdcedc7ceaefaaae785368f8b343457a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744760"
---
# <a name="compile-a-wpf-application"></a>編譯 WPF 應用程式

Windows Presentation Foundation （WPF）應用程式可以建立為 .NET Framework 可執行檔（.exe）、程式庫（.dll），或這兩種元件類型的組合。 本主題將介紹如何建立 WPF 應用程式，並說明組建流程中的主要步驟。

<a name="Building_a_WPF_Application_using_Command_Line"></a>

## <a name="building-a-wpf-application"></a>建置 WPF 應用程式

WPF 應用程式可透過下列方式編譯：

- 命令列。 應用程式只能包含程式碼 (沒有 XAML) 和一個應用程式定義檔。 如需詳細資訊，請參閱[使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列建置 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。

- Microsoft Build Engine (MSBuild)。 除了程式碼和 XAML 檔案，應用程式還必須包含 MSBuild 專案檔。 如需詳細資訊，請參閱＜MSBuild＞。

- Visual Studio. Visual Studio 是整合式開發環境，可使用 MSBuild 編譯 WPF 應用程式，並包含用於建立 UI 的視覺化設計工具。 如需詳細資訊，請參閱[在 Visual Studio 中](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)使用 Visual Studio 和設計 XAML 來[撰寫和管理程式碼](/visualstudio/ide/index-writing-code)。

<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>

## <a name="wpf-build-pipeline"></a>WPF 組建管線

建立 WPF 專案時，會叫用語言特定和 WPF 特定目標的組合。 執行這些目標的程序稱為組建管線，下圖說明主要步驟。

![WPF 組建進程](./media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")

<a name="Pre_Build_Initializations"></a>

### <a name="pre-build-initializations"></a>建置前初始化

建立之前，MSBuild 會決定重要工具和程式庫的位置，包括下列各項：

- .NET Framework。

- Windows SDK 目錄。

- WPF 參考元件的位置。

- 組件搜尋路徑的屬性。

MSBuild 搜尋元件的第一個位置是參考元件目錄（%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\）。 在此步驟期間，建置流程也會初始化各種屬性和項目群組，並執行任何必要的清除工作。

<a name="Resolving_references"></a>

### <a name="resolving-references"></a>解析參考

建置流程會找出並繫結建置應用程式專案所需的組件。 此邏輯包含在 `ResolveAssemblyReference` 工作中。 在專案檔中宣告為 `Reference` 的所有組件會連同有關系統上已安裝組件之搜尋路徑和中繼資料的資訊，一起提供給工作。 此工作會查詢元件，並使用已安裝元件的中繼資料，篩選出不需要在輸出資訊清單中顯示的核心 WPF 元件。 這樣做是為了避免在 ClickOnce 資訊清單中出現多餘的資訊。 例如，由於 PresentationFramework 可視為建立在上的應用程式和 WPF 的代表，而且所有的 WPF 元件都存在於安裝 .NET Framework 的每部電腦上的相同位置，因此不需要全部包含資訊清單中所有 .NET Framework 參考元件的資訊。

<a name="Markup_Compilation___Pass_1"></a>

### <a name="markup-compilationpass-1"></a>標記編譯 - 第一階段

在此步驟中，會剖析並編譯 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的檔案，讓執行時間不會花費時間剖析 XML 和驗證屬性值。 已編譯的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案會預先語彙基元化，因此在執行階段將它載入時，應該會比載入 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案更快。

在此步驟期間，以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 組建項目表示的每個 `Page` 檔案會發生下列活動：

1. 標記編譯器會剖析 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案。

2. 建立該 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的編譯表示，並複製到 obj\Release 資料夾。

3. 建立新部分類別的 CodeDOM 表示，並複製到 obj\Release 資料夾。

此外，每個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案會產生特定語言的程式碼檔。 例如，針對 Visual Basic 專案中的 Page1. xaml 頁面，會產生 Page1. g. .vb;若為C#專案中的 Page1. xaml 頁面，則會產生 Page1.g.cs。 檔案名稱中的 ".g" 表示檔案是產生的程式碼，其具有標記檔案最上層項目 (例如 `Page` 或 `Window`) 的部分類別宣告。 類別是使用中C#的 `partial` 修飾詞來宣告（Visual Basic 中的`Extends`），表示在其他地方有類別的另一個宣告，通常是在程式碼後置檔案 Page1.xaml.cs 中。

部分類別會從適當的基類（例如頁面的 <xref:System.Windows.Controls.Page>）延伸，並會執行 <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> 介面。 <xref:System.Windows.Markup.IComponentConnector> 介面具有初始化元件的方法，並連接其內容中專案的名稱和事件。 因此，產生的程式碼檔具有如下的方法實作：

```csharp
public void InitializeComponent() {
    if (_contentLoaded) {
        return;
    }
    _contentLoaded = true;
    System.Uri resourceLocater =
        new System.Uri(
            "window1.xaml",
            System.UriKind.RelativeOrAbsolute);
    System.Windows.Application.LoadComponent(this, resourceLocater);
}
```

```vb
Public Sub InitializeComponent() _

    If _contentLoaded Then
        Return
    End If

    _contentLoaded = True
    Dim resourceLocater As System.Uri = _
        New System.Uri("mainwindow.xaml", System.UriKind.Relative)

    System.Windows.Application.LoadComponent(Me, resourceLocater)

End Sub
```

根據預設，標記編譯會在與 MSBuild 引擎相同的 <xref:System.AppDomain> 中執行。 這會大幅提升效能。 您可以使用 `AlwaysCompileMarkupFilesInSeparateDomain` 屬性來切換此行為。 這有一項優點，就是卸載個別的 <xref:System.AppDomain>來卸載所有的參考元件。

<a name="Pass_2_of_Markup_Compilation"></a>

### <a name="markup-compilationpass-2"></a>標記編譯 - 第二階段

並非所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面都會在第一階段的標記編譯進行編譯。 已在本機定義類型參考 (相同專案中任何地方之程式碼中所定義的類型參考) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案就不是在此時編譯。 這是因為這些本機定義的類型只存在於來源中，而且尚未經過編譯。 為了判斷此情況，剖析器會使用牽涉到在標記檔案中尋找 `x:Name` 等項目的啟發方式。 找到這類執行個體之後，就會將標記檔案的編譯延後到程式碼檔編譯完成，在那之後，第二階段的標記編譯才會處理這些檔案。

<a name="File_Classification"></a>

### <a name="file-classification"></a>檔案分類

建置流程會根據作為目標位置的應用程式組件，將輸出檔案放在不同的資源群組中。 在一般未當地語系化的應用程式中，所有標記為 `Resource` 的資料檔案會放在主組件 (可執行檔或程式庫) 中。 當專案中已設定 `UICulture` 時，所有編譯的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案和特別標記為特定語言的資源會放在附屬資源組件中。 此外，所有非語言相關的資源會放在主組件中。 在建置流程的這個步驟中，會做出判斷。

專案檔中的 `ApplicationDefinition`、`Page` 和 `Resource` 建置動作可以用 `Localizable` 中繼資料 (可接受的值為 `true` 和 `false`) 增強，該中繼資料會指出檔案為特定語言或非語言相關。

<a name="Core_Compilation"></a>

### <a name="core-compilation"></a>核心編譯

核心編譯步驟牽涉到程式碼檔的編譯。 這是由特定語言之目標檔案 Microsoft.CSharp.targets 和 Microsoft.VisualBasic.targets 的邏輯進行協調。 如果啟發方式判斷標記編譯器的單一階段即已足夠，則會產生主組件。 不過，如果專案中有一或多個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案參考本機定義的類型，則會產生暫存 .dll 檔案，因此最終的應用程式組件可能會在標記編譯的第二階段完成之後建立。

<a name="Manifest_generation"></a>

### <a name="manifest-generation"></a>資訊清單產生

在組建程式結束時，當所有應用程式元件和內容檔案都準備就緒之後，就會產生應用程式的 ClickOnce 資訊清單。

部署資訊清單檔會描述部署模型︰目前的版本、更新行為，以及發行者身分識別和數位簽章。 此資訊清單預期是由處理部署的系統管理員所撰寫。 副檔名為 xbap （適用于 XAML 瀏覽器應用程式（Xbap））和應用程式（適用于已安裝的應用程式）。 前者是由 `HostInBrowser` 專案屬性所指定，因此資訊清單會將應用程式識別為由瀏覽器裝載。

應用程式資訊清單 (.exe.manifest 檔案) 會描述應用程式組件和相依程式庫，並列出應用程式所需的權限。 此檔案預期是由應用程式開發人員所撰寫。 為了啟動 ClickOnce 應用程式，使用者會開啟應用程式的部署資訊清單檔案。

這些資訊清單檔案一律會針對 Xbap 建立。 若是已安裝的應用程式，除非將專案檔中的 `GenerateManifests` 屬性指定為 `true` 值，否則不會建立這些檔案。

Xbap 會在指派給一般網際網路區域應用程式的許可權之外，取得兩個額外的許可權： <xref:System.Security.Permissions.WebBrowserPermission> 和 <xref:System.Security.Permissions.MediaPermission>。 WPF 組建系統會在應用程式資訊清單中宣告這些許可權。

<a name="Incremental_Build_Support"></a>

## <a name="incremental-build-support"></a>累加建置支援

WPF 組建系統提供累加式組建的支援。 該系統對於偵測標記或程式碼中所做的變更相當明確，而且只會編譯受變更影響的成品。 累加建置機制使用下列檔案：

- $(*組件名稱*)_MarkupCompiler.Cache 檔案，用於維護目前的編譯器狀態。

- $(*組件名稱*)_MarkupCompiler.lref 檔案，用於快取具有本機定義之類型參考的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案。

以下是管理累加建置的一組規則：

- 檔案是建置系統偵測變更的最小單位。 因此對於程式碼檔，建置系統無法得知是否變更類型或是否新增程式碼。 同樣的情況也適用於專案檔。

- 累加建置機制必須認定 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面有定義類別或使用其他類別。

- 如果 `Reference` 項目變更，則會重新編譯所有頁面。

- 如果程式碼檔變更，則會重新編譯所有具有本機定義之類型參考的頁面。

- 如果 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案變更：

  - 如果 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在專案中宣告為 `Page`：如果 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 沒有本機定義的類型參考，請重新編譯該 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，再加上所有具有本機參考的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面；如果 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 有本機參考，請重新編譯所有具有本機參考的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面。

  - 如果 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在專案中宣告為 `ApplicationDefinition`：重新編譯所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面（原因：每個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 都參考到可能已變更的 <xref:System.Windows.Application> 類型）。

- 如果專案檔將程式碼檔宣告為應用程式定義，而不是 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案：

  - 檢查專案檔中的 `ApplicationClassName` 值是否已變更 (是否有新的應用程式類型)。 如果是，請重新編譯整個應用程式。

  - 否則，請重新編譯所有具有本機參考的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面。

- 如果專案檔變更︰請套用所有前述規則，並查看哪些項目需要重新編譯。 對下列屬性的變更會觸發完整的重新編譯：`AssemblyName`、`IntermediateOutputPath`、`RootNamespace` 和 `HostInBrowser`。

以下是可能發生的重新編譯情節：

- 重新編譯整個應用程式。

- 只重新編譯具有本機定義之類型參考的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案。

- 不重新編譯任何項目 (如果專案中沒有任何變更)。

## <a name="see-also"></a>另請參閱

- [部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)
- [WPF MSBuild 參考](/visualstudio/msbuild/wpf-msbuild-reference)
- [WPF 中的 Pack URI](pack-uris-in-wpf.md)
- [WPF 應用程式資源、內容和資料檔案](wpf-application-resource-content-and-data-files.md)
