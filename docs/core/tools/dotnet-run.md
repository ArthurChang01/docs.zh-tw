---
title: dotnet run 命令
description: dotnet run 命令提供方便的選項，以透過原始程式碼來執行應用程式。
ms.date: 10/31/2019
ms.openlocfilehash: 5920f0d1f04204b286fdf6f51f5fd13644846390
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734111"
---
# <a name="dotnet-run"></a>dotnet run

**本文適用于：** ✔️ .net CORE 1.x SDK 和更新版本

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet run` - 執行原始程式碼，而不需要有任何明確的編譯或啟動命令。

## <a name="synopsis"></a>概要

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a>描述

`dotnet run` 命令提供方便的選項，以使用一個命令透過原始程式碼來執行應用程式。 可用於在命令列中快速進行反覆開發。 此命令仰賴 [`dotnet build`](dotnet-build.md) 命令來建置程式碼。 建置的任何需求 (例如必須先還原專案) 也同樣適用於 `dotnet run`。

輸出檔會寫入至預設位置，也就是 `bin/<configuration>/<target>`。 例如，如果您有 `netcoreapp2.1` 應用程式並執行 `dotnet run`，輸出將會放置在 `bin/Debug/netcoreapp2.1` 中。 而且會視需要覆寫檔案。 暫存檔案會放置在 `obj` 目錄中。

如果專案指定多個架構，執行 `dotnet run` 會導致錯誤，除非使用 `-f|--framework <FRAMEWORK>` 選項來指定架構。

`dotnet run` 命令用於專案內容中，而非已建置的組件。 如果您改為嘗試執行與 Framework 相依的應用程式 DLL，您必須不透過命令使用 [dotnet](dotnet.md)。 例如，若要執行 `myapp.dll`，使用︰

```dotnetcli
dotnet myapp.dll
```

如需 `dotnet` 驅動程式的詳細資訊，請參閱 [.NET Core 命令列工具 (CLI)](index.md) 主題。

為了執行應用程式，`dotnet run` 命令會從 NuGet 快取解析共用執行階段之外的應用程式相依性。 因為它會使用快取相依性，不建議您在生產環境中使用 `dotnet run` 執行應用程式。 相反地，使用 [`dotnet publish`](dotnet-publish.md) 命令[建立部署](../deploying/index.md)，並部署已發佈的輸出。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>選項

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

`--`

分隔 `dotnet run` 的引數與執行中應用程式的引數。 此分隔符號之後的所有引數會傳遞至執行的應用程式。

`-c|--configuration {Debug|Release}`

定義組建組態。 大部分專案的預設值為 `Debug`。

`-f|--framework <FRAMEWORK>`

使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。 架構必須在專案檔中指定。

`--force`

即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

`-h|--help`

印出命令的簡短說明。

`--interactive`

允許命令停止並等候使用者輸入或動作 (例如完成驗證)。

`--launch-profile <NAME>`

啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。 啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。 如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。

`--no-build`

不會在執行前建置專案。 它也會隱含設定 `--no-restore` 旗標。

`--no-dependencies`

在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。

`--no-launch-profile`

不會嘗試使用 *launchSettings.json* 來設定應用程式。

`--no-restore`

執行命令時，不會執行隱含還原。

`-p|--project <PATH>`

指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。 如果未指定，則會預設為目前目錄。

`--runtime <RUNTIME_IDENTIFIER>`

指定要還原套件的目標執行階段。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--`

分隔 `dotnet run` 的引數與執行中應用程式的引數。 此分隔符號之後的所有引數會傳遞至執行的應用程式。

`-c|--configuration {Debug|Release}`

定義組建組態。 大部分專案的預設值為 `Debug`。

`-f|--framework <FRAMEWORK>`

使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。 架構必須在專案檔中指定。

`--force`

即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

`-h|--help`

印出命令的簡短說明。

`--launch-profile <NAME>`

啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。 啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。 如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。

`--no-build`

不會在執行前建置專案。 它也會隱含設定 `--no-restore` 旗標。

`--no-dependencies`

在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。

`--no-launch-profile`

不會嘗試使用 *launchSettings.json* 來設定應用程式。

`--no-restore`

執行命令時，不會執行隱含還原。

`-p|--project <PATH>`

指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。 如果未指定，則會預設為目前目錄。

`--runtime <RUNTIME_IDENTIFIER>`

指定要還原套件的目標執行階段。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--`

分隔 `dotnet run` 的引數與執行中應用程式的引數。 此分隔符號之後的所有引數會傳遞至執行的應用程式。

`-c|--configuration {Debug|Release}`

定義組建組態。 大部分專案的預設值為 `Debug`。

`-f|--framework <FRAMEWORK>`

使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。 架構必須在專案檔中指定。

`--force`

即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

`-h|--help`

印出命令的簡短說明。

`--launch-profile <NAME>`

啟動應用程式時使用的啟動設定檔名稱 (如果有的話)。 啟動設定檔是在 *launchSettings.json* 檔案中定義，通常稱為 `Development`、`Staging` 和 `Production`。 如需詳細資訊，請參閱[使用多個環境](/aspnet/core/fundamentals/environments)。

`--no-build`

不會在執行前建置專案。 它也會隱含設定 `--no-restore` 旗標。

`--no-dependencies`

在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。

`--no-launch-profile`

不會嘗試使用 *launchSettings.json* 來設定應用程式。

`--no-restore`

執行命令時，不會執行隱含還原。

`-p|--project <PATH>`

指定要執行的專案檔路徑 (資料夾名稱或完整路徑)。 如果未指定，則會預設為目前目錄。

`--runtime <RUNTIME_IDENTIFIER>`

指定要還原套件的目標執行階段。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--`

分隔 `dotnet run` 的引數與執行中應用程式的引數。 此分隔符號之後的所有引數會傳遞至執行的應用程式。

`-c|--configuration {Debug|Release}`

定義組建組態。 大部分專案的預設值為 `Debug`。

`-f|--framework <FRAMEWORK>`

使用指定的[架構](../../standard/frameworks.md)建置並執行應用程式。 架構必須在專案檔中指定。

`-h|--help`

印出命令的簡短說明。

`-p|--project <PATH/PROJECT.csproj>`

指定專案檔的路徑和名稱。 （請參閱附注）。如果未指定，則會預設為目前目錄。

> [!NOTE]
> 透過 `-p|--project` 選項使用專案檔的路徑和名稱。 CLI 中出現迴歸會無法提供具有 NET Core SDK 1.x 的資料夾路徑。 如需此問題的詳細資訊，請參閱 [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992) (dotnet run -p，無法啟動專案 (dotnet/cli #5992))。

---

## <a name="examples"></a>範例

執行目前目錄中的專案：

`dotnet run`

執行指定的專案：

`dotnet run --project ./projects/proj1/proj1.csproj`

執行目前目錄中的專案 (因為已使用空白的 `--` 選項，所以這個範例中的 `--help` 引數會傳遞給應用程式)：

`dotnet run --configuration Release -- --help`

還原相依性及目前目錄中專案的工具，只會顯示最基本的輸出，然後執行專案：(.NET Core SDK 2.0 及更新版本)：

`dotnet run --verbosity m`
