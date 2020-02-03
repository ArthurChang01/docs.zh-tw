---
title: WPF 主應用程式 (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743395"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="5c616-102">WPF 主應用程式 (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="5c616-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="5c616-103">Windows Presentation Foundation （WPF）主機（Presentationhost.exe）是應用程式，可讓 WPF 應用程式裝載在相容的瀏覽器中（包括 Microsoft Internet Explorer 6 和更新版本）。</span><span class="sxs-lookup"><span data-stu-id="5c616-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="5c616-104">根據預設，Windows Presentation Foundation （WPF）主機會註冊為瀏覽器裝載 WPF 內容的 shell 和 MIME 處理常式，其中包括：</span><span class="sxs-lookup"><span data-stu-id="5c616-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="5c616-105">鬆散 (未編譯) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案 (.xaml)。</span><span class="sxs-lookup"><span data-stu-id="5c616-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="5c616-106">XAML 瀏覽器應用程式（XBAP）（xbap）。</span><span class="sxs-lookup"><span data-stu-id="5c616-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="5c616-107">對於這些類型的檔案，請 Windows Presentation Foundation （WPF）主機：</span><span class="sxs-lookup"><span data-stu-id="5c616-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="5c616-108">啟動已註冊的 HTML 處理常式，以裝載 Windows Presentation Foundation （WPF）內容。</span><span class="sxs-lookup"><span data-stu-id="5c616-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="5c616-109">載入所需 common language runtime （CLR）和 Windows Presentation Foundation （WPF）元件的正確版本。</span><span class="sxs-lookup"><span data-stu-id="5c616-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="5c616-110">確保部署區域的適當權限等級都已就緒。</span><span class="sxs-lookup"><span data-stu-id="5c616-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="5c616-111">本主題說明可以搭配使用 PresentationHost.exe 的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="5c616-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5c616-112">使用方式</span><span class="sxs-lookup"><span data-stu-id="5c616-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="5c616-113">參數</span><span class="sxs-lookup"><span data-stu-id="5c616-113">Parameters</span></span>  
  
|<span data-ttu-id="5c616-114">參數</span><span class="sxs-lookup"><span data-stu-id="5c616-114">Parameter</span></span>|<span data-ttu-id="5c616-115">描述</span><span class="sxs-lookup"><span data-stu-id="5c616-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c616-116">filename</span><span class="sxs-lookup"><span data-stu-id="5c616-116">filename</span></span>|<span data-ttu-id="5c616-117">要啟動的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="5c616-117">The path of the file to be activated.</span></span> <span data-ttu-id="5c616-118">也可以是 URI。</span><span class="sxs-lookup"><span data-stu-id="5c616-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="5c616-119">-debug</span><span class="sxs-lookup"><span data-stu-id="5c616-119">-debug</span></span>|<span data-ttu-id="5c616-120">當啟動應用程式時，不會從存放區認可或執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c616-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="5c616-121">這只有在已啟動本機檔案時才有用。</span><span class="sxs-lookup"><span data-stu-id="5c616-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="5c616-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="5c616-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="5c616-123">與 URL 值搭配使用，以指示 Presentationhost.exe 應用程式應該進行調試，如同從指定的 URL 部署一樣。</span><span class="sxs-lookup"><span data-stu-id="5c616-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="5c616-124">這會決定部署區域與原始站台。</span><span class="sxs-lookup"><span data-stu-id="5c616-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="5c616-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="5c616-125">-embedding</span></span>|<span data-ttu-id="5c616-126">為 OLE 的必要項。</span><span class="sxs-lookup"><span data-stu-id="5c616-126">Required by OLE.</span></span> <span data-ttu-id="5c616-127">如果已指定 `-event` 或 `-debug` 參數，就不需要指定 `-embedding` 參數，因為該參數已在內部設定。</span><span class="sxs-lookup"><span data-stu-id="5c616-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="5c616-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="5c616-128">-event \<eventname></span></span>|<span data-ttu-id="5c616-129">開啟具有這個名稱的事件，並在 Presentationhost.exe 初始化並準備好裝載 WPF 內容時發出通知。</span><span class="sxs-lookup"><span data-stu-id="5c616-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="5c616-130">如果開啟事件時發生錯誤 (例如事件尚未建立)，則會終止 PresentationHost.exe。</span><span class="sxs-lookup"><span data-stu-id="5c616-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="5c616-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="5c616-131">-launchApplication \<url></span></span>|<span data-ttu-id="5c616-132">從指定的 URL 啟動獨立 ClickOnce 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c616-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="5c616-133">適用于 .NET 應用程式的 Internet Explorer 和 WinINet 安全性原則會套用。</span><span class="sxs-lookup"><span data-stu-id="5c616-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="5c616-134">案例</span><span class="sxs-lookup"><span data-stu-id="5c616-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="5c616-135">殼層處理常式</span><span class="sxs-lookup"><span data-stu-id="5c616-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="5c616-136">MIME 處理常式</span><span class="sxs-lookup"><span data-stu-id="5c616-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="5c616-137">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="5c616-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="5c616-138">Visual Studio 區域中偵錯</span><span class="sxs-lookup"><span data-stu-id="5c616-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="5c616-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c616-139">See also</span></span>

- [<span data-ttu-id="5c616-140">安全性</span><span class="sxs-lookup"><span data-stu-id="5c616-140">Security</span></span>](../security-wpf.md)
