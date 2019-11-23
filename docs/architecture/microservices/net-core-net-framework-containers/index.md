---
title: 針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇
ms.date: 09/11/2018
ms.openlocfilehash: b01aaf25f4071e8e4a07905a12ec9dd0d89a738d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849268"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="60207-103">針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="60207-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="60207-104">有兩個支援的架構，可使用 .NET 來建置伺服器端容器化 Docker 應用程式：[.NET Framework 及 .NET Core](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="60207-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="60207-105">這兩者共用許多 .NET 平台元件，而您可以在這兩者間共用程式碼。</span><span class="sxs-lookup"><span data-stu-id="60207-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="60207-106">不過，兩者間有一些基本差異，而您可以依據想要完成的目標決定要使用的架構。</span><span class="sxs-lookup"><span data-stu-id="60207-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="60207-107">本節提供每個架構選擇時機的指引。</span><span class="sxs-lookup"><span data-stu-id="60207-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="60207-108">[上一頁](../container-docker-introduction/docker-containers-images-registries.md)
>[下一頁](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="60207-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
