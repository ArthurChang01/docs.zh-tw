---
title: dotnet msbuild 命令
description: dotnet msbuild 命令提供對 MSBuild 命令列的存取。
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733191"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="e71fd-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="e71fd-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e71fd-104">Name</span><span class="sxs-lookup"><span data-stu-id="e71fd-104">Name</span></span>

<span data-ttu-id="e71fd-105">`dotnet msbuild` - 建置專案和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="e71fd-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e71fd-106">概要</span><span class="sxs-lookup"><span data-stu-id="e71fd-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="e71fd-107">描述</span><span class="sxs-lookup"><span data-stu-id="e71fd-107">Description</span></span>

<span data-ttu-id="e71fd-108">`dotnet msbuild` 命令可存取完整功能的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="e71fd-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="e71fd-109">此命令與僅適用于 SDK 樣式專案的現有 MSBuild 命令列用戶端具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="e71fd-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="e71fd-110">選項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="e71fd-110">The options are all the same.</span></span> <span data-ttu-id="e71fd-111">如需可用選項的詳細資訊，請參閱[MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="e71fd-111">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="e71fd-112">[dotnet build](dotnet-build.md) 命令等同於 `dotnet msbuild -restore -target:Build`。</span><span class="sxs-lookup"><span data-stu-id="e71fd-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="e71fd-113">[dotnet build](dotnet-build.md)較常用來建立專案，但因為它一律會執行組建目標，所以當您不想要建立專案時，可以使用 `dotnet msbuild`。</span><span class="sxs-lookup"><span data-stu-id="e71fd-113">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="e71fd-114">例如，如果您有想要執行而不建立專案的特定目標，請使用 `dotnet msbuild` 並指定目標。</span><span class="sxs-lookup"><span data-stu-id="e71fd-114">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="e71fd-115">範例</span><span class="sxs-lookup"><span data-stu-id="e71fd-115">Examples</span></span>

* <span data-ttu-id="e71fd-116">建置專案和其相依性：</span><span class="sxs-lookup"><span data-stu-id="e71fd-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="e71fd-117">使用發行組態來建置專案和其相依性︰</span><span class="sxs-lookup"><span data-stu-id="e71fd-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* <span data-ttu-id="e71fd-118">執行發行目標並針對 `osx.10.11-x64` RID 發行：</span><span class="sxs-lookup"><span data-stu-id="e71fd-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="e71fd-119">查看整個專案和 SDK 包含的所有目標：</span><span class="sxs-lookup"><span data-stu-id="e71fd-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
