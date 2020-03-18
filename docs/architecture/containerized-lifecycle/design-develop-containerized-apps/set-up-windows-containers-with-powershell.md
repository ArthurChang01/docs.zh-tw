---
title: 在 DockerFile 中使用 Windows PowerShell 命令來設定 Windows 容器 (以 Docker 標準為基礎)
description: 了解如何在 Windows 容器中使用 Docker 時利用 PowerShell
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "68673575"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="92097-103">在 DockerFile 中使用 Windows PowerShell 命令來設定 Windows 容器 (以 Docker 標準為基礎)</span><span class="sxs-lookup"><span data-stu-id="92097-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="92097-104">透過 [Windows 容器](/virtualization/windowscontainers/about/index)，您可以將現有的 Windows 應用程式轉換成 Docker 映像，並使用相同工具將它們部署為 Docker 生態系統的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="92097-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="92097-105">若要使用 Windows 容器，您只需要在 Dockerfile 中撰寫 Windows PowerShell 命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="92097-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="92097-106">在此案例中，我們會使用 Windows PowerShell 來安裝 Windows Server Core 基本映像以及 IIS。</span><span class="sxs-lookup"><span data-stu-id="92097-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="92097-107">使用類似的方式，您也可以使用 Windows PowerShell 命令來安裝其他元件，例如傳統的 ASP.NET 4.x 和 .NET 4.6 或任何其他 Windows 軟體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="92097-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="92097-108">[上一個](visual-studio-tools-for-docker.md)
>[下一個](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="92097-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
