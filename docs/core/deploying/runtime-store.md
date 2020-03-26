---
title: 執行階段套件存放區
description: 了解如何使用 .NET Core 所使用的執行階段套件存放區和目標資訊清單。
ms.date: 08/12/2017
ms.openlocfilehash: ba3182b682e8a47397ac09ed46afe25190d34e5f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134266"
---
# <a name="runtime-package-store"></a><span data-ttu-id="be8d9-103">執行階段套件存放區</span><span class="sxs-lookup"><span data-stu-id="be8d9-103">Runtime package store</span></span>

<span data-ttu-id="be8d9-104">從 .NET Core 2.0 開始，可針對目標環境中存在的已知套件集合封裝和部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="be8d9-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="be8d9-105">優點是部署更快、磁碟空間使用量較少，而且啟動效能在某些情況下有所改善。</span><span class="sxs-lookup"><span data-stu-id="be8d9-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="be8d9-106">這項功能實作為「執行階段套件存放區」\*\*，這是套件儲存所在磁碟的目錄 (通常在 macOS/Linux 是 */usr/local/share/dotnet/store*，在 Windows 是 *C:/Program Files/dotnet/store*)。</span><span class="sxs-lookup"><span data-stu-id="be8d9-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="be8d9-107">在此目錄下，有架構和[目標 Framework](../../standard/frameworks.md) 的子目錄。</span><span class="sxs-lookup"><span data-stu-id="be8d9-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="be8d9-108">檔案配置類似於[磁碟上的 NuGet 資產配置](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)方式：</span><span class="sxs-lookup"><span data-stu-id="be8d9-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

<span data-ttu-id="be8d9-109">「目標資訊清單」\*\* 檔會列出執行階段套件存放區中的套件。</span><span class="sxs-lookup"><span data-stu-id="be8d9-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="be8d9-110">開發人員可在發佈其應用程式時，以此資訊清單為目標。</span><span class="sxs-lookup"><span data-stu-id="be8d9-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="be8d9-111">目標資訊清單通常是由目標生產環境的擁有者提供。</span><span class="sxs-lookup"><span data-stu-id="be8d9-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="be8d9-112">準備執行階段環境</span><span class="sxs-lookup"><span data-stu-id="be8d9-112">Preparing a runtime environment</span></span>

<span data-ttu-id="be8d9-113">執行階段環境的系統管理員可以建置執行階段套件存放區和對應的目標資訊清單，以最佳化應用程式，取得更快的部署和較少的磁碟使用空間。</span><span class="sxs-lookup"><span data-stu-id="be8d9-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="be8d9-114">第一個步驟是建立「套件存放區資訊清單」\*\*，列出撰寫執行階段套件存放區的套件。</span><span class="sxs-lookup"><span data-stu-id="be8d9-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="be8d9-115">此檔案格式與專案檔格式 (*csproj*) 相容。</span><span class="sxs-lookup"><span data-stu-id="be8d9-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="be8d9-116">**範例**</span><span class="sxs-lookup"><span data-stu-id="be8d9-116">**Example**</span></span>

<span data-ttu-id="be8d9-117">下例使用套件存放區資訊清單 (*packages.csproj*) 將 [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) 和 [`Moq`](https://www.nuget.org/packages/moq/) 新增至執行階段套件存放區：</span><span class="sxs-lookup"><span data-stu-id="be8d9-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="be8d9-118">執行 `dotnet store` 加上套件存放區資訊清單、執行階段和架構，佈建執行階段套件存放區：</span><span class="sxs-lookup"><span data-stu-id="be8d9-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="be8d9-119">**範例**</span><span class="sxs-lookup"><span data-stu-id="be8d9-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="be8d9-120">通過在命令中重複選項和路徑，可以將多個目標包[`dotnet store`](../tools/dotnet-store.md)存儲清單路徑傳遞給單個命令。</span><span class="sxs-lookup"><span data-stu-id="be8d9-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="be8d9-121">根據預設，命令的輸出位在使用者設定檔的 *.dotnet/store* 子目錄下的套件存放區中。</span><span class="sxs-lookup"><span data-stu-id="be8d9-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="be8d9-122">您可以使用 `--output <OUTPUT_DIRECTORY>` 選項指定不同的位置。</span><span class="sxs-lookup"><span data-stu-id="be8d9-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="be8d9-123">存放區的根目錄包含目標資訊清單 *artifact.xml* 檔案。</span><span class="sxs-lookup"><span data-stu-id="be8d9-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="be8d9-124">此檔案可供下載，並可供想要在發行時以此存放區為目標的應用程式作者使用。</span><span class="sxs-lookup"><span data-stu-id="be8d9-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="be8d9-125">**範例**</span><span class="sxs-lookup"><span data-stu-id="be8d9-125">**Example**</span></span>

<span data-ttu-id="be8d9-126">執行上例後，會產生以下 *artifact.xml* 檔案。</span><span class="sxs-lookup"><span data-stu-id="be8d9-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="be8d9-127">請注意，[`Castle.Core`](https://www.nuget.org/packages/Castle.Core/)它是 的依賴項`Moq`，因此它會自動包含在*工件.xml*清單檔中。</span><span class="sxs-lookup"><span data-stu-id="be8d9-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="be8d9-128">針對目標資訊清單發行應用程式</span><span class="sxs-lookup"><span data-stu-id="be8d9-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="be8d9-129">如果磁片上具有目標清單檔，則在使用[`dotnet publish`](../tools/dotnet-publish.md)以下命令發佈應用時指定檔的路徑：</span><span class="sxs-lookup"><span data-stu-id="be8d9-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="be8d9-130">**範例**</span><span class="sxs-lookup"><span data-stu-id="be8d9-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="be8d9-131">您會將所產生的已發行應用程式，部署到有目標資訊清單所述套件的環境中。</span><span class="sxs-lookup"><span data-stu-id="be8d9-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="be8d9-132">無法這樣做，會導致應用程式無法啟動。</span><span class="sxs-lookup"><span data-stu-id="be8d9-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="be8d9-133">重複選項和路徑 (例如 `--manifest manifest1.xml --manifest manifest2.xml`)，以在發行應用程式時，指定多個目標資訊清單。</span><span class="sxs-lookup"><span data-stu-id="be8d9-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="be8d9-134">當您這樣做時，會針對提供給命令的目標資訊清單檔中指定的套件聯集修剪應用程式。</span><span class="sxs-lookup"><span data-stu-id="be8d9-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="be8d9-135">在專案檔中指定目標資訊清單</span><span class="sxs-lookup"><span data-stu-id="be8d9-135">Specifying target manifests in the project file</span></span>

<span data-ttu-id="be8d9-136">使用[`dotnet publish`](../tools/dotnet-publish.md)命令指定目標清單的替代方法是在專案檔案中將它們指定為**\<目標清單>** 標記下的路徑分號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="be8d9-136">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="be8d9-137">只有當應用程式的目標環境為已知時，例如 .NET Core 專案，才在專案檔中指定目標資訊清單。</span><span class="sxs-lookup"><span data-stu-id="be8d9-137">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="be8d9-138">這不是開放原始碼專案的情況。</span><span class="sxs-lookup"><span data-stu-id="be8d9-138">This isn't the case for open-source projects.</span></span> <span data-ttu-id="be8d9-139">開放原始碼專案的使用者通常會將它部署到不同的生產環境中。</span><span class="sxs-lookup"><span data-stu-id="be8d9-139">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="be8d9-140">這些生產環境通常會有不同的預先安裝的套件集。</span><span class="sxs-lookup"><span data-stu-id="be8d9-140">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="be8d9-141">不能在這樣的環境中對目標清單進行假設，因此應使用`--manifest`選項。 [`dotnet publish`](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="be8d9-141">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="be8d9-142">ASP.NET Core 隱含存放區</span><span class="sxs-lookup"><span data-stu-id="be8d9-142">ASP.NET Core implicit store</span></span>

<span data-ttu-id="be8d9-143">ASP.NET Core 隱含存放區只適用於 ASP.NET Core 2.0。</span><span class="sxs-lookup"><span data-stu-id="be8d9-143">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="be8d9-144">強烈建議應用程式使用 ASP.NET Core 2.1 和更新版本，這些**不**會使用隱含存放區。</span><span class="sxs-lookup"><span data-stu-id="be8d9-144">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="be8d9-145">ASP.NET Core 2.1 和更新版本會使用共用的架構。</span><span class="sxs-lookup"><span data-stu-id="be8d9-145">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="be8d9-146">當應用程式部署為[與 Framework 相依的部署 (FDD)](index.md#publish-runtime-dependent) 應用程式時，ASP.NET Core 應用程式會以隱含方式使用執行階段套件存放區功能。</span><span class="sxs-lookup"><span data-stu-id="be8d9-146">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app.</span></span> <span data-ttu-id="be8d9-147">中[`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk)的目標包括引用目標系統上的隱式包存儲的清單。</span><span class="sxs-lookup"><span data-stu-id="be8d9-147">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="be8d9-148">此外，任何相依於 `Microsoft.AspNetCore.All` 套件的 FDD 應用程式，都會造成已發行的應用程式只包含應用程式及其資產，不包含 `Microsoft.AspNetCore.All` 中繼套件列出的套件。</span><span class="sxs-lookup"><span data-stu-id="be8d9-148">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="be8d9-149">假設這些套件存在於目標系統上。</span><span class="sxs-lookup"><span data-stu-id="be8d9-149">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="be8d9-150">安裝 .NET Core SDK 時，執行階段套件存放區會安裝在主機上。</span><span class="sxs-lookup"><span data-stu-id="be8d9-150">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="be8d9-151">其他的安裝程式可能會提供執行階段套件存放區，包括 .NET Core SDK 的 Zip/tarball 安裝、`apt-get`、Red Hat Yum、.NET Core Windows Server 裝載組合，以及手動的執行階段套件存放區安裝。</span><span class="sxs-lookup"><span data-stu-id="be8d9-151">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="be8d9-152">部署[與 Framework 相依的部署 (FDD)](index.md#publish-runtime-dependent) 應用程式時，請確定目標環境已安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="be8d9-152">When deploying a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="be8d9-153">如果應用部署到不包含ASP.NET酷睿的環境，則可以通過指定`false`**\<PublishAspNetCoreTarget>** 在專案檔案中設置為"隱式存儲"，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="be8d9-153">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="be8d9-154">若為[獨立部署 (SCD)](index.md#publish-self-contained) 應用程式，假設目標系統不必然包含必要的資訊清單套件。</span><span class="sxs-lookup"><span data-stu-id="be8d9-154">For [self-contained deployment (SCD)](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="be8d9-155">因此，`true`無法為 SCD 應用設置**\<發佈AspNetCoreTargetmanifest>。**</span><span class="sxs-lookup"><span data-stu-id="be8d9-155">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="be8d9-156">如果您部署的應用程式具有存在於部署中的資訊清單相依性 (組件位於 *bin* 資料夾)，主機對該組件「不會使用」\*\* 執行階段套件存放區。</span><span class="sxs-lookup"><span data-stu-id="be8d9-156">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="be8d9-157">無論主機的執行階段套件存放區是否有 *bin* 資料夾組件，都使用它。</span><span class="sxs-lookup"><span data-stu-id="be8d9-157">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="be8d9-158">資訊清單中指示的相依性版本，必須符合執行階段套件存放區中的相依性版本。</span><span class="sxs-lookup"><span data-stu-id="be8d9-158">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="be8d9-159">如果目標資訊清單中的相依性版本與執行階段套件存放區的版本不相符，而應用程式的部署中不包含必要的套件版本，則應用程式無法啟動。</span><span class="sxs-lookup"><span data-stu-id="be8d9-159">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="be8d9-160">例外狀況包含目標資訊清單的名稱，為執行階段套件存放區組件所稱呼的名稱，有利於針對不符合進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="be8d9-160">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="be8d9-161">於發行時「修剪」\*\* 部署，已發行的輸出只保留您指定的資訊清單套件特定版本。</span><span class="sxs-lookup"><span data-stu-id="be8d9-161">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="be8d9-162">主機必須要有指定版本的套件，應用程式才能啟動。</span><span class="sxs-lookup"><span data-stu-id="be8d9-162">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="be8d9-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be8d9-163">See also</span></span>

- [<span data-ttu-id="be8d9-164">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="be8d9-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="be8d9-165">dotnet-store</span><span class="sxs-lookup"><span data-stu-id="be8d9-165">dotnet-store</span></span>](../tools/dotnet-store.md)
