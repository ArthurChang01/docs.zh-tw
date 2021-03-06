---
title: 在 SLES 15-套件管理員上安裝 .NET Core-.NET Core
description: 使用封裝管理員，在 SLES 15 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: be5a21db8c3942bfe8827dfbce41bcf88aec342a
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595602"
---
# <a name="sles-15-package-manager---install-net-core"></a>SLES 15 套件管理員-安裝 .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

本文說明如何使用套件管理員，在 SLES 15 上安裝 .NET Core。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>新增 Microsoft 存放庫金鑰和摘要

安裝 .NET 之前，您必須：

- 將 Microsoft 封裝簽署金鑰新增至受信任的金鑰清單。
- 將存放庫新增至套件管理員。
- 安裝必要的相依性。

每部電腦只需要執行這項作業一次。

開啟終端機並執行下列命令。

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

目前，SLES 15 Microsoft 存放庫安裝套件會將*Microsoft*存放庫檔案安裝至錯誤的目錄，以防止 zypper 尋找 .net Core 套件。 若要修正此問題，請在正確的目錄中建立符號連結。

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

更新可供安裝的產品，然後安裝 .NET Core SDK。 在您的終端機中，執行下列命令。

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>安裝 ASP.NET Core 執行時間

更新可供安裝的產品，然後安裝 ASP.NET 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行時間

更新可供安裝的產品，然後安裝 .NET Core 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>針對套件管理員進行疑難排解

本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。

### <a name="failed-to-fetch"></a>無法提取

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
