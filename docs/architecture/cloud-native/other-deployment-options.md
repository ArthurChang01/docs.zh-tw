---
title: 其他容器部署選項
description: 使用 Azure 的其他容器部署選項
ms.date: 06/30/2019
ms.openlocfilehash: 1fcb57eedec8c9f5574fffcf409b316332032062
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214452"
---
# <a name="other-container-deployment-options"></a><span data-ttu-id="2a29e-103">其他容器部署選項</span><span class="sxs-lookup"><span data-stu-id="2a29e-103">Other container deployment options</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2a29e-104">除了部署至 AKS，您也可以將容器部署到容器和 Azure 容器實例的 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="2a29e-104">In addition to deploying to AKS, you can also deploy containers to Azure App Service for Containers and Azure Container Instances.</span></span>

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a><span data-ttu-id="2a29e-105">部署至容器的 App Service 有何意義？</span><span class="sxs-lookup"><span data-stu-id="2a29e-105">When does it make sense to deploy to App Service for Containers?</span></span>

<span data-ttu-id="2a29e-106">不需要協調流程的簡單生產應用程式很適合用於容器 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="2a29e-106">Simple production applications that don't require orchestration are well-suited to Azure App Service for Containers.</span></span>

## <a name="how-to-deploy-to-app-service-for-containers"></a><span data-ttu-id="2a29e-107">如何部署至容器的 App Service</span><span class="sxs-lookup"><span data-stu-id="2a29e-107">How to deploy to App Service for Containers</span></span>

<span data-ttu-id="2a29e-108">若要部署至[容器的 Azure App Service](https://azure.microsoft.com/services/app-service/containers/)，您必須已設定 AZURE CONTAINER REGISTRY （ACR）和認證來進行存取。</span><span class="sxs-lookup"><span data-stu-id="2a29e-108">To deploy to [Azure App Service for Containers](https://azure.microsoft.com/services/app-service/containers/), you need to have configured an Azure Container Registry (ACR) and credentials for accessing it.</span></span> <span data-ttu-id="2a29e-109">將您想要裝載的容器推送至登錄，使其可供提取到您的 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="2a29e-109">Push the container you intend to host to the registry so it's available to pull into your Azure App Service.</span></span> <span data-ttu-id="2a29e-110">建立之後，您可以設定應用程式進行持續部署，每當您更新 ACR 中的對應映射時，它就會自動將更新部署至應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a29e-110">Once created, you can configure the app for Continuous Deployment, which will automatically deploy updates to the app whenever you update its corresponding image in ACR.</span></span>

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a><span data-ttu-id="2a29e-111">部署至 Azure 容器實例的時機為何？</span><span class="sxs-lookup"><span data-stu-id="2a29e-111">When does it make sense to deploy to Azure Container Instances?</span></span>

<span data-ttu-id="2a29e-112">Azure 容器實例最適合用於測試案例。</span><span class="sxs-lookup"><span data-stu-id="2a29e-112">Azure Container Instances are best used for testing scenarios.</span></span> <span data-ttu-id="2a29e-113">它們提供快速且簡單的方法，將應用程式部署至雲端裝載的容器實例。</span><span class="sxs-lookup"><span data-stu-id="2a29e-113">They provide a fast, simple way to deploy an application to a cloud-hosted container instance.</span></span> <span data-ttu-id="2a29e-114">當您不需要 Azure Kubernetes Service 所提供的調整和協調流程功能時，可使用它們來測試或示範應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a29e-114">Use them to test or demo applications when you don't require scaling and orchestration features offered by Azure Kubernetes Service.</span></span>

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a><span data-ttu-id="2a29e-115">如何將應用程式部署至 Azure 容器實例</span><span class="sxs-lookup"><span data-stu-id="2a29e-115">How to deploy an app to Azure Container Instances</span></span>

<span data-ttu-id="2a29e-116">若要部署至[Azure 容器實例（ACI）](https://docs.microsoft.com/azure/container-instances/)，您必須已設定 AZURE CONTAINER REGISTRY （ACR）和認證來進行存取。</span><span class="sxs-lookup"><span data-stu-id="2a29e-116">To deploy to [Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/), you need to have configured an Azure Container Registry (ACR) and credentials for accessing it.</span></span> <span data-ttu-id="2a29e-117">您也必須先將容器映射推送至登錄，才能將它提取到 ACI 中。</span><span class="sxs-lookup"><span data-stu-id="2a29e-117">You must also have previously pushed your container image to the registry, so it's available to pull into ACI.</span></span> <span data-ttu-id="2a29e-118">您可以使用 Azure CLI 或透過入口網站來處理 ACI。</span><span class="sxs-lookup"><span data-stu-id="2a29e-118">You can work with ACI using the Azure CLI or through the portal.</span></span> <span data-ttu-id="2a29e-119">Azure Container registry 可讓您輕鬆地直接從登錄內將個別容器實例部署至 ACI，如圖3-14 所示。</span><span class="sxs-lookup"><span data-stu-id="2a29e-119">Azure Container Registries make it easy to deploy individual container instances to ACI directly from within the registry, as shown in Figure 3-14.</span></span>

![Azure Container Registry 執行實例](./media/acr-runinstance-contextmenu.png)

<span data-ttu-id="2a29e-121">**圖 3-14**。</span><span class="sxs-lookup"><span data-stu-id="2a29e-121">**Figure 3-14**.</span></span> <span data-ttu-id="2a29e-122">Azure Container Registry 執行實例</span><span class="sxs-lookup"><span data-stu-id="2a29e-122">Azure Container Registry Run Instance</span></span>

<span data-ttu-id="2a29e-123">從登錄建立容器實例只需要您指定一般的 Azure 設定（名稱、訂用帳戶、資源群組和位置）、要配置給容器的記憶體數量，以及應該接聽的埠。</span><span class="sxs-lookup"><span data-stu-id="2a29e-123">Creating a container instance from the registry just requires you to specify the usual Azure settings (name, subscription, resource group, and location), how much memory to allocate to the container, and which port it should listen on.</span></span> <span data-ttu-id="2a29e-124">本[快速入門說明如何使用 Azure 入口網站將容器實例部署至 ACI](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal)。</span><span class="sxs-lookup"><span data-stu-id="2a29e-124">This [quickstart shows how to deploy a container instance to ACI using the Azure portal](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).</span></span>

<span data-ttu-id="2a29e-125">部署完成之後，尋找新部署容器的 IP 位址，並透過您指定的埠與其通訊。</span><span class="sxs-lookup"><span data-stu-id="2a29e-125">Once the deployment completes, find the newly deployed container's IP address and communicate with it over the port you specified.</span></span>

<span data-ttu-id="2a29e-126">Azure 容器實例提供最快速且最簡單的方式，讓您在 Azure 中執行容器。</span><span class="sxs-lookup"><span data-stu-id="2a29e-126">Azure Container Instances offers the fastest, simplest way to run a container in Azure.</span></span> <span data-ttu-id="2a29e-127">不需要設定 app service 或 orchestrator，或處理虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="2a29e-127">There's no need to configure an app service or an orchestrator or to deal with virtual machines.</span></span> <span data-ttu-id="2a29e-128">不過，由於簡單起見，ACI 主要應該用於測試用途。</span><span class="sxs-lookup"><span data-stu-id="2a29e-128">However, because of its simplicity, ACI should primarily be used for testing purposes.</span></span> <span data-ttu-id="2a29e-129">如果您的應用程式需要自動調整、多個設定為一起運作的容器，或任何其他複雜的功能，則可使用其他更適合的 Azure 服務來裝載您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a29e-129">If your application requires automatic scalability, multiple containers configured to work together, or any additional complex features, there are other better-suited Azure services available to host your app.</span></span>

## <a name="references"></a><span data-ttu-id="2a29e-130">參考</span><span class="sxs-lookup"><span data-stu-id="2a29e-130">References</span></span>

- [<span data-ttu-id="2a29e-131">Azure 容器實例檔</span><span class="sxs-lookup"><span data-stu-id="2a29e-131">Azure Container Instances Docs</span></span>](https://docs.microsoft.com/azure/container-instances/)
- [<span data-ttu-id="2a29e-132">從 ACR 部署容器實例</span><span class="sxs-lookup"><span data-stu-id="2a29e-132">Deploy Container Instance from ACR</span></span>](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
><span data-ttu-id="2a29e-133">[上一頁](scale-containers-serverless.md)
>[下一頁](communication-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="2a29e-133">[Previous](scale-containers-serverless.md)
[Next](communication-patterns.md)</span></span>
