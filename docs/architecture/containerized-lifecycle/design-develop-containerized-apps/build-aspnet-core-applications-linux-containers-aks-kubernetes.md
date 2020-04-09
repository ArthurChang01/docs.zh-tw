---
title: 建置以 Linux 容器部署到 AKS/Kubernetes 叢集的 ASP.NET Core 2.2 應用程式
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.date: 02/25/2019
ms.openlocfilehash: 83d4d0a60db4bdc112bb35bfbf61c0396646ad31
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989021"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>建置以 Linux 容器部署到 AKS/Kubernetes 協調器的 ASP.NET Core 2.2 應用程式

Azure Kubernetes Service (AKS) 是 Azure 的受控 Kubernetes 協調流程服務，可簡化容器部署和管理。

AKS 的主要功能包括：

- Azure 裝載的控制平面
- 自動升級
- 自我修復
- 可由使用者設定的調整大小功能
- 對開發人員和叢集操作員更簡單的使用者體驗。

下列範例探索如何建立在 Linux 上執行並部署到 Azure 中 AKS 叢集的 ASP.NET Core 2.2 應用程式，同時使用 Visual Studio 2017 進行開發。

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>使用 Visual Studio 2017 建立 ASP.NET Core 2.2 專案

ASP.NET Core 是一般用途的開發平台，由 Microsoft 和 GitHub 上的 .NET 社群共同維護。 它可以跨平台支援 Windows、macOS 及 Linux，並可用於裝置、雲端和內嵌式系統/IoT 等應用情節。

此範例使用以 Visual Studio Web API 範本為基礎的簡單專案，因此您不需要任何額外的知識來建立範例。 您只需要使用一個標準範本來建立專案，該範本採用 ASP.NET Core 2.2 技術，內含可透過 REST API 執行小型專案的所有項目。

![在 Visual Studio 中新增專案視窗，並選取 ASP.NET Core Web 應用程式。](media/create-aspnet-core-application.png)

**圖 4-36**. 建立 ASP.NET Core 應用程式

您可以在 Visual Studio 建立範例**專案**,請選擇 **「檔案** > **新專案** > 」,在左邊窗格中選擇**Web**專案類型,然後**選擇 ASP.NET 核心 Web 應用程式**。

Visual Studio 會列出適用於 Web 專案的範本。 在我們的範例中，選取 [API]**** 以建立 ASP.NET Web API 應用程式。

確認您已選取 ASP.NET Core 2.2 作為架構。 .NET Core 2.2 隨附於上一版的 Visual Studio 2017，並會在您安裝 Visual Studio 2017 時自動為您安裝和設定。

![用於選取 ASP.NET Core Web 應用程式類型並已選取 API 選項的 Visual Studio 對話方塊。](media/create-web-api-application.png)

**圖 4-37**. 選取 ASP.NET CORE 2.2 和 Web API 專案類型

如果您有任何舊版 .NET Core，您可以從 <https://dotnet.microsoft.com/download> 下載並安裝 2.2 版。

您可以在建立專案期間或之後新增 Docker 支援，以便可隨時將您的專案「Docker 化」。 要在項目創建後添加 Docker 支援,請右鍵單擊解決方案資源管理器中的專案節點,並在上下文菜單上選擇 **「添加** > **Docker 支援**」。

![將 Docker 支援添加到現有專案的上下文選單選項:右鍵單擊(在專案上)>添加> Docker 支援。](media/add-docker-support-to-project.png)

**圖 4-38**. 將 Docker 支援新增至現有的專案

若要完成新增 Docker 支援，您可以選擇 [Windows] 或 [Linux]。 在這種情況下,選擇**Linux**,因為 AKS 不支援 Windows 容器(截至 2018 年末)。

![用於選取 Dockerfile 目標 OS 的選項對話方塊。](media/select-linux-docker-support.png)

**圖 4-39**. 選取 Linux 容器。

透過這些簡單的步驟，您就會有在 Linux 容器上執行的 ASP.NET Core 2.2 應用程式。

正如您所看到的,Visual Studio 2017 和 Docker 之間的整合完全面向開發人員的工作效率。

現在，您可以按 **F5** 鍵或使用 [播放]**** 按鈕來執行應用程式。

執行專案之後，您可以使用 `docker images` 命令列出映像。 您應該會看到使用 Visual Studio 2017 自動部署專案所建立的 `mssampleapplication` 映像。

```console
docker images
```

![來自 Docker 映像命令的主控台輸出顯示具有:儲存庫、標記、圖像 ID、已創建(日期)和大小的清單。](media/docker-images-command.png)

**圖 4-40**. Docker 映像檢視

## <a name="register-the-solution-in-the-azure-container-registry"></a>在 Azure Container Registry 中註冊方案

將映像上傳到任何 Docker 登錄 (例如 [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) 或 Docker Hub)，以便將映像從該登錄部署到 AKS 叢集。 在這種情況下,我們將映射上載到 Azure 容器註冊表。

### <a name="create-the-image-in-release-mode"></a>在 [發行] 模式中建立映像

我們現在要在 [發行]**** 模式中建立映像 (用於生產環境)，做法是變更為 [發行]**** (如圖 4-41 所示)，然後如往常般執行應用程式。

![在 [發行] 模式中建置的 VS 工具列選項。](media/select-release-mode.png)

**圖 4-41**. 選取 [發行] 模式

如果您執行 `docker image` 命令，您會看到建立兩個映像，一個用於 `debug` 模式，另一個用於 `release` 模式。

### <a name="create-a-new-tag-for-the-image"></a>為映像建立新的標記

每個容器映像都必須標記登錄的 `loginServer` 名稱。 將容器映像推送到映像登錄時，此標籤可用於路由傳送。

您可以從 Azure 入口網站檢視 `loginServer` 名稱，然後從 Azure Container Registry 擷取資訊

![Azure Container Registry 名稱的瀏覽器檢視，位於右上方。](media/loginServer-name.png)

**圖 4-42**. Registry 名稱檢視

或執行下列命令：

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![上述命令的主控台輸出。](media/az-cli-loginServer-name.png)

**圖 4-43**. 使用 PowerShell 取得登錄名稱

在這兩種情況下，您都會取得名稱。 在我們的範例中為 `mssampleacr.azurecr.io`。

現在您可以使用命令來標記映像，然後擷取最新的映像 (發行映像)：

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

執行 `docker tag` 命令之後，請使用 `docker images` 命令列出映像，您應該會看到具有新標記的映像。

![docker images 命令的主控台輸出。](media/tagged-docker-images-list.png)

**圖 4-44**. 已標記的映像檢視

### <a name="push-the-image-into-the-azure-acr"></a>將映像推送到 Azure ACR

登入 Azure Container Registry

```console
az acr login --name mssampleacr
```

使用下列命令將映像推送到 Azure ACR：

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

此命令需要一些時間上傳映像，但會在程序中提供回饋給您。

![docker push 命令的主控台輸出：顯示以字元為主的進度列來表示每個圖層。](media/uploading-image-to-acr.png)

**圖 4-45**. 將映像上傳到 ACR

當程序完成時，您應該會收到如下所示的結果：

![docker push 命令的主控台輸出，已完成，並顯示所有圖層或節點。](media/uploading-docker-images-complete.png)

**圖 4-46**. 節點檢視

下一個步驟是將您的容器部署到 AKS Kubernetess 叢集。 為此，您需要包含下列內容的檔案 (**.yml 部署檔案**)：

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - name: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> 如需使用 Kubernetes 部署的詳細資訊，請參閱：<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

現在，您幾乎準備好使用 **Kubectl** 進行部署，但首先，您必須使用下列命令將認證擷取到 AKS 叢集：

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![來自上述指令的主控台輸出:合併的「MSSampleK8Cluster」為 /root/.kube/config 中的目前上下文](media/getting-aks-credentials.png)

**圖 4-47**. 取得認證

然後，使用 `kubectl create` 命令啟動部署。

```console
kubectl create -f mssample-deploy.yml
```

![上述命令的主控台輸出：已建立部署 "mssamplesbook"。 已建立服務 "mssample-kub-app"。](media/kubectl-create-command.png)

**圖 4-48**. 部署至 Kubernetes

部署完成時，您可以使用可透過下列命令暫時存取的本機 Proxy 來存取 Kubernetes 主控台：

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

然後存取 URL `http://127.0.0.1:8001`。

![Kubernetes 儀表板的瀏覽器檢視，其中顯示 [部署]、[Pod]、[複本集] 和 [服務]。](media/kubernetes-cluster-information.png)

**圖 4-49**. 檢視 Kubernetes 叢集資訊

現在您已使用 Linux 容器和 AKS Kubernetes 叢集在 Azure 上部署應用程式。 您可以存取瀏覽至您服務公用 IP 的應用程式，並可從 Azure 入口網站取得此服務。

> [!NOTE]
> 您可以在本指南的[**部署到 Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) 一節中，了解如何為此範例建立 AKS 叢集。

>[!div class="step-by-step"]
>[前一個](set-up-windows-containers-with-powershell.md)
>[下一個](../docker-devops-workflow/index.md)
