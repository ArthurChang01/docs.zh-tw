---
title: WPF 安全性策略 – 平台安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
ms.openlocfilehash: 9c237c06de1388de4c1fe6a6edb3fb5b52522d1f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424633"
---
# <a name="wpf-security-strategy---platform-security"></a>WPF 安全性策略 – 平台安全性
雖然 Windows Presentation Foundation （WPF）提供各種安全性服務，但它也會利用基礎平臺的安全性功能，其中包括作業系統、CLR 和 Internet Explorer。 這三層安全性功能一起為 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 提供了強大、深入防禦的安全性模型，即使其中一層失敗，還有兩層可以幫忙把關，如下圖所示：  
  
 ![顯示 WPF 安全性模型的圖表。](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 本主題的其餘部分會針對每一層安全性功能當中，與 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 特別有關的功能進行討論。  

## <a name="operating-system-security"></a>作業系統安全性  
Windows 的核心提供數項安全性功能，可構成所有 Windows 應用程式的安全性基礎，包括 WPF 所建立的。 本主題將討論這些對 WPF 而言很重要的安全性功能，以及 WPF 如何與它們整合以提供進一步的深度防禦。  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 除了一般的審查和強化的 Windows，我們還會在本主題中討論 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] 的三項主要功能：  
  
- /GS 編譯  
  
- Microsoft Windows Update。  
  
#### <a name="gs-compilation"></a>/GS 編譯  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] 藉由重新編譯許多核心系統程式庫（包括所有 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 相依性，例如 CLR）來提供保護，以協助減輕緩衝區溢位。 搭配 C/C++ 命令列編譯器使用 /GS 參數即可達成這個目的。 雖然這樣做應該能夠明確避免發生緩衝區滿溢的情況，但是 /GS 編譯還提供一個深入防禦範例，可防止無意中或惡意利用緩衝區滿溢所造成的潛在弱點遭到攻擊。  
  
 在過去，緩衝區滿溢一直是造成許多重大安全性攻擊的原因。 當攻擊者利用程式碼弱點，插入將緩衝區寫爆的惡意程式碼時，就會發生緩衝區滿溢的情況。 這會讓攻擊者有機會透過覆寫函式的傳回位址，來劫持執行該程式碼的處理序，以執行攻擊者的程式碼。 結果是，惡意程式碼可以利用與被劫持的處理序相同的權限來執行任意程式碼。  
  
 概括而言，-GS 編譯器旗標會藉由插入特殊的安全性 cookie 來保護具有本機字串緩衝區的函式的傳回位址，藉此防止部分可能的緩衝區溢位。 在函式傳回之後，安全性 Cookie 會與其原先的值做比較。 如果這個值已變更，則可能發生緩衝區滿溢的情況，而且會停止處理序並顯示錯誤狀況。 停止處理序可防止執行可能惡意的程式碼。 如需詳細資訊，請參閱[-GS （緩衝區安全性檢查）](/cpp/build/reference/gs-buffer-security-check) 。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 會利用 /GS 旗標進行編譯，可為 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 應用程式提供多一層的防禦。  
  
### <a name="windows-vista"></a>Windows Vista  
Windows Vista 上的 WPF 使用者將受益于作業系統的其他安全性增強功能，包括「最低許可權使用者存取」、程式碼完整性檢查和許可權隔離。  
  
#### <a name="user-account-control-uac"></a>使用者帳戶控制 (UAC)  
 目前，Windows 使用者通常會以系統管理員許可權執行，因為許多應用程式都需要它們來進行安裝或執行，或兩者都有。 其中一個例子是，使用者必須能夠將預設應用程式設定寫入至登錄。  
  
 以系統管理員權限執行，實際上表示應用程式會從具有系統管理員權限的處理序執行。 這樣做會有安全性風險，那就是劫持以系統管理員權限執行之處理序的任何惡意程式碼，都會自動繼承這些權限，包括重要系統資源的存取權。  
  
 防範這個安全性威脅的方法之一，就是以最少的必要權限執行應用程式。 這就是所謂的最低許可權原則，也是 Windows 作業系統的核心功能。 這項功能稱為使用者帳戶控制（UAC），由 Windows UAC 以兩種主要方式使用：  
  
- 讓大多數的應用程式預設以 UAC 權限執行，即使使用者是系統管理員也一樣。只有需要系統管理員權限的應用程式才會以系統管理員權限執行。 若要以系統管理員權限執行，應用程式必須在其應用程式資訊清單中明確標記，或明確標記為安全性原則中的項目。  
  
- 提供像是虛擬化的相容性解決方案。 例如，許多應用程式會嘗試寫入限制位置，例如 C:\Program Files。 如果應用程式是以 UAC 執行，則會建立依使用者而定的替代位置，應用程式不需要有系統管理員權限就能寫入至這個位置。 如果應用程式是以 UAC 執行，則 UAC 會將 C:\Program Files 虛擬化，讓以為寫入至這個位置的應用程式，實際上是寫入至依使用者而定的替代位置。 這種相容性轉換工作可讓作業系統執行更多應用程式 (之前在 UAC 中執行時，並無法執行這麼多應用程式)。  
  
#### <a name="code-integrity-checks"></a>程式碼完整性檢查  
 Windows Vista 整合了更深入的程式碼完整性檢查，協助防止惡意程式碼在載入/執行時間插入系統檔案或核心。 這已經超過系統檔案保護範圍。  
   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>瀏覽器裝載之應用程式的有限權限處理序  
 瀏覽器裝載的 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 應用程式是在網際網路區域沙箱中執行。 與 Microsoft Internet Explorer [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 的整合會以額外的支援擴充此保護。  
  
 因為 XAML 瀏覽器應用程式（Xbap）通常是由網際網路區域許可權集合進行沙箱化，所以移除這些許可權並不會從相容性的觀點來傷害 XAML 瀏覽器應用程式（Xbap）。 反而可以建立多一層的深層防禦。即使沙箱化的應用程式能夠攻擊其他層級並劫持處理序，處理序仍然只會有有限的權限。  
  
 請參閱[使用最低許可權的使用者帳戶](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29)。  
  
## <a name="common-language-runtime-security"></a>Common Language Runtime 安全性  
 Common language runtime （CLR）提供一些重要的安全性優點，包括驗證和驗證、代碼啟用安全性（CAS）和安全性關鍵方法。  
    
### <a name="validation-and-verification"></a>驗證 (Validation 和 Verification)  
 為了提供元件隔離和完整性，CLR 會使用驗證處理常式。 CLR 驗證會藉由針對指向元件外部的位址驗證其可移植執行檔（PE）檔案格式，以確保元件隔離。 CLR 驗證也會驗證內嵌在元件內之中繼資料的完整性。  
  
 為確保型別安全，請協助避免常見的安全性問題（例如緩衝區溢位），並透過子進程隔離來啟用沙箱，CLR 安全性會使用驗證的概念。  
  
 Managed 應用程式會編譯成 Microsoft 中繼語言 (MSIL)。 執行 Managed 應用程式中的方法時，應用程式的 MSIL 會透過 Just-In-Time (JIT) 編譯被編譯成機器碼。 JIT 編譯包含驗證程序，這個程序會套用許多安全和穩定性規則，以確保程式碼不會：  
  
- 違反類型合約  
  
- 引入緩衝區滿溢  
  
- 大量存取記憶體  
  
 不符合驗證規則的 Managed 程式碼除非受到信任，否則無法執行。  
  
 可驗證程式代碼的優點是 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 建置於 .NET Framework 上的主要原因。 只要是使用可驗證程式碼的地方，潛在弱點遭受攻擊的可能性都會大幅降低。  
  
### <a name="code-access-security"></a>程式碼存取安全性  
 用戶端電腦公開了可供 Managed 應用程式存取的各種資源，包括檔案系統、登錄、列印服務、使用者介面、反映和環境變數。 在受控應用程式可以存取用戶端電腦上的任何資源之前，它必須具有 .NET Framework 的許可權才能執行這項操作。 CA 中的許可權是 <xref:System.Security.CodeAccessPermission> 的子類別。CAS 會針對受控應用程式可存取的每個資源，執行一個子類別。  
  
 CA 在啟動執行時授與的一組許可權，稱為許可權集合，由應用程式所提供的辨識項來決定。 如果是 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 應用程式，所提供的辨識項就是應用程式啟動的位置 (或區域)。 CA 可識別下欄區域：  
  
- **我的電腦**。 從用戶端電腦啟動的應用程式 (完全信任)。  
  
- **近端內部網路**。 從內部網路啟動的應用程式 (部分受信任)。  
  
- **Internet**。 從網際網路啟動的應用程式 (最不受信任)。  
  
- **信任的網站**。 使用者指定要信任的應用程式 (最不受信任)。  
  
- **限制的網站**。 使用者指定不要信任的應用程式 (未受信任)。  
  
 CA 會針對每個區域提供預先定義的許可權集合，其中包含符合與每個相關聯之信任層級的許可權。 它們包括：  
  
- **FullTrust**。 針對從**我的電腦**區域啟動的應用程式。 會授與所有可能的權限。  
  
- **LocalIntranet**。 適用于從近端**內部**網路區域啟動的應用程式。 會授與權限的子集，以提供對用戶端電腦資源的中度存取權，包括隔離儲存區、無限制的 UI 存取權、無限制的檔案對話方塊、有限的反映、對環境變數的有限存取權。 不會提供重要資源 (例如登錄) 的權限。  
  
- **Internet**。 適用于從**網際網路**或信任的**網站**區域啟動的應用程式。 會授與權限的子集，以提供對用戶端電腦資源的有限存取權，包括隔離儲存區、限檔案開啟，以及有限的 UI。 基本上，此許可權集合會將應用程式與用戶端電腦隔離。  
  
 識別為來自**不受信任的網站**區域的應用程式完全不會被 ca 授與任何許可權。 因此，這些應用程式沒有預先定義的權限集合。  
  
 下圖說明區域、許可權集合、許可權和資源之間的關聯性：  
  
 ![顯示 CAS 許可權集合的圖表。](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 網際網路區域安全性沙箱的限制同樣適用于 XBAP 從系統程式庫（包括 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]）匯入的任何程式碼。 如此可確保程式碼的每個位元都被鎖定，即使是 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 也一樣。 可惜的是，若要能夠執行，XBAP 必須執行需要比網際網路區域安全性沙箱所啟用的許可權更多的功能。  
  
 請考慮包含下列頁面的 XBAP 應用程式：  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 若要執行這個 XBAP，基礎 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 程式碼必須執行比呼叫 XBAP 可用的功能更多，包括：  
  
- 建立用於呈現的視窗控制碼（HWND）  
  
- 分派訊息  
  
- 載入新細明體字型  
  
 從安全性觀點來看，允許沙箱化應用程式直接存取上述任何作業將會引發十分嚴重的後果。  
  
 好在 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 已經考慮到這種情況，它會允許這些作業以代表沙箱化應用程式的更高權限來執行。 雖然所有 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 作業會針對 XBAP 的應用程式域的有限網際網路區域安全性許可權進行檢查，但 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] （與其他系統程式庫相同）會被授與許可權集合，其中包含所有可能的許可權。
  
 這表示 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 必須得到更高的權限，同時又要避免這些權限受到主應用程式定義域之 [網際網路] 區域權限集合的控制。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 使用許可權的**Assert**方法來執行這項工作。 下列程式碼會顯示這個過程。  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 判斷**提示基本上可**防止 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 所需的無限制許可權受到 XBAP 的網際網路區域許可權所限制。  
  
 從平臺的觀點來看，[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 會負責正確地使用**Assert** ;不正確地使用**Assert**可能會讓惡意程式碼提升許可權。 因此，只有在必要時才呼叫**Assert** ，並確保沙箱限制保持不變。 例如，沙箱化程式碼不可以開啟隨機檔案，但可以使用字型。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 可讓沙箱化應用程式藉由呼叫**Assert**來使用字型功能，並讓 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 讀取可代表沙箱應用程式包含這些字型的檔案。  
  
### <a name="clickonce-deployment"></a>ClickOnce 部署  
 ClickOnce 是包含在 .NET Framework 中的全方位部署技術，並與 Visual Studio 整合（如需詳細資訊，請參閱[ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)）。 獨立 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 應用程式可以使用 ClickOnce 來部署，而瀏覽器裝載的應用程式則必須使用 ClickOnce 進行部署。  
  
 使用 ClickOnce 部署的應用程式會透過代碼啟用安全性（CAS）獲得額外的安全性層級;基本上，ClickOnce 部署的應用程式會要求所需的許可權。 只有在所要求的權限不超過應用程式部署來源區域的權限集合時，才會將這些權限授與應用程式。 藉由減少許可權的集合，即使它們少於啟動區域的許可權集合所提供的許可權，應用程式可以存取的資源數目也會降到最低。 因此，如果應用程式遭到劫持，用戶端電腦遭到破壞的可能性將會降低。  
  
### <a name="security-critical-methodology"></a>安全性關鍵方法  
 使用許可權啟用 XBAP 應用程式之網際網路區域沙箱的 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 程式碼，必須保持在最高可能的安全性審查和控制程度。 為了協助這項需求，.NET Framework 提供新的支援來管理提升許可權的程式碼。 具體而言，CLR 可讓您識別提升許可權的程式碼，並將其標示為 <xref:System.Security.SecurityCriticalAttribute>;任何未使用 <xref:System.Security.SecurityCriticalAttribute> 標記的程式碼都會使用此方法變成*透明*。 相反地，未標記為 <xref:System.Security.SecurityCriticalAttribute> 的 Managed 程式碼將無法提高權限。  
  
 安全性關鍵方法可讓您將提高許可權的 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 程式碼組織成*安全性關鍵核心*，其餘部分則是透明的。 隔離安全性關鍵程式碼可讓 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 工程小組專注于高於標準安全性實務的安全性關鍵核心上的額外安全性分析和原始檔控制（請參閱[WPF 安全性策略-安全性工程](wpf-security-strategy-security-engineering.md)）。  
  
 請注意，.NET Framework 允許受信任的程式碼擴充 XBAP 網際網路區域沙箱，方法是允許開發人員撰寫以 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）標記並部署到使用者的全域組件快取（GAC）的 managed 元件。 在組件上標記 APTCA 是一項極為敏感的安全性作業，因為這可讓任何程式碼 (包括來自網際網路的惡意程式碼) 呼叫該組件。 執行這項操作時請謹慎為之，一定要採取最佳做法，而且使用者必須選擇信任該軟體才能安裝軟體。  
  
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer 安全性  
 除了減少安全性問題和簡化安全性設定之外，Microsoft Internet Explorer 6 （SP2）還包含數項安全性增強功能，可加強 XAML 瀏覽器應用程式使用者（Xbap）的安全性。 這些功能的主要目的是要讓使用者更能掌控自己的瀏覽體驗。  
  
 在 IE6 SP2 之前，使用者可能會受到下列任何一項：  
  
- 隨機跳出的快顯視窗。  
  
- 令人困惑的指令碼重新導向。  
  
- 某些網站上的大量安全性對話方塊。  
  
 在某些情況下，不信任的網站會嘗試藉由詐騙安裝來誘騙使用者 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 或重複顯示 Microsoft ActiveX 安裝對話方塊，即使使用者已將它取消也一樣。 透過這些手法，許多使用者可能信以為真，做出錯誤決定，因而安裝了間諜軟體應用程式。  
  
 IE6 SP2 包含數項功能來減輕這些類型的問題，這會圍繞使用者起始的概念。 IE6 SP2 會偵測使用者在動作之前按下的連結或頁面專案（稱為「*使用者初始*」），並將其視為不同于頁面上的腳本所觸發的類似動作。 例如，IE6 SP2 包含快顯封鎖程式，它會偵測使用者在頁面建立快顯視窗**之前，按一下**按鈕的時間。 這可讓 IE6 SP2 允許大部分無害的快顯，同時防止使用者不會要求或不想要的快顯視窗。 封鎖的快顯視窗會在新的**資訊**列之下受到攔截，讓使用者可以手動覆寫區塊並觀看快顯視窗。  
  
 相同的使用者起始邏輯也適用于**開啟**/**儲存**安全性提示。 除非是從先前安裝的控制項升級，否則 ActiveX 安裝對話方塊一律會在資訊列之下受到攔截。 這些措施一起為使用者提供了更安全、更受控制的使用者經驗，因為使用者將可擺脫陌生網站為了讓使用者安裝不必要或惡意的軟體，而一再進行的騷擾。  
  
 這些功能也會保護使用 IE6 SP2 流覽網站的客戶，讓他們能夠下載及安裝 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 應用程式。 具體而言，這是因為 IE6 SP2 提供較佳的使用者體驗，可減少使用者安裝惡意或迂回應用程式的機會，而不論用來建立它的技術為何，包括 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 使用 ClickOnce 新增至這些保護，以協助透過網際網路下載其應用程式。 由於 XAML 瀏覽器應用程式（Xbap）是在網際網路區域安全性沙箱中執行，因此可以順暢地啟動。 另一方面，獨立 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 應用程式則需要完全信任才能執行。 針對這些應用程式，ClickOnce 會在啟動程式期間顯示安全性對話方塊，以通知使用應用程式的其他安全性需求。 不過，這必須由使用者啟始、同時受到使用者啟始的邏輯控制，並且可以取消。  
  
 Internet Explorer 7 納入並擴充 IE6 SP2 的安全性功能，以做為安全性承諾的一部分。  
  
## <a name="see-also"></a>請參閱

- [程式碼存取安全性](../misc/code-access-security.md)
- [Security](security-wpf.md)
- [WPF 部分信任安全性](wpf-partial-trust-security.md)
- [WPF 安全性策略 – 安全性工程](wpf-security-strategy-security-engineering.md)
