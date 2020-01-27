---
title: 增益集總覽
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: 93904e308932ea41c736ca849ce0efb200502a7e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738937"
---
# <a name="wpf-add-ins-overview"></a>WPF 增益集概觀

<a name="Introduction"></a>.NET Framework 包含一個增益集模型，開發人員可以用來建立支援增益集擴充性的應用程式。 此增益集模型可讓您建立增益集，整合並擴充應用程式的功能。 在某些情況下，應用程式也需要顯示增益集所提供的使用者介面。本主題說明 WPF 如何擴充 .NET Framework 增益集模型，以啟用這些案例、其背後的架構、優點和其限制。

<a name="Requirements"></a>

## <a name="prerequisites"></a>必要條件：

必須熟悉 .NET Framework 增益集模型。 如需詳細資訊，請參閱[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。

<a name="AddInsOverview"></a>

## <a name="add-ins-overview"></a>增益集概觀

為避免新功能包含複雜的應用程式重新編譯和重新部署，應用程式會實作擴充性機制，讓開發人員 (第一方和第三方) 建立整合它們的其他應用程式。 支援此擴充性類型最常見的方式是使用增益集 (也稱為「附加元件」和「外掛程式」)。 公開增益集擴充性的真實世界應用程式範例包括︰

- Internet Explorer 附加元件。

- Windows Media Player 外掛程式。

- Visual Studio 增益集。

例如，Windows Media Player 增益集模型讓協力廠商開發人員實作以各種方式擴充 Windows Media Player 的「外掛程式」，包括建立適用於 Windows Media Player 原本不支援之媒體格式的解碼器和編碼器 (例如 DVD、MP3)、音訊效果和面板。 每個增益集模型都是建置來公開對應用程式的獨特功能，雖然有幾個實體和行為通用所有的增益集模型。

一般增益集擴充性解決方案的三個主要實體是「合約」、「增益集」和「主應用程式」。 合約定義增益集與主應用程式整合的兩種方式︰

- 增益集整合主應用程式所實作的功能。

- 主應用程式公開要整合的增益集功能。

為能使用增益集，主應用程式需要在執行階段找到並載入它們。 因此，支援增益集的應用程式有下列額外的責任︰

- **探索**︰尋找遵守主應用程式所支援合約的增益集。

- **啟用**︰載入、執行及建立與增益集的通訊。

- **隔離**︰使用應用程式定義域或處理程序來建立隔離界限，保護應用程式不受增益集的潛在安全性和執行問題影響。

- **通訊**︰透過呼叫方法及傳送資料，讓增益集及主應用程式跨越隔離界限互相通訊。

- **存留期管理**︰以簡潔、可預測的方式載入和卸載應用程式定義域和處理程序 (請參閱[應用程式定義域](../../app-domains/application-domains.md))。

- **版本控制**︰確保建立任一新版本時，主應用程式和增益集仍可通訊。

最後，開發強固的增益集模型是重要的工作。 基於這個理由，.NET Framework 會提供基礎結構來建立增益集模型。

> [!NOTE]
> 如需增益集的詳細資訊，請參閱[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a>.NET Framework 增益集模型概觀

在 <xref:System.AddIn> 命名空間中找到的 .NET Framework 增益集模型包含一組類型，其設計目的是為了簡化增益集擴充性的開發。 .NET Framework 增益集模型的基本單位是*合約*，它會定義主應用程式和增益集彼此通訊的方式。 合約會向使用合約主應用程式特定「檢視」的主應用程式公開。 同樣地，合約的增益集專用「檢視」也會向增益集公開。 「配接器」用以讓主應用程式和增益集在其各自的合約檢視間進行通訊。 合約、檢視和配接器稱為區段，一組相關的區段構成「管線」。 管線是 .NET Framework 增益集模型支援探索、啟用、安全性隔離、執行隔離（使用應用程式域和進程）、通訊、存留期管理和版本設定的基礎。

這項支援的要點是讓開發人員建置增益集，整合主應用程式的功能。 不過，某些案例需要主應用程式顯示增益集所提供的使用者介面。由於 .NET Framework 中的每個呈現技術都有自己的模型來執行使用者介面，因此 .NET Framework 增益集模型不支援任何特定的呈現技術。 WPF 會以增益集的 UI 支援來擴充 .NET Framework 增益集模型。

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a>WPF 增益集

WPF 與 .NET Framework 增益集模型結合，可讓您處理各種需要主應用程式從增益集顯示使用者介面的案例。特別的是，WPF 會使用下列兩種程式設計模型來解決這些案例：

1. **增益集傳回 UI**。 增益集會透過方法呼叫（如合約所定義），將 UI 傳回到主應用程式。 此案例用於下列情況︰

    - 增益集所傳回之 UI 的外觀取決於只存在於執行時間的資料或條件，例如動態產生的報表。

    - 增益集提供之服務的 UI 與可使用增益集之主應用程式的 UI 不同。

    - 此增益集主要會執行主應用程式的服務，並使用 UI 向主應用程式報告狀態。

2. **增益集為 UI**。 增益集是使用者介面，如合約所定義。 此案例用於下列情況︰

    - 增益集不提供顯示以外的服務，例如廣告。

    - 增益集提供之服務的 UI 通用於所有可使用該增益集的主應用程式，例如計算機或色彩選擇器。

這些案例需要 UI 物件可以在主應用程式和增益集應用程式域之間傳遞。 由於 .NET Framework 增益集模型依賴遠端處理來進行應用程式域之間的通訊，因此在它們之間傳遞的物件必須可以遠端執行。

可在遠端處理的物件是執行下列一或多個工作的類別執行個體︰

- 衍生自 <xref:System.MarshalByRefObject> 類別。

- 實作 <xref:System.Runtime.Serialization.ISerializable> 介面。

- 已套用 <xref:System.SerializableAttribute> 屬性。

> [!NOTE]
> 如需有關建立可遠端 .NET Framework 物件的詳細資訊，請參閱[讓物件可遠端](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))處理。

WPF UI 類型無法遠端處理。 為了解決這個問題，WPF 擴充了 .NET Framework 增益集模型，讓增益集所建立的 WPF UI 能夠從主應用程式中顯示。 WPF 提供這項支援的兩種類型： <xref:System.AddIn.Contract.INativeHandleContract> 介面和兩個由 <xref:System.AddIn.Pipeline.FrameworkElementAdapters> 類別所執行的靜態方法： <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。 概括而言，這些類型和方法的使用方式如下︰

1. WPF 要求增益集所提供的使用者介面是直接或間接衍生自 <xref:System.Windows.FrameworkElement>的類別，例如圖形、控制項、使用者控制項、版面配置面板和頁面。

2. 當合約宣告 UI 會在增益集和主應用程式之間傳遞時，就必須將它宣告為 <xref:System.AddIn.Contract.INativeHandleContract> （而非 <xref:System.Windows.FrameworkElement>）;<xref:System.AddIn.Contract.INativeHandleContract> 是可遠端表示的增益集 UI，可以跨隔離界限傳遞。

3. 從增益集的應用程式域傳遞之前，會藉由呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，將 <xref:System.Windows.FrameworkElement> 封裝為 <xref:System.AddIn.Contract.INativeHandleContract>。

4. 傳遞至主應用程式的應用程式域之後，必須呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，將 <xref:System.AddIn.Contract.INativeHandleContract> 重新封裝為 <xref:System.Windows.FrameworkElement>。

<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 的使用方式，取決於特定案例。 下列各節提供每個程式設計模型的詳細資料。

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a>增益集傳回使用者介面

若要讓增益集將 UI 傳回給主應用程式，則需要下列各項：

1. 必須建立主應用程式、增益集和管線，如 .NET Framework[增益集和](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))擴充性檔中所述。

2. 合約必須執行 <xref:System.AddIn.Contract.IContract>，而若要傳回 UI，合約必須宣告具有 <xref:System.AddIn.Contract.INativeHandleContract>類型之傳回值的方法。

3. 在增益集與主應用程式之間傳遞的 UI，必須直接或間接衍生自 <xref:System.Windows.FrameworkElement>。

4. 增益集所傳回的 UI 必須先從 <xref:System.Windows.FrameworkElement> 轉換成 <xref:System.AddIn.Contract.INativeHandleContract>，才能跨越隔離界限。

5. 在跨越隔離界限之後，必須從 <xref:System.AddIn.Contract.INativeHandleContract> 將傳回的 UI 轉換成 <xref:System.Windows.FrameworkElement>。

6. 主應用程式會顯示傳回的 <xref:System.Windows.FrameworkElement>。

如需示範如何執行可傳回 UI 之增益集的範例，請參閱建立可傳回[ui 的增益集](how-to-create-an-add-in-that-returns-a-ui.md)。

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a>增益集是使用者介面

當增益集是 UI 時，需要下列各項：

1. 必須建立主應用程式、增益集和管線，如 .NET Framework[增益集和](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))擴充性檔中所述。

2. 增益集的合約介面必須執行 <xref:System.AddIn.Contract.INativeHandleContract>。

3. 傳遞至主應用程式的增益集必須直接或間接衍生自 <xref:System.Windows.FrameworkElement>。

4. 增益集必須先從 <xref:System.Windows.FrameworkElement> 轉換成 <xref:System.AddIn.Contract.INativeHandleContract>，才能跨越隔離界限。

5. 在跨越隔離界限之後，此增益集必須從 <xref:System.AddIn.Contract.INativeHandleContract> 轉換成 <xref:System.Windows.FrameworkElement>。

6. 主應用程式會顯示傳回的 <xref:System.Windows.FrameworkElement>。

如需示範如何執行屬於 UI 之增益集的範例，請參閱[建立屬於 ui 的增益集](how-to-create-an-add-in-that-is-a-ui.md)。

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a>從增益集傳回多個 UI

增益集通常會提供多個使用者介面來顯示主應用程式。 例如，假設有一個 UI 的增益集也提供主應用程式的狀態資訊，同時也是一個 UI。 像這樣的增益集的實作方法是，使用[增益集傳回使用者介面](#ReturnUIFromAddInContract)和[增益集是使用者介面](#AddInIsAUI)模型這兩種技術的組合。

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a>增益集和 XAML 瀏覽器應用程式

在到目前為止的範例中，主應用程式一直是已安裝的獨立應用程式。 但是，XAML 瀏覽器應用程式（Xbap）也可以裝載增益集，但具有下列額外的組建和執行需求：

- XBAP 應用程式資訊清單必須特別設定，才能將管線（資料夾和元件）和增益集元件下載至用戶端電腦上的 ClickOnce 應用程式快取（在與 XBAP 相同的資料夾中）。

- 用來探索及載入增益集的 XBAP 程式碼必須使用 XBAP 的 ClickOnce 應用程式快取，做為管線和增益集的位置。

- 如果增益集參考位於來源網站上的鬆散檔案，XBAP 就必須將增益集載入到特殊的安全性內容中。以 Xbap 裝載時，增益集只能參考位於主應用程式的來源網站上的鬆散檔案。

下列各小節將詳細說明這些工作。

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>設定 ClickOnce 部署的管線和增益集

Xbap 會下載至 ClickOnce 部署快取中的安全資料夾並從中執行。 為了讓 XBAP 裝載增益集，管線和增益集元件也必須下載至 safe 資料夾。 為達到此目的，您需要設定應用程式資訊清單包含管線和增益集組件以供下載。 雖然管線和增益集元件必須位於主機 XBAP 專案的根資料夾中，才能讓 Visual Studio 偵測管線元件，但這最容易在 Visual Studio 中完成。

因此，第一個步驟是設定每個管線元件和增益集元件專案的組建輸出，以將管線和增益集元件建立至 XBAP 專案的根目錄。 下表顯示管線元件專案和增益集元件專案的組建輸出路徑，其位於與主機 XBAP 專案相同的方案和根資料夾中。

表 1：XBAP 裝載之管線組件的組建輸出路徑

|管線組件專案|建置輸出路徑|
|-------------------------------|-----------------------|
|合約|`..\HostXBAP\Contracts\`|
|增益集檢視|`..\HostXBAP\AddInViews\`|
|增益集端配接器|`..\HostXBAP\AddInSideAdapters\`|
|主控件端配接器|`..\HostXBAP\HostSideAdapters\`|
|增益集|`..\HostXBAP\AddIns\WPFAddIn1`|

下一個步驟是執行下列動作，將管線元件和增益集元件指定為 Visual Studio 中的 Xbap 內容檔案：

1. 以滑鼠右鍵按一下方案總管中每個管線資料夾，然後選擇 [加入至專案]，在專案中包含管線和增益集組件。

2. 從 [屬性] 視窗將每個管線組件和增益集組件的 [建置動作] 設定為 [內容]。

最後一個步驟，是設定應用程式資訊清單包含管線組件檔和增益集組件檔以供下載。 檔案應該位於 XBAP 應用程式所佔用之 ClickOnce 快取資料夾根目錄的資料夾中。 您可以藉由執行下列動作，在 Visual Studio 中達到設定：

1. 以滑鼠右鍵按一下 XBAP 專案，依序按一下 [**屬性**]、[**發佈**]，然後按一下 [**應用程式檔**] 按鈕。

2. 在 [應用程式檔案] 對話方塊中，將每個管線和增益集 DLL 的 [發行狀態] 設成 [Include (Auto)] (包含 (自動))，並將每個管線和增益集 DLL 的 [下載群組] 設成 [(必要項)]。

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>使用來自應用程式基底的管線和增益集

當管線和增益集設定進行 ClickOnce 部署時，會將它們下載到與 XBAP 相同的 ClickOnce 快取資料夾。 若要從 XBAP 使用管線和增益集，XBAP 程式碼必須從應用程式基底取得它們。 使用管線和增益集之 .NET Framework 增益集模型的各種類型和成員，會針對此案例提供特殊支援。 首先，路徑是由 <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> 列舉值所識別。 您使用此值與相關增益集成員的多載處理使用包含下列各項的管線︰

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a>存取裝載的原始網站

為確保增益集能參考原始網站的檔案，必須使用相當於主應用程式的安全性隔離載入增益集。 此安全性層級是由 <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> 列舉值所識別，並在增益集啟動時傳遞至 <xref:System.AddIn.Hosting.AddInToken.Activate%2A> 方法。

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a>WPF 增益集架構

就如我們所見，WPF 可讓 .NET Framework 增益集使用 <xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>來執行使用者介面（這是直接或間接衍生自 <xref:System.Windows.FrameworkElement>）。 結果是主應用程式傳回的是從主應用程式的 UI 中顯示的 <xref:System.Windows.FrameworkElement>。

針對簡單的 UI 增益集案例，這是開發人員需求的詳細資料。 針對更複雜的案例，特別是嘗試使用其他 WPF 服務（例如版面配置、資源和資料系結）的情況，需要 WPF 如何擴充 .NET Framework 增益集模型與 UI 支援的詳細知識，以瞭解其優點和限制。

基本上，WPF 不會將 UI 從增益集傳遞至主應用程式;相反地，WPF 會使用 WPF 互通性來傳遞 UI 的 Win32 視窗控制碼。 因此，當增益集的 UI 傳遞至主應用程式時，將會發生下列情況：

- 在增益集端，WPF 會針對將由主應用程式顯示的 UI 取得視窗控制碼。 視窗控制碼是由衍生自 <xref:System.Windows.Interop.HwndSource> 並實 <xref:System.AddIn.Contract.INativeHandleContract>的內部 WPF 類別所封裝。 這個類別的實例是由 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 傳回，而且會從增益集的應用程式域封送處理到主應用程式的應用程式域。

- 在主應用程式端，WPF 會將 <xref:System.Windows.Interop.HwndSource> 重新封裝為衍生自 <xref:System.Windows.Interop.HwndHost> 的內部 WPF 類別，並使用 <xref:System.AddIn.Contract.INativeHandleContract>。 這個類別的實例會由 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 傳回給主應用程式。

<xref:System.Windows.Interop.HwndHost> 存在，可從 WPF 使用者介面顯示視窗控制碼所識別的使用者介面。 如需詳細資訊，請參閱 [WPF 和 Win32 互通](../advanced/wpf-and-win32-interoperation.md)。

總而言之，<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 都存在，可讓 WPF UI 的視窗控制碼從增益集傳遞至主應用程式，其中會由 <xref:System.Windows.Interop.HwndHost> 封裝，並顯示主應用程式的 UI。

> [!NOTE]
> 因為主應用程式會取得 <xref:System.Windows.Interop.HwndHost>，所以主應用程式無法將 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 傳回的物件轉換為增益集所實作為的型別（例如，<xref:System.Windows.Controls.UserControl>）。

根據其本質，<xref:System.Windows.Interop.HwndHost> 有某些限制，會影響主應用程式可以使用它們的方式。 不過，WPF 會使用增益集案例的數個功能來擴充 <xref:System.Windows.Interop.HwndHost>。 下文說明這些優點與限制。

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a>WPF 增益集的優點

由於 WPF 增益集使用者介面是從使用衍生自 <xref:System.Windows.Interop.HwndHost>之內部類別的主應用程式中顯示，因此這些使用者介面會受到與 WPF UI 服務（例如版面配置、轉譯、資料系結、樣式、範本和資源）相關的 <xref:System.Windows.Interop.HwndHost> 功能所限制。 不過，WPF 會以包含下列的其他功能來增強其內部 <xref:System.Windows.Interop.HwndHost> 子類別：

- 在主應用程式的 UI 與增益集的 UI 之間切換。 請注意，「增益集是 UI」程式設計模型需要增益集端介面卡覆寫 <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> 以啟用 tab 鍵，不論增益集是完全信任還是部分信任。

- 接受從主應用程式使用者介面顯示的增益集使用者介面的協助工具需求。

- 讓 WPF 應用程式安全地在多個應用程式域案例中執行。

- 當增益集以安全性隔離（也就是部分信任安全性沙箱）執行時，防止不合法存取增益集 UI 視窗控制碼。 呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 可確保此安全性：

  - 針對「增益集傳回 UI」程式設計模型，在隔離界限上傳遞增益集 UI 之視窗控制碼的唯一方式，就是呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。

  - 針對「增益集是 UI」程式設計模型，需要覆寫增益集端介面卡上的 <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>，並呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> （如先前範例所示）是必要的，因為它會從主機端介面卡呼叫增益集端介面卡的 `QueryContract` 執行。

- 提供多個應用程式定義域執行保護。 由於應用程式定義域的限制，增益集應用程式定義域中擲回的未處理例外狀況會導致整個應用程式當機，即使有隔離界限。 不過，WPF 和 .NET Framework 增益集模型提供簡單的方法來解決此問題，並改善應用程式穩定性。 如果主應用程式是 WPF 應用程式，則會顯示 UI 的 WPF 增益集會為應用程式域執行所在的執行緒建立 <xref:System.Windows.Threading.Dispatcher>。 您可以藉由處理 WPF 增益集 <xref:System.Windows.Threading.Dispatcher>的 <xref:System.Windows.Threading.Dispatcher.UnhandledException> 事件，來偵測應用程式域中發生的所有未處理的例外狀況。 您可以從 [<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>] 屬性取得 <xref:System.Windows.Threading.Dispatcher>。

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a>WPF 增益集限制

除了 WPF 加入 <xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.HwndHost>和視窗控制碼所提供之預設行為的優點之外，也有從主應用程式顯示的增益集使用者介面的限制：

- 從主應用程式顯示的增益集使用者介面不會遵守主應用程式的裁剪行為。

- 互通性案例中的「空間」概念也適用於增益集 (請參閱[技術領域概觀](../advanced/technology-regions-overview.md))。

- 裝載應用程式的 UI 服務（例如資源繼承、資料系結和命令）不會自動提供給增益集使用者介面。 若要向增益集提供這些服務，您需要更新管線。

- 增益集 UI 無法旋轉、縮放、扭曲，或以其他方式受到轉換影響（請參閱[轉換總覽](../graphics-multimedia/transforms-overview.md)）。

- 從 <xref:System.Drawing> 命名空間的繪製作業所轉譯之增益集使用者介面內的內容，可以包含 Alpha 混合。 不過，增益集 UI 和包含它的主應用程式 UI 都必須是100% 不透明;換句話說，兩者的 `Opacity` 屬性都必須設定為1。

- 如果主應用程式中包含增益集 UI 之視窗的 [<xref:System.Windows.Window.AllowsTransparency%2A>] 屬性設定為 [`true`]，則不會隱藏增益集。 即使增益集 UI 是100% 不透明（也就是 `Opacity` 屬性的值為1），也是如此。

- 增益集 UI 必須出現在同一個最上層視窗中的其他 WPF 元素之上。

- 您無法使用 <xref:System.Windows.Media.VisualBrush>來轉譯增益集 UI 的任何部分。 相反地，增益集可能會製作產生之 UI 的快照集，以建立可使用合約所定義的方法傳遞給主應用程式的點陣圖。

- 無法從增益集 UI 中的 <xref:System.Windows.Controls.MediaElement> 播放媒體檔案。

- 主機應用程式不會收到或引發針對增益集 UI 所產生的滑鼠事件，而且主應用程式 UI 的 `IsMouseOver` 屬性具有 `false`的值。

- 當焦點在增益集 UI 中的控制項之間移動時，主應用程式不會接收或引發 `GotFocus` 和 `LostFocus` 事件。

- 包含增益集 UI 的主應用程式部分，會在列印時顯示為白色。

- 如果主應用程式繼續執行，則必須先手動關閉增益集 UI 所建立的所有發送器（請參閱 <xref:System.Windows.Threading.Dispatcher>），才能卸載擁有者增益集。 合約可以執行方法，讓主應用程式在卸載增益集之前對增益集發出信號，藉此允許增益集 UI 關閉其發送器。

- 如果增益集 UI 是 <xref:System.Windows.Controls.InkCanvas> 或包含 <xref:System.Windows.Controls.InkCanvas>，您就無法卸載增益集。

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a>效能最佳化

根據預設，當使用多個應用程式域時，每個應用程式所需的各種 .NET Framework 元件都會載入至該應用程式的網域。 如此一來，建立新應用程式定義域以及從其中啟動應用程式所需的時間，可能會影響效能。 不過，.NET Framework 可讓您藉由指示應用程式跨應用程式域共用元件（如果已載入的話），來縮短開始時間。 若要這麼做，您可以使用 <xref:System.LoaderOptimizationAttribute> 屬性，這必須套用至進入點方法（`Main`）。 在此情況下，您必須只使用程式碼實作您的應用程式定義 (請參閱[應用程式管理概觀](application-management-overview.md))。

## <a name="see-also"></a>請參閱

- <xref:System.LoaderOptimizationAttribute>
- [增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [應用程式定義域](../../app-domains/application-domains.md)
- [.NET Framework 遠端處理總覽](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [使物件可遠端處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [「如何」主題](how-to-topics.md)
