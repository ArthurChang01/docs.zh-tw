---
title: 在 Ubuntu 19.10 套件管理員上安裝 .NET Core-.NET Core
description: 使用套件管理員在 Ubuntu 19.10 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 01/16/2020
ms.openlocfilehash: afba761e2237ed84528157841e538a9b44d9a966
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164081"
---
# <a name="ubuntu-1910-package-manager---install-net-core"></a><span data-ttu-id="d3ca1-103">Ubuntu 19.10 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="d3ca1-103">Ubuntu 19.10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="d3ca1-104">本文說明如何使用套件管理員在 Ubuntu 19.10 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.10.</span></span> <span data-ttu-id="d3ca1-105">如果您要安裝執行時間，我們建議您安裝[ASP.NET Core 運行](#install-the-aspnet-core-runtime)時間，因為它同時包含 .net Core 和 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="d3ca1-106">註冊 Microsoft 金鑰和總結</span><span class="sxs-lookup"><span data-stu-id="d3ca1-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="d3ca1-107">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="d3ca1-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="d3ca1-108">註冊 Microsoft 金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="d3ca1-109">註冊產品存放庫。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-109">Register the product repository.</span></span>
- <span data-ttu-id="d3ca1-110">安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-110">Install required dependencies.</span></span>

<span data-ttu-id="d3ca1-111">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="d3ca1-112">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="d3ca1-113">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="d3ca1-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="d3ca1-114">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="d3ca1-115">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="d3ca1-116">如果您收到類似 [**找不到封裝 dotnet-sdk-3.1**] 的錯誤訊息，請參閱[疑難排解套件管理員](#troubleshoot-the-package-manager)一節。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="d3ca1-117">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="d3ca1-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="d3ca1-118">更新可供安裝的產品，然後安裝 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="d3ca1-119">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="d3ca1-120">如果您收到類似 [**找不到封裝 aspnetcore-執行時間-3.1**] 的錯誤訊息，請參閱[疑難排解封裝管理員](#troubleshoot-the-package-manager)一節。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="d3ca1-121">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="d3ca1-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="d3ca1-122">更新可供安裝的產品，然後安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="d3ca1-123">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="d3ca1-124">如果您收到類似 [**找不到封裝 dotnet-執行時間-3.1**] 的錯誤訊息，請參閱[疑難排解封裝管理員](#troubleshoot-the-package-manager)一節。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="d3ca1-125">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="d3ca1-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="d3ca1-126">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="d3ca1-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="d3ca1-127">如果您收到類似「**找不到封裝 {.Net Core 封裝}** 」的錯誤訊息，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="d3ca1-128">如果無法解決問題，您可以使用下列命令來執行手動安裝。</span><span class="sxs-lookup"><span data-stu-id="d3ca1-128">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```