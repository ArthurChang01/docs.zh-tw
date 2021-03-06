---
title: 將您的 .NET Web 應用程式或服務遷移至 Azure App Service
description: 瞭解如何將 .NET web 應用程式或服務從內部部署遷移至 Azure App Service。
ms.topic: conceptual
ms.date: 08/11/2018
ms.openlocfilehash: 57f3b981a1d94c2193160f55f9c8242da694c169
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072134"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>將您的 .NET Web 應用程式或服務遷移至 Azure App Service

[App Service](https://docs.microsoft.com/azure/app-service/overview)是完全受控的計算平臺服務，最適合用來裝載可擴充的網站和 web 應用程式。 本文提供如何將現有的應用程式隨即轉移至 Azure App Service、考慮的修改，以及[移至雲端](https://azure.microsoft.com/migration/web-applications/)的其他資源的相關資訊。 大部分 ASP.NET 網站 (Webforms、MVC) 和服務 (Web API、WCF) 都可以在沒有變更的情況下直接移至 Azure App Service。 一些服務可能需要些微變更，而其他服務則可能需要進行一些重構。

準備好開始了嗎？ [將 ASP.NET + SQL 應用程式發佈至 Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro)。

## <a name="considerations"></a>考量

### <a name="on-premises-resources-including-sql-server"></a>內部部署資源 (包括 SQL Server)

因為內部部署資源可能需要遷移或變更，所以請確認內部部署資源的存取權。 減少內部部署資源存取權的選項如下：

* 使用 [Azure 虛擬網路](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet)建立 VPN，讓 App Service 與內部部署資源連線。
* 使用 [Azure 轉送](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)安全地將內部部署服務公開至雲端，而不變更防火牆。
* 將例如 [SQL 資料庫](https://go.microsoft.com/fwlink/?linkid=863217) 的相依性遷移至 Azure。
* 使用雲端中的平臺即服務供應專案來減少相依性。 例如，請考慮使用 [SendGrid](https://docs.microsoft.com/azure/sendgrid-dotnet-how-to-send-email)，而不是連線到內部部署郵件伺服器。

### <a name="port-bindings"></a>連接埠繫結

Azure App Service 支援連接埠 80 (適用於 HTTP) 和連接埠 443 (適用於 HTTPS 流量)。

針對 WCF，支援下列繫結：

繫結 | 注意
--------|--------
BasicHttp |
WSHttp |
WSDualHttpBinding | 必須啟用 [Web 通訊端支援](https://docs.microsoft.com/azure/app-service/web-sites-configure)。
NetHttpBinding | 必須針對雙面合約啟用 [Web 通訊端支援](https://docs.microsoft.com/azure/app-service/web-sites-configure)。
NetHttpsBinding | 必須針對雙面合約啟用 [Web 通訊端支援](https://docs.microsoft.com/azure/app-service/web-sites-configure)。
BasicHttpContextBinding |
WebHttpBinding |
WSHttpContextBinding |

### <a name="authentication"></a>驗證

Azure App Service 預設支援匿名驗證，在想要使用時支援表單驗證。 只有與 Azure Active Directory 和 ADFS 整合，才能使用 Windows 驗證。 [深入了解如何整合您的內部部署目錄與 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>GAC (全域組件快取) 中的組件

不支援此做法。 請考慮將必要的元件複製到應用程式的*\bin*資料夾。 無法使用安裝在伺服器上的自訂 *.msi*檔案（例如，PDF 產生器）。

### <a name="iis-settings"></a>IIS 設定
傳統上透過應用程式中 applicationHost.config 設定的所有項目現在皆可透過 Azure 入口網站設定。 這適用于 AppPool 位、啟用/停用 Websocket、受管理的管線版本、.NET Framework 版本（2.0/4.0）等等。 若要修改[應用程式設定](https://docs.microsoft.com/azure/app-service/web-sites-configure)，瀏覽至 [Azure 入口網站](https://portal.azure.com)，開啟 Web 應用程式刀鋒視窗，然後選取 [應用程式設定]**** 索引標籤。

#### <a name="iis5-compatibility-mode"></a>IIS5 相容性模式
不支援 IIS5 相容性模式。 在 Azure App Service 中，每個 web 應用程式和其下的所有應用程式會在相同的工作者進程中，使用一組特定的[應用程式](https://technet.microsoft.com/library/cc735247(v=WS.10).aspx)集區來執行。

#### <a name="iis7-schema-compliance"></a>IIS7+ 結構描述合規性  
部分元素和屬性未在 Azure App Service IIS 結構描述中定義。 如果您遇到問題，請考慮使用 [XDT 轉換](https://azure.microsoft.com/documentation/articles/web-sites-transform-extend/)。

#### <a name="single-application-pool-per-site"></a>每個網站單一應用程式集區  
在 Azure App Service 中，每個 web 應用程式和其下的所有應用程式都會在相同的應用程式集區中執行。 請考慮建立具有一般設定的單一應用程式集區，或為每個應用程式建立個別的 web 應用程式。

### <a name="com-and-com-components"></a>COM 和 COM+ 元件  
Azure App Service 不允許在平台上註冊 COM 元件。 如果您的應用程式使用任何 COM 元件，則需要在 managed 程式碼中改寫，並與網站或應用程式一起部署。

### <a name="physical-directories"></a>實體目錄
Azure App Service 不允許實體磁碟存取。 您可能需要使用[Azure 檔案儲存體](https://docs.microsoft.com/azure/storage/files/storage-files-introduction)透過 SMB 存取檔案。 [Azure Blob 儲存體](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction)可以儲存檔案，以供透過 HTTPS 存取。

### <a name="isapi-filters"></a>ISAPI 篩選  
Azure App Service 支援使用 ISAPI 篩選；不過，ISAPI DLL 必須部署到您的網站，並透過 web.config 註冊。

### <a name="https-bindings-and-ssl"></a>HTTPS 繫結和 SSL
HTTPS 系結不會遷移，也不會與您的網站相關聯的 SSL 憑證。 但是，在網站移轉完成之後，[可以手動上傳 SSL 憑證](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl)。

### <a name="sharepoint-and-frontpage"></a>SharePoint 和 FrontPage
不支援 SharePoint 和 FrontPage Server Extensions (FPSE)。

### <a name="web-site-size"></a>網站大小  
可用網站具有 1 GB 內容的大小限制。 如果您的網站大於 1 GB，您必須升級為付費 SKU。 請參閱 [App Service 定價](https://azure.microsoft.com/pricing/details/app-service/windows/)。

### <a name="database-size"></a>資料庫大小  
針對 SQL Server 資料庫，請參閱目前的 [SQL Database 定價](https://azure.microsoft.com/pricing/details/sql-database)。

### <a name="azure-active-directory-aad-integration"></a>Azure Active Directory (AAD) 整合  
AAD 無法使用免費應用程式。 若要使用 AAD，您必須升級應用程式 SKU。 請參閱 [App Service 定價](https://azure.microsoft.com/pricing/details/app-service/windows/)。

### <a name="monitoring-and-diagnostics"></a>監視和診斷
您目前的監控和診斷內部部署解決方案無法在雲端中運作。 不過，Azure 提供記錄、監控和診斷工具，以便識別及偵錯 Web 應用程式的問題。 您可以輕鬆地在設定中啟用 Web 應用程式診斷，且可以檢視 Azure Application Insights 中所記的記錄。 [深入了解啟用 Web 應用程式的診斷記錄](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log)。

### <a name="connection-strings-and-application-settings"></a>連接字串和應用程式設定
請考慮使用 [Azure KeyVault](https://docs.microsoft.com/azure/key-vault/)，這項服務可以安全地儲存應用程式中所使用的敏感資訊。 或者，您可以將此資料儲存為 App Service 設定。

### <a name="dns"></a>DNS
您可能需要根據應用程式需求更新 DNS 設定。 這些 DNS 設定可在 App Service 的[自訂網域設定](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain)中進行設定。

## <a name="azure-app-service-with-windows-containers"></a>Azure App Service 與 Windows 容器
如果您的應用程式無法直接遷移至 App Service，請考慮使用 Windows 容器的 App Service，它可以使用 GAC、COM 元件、MSI 並完整存取 .NET FX API、DirectX 等等。

## <a name="see-also"></a>另請參閱

* [如何判斷您的應用程式是否符合 App Service](https://appmigration.microsoft.com/)
* [將您的資料庫移至雲端](https://go.microsoft.com/fwlink/?linkid=863217)
* [Azure web 應用程式沙箱詳細資料和限制](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
