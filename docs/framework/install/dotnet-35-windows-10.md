---
title: 在 Windows 10、8.1、8上安裝 .NET Framework 3。5
description: 了解如何在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5。
ms.date: 07/16/2018
ms.openlocfilehash: 208016e22eed324a3996552284072c6ad29637a5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716383"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="6efc3-103">在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="6efc3-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="6efc3-104">您可能需要 .NET Framework 3.5，才能在 Windows 10、Windows 8.1 及 Windows 8 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6efc3-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="6efc3-105">這些指示也適用於較舊的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="6efc3-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="6efc3-106">視需要安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="6efc3-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="6efc3-107">如果您嘗試執行需要 .NET Framework 3.5 的應用程式，可能會看到下列設定對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6efc3-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="6efc3-108">請選擇 [安裝此功能] 來啟用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="6efc3-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="6efc3-109">這個選項需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="6efc3-109">This option requires an Internet connection.</span></span>

![[.NET Framework 安裝] 對話方塊的螢幕擷取畫面。](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a><span data-ttu-id="6efc3-111">為什麼我會收到這個快顯？</span><span class="sxs-lookup"><span data-stu-id="6efc3-111">Why am I getting this pop-up?</span></span>

<span data-ttu-id="6efc3-112">.NET Framework 由 Microsoft 建立，並提供執行應用程式的環境。</span><span class="sxs-lookup"><span data-stu-id="6efc3-112">The .NET Framework is created by Microsoft and provides an environment for running applications.</span></span> <span data-ttu-id="6efc3-113">有不同的版本可以使用。</span><span class="sxs-lookup"><span data-stu-id="6efc3-113">There are different versions available.</span></span> <span data-ttu-id="6efc3-114">許多公司開發使用 .NET Framework 執行的應用程式，而這些應用程式以特定版本為目標。</span><span class="sxs-lookup"><span data-stu-id="6efc3-114">Many companies develop their apps to run using the .NET Framework, and these apps target a specific version.</span></span> <span data-ttu-id="6efc3-115">如果您看到這個這個快顯視窗，表示您正在執行一個需要 .NET Framework 3.5 版的應用程式，但您的系統上並未安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="6efc3-115">If you see this pop-up, you're trying to run an application that requires the .NET Framework version 3.5, but that version is not installed on your system.</span></span>

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="6efc3-116">在控制台中啟用 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="6efc3-116">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="6efc3-117">您可以透過 Windows 的 [控制台] 啟用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="6efc3-117">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="6efc3-118">這個選項需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="6efc3-118">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="6efc3-119">按 Windows 鍵 ![Windows 按鍵標誌的螢幕擷取畫面。](./media/dotnet-35-windows-10/windows-keyboard-logo.png)</span><span class="sxs-lookup"><span data-stu-id="6efc3-119">Press the Windows key ![Screenshot of the Windows key logo.](./media/dotnet-35-windows-10/windows-keyboard-logo.png)</span></span> <span data-ttu-id="6efc3-120">在您的鍵盤上輸入「Windows 功能」，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="6efc3-120">on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="6efc3-121">[開啟或關閉 Windows 功能] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="6efc3-121">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="6efc3-122">選取 [.NET Framework 3.5 (包括 .NET 2.0 和 3.0)] 核取方塊，選取 [確定]，然後在出現提示時重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="6efc3-122">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![螢幕擷取畫面：顯示使用 [控制台] 安裝 .NET。](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   <span data-ttu-id="6efc3-124">您不需要選取 [Windows Communication Foundation (WCF) HTTP 啟用] 和 [Windows Communication Foundation (WCF) 非 HTTP 啟用] 的子項目，除非您是需要這項功能的開發人員或伺服器系統管理員。</span><span class="sxs-lookup"><span data-stu-id="6efc3-124">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="6efc3-125">進行 .NET Framework 3.5 安裝的疑難排解</span><span class="sxs-lookup"><span data-stu-id="6efc3-125">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="6efc3-126">在安裝過程中，可能會出現錯誤 0x800f0906、0x800f0907、0x800f081f 或 0x800F0922，如果發生這種情況，請參考 [.NET Framework 3.5 安裝錯誤：0x800f0906、0x800f0907 或 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09)，了解如何解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="6efc3-126">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="6efc3-127">如果您仍無法解決您的安裝問題，或者您沒有網際網路連線，則可以嘗試使用 Windows 安裝媒體進行安裝。</span><span class="sxs-lookup"><span data-stu-id="6efc3-127">If you still can't resolve your installation issue or you don't have an Internet connection, you can try installing it using your Windows installation media.</span></span> <span data-ttu-id="6efc3-128">如需詳細資訊，請參閱[使用部署映像服務與管理 (DISM) 部署 .NET Framework 3.5](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism)。</span><span class="sxs-lookup"><span data-stu-id="6efc3-128">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="6efc3-129">如果您沒有安裝媒體，請參閱[建立 Windows 的安裝媒體](https://support.microsoft.com/help/15088/windows-create-installation-media)。</span><span class="sxs-lookup"><span data-stu-id="6efc3-129">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>

> [!WARNING]
> <span data-ttu-id="6efc3-130">如果您不依賴 Windows Update 做為安裝.NET Framework 3.5 的來源，則必須確定務必使用對應到相同 Windows 作業系統版本的來源。</span><span class="sxs-lookup"><span data-stu-id="6efc3-130">If you're not relying on Windows Update as the source for installing the .NET Framework 3.5, you must ensure to strictly use sources from the same corresponding Windows operating system version.</span></span> <span data-ttu-id="6efc3-131">使用未對應到相同 Windows 版本的來源路徑不會防止安裝不相符的 NET Framework 3.5 版本。</span><span class="sxs-lookup"><span data-stu-id="6efc3-131">Using a source path that doesn't correspond to the same version of Windows won't prevent a mismatched version of .NET Framework 3.5 from being installed.</span></span> <span data-ttu-id="6efc3-132">不過，這會導致系統不受支援且無法提供服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="6efc3-132">However, this will cause the system to be in an unsupported and unserviceable state.</span></span>
