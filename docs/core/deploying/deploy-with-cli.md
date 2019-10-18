---
title: 使用 CLI 發佈 .NET Core 應用程式
description: 了解如何使用 .NET Core SDK 命令列介面 (CLI) 工具發佈 .NET Core 應用程式。
author: thraka
ms.author: adegeo
ms.date: 01/16/2019
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: c8b4c60eb4ea09c8b10bd0b2fffc803d0a5fb6e0
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834286"
---
# <a name="publish-net-core-apps-with-the-cli"></a><span data-ttu-id="cf4e8-103">使用 CLI 發佈 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="cf4e8-103">Publish .NET Core apps with the CLI</span></span>

<span data-ttu-id="cf4e8-104">本文示範如何從命令列發佈 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-104">This article demonstrates how you can publish your .NET Core application from the command line.</span></span> <span data-ttu-id="cf4e8-105">.NET Core 提供三種發佈應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-105">.NET Core provides three ways to publish your applications.</span></span> <span data-ttu-id="cf4e8-106">Framework 相依部署會產生跨平台的 .dll 檔案，以使用本機安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-106">Framework-dependent deployment produces a cross-platform .dll file that uses the locally installed .NET Core runtime.</span></span> <span data-ttu-id="cf4e8-107">Framework 相依可執行檔會產生平台特定的可執行檔，來使用本機安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-107">Framework-dependent executable produces a platform-specific executable that uses the locally installed .NET Core runtime.</span></span> <span data-ttu-id="cf4e8-108">獨立式可執行檔則會產生平台特定的可執行檔，並包含 .NET Core 執行階段的本機複本。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-108">Self-contained executable produces a platform-specific executable and includes a local copy of the .NET Core runtime.</span></span>

<span data-ttu-id="cf4e8-109">如需這些發佈模式的概觀，請參閱 [.NET Core 應用程式部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-109">For an overview of these publishing modes, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="cf4e8-110">需要一些使用 CLI 的快速說明嗎？</span><span class="sxs-lookup"><span data-stu-id="cf4e8-110">Looking for some quick help on using the CLI?</span></span> <span data-ttu-id="cf4e8-111">下表顯示一些如何發佈應用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-111">The following table shows some examples of how to publish your app.</span></span> <span data-ttu-id="cf4e8-112">您可以使用 `-f <TFM>` 參數或藉由編輯專案檔來指定目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-112">You can specify the target framework with the `-f <TFM>` parameter or by editing the project file.</span></span> <span data-ttu-id="cf4e8-113">如需詳細資訊，請參閱[發佈基本概念](#publishing-basics)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-113">For more information, see [Publishing basics](#publishing-basics).</span></span>

| <span data-ttu-id="cf4e8-114">發佈模式</span><span class="sxs-lookup"><span data-stu-id="cf4e8-114">Publish Mode</span></span> | <span data-ttu-id="cf4e8-115">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="cf4e8-115">SDK Version</span></span> | <span data-ttu-id="cf4e8-116">命令</span><span class="sxs-lookup"><span data-stu-id="cf4e8-116">Command</span></span> |
| ------------ | ----------- | ------- |
| <span data-ttu-id="cf4e8-117">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="cf4e8-117">Framework-dependent deployment</span></span> | <span data-ttu-id="cf4e8-118">2.x</span><span class="sxs-lookup"><span data-stu-id="cf4e8-118">2.x</span></span> | `dotnet publish -c Release` |
| <span data-ttu-id="cf4e8-119">Framework 相依可執行檔</span><span class="sxs-lookup"><span data-stu-id="cf4e8-119">Framework-dependent executable</span></span> | <span data-ttu-id="cf4e8-120">2.2</span><span class="sxs-lookup"><span data-stu-id="cf4e8-120">2.2</span></span> | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | <span data-ttu-id="cf4e8-121">3.0</span><span class="sxs-lookup"><span data-stu-id="cf4e8-121">3.0</span></span> | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | <span data-ttu-id="cf4e8-122">3.0\*</span><span class="sxs-lookup"><span data-stu-id="cf4e8-122">3.0\*</span></span> | `dotnet publish -c Release` |
| <span data-ttu-id="cf4e8-123">自封式部署</span><span class="sxs-lookup"><span data-stu-id="cf4e8-123">Self-contained deployment</span></span>      | <span data-ttu-id="cf4e8-124">2.1</span><span class="sxs-lookup"><span data-stu-id="cf4e8-124">2.1</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | <span data-ttu-id="cf4e8-125">2.2</span><span class="sxs-lookup"><span data-stu-id="cf4e8-125">2.2</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | <span data-ttu-id="cf4e8-126">3.0</span><span class="sxs-lookup"><span data-stu-id="cf4e8-126">3.0</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |

<span data-ttu-id="cf4e8-127">\* 使用 SDK 3.0 版時，相依於架構的可執行檔是執行基本 `dotnet publish` 命令時的預設發佈模式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-127">\* When using SDK version 3.0, framework-dependent executable is the default publishing mode when running the basic `dotnet publish` command.</span></span> <span data-ttu-id="cf4e8-128">這只適用於以 **.NET Core 2.1** 或 **.NET Core 3.0** 為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-128">This only applies when the project targets either **.NET Core 2.1** or **.NET Core 3.0**.</span></span>

## <a name="publishing-basics"></a><span data-ttu-id="cf4e8-129">發佈基本概念</span><span class="sxs-lookup"><span data-stu-id="cf4e8-129">Publishing basics</span></span>

<span data-ttu-id="cf4e8-130">專案檔的 `<TargetFramework>` 設定會指定發佈應用程式時的預設目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-130">The `<TargetFramework>` setting of the project file specifies the default target framework when you publish your app.</span></span> <span data-ttu-id="cf4e8-131">您可以將目標 Framework 變更為任何有效的[目標 Framework Moniker (TFM)](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-131">You can change the target framework to any valid [Target Framework Moniker (TFM)](../../standard/frameworks.md).</span></span> <span data-ttu-id="cf4e8-132">例如，如果您的專案使用 `<TargetFramework>netcoreapp2.2</TargetFramework>`，就會建立以 .NET Core 2.2 為目標的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-132">For example, if your project uses `<TargetFramework>netcoreapp2.2</TargetFramework>`, a binary that targets .NET Core 2.2 is created.</span></span> <span data-ttu-id="cf4e8-133">此設定中所指定 TFM 是 [`dotnet publish`](../tools/dotnet-publish.md) 命令使用的預設目標。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-133">The TFM specified in this setting is the default target used by the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="cf4e8-134">如果您想要以多個 Framework 為目標，則可以將 `<TargetFrameworks>` 設定設為以分號隔開的多個 TFM 值。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-134">If you want to target more than one framework, you can set the `<TargetFrameworks>` setting to more than one TFM value separated by a semicolon.</span></span> <span data-ttu-id="cf4e8-135">您可以使用 `dotnet publish -f <TFM>` 命令來發佈其中一個 Framework。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-135">You can publish one of the frameworks with the `dotnet publish -f <TFM>` command.</span></span> <span data-ttu-id="cf4e8-136">例如，如果您的專案具有 `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` 並執行 `dotnet publish -f netcoreapp2.1`，就會建立以 .NET Core 2.1 為目標的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-136">For example, if you have `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` and run `dotnet publish -f netcoreapp2.1`, a binary that targets .NET Core 2.1 is created.</span></span>

<span data-ttu-id="cf4e8-137">除非另行設定，否則 [`dotnet publish`](../tools/dotnet-publish.md) 命令的輸出目錄為 `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-137">Unless otherwise set, the output directory of the [`dotnet publish`](../tools/dotnet-publish.md) command is `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`.</span></span> <span data-ttu-id="cf4e8-138">除非使用 `-c` 參數加以變更，否則預設的**組建組態**模式為 [偵錯]。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-138">The default **BUILD-CONFIGURATION** mode is **Debug** unless changed with the `-c` parameter.</span></span> <span data-ttu-id="cf4e8-139">例如，`dotnet publish -c Release -f netcoreapp2.1` 會發佈至 `myfolder/bin/Release/netcoreapp2.1/publish/`。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-139">For example, `dotnet publish -c Release -f netcoreapp2.1` publishes to `myfolder/bin/Release/netcoreapp2.1/publish/`.</span></span>

<span data-ttu-id="cf4e8-140">如果您使用 .NET Core SDK 3.0，則以 .NET Core 2.1 版、2.2 版或 3.0 版為目標的應用程式其預設發佈模式為 Framework 相依可執行檔。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-140">If you use .NET Core SDK 3.0, the default publish mode for apps that target .NET Core versions 2.1, 2.2, or 3.0 is framework-dependent executable.</span></span>

<span data-ttu-id="cf4e8-141">如果您使用 .NET Core SDK 2.1，則以 .NET Core 2.1 版、2.2 版為目標的應用程式其預設發佈模式為 Framework 相依部署。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-141">If you use .NET Core SDK 2.1, the default publish mode for apps that target .NET Core versions 2.1, 2.2 is framework-dependent deployment.</span></span>

### <a name="native-dependencies"></a><span data-ttu-id="cf4e8-142">原生相依性</span><span class="sxs-lookup"><span data-stu-id="cf4e8-142">Native dependencies</span></span>

<span data-ttu-id="cf4e8-143">如果您的應用程式具有原生相依性，它可能無法在不同的作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-143">If your app has native dependencies, it may not run on a different operating system.</span></span> <span data-ttu-id="cf4e8-144">例如，如果您的應用程式使用原生 Windows API，它就不會在 macOS 或 Linux 上執行。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-144">For example, if your app uses the native Windows API, it won't run on macOS or Linux.</span></span> <span data-ttu-id="cf4e8-145">您必須提供平台特定程式碼，並為每個平台編譯可執行檔。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-145">You would need to provide platform-specific code and compile an executable for each platform.</span></span>

<span data-ttu-id="cf4e8-146">另外，請考慮如果您參考的程式庫具有原生相依性，您的應用程式可能無法在每個平台上執行。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-146">Consider also, if a library you referenced has a native dependency, your app may not run on every platform.</span></span> <span data-ttu-id="cf4e8-147">不過，您參考的 NuGet 套件可能包含了平台特定版本，以便為您處理必要的原生相依性。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-147">However, it's possible a NuGet package you're referencing has included platform-specific versions to handle the required native dependencies for you.</span></span>

<span data-ttu-id="cf4e8-148">散發具有原生相依性的應用程式時，您可能需要使用 `dotnet publish -r <RID>` 參數來指定想要為其發佈的目標平台。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-148">When distributing an app with native dependencies, you may need to use the `dotnet publish -r <RID>` switch to specify the target platform you want to publish for.</span></span> <span data-ttu-id="cf4e8-149">如需執行階段識別碼清單，請參閱[執行階段識別碼 (RID) 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-149">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

<span data-ttu-id="cf4e8-150">平台特定二進位檔的詳細資訊涵蓋在 [Framework 相依可執行檔](#framework-dependent-executable)和[獨立式部署](#self-contained-deployment)章節中。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-150">More information about platform-specific binaries is covered in the [Framework-dependent executable](#framework-dependent-executable) and [Self-contained deployment](#self-contained-deployment) sections.</span></span>

## <a name="sample-app"></a><span data-ttu-id="cf4e8-151">範例應用程式</span><span class="sxs-lookup"><span data-stu-id="cf4e8-151">Sample app</span></span>

<span data-ttu-id="cf4e8-152">您可以使用下列應用程式來流覽發佈命令。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-152">You can use the following app to explore the publishing commands.</span></span> <span data-ttu-id="cf4e8-153">在終端機中執行下列命令即可建立此應用程式：</span><span class="sxs-lookup"><span data-stu-id="cf4e8-153">The app is created by running the following commands in your terminal:</span></span>

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

<span data-ttu-id="cf4e8-154">主控台範本所產生的 `Program.cs` 或 `Program.vb` 檔案必須變更如下：</span><span class="sxs-lookup"><span data-stu-id="cf4e8-154">The `Program.cs` or `Program.vb` file that is generated by the console template needs to be changed to the following:</span></span>

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

<span data-ttu-id="cf4e8-155">當您執行應用程式 ([`dotnet run`](../tools/dotnet-run.md)) 時，即會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cf4e8-155">When you run the app ([`dotnet run`](../tools/dotnet-run.md)), the following output is displayed:</span></span>

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a><span data-ttu-id="cf4e8-156">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="cf4e8-156">Framework-dependent deployment</span></span>

<span data-ttu-id="cf4e8-157">若為 .NET Core SDK 2.x CLI，Framework 相依部署 (FDD) 是基本 `dotnet publish` 命令的預設模式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-157">For the .NET Core SDK 2.x CLI, framework-dependent deployment (FDD) is the default mode for the basic `dotnet publish` command.</span></span>

<span data-ttu-id="cf4e8-158">當您將應用程式發佈為 FDD 時，就會在 `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` 資料夾中建立 `<PROJECT-NAME>.dll` 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-158">When you publish your app as an FDD, a `<PROJECT-NAME>.dll` file is created in the `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` folder.</span></span> <span data-ttu-id="cf4e8-159">若要執行您的應用程式，請巡覽至輸出資料夾，並使用 `dotnet <PROJECT-NAME>.dll` 命令。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-159">To run your app, navigate to the output folder and use the `dotnet <PROJECT-NAME>.dll` command.</span></span>

<span data-ttu-id="cf4e8-160">您的應用程式會設定為以 .NET Core 特定版本為目標。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-160">Your app is configured to target a specific version of .NET Core.</span></span> <span data-ttu-id="cf4e8-161">該目標 .NET Core 執行階段必須位於您想要用來執行應用程式的電腦上。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-161">That targeted .NET Core runtime is required to be on the machine where you want to run your app.</span></span> <span data-ttu-id="cf4e8-162">例如，如果您的應用程式以 .NET Core 2.2 為目標，則應用程式執行所在的任何電腦都必須已安裝 .NET Core 2.2 執行階段。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-162">For example, if your app targets .NET Core 2.2, any machine that your app runs on must have the .NET Core 2.2 runtime installed.</span></span> <span data-ttu-id="cf4e8-163">依照[發佈基本概念](#publishing-basics)一節中所述，您可以編輯專案檔來變更預設的目標 Framework，或以多個 Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-163">As stated in the [Publishing basics](#publishing-basics) section, you can edit your project file to change the default target framework or to target more than one framework.</span></span>

<span data-ttu-id="cf4e8-164">發佈 FDD 會建立一個應用程式，以自動向前復原到應用程式執行所在系統上可用的最新 .NET Core 安全性修補程式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-164">Publishing an FDD creates an app that automatically rolls-forward to the latest .NET Core security patch available on the system that runs the app.</span></span> <span data-ttu-id="cf4e8-165">如需編譯時期版本繫結的詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md#framework-dependent-apps-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-165">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

## <a name="framework-dependent-executable"></a><span data-ttu-id="cf4e8-166">Framework 相依可執行檔</span><span class="sxs-lookup"><span data-stu-id="cf4e8-166">Framework-dependent executable</span></span>

<span data-ttu-id="cf4e8-167">針對 .NET Core SDK 3.x CLI，與 Framework 相依的可執行檔（FDE）是基本 `dotnet publish` 命令的預設模式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-167">For the .NET Core SDK 3.x CLI, framework-dependent executable (FDE) is the default mode for the basic `dotnet publish` command.</span></span> <span data-ttu-id="cf4e8-168">只要您想要以目前的作業系統為目標，就不需要指定任何其他參數。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-168">You don't need to specify any other parameters as long as you want to target the current operating system.</span></span>

<span data-ttu-id="cf4e8-169">在此模式中，將會建立平台特定可執行檔主機來裝載您的跨平台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-169">In this mode, a platform-specific executable host is created to host your cross-platform app.</span></span> <span data-ttu-id="cf4e8-170">此模式類似於 FDD，因為 FDD 需要 `dotnet` 命令形式的主機。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-170">This mode is similar to FDD as FDD requires a host in the form of the `dotnet` command.</span></span> <span data-ttu-id="cf4e8-171">主機可執行檔的檔名因平台而異，且其名稱類似於 `<PROJECT-FILE>.exe`。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-171">The host executable filename varies per platform, and is named something similar to `<PROJECT-FILE>.exe`.</span></span> <span data-ttu-id="cf4e8-172">您可以直接執行這個可執行檔，而不是呼叫 `dotnet <PROJECT-FILE>.dll` (這仍然是可接受的應用程式執行方式)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-172">You can run this executable directly instead of calling `dotnet <PROJECT-FILE>.dll` which is still an acceptable way to run the app.</span></span>

<span data-ttu-id="cf4e8-173">您的應用程式會設定為以 .NET Core 特定版本為目標。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-173">Your app is configured to target a specific version of .NET Core.</span></span> <span data-ttu-id="cf4e8-174">該目標 .NET Core 執行階段必須位於您想要用來執行應用程式的電腦上。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-174">That targeted .NET Core runtime is required to be on the machine where you want to run your app.</span></span> <span data-ttu-id="cf4e8-175">例如，如果您的應用程式以 .NET Core 2.2 為目標，則應用程式執行所在的任何電腦都必須已安裝 .NET Core 2.2 執行階段。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-175">For example, if your app targets .NET Core 2.2, any machine that your app runs on must have the .NET Core 2.2 runtime installed.</span></span> <span data-ttu-id="cf4e8-176">依照[發佈基本概念](#publishing-basics)一節中所述，您可以編輯專案檔來變更預設的目標 Framework，或以多個 Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-176">As stated in the [Publishing basics](#publishing-basics) section, you can edit your project file to change the default target framework or to target more than one framework.</span></span>

<span data-ttu-id="cf4e8-177">發佈 FDE 會建立一個應用程式，以自動向前復原到應用程式執行所在系統上可用的最新 .NET Core 安全性修補程式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-177">Publishing an FDE creates an app that automatically rolls-forward to the latest .NET Core security patch available on the system that runs the app.</span></span> <span data-ttu-id="cf4e8-178">如需編譯時期版本繫結的詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md#framework-dependent-apps-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-178">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

<span data-ttu-id="cf4e8-179">您必須 (當您以目前平台為目標時，.NET Core 3.x 除外) 使用下列參數搭配 `dotnet publish` 命令來發佈 FDE：</span><span class="sxs-lookup"><span data-stu-id="cf4e8-179">You must (except for .NET Core 3.x when you target the current platform) use the following switches with the `dotnet publish` command to publish an FDE:</span></span>

- <span data-ttu-id="cf4e8-180">`-r <RID>` 此參數會使用識別碼 (RID) 來指定目標平台。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-180">`-r <RID>` This switch uses an identifier (RID) to specify the target platform.</span></span> <span data-ttu-id="cf4e8-181">如需執行階段識別碼清單，請參閱[執行階段識別碼 (RID) 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-181">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

- <span data-ttu-id="cf4e8-182">`--self-contained false` 此參數會指示 .NET Core SDK 將可執行檔建立為 FDE。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-182">`--self-contained false` This switch tells the .NET Core SDK to create an executable as an FDE.</span></span>

<span data-ttu-id="cf4e8-183">只要您使用 `-r` 參數，輸出資料夾路徑就會變更為： `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`</span><span class="sxs-lookup"><span data-stu-id="cf4e8-183">Whenever you use the `-r` switch, the output folder path changes to: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`</span></span>

<span data-ttu-id="cf4e8-184">如果您使用[範例應用程式](#sample-app)，請執行 `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-184">If you use the [example app](#sample-app), run `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`.</span></span> <span data-ttu-id="cf4e8-185">此命令會建立下列可執行檔： `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`</span><span class="sxs-lookup"><span data-stu-id="cf4e8-185">This command creates the following executable: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="cf4e8-186">您可以啟用**全域無差異模式**來減少您部署的大小總計。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-186">You can reduce the total size of your deployment by enabling **globalization invariant mode**.</span></span> <span data-ttu-id="cf4e8-187">此模式適用於非全域應用程式，其能使用格式化慣例、大小寫慣例及字串比較，還有[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture)的排序次序。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-187">This mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span> <span data-ttu-id="cf4e8-188">如需**全球化不變模式**和如何啟用的詳細資訊，請參閱[.Net Core 全球化不變模式](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-188">For more information about **globalization invariant mode** and how to enable it, see [.NET Core Globalization Invariant Mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span>

## <a name="self-contained-deployment"></a><span data-ttu-id="cf4e8-189">自封式部署</span><span class="sxs-lookup"><span data-stu-id="cf4e8-189">Self-contained deployment</span></span>

<span data-ttu-id="cf4e8-190">當您發佈獨立式部署 (SCD) 時，.NET Core SDK 會建立平台特定的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-190">When you publish a self-contained deployment (SCD), the .NET Core SDK creates a platform-specific executable.</span></span> <span data-ttu-id="cf4e8-191">發佈 SCD 包含執行應用程式所需的所有 .NET Core 檔案，但不包含[.Net Core 的原生](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)相依性。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-191">Publishing an SCD includes all required .NET Core files to run your app but it doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span> <span data-ttu-id="cf4e8-192">在執行應用程式之前，系統上必須具有這些相依性。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-192">These dependencies must be present on the system before the app runs.</span></span>

<span data-ttu-id="cf4e8-193">發佈 SCD 會建立一個應用程式，該應用程式不會向前復原到最新可用的 .NET Core 安全性修補程式。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-193">Publishing an SCD creates an app that doesn't roll-forward to the latest available .NET Core security patch.</span></span> <span data-ttu-id="cf4e8-194">如需編譯時期版本繫結的詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md#self-contained-deployments-include-the-selected-runtime)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-194">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).</span></span>

<span data-ttu-id="cf4e8-195">您必須使用下列參數搭配 `dotnet publish` 命令來發佈 SCD：</span><span class="sxs-lookup"><span data-stu-id="cf4e8-195">You must use the following switches with the `dotnet publish` command to publish an SCD:</span></span>

- <span data-ttu-id="cf4e8-196">`-r <RID>` 此參數會使用識別碼 (RID) 來指定目標平台。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-196">`-r <RID>` This switch uses an identifier (RID) to specify the target platform.</span></span> <span data-ttu-id="cf4e8-197">如需執行階段識別碼清單，請參閱[執行階段識別碼 (RID) 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-197">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

- <span data-ttu-id="cf4e8-198">`--self-contained true` 此參數會指示 .NET Core SDK 將可執行檔建立為 SCD。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-198">`--self-contained true` This switch tells the .NET Core SDK to create an executable as an SCD.</span></span>

> [!NOTE]
> <span data-ttu-id="cf4e8-199">您可以啟用**全域無差異模式**來減少您部署的大小總計。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-199">You can reduce the total size of your deployment by enabling **globalization invariant mode**.</span></span> <span data-ttu-id="cf4e8-200">此模式適用於非全域應用程式，其能使用格式化慣例、大小寫慣例及字串比較，還有[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture)的排序次序。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-200">This mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span> <span data-ttu-id="cf4e8-201">如需**全球化不變模式**和如何啟用的詳細資訊，請參閱[.Net Core 全球化不變模式](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4e8-201">For more information about **globalization invariant mode** and how to enable it, see [.NET Core Globalization Invariant Mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf4e8-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf4e8-202">See also</span></span>

- [<span data-ttu-id="cf4e8-203">.NET Core 應用程式部署概觀</span><span class="sxs-lookup"><span data-stu-id="cf4e8-203">.NET Core Application Deployment Overview</span></span>](index.md)
- [<span data-ttu-id="cf4e8-204">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="cf4e8-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
