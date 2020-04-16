---
title: 設定用於 Windows Communication Foundation 的 Windows Process Activation Service
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 86e50b80d84479ca32b3d4d1fe3f205983640c76
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464174"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="f0896-102">設定用於 Windows Communication Foundation 的 Windows Process Activation Service</span><span class="sxs-lookup"><span data-stu-id="f0896-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="f0896-103">本主題介紹在 Windows Vista 中設置 Windows 進程啟動服務(也稱為 WAS)以託管不通過 HTTP 網路協定進行通信的 Windows 通信基礎 (WCF) 服務所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="f0896-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="f0896-104">下列各節將概述此組態的各項步驟：</span><span class="sxs-lookup"><span data-stu-id="f0896-104">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="f0896-105">安裝(或確認安裝)所需的 WCF 啟動元件。</span><span class="sxs-lookup"><span data-stu-id="f0896-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="f0896-106">運用您希望使用的網路通訊協定繫結來建立 WAS 網站，或是將新通訊協定繫結新增至現有網站。</span><span class="sxs-lookup"><span data-stu-id="f0896-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="f0896-107">建立應用程式來裝載服務，並啟用該應用程式來使用所需的網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f0896-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="f0896-108">生成公開非 HTTP 終結點的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="f0896-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="f0896-109">使用非 HTTP 繫結來設定網站</span><span class="sxs-lookup"><span data-stu-id="f0896-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="f0896-110">若要以非 HTTP 繫結來搭配 WAS 一起使用，必須將網站繫結新增至 WAS 組態。</span><span class="sxs-lookup"><span data-stu-id="f0896-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="f0896-111">WAS 的組態存放區就是 applicationHost.config 檔 (位於 %windir%\system32\inetsrv\config 目錄)。</span><span class="sxs-lookup"><span data-stu-id="f0896-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="f0896-112">這個組態存取區可由 WAS 和 IIS 7.0 同時共用。</span><span class="sxs-lookup"><span data-stu-id="f0896-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="f0896-113">applicationHost.config 是一個可使用任何標準文字編輯器 (例如 [記事本]) 來開啟的 XML 文字檔。</span><span class="sxs-lookup"><span data-stu-id="f0896-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="f0896-114">但是,IIS 7.0 命令列配置工具 (appcmd.exe) 是添加非 HTTP 站點綁定的首選方式。</span><span class="sxs-lookup"><span data-stu-id="f0896-114">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="f0896-115">下列命令會使用 appcmd.exe 將 net.tcp 網站繫結新增至預設的網站 (此命令需以單行方式輸入)。</span><span class="sxs-lookup"><span data-stu-id="f0896-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="f0896-116">此命令會將下列所示字行新增至 applicationHost.config 檔，以將新的 net.tcp 繫結新增至預設的網站。</span><span class="sxs-lookup"><span data-stu-id="f0896-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="f0896-117">啟用應用程式來使用非 HTTP 通訊協定</span><span class="sxs-lookup"><span data-stu-id="f0896-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="f0896-118">您可以在應用程式等級啟用或禁用單個網路協定。</span><span class="sxs-lookup"><span data-stu-id="f0896-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="f0896-119">下列命令說明如何針對在 `Default Web Site` 中執行的應用程式同時啟用 HTTP 和 net.tcp 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f0896-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="f0896-120">還可以在\<應用程式中設置已啟用的協定清單,>存储在应用程序Host.config中的網站 XML 配置的元素。</span><span class="sxs-lookup"><span data-stu-id="f0896-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="f0896-121">下列來自 applicationHost.config 的 XML 程式碼說明同時繫結至 HTTP 和非 HTTP 通訊協定的網站。</span><span class="sxs-lookup"><span data-stu-id="f0896-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="f0896-122">支援非 HTTP 通訊協定所需的額外組態可以藉由註解來呼叫。</span><span class="sxs-lookup"><span data-stu-id="f0896-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="f0896-123">如果您嘗試使用 WAS 進行非 HTTP 啟用以啟動服務，但是尚未安裝並設定 WAS，您可能會看到以下錯誤：</span><span class="sxs-lookup"><span data-stu-id="f0896-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="f0896-124">如果您收到這個錯誤，請確認已安裝並正確設定適用於非 HTTP 啟用的 WAS。</span><span class="sxs-lookup"><span data-stu-id="f0896-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="f0896-125">有關詳細資訊,請參閱[如何:安裝和設定 WCF 啟動元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)。</span><span class="sxs-lookup"><span data-stu-id="f0896-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="f0896-126">針對非 HTTP 啟動建置使用 WAS 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="f0896-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="f0896-127">執行安裝和設定 WAS 的步驟(請參閱[:安裝和設定 WCF 啟動元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)),將服務配置為使用 WAS 進行啟動類似於配置 IIS 中託管的服務。</span><span class="sxs-lookup"><span data-stu-id="f0896-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="f0896-128">有關構建 WAS 啟動的 WCF 服務的詳細說明,請參閱[如何:在 WAS 中託管 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)。</span><span class="sxs-lookup"><span data-stu-id="f0896-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0896-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0896-129">See also</span></span>

- [<span data-ttu-id="f0896-130">在 Windows 處理序啟用服務中裝載</span><span class="sxs-lookup"><span data-stu-id="f0896-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="f0896-131">[Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f0896-131">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
