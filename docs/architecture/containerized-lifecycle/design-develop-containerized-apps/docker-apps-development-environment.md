---
title: Docker 應用程式的開發環境
description: 了解可支援 Docker 開發生命週期的最重要開發工具選項。
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214299"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="3f0b4-103">Docker 應用程式的開發環境</span><span class="sxs-lookup"><span data-stu-id="3f0b4-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="3f0b4-104">開發工具選擇：IDE 或編輯器</span><span class="sxs-lookup"><span data-stu-id="3f0b4-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="3f0b4-105">不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都能支援您開發 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="3f0b4-106">Visual Studio Code 和 Docker CLI (適用於 Mac、Linux 和 Windows 的跨平台工具)</span><span class="sxs-lookup"><span data-stu-id="3f0b4-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="3f0b4-107">如果您偏好使用支援任何開發語言的輕量型、跨平台編輯器，您可以使用 Visual Studio Code 和 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="3f0b4-108">這些產品提供簡單但強大的體驗，這對簡化開發人員工作流程來說非常重要。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="3f0b4-109">藉由安裝「適用於 Mac 的 Docker」或「適用於 Windows 的 Docker」(開發環境)，Docker 開發人員可以使用單一 Docker CLI 來建置 Windows 或 Linux (執行階段環境) 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="3f0b4-110">此外，Visual Studio Code 支援 Docker 的延伸模組 (內含適用於 Dockerfile 的 IntelliSense)，以及可從編輯器執行 Docker 命令的捷徑工作。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="3f0b4-111">若要下載 Visual Studio Code，請前往 <https://code.visualstudio.com/download>。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="3f0b4-112">若要下載適用於 Mac 和 Windows 的 Docker，請前往 <https://www.docker.com/products/docker>。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="3f0b4-113">具備 Docker 工具的 Visual Studio (Windows 開發電腦)</span><span class="sxs-lookup"><span data-stu-id="3f0b4-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="3f0b4-114">我們建議您使用已啟用內建 Docker 工具的 Visual Studio 2017 (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="3f0b4-115">使用 Visual Studio，您可以直接在所選 Docker 環境中開發、執行及驗證應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="3f0b4-116">請按 F5 鍵直接在 Docker 主機中對您的應用程式 (單一容器或多個容器) 進行偵錯，或按 Ctrl+F5 來編輯及重新整理您的應用程式，而不需要重建容器。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="3f0b4-117">這是 Windows 開發人員用以建立 Linux 或 Windows 之 Docker 容器的最簡單且最強大選擇。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="3f0b4-118">Visual Studio for Mac (Mac 開發電腦)</span><span class="sxs-lookup"><span data-stu-id="3f0b4-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="3f0b4-119">您可以在開發以 Docker 為基礎的應用程式時，使用 [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="3f0b4-120">相較於 Visual Studio Code for Mac，Visual Studio for Mac 提供更豐富的 IDE。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="3f0b4-121">語言和架構選擇</span><span class="sxs-lookup"><span data-stu-id="3f0b4-121">Language and framework choices</span></span>

<span data-ttu-id="3f0b4-122">您可以使用 Microsoft 工具　搭配大部分的現代語言來開發 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="3f0b4-123">下列是初始清單，但不僅限於此：</span><span class="sxs-lookup"><span data-stu-id="3f0b4-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="3f0b4-124">.NET Core 與 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3f0b4-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="3f0b4-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="3f0b4-125">Node.js</span></span>
- <span data-ttu-id="3f0b4-126">移至</span><span class="sxs-lookup"><span data-stu-id="3f0b4-126">Go</span></span>
- <span data-ttu-id="3f0b4-127">Java</span><span class="sxs-lookup"><span data-stu-id="3f0b4-127">Java</span></span>
- <span data-ttu-id="3f0b4-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="3f0b4-128">Ruby</span></span>
- <span data-ttu-id="3f0b4-129">Python</span><span class="sxs-lookup"><span data-stu-id="3f0b4-129">Python</span></span>

<span data-ttu-id="3f0b4-130">基本上，您可以使用 Linux 或 Windows 中 Docker 所援的任何現代語言。</span><span class="sxs-lookup"><span data-stu-id="3f0b4-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3f0b4-131">[上一頁](deploy-azure-kubernetes-service.md)
>[下一頁](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3f0b4-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
