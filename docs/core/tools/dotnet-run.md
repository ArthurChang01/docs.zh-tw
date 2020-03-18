---
title: dotnet run 命令
description: dotnet run 命令提供方便的選項，以透過原始程式碼來執行應用程式。
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157072"
---
# <a name="dotnet-run"></a><span data-ttu-id="bedb5-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="bedb5-103">dotnet run</span></span>

<span data-ttu-id="bedb5-104">**本文適用于：✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="bedb5-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bedb5-105">名稱</span><span class="sxs-lookup"><span data-stu-id="bedb5-105">Name</span></span>

<span data-ttu-id="bedb5-106">`dotnet run` - 執行原始程式碼，而不需要有任何明確的編譯或啟動命令。</span><span class="sxs-lookup"><span data-stu-id="bedb5-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bedb5-107">概要</span><span class="sxs-lookup"><span data-stu-id="bedb5-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a><span data-ttu-id="bedb5-108">描述</span><span class="sxs-lookup"><span data-stu-id="bedb5-108">Description</span></span>

<span data-ttu-id="bedb5-109">`dotnet run` 命令提供方便的選項，以使用一個命令透過原始程式碼來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="bedb5-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="bedb5-110">可用於在命令列中快速進行反覆開發。</span><span class="sxs-lookup"><span data-stu-id="bedb5-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="bedb5-111">該命令取決於生成代碼[`dotnet build`](dotnet-build.md)的命令。</span><span class="sxs-lookup"><span data-stu-id="bedb5-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="bedb5-112">建置的任何需求 (例如必須先還原專案) 也同樣適用於 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="bedb5-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="bedb5-113">輸出檔會寫入至預設位置，也就是 `bin/<configuration>/<target>`。</span><span class="sxs-lookup"><span data-stu-id="bedb5-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="bedb5-114">例如，如果您有 `netcoreapp2.1` 應用程式並執行 `dotnet run`，輸出將會放置在 `bin/Debug/netcoreapp2.1` 中。</span><span class="sxs-lookup"><span data-stu-id="bedb5-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="bedb5-115">而且會視需要覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="bedb5-115">Files are overwritten as needed.</span></span> <span data-ttu-id="bedb5-116">暫存檔案會放置在 `obj` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="bedb5-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="bedb5-117">如果專案指定多個架構，執行 `dotnet run` 會導致錯誤，除非使用 `-f|--framework <FRAMEWORK>` 選項來指定架構。</span><span class="sxs-lookup"><span data-stu-id="bedb5-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="bedb5-118">`dotnet run` 命令用於專案內容中，而非已建置的組件。</span><span class="sxs-lookup"><span data-stu-id="bedb5-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="bedb5-119">如果您改為嘗試執行與 Framework 相依的應用程式 DLL，您必須不透過命令使用 [dotnet](dotnet.md)。</span><span class="sxs-lookup"><span data-stu-id="bedb5-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="bedb5-120">例如，若要執行 `myapp.dll`，使用︰</span><span class="sxs-lookup"><span data-stu-id="bedb5-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="bedb5-121">如需 `dotnet` 驅動程式的詳細資訊，請參閱 [.NET Core 命令列工具 (CLI)](index.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="bedb5-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="bedb5-122">為了執行應用程式，`dotnet run` 命令會從 NuGet 快取解析共用執行階段之外的應用程式相依性。</span><span class="sxs-lookup"><span data-stu-id="bedb5-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="bedb5-123">因為它會使用快取相依性，不建議您在生產環境中使用 `dotnet run` 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="bedb5-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="bedb5-124">相反地，使用 [`dotnet publish`](dotnet-publish.md) 命令[建立部署](../deploying/index.md)，並部署已發佈的輸出。</span><span class="sxs-lookup"><span data-stu-id="bedb5-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="bedb5-125">選項。</span><span class="sxs-lookup"><span data-stu-id="bedb5-125">Options</span></span>

- **`--`**

  <span data-ttu-id="bedb5-126">分隔 `dotnet run` 的引數與執行中應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="bedb5-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="bedb5-127">此分隔符號之後的所有引數會傳遞至執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bedb5-127">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="bedb5-128">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="bedb5-128">Defines the build configuration.</span></span> <span data-ttu-id="bedb5-129">大多數專案的預設值為 ，`Debug`但您可以覆蓋專案中的組建組態設置。</span><span class="sxs-lookup"><span data-stu-id="bedb5-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bedb5-130">使用指定的[框架](../../standard/frameworks.md)生成並運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="bedb5-130">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="bedb5-131">架構必須在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="bedb5-131">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="bedb5-132">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="bedb5-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="bedb5-133">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="bedb5-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bedb5-134">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="bedb5-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="bedb5-135">允許命令停止並等候使用者輸入或動作 (例如完成驗證)。</span><span class="sxs-lookup"><span data-stu-id="bedb5-135">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="bedb5-136">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="bedb5-136">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="bedb5-137">啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="bedb5-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="bedb5-138">啟動設定檔在*啟動設置.json*檔中定義，通常稱為`Development`和`Staging`。 `Production`</span><span class="sxs-lookup"><span data-stu-id="bedb5-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="bedb5-139">有關詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。</span><span class="sxs-lookup"><span data-stu-id="bedb5-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="bedb5-140">不會在執行前建置專案。</span><span class="sxs-lookup"><span data-stu-id="bedb5-140">Doesn't build the project before running.</span></span> <span data-ttu-id="bedb5-141">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="bedb5-141">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="bedb5-142">在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。</span><span class="sxs-lookup"><span data-stu-id="bedb5-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="bedb5-143">不會嘗試使用 *launchSettings.json* 來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="bedb5-143">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bedb5-144">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="bedb5-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="bedb5-145">指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。</span><span class="sxs-lookup"><span data-stu-id="bedb5-145">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="bedb5-146">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="bedb5-146">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="bedb5-147">指定要還原套件的目標執行階段。</span><span class="sxs-lookup"><span data-stu-id="bedb5-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="bedb5-148">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="bedb5-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="bedb5-149">`-r`短選項可用，因為 .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="bedb5-149">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bedb5-150">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="bedb5-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bedb5-151">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="bedb5-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="bedb5-152">預設值是 `m`。</span><span class="sxs-lookup"><span data-stu-id="bedb5-152">The default value is `m`.</span></span> <span data-ttu-id="bedb5-153">自 .NET 核心 2.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="bedb5-153">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="bedb5-154">範例</span><span class="sxs-lookup"><span data-stu-id="bedb5-154">Examples</span></span>

- <span data-ttu-id="bedb5-155">執行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="bedb5-155">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="bedb5-156">執行指定的專案：</span><span class="sxs-lookup"><span data-stu-id="bedb5-156">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="bedb5-157">執行目前目錄中的專案 (因為已使用空白的 `--` 選項，所以這個範例中的 `--help` 引數會傳遞給應用程式)：</span><span class="sxs-lookup"><span data-stu-id="bedb5-157">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="bedb5-158">還原相依性及目前目錄中專案的工具，只會顯示最基本的輸出，然後執行專案：(.NET Core SDK 2.0 及更新版本)：</span><span class="sxs-lookup"><span data-stu-id="bedb5-158">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
