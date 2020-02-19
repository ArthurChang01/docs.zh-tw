---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 05/29/2018
ms.openlocfilehash: 909815151265117395c6d8d13b4443a245c05f9e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451190"
---
# <a name="dotnet-test"></a>dotnet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。

## <a name="synopsis"></a>概要

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a>描述

`dotnet test` 命令是用來在指定的專案中執行單元測試。 `dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。 測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。 如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。 測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。

測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>引數

`PROJECT`

測試專案的路徑。 如果未指定，則會預設為目前目錄。

## <a name="options"></a>選項。

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

在測試執行中，從指定的路徑使用自訂測試配接器。

`--blame`

在歸責模式下執行測試。 這個選項有助於隔離造成測試主機損毀的問題。 它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

測試回合啟用資料收集器。 如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。

`-f|--framework <FRAMEWORK>`

尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。

`--filter <EXPRESSION>`

使用指定的運算式篩選出目前專案中的測試。 如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。 如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

`-h|--help`

印出命令的簡短說明。

`-l|--logger <LoggerUri/FriendlyName>`

指定測試結果的記錄器。

`--no-build`

不會在執行前建置測試專案。 它也會隱含設定 `--no-restore` 旗標。

`--no-restore`

執行命令時，不會執行隱含的還原。

`-o|--output <OUTPUT_DIRECTORY>`

在其中尋找要執行的二進位檔的目錄。

`-r|--results-directory <PATH>`

要放置測試結果的目錄。 如果指定的目錄不存在，則會建立該目錄。

`-s|--settings <SETTINGS_FILE>`

用來執行測試的 `.runsettings` 檔案。 [使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。

`-t|--list-tests`

列出在目前專案中探索到的所有測試。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

`RunSettings arguments`

針對測試傳遞為 RunSettings 設定的引數。 指定為 "-- " 後 (注意 -- 後方的空格) 之 `[name]=[value]` 組的引數。 空格適用來分隔多個 `[name]=[value]` 組。

範例： `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

如需有關 RunSettings 的詳細資訊，請參閱 [vstest.console.exe：傳遞 RunSettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md) \(英文\)。

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

在測試執行中，從指定的路徑使用自訂測試配接器。

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

測試回合啟用資料收集器。 如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。

`-f|--framework <FRAMEWORK>`

尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。

`--filter <EXPRESSION>`

使用指定的運算式篩選出目前專案中的測試。 如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。 如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

`-h|--help`

印出命令的簡短說明。

`-l|--logger <LoggerUri/FriendlyName>`

指定測試結果的記錄器。

`--no-build`

不會在執行前建置測試專案。 它也會隱含設定 `--no-restore` 旗標。

`--no-restore`

執行命令時，不會執行隱含的還原。

`-o|--output <OUTPUT_DIRECTORY>`

在其中尋找要執行的二進位檔的目錄。

`-r|--results-directory <PATH>`

要放置測試結果的目錄。 如果指定的目錄不存在，則會建立該目錄。

`-s|--settings <SETTINGS_FILE>`

用來執行測試的 `.runsettings` 檔案。 [使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。

`-t|--list-tests`

列出在目前專案中探索到的所有測試。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

在測試執行中，從指定的路徑使用自訂測試配接器。

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。

`-f|--framework <FRAMEWORK>`

尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。

`--filter <EXPRESSION>`

使用指定的運算式篩選出目前專案中的測試。 如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。 如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

`-h|--help`

印出命令的簡短說明。

`-l|--logger <LoggerUri/FriendlyName>`

指定測試結果的記錄器。

`--no-build`

不會在執行前建置測試專案。

`-o|--output <OUTPUT_DIRECTORY>`

在其中尋找要執行的二進位檔的目錄。

`-s|--settings <SETTINGS_FILE>`

用來執行測試的 `.runsettings` 檔案。 [使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。

`-t|--list-tests`

列出在目前專案中探索到的所有測試。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

---

## <a name="examples"></a>範例

執行目前目錄之專案中的測試：

`dotnet test`

執行 `test1` 專案中的測試︰

`dotnet test ~/projects/test1/test1.csproj`

在目前目錄中的專案中執行測試，並以 trx 格式產生測試結果檔案：

`dotnet test --logger trx`

## <a name="filter-option-details"></a>篩選選項詳細資料

`--filter <EXPRESSION>`

`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。

`<property>` 為 `Test Case` 的屬性。 以下為熱門單元測試架構所支援的屬性：

| 測試架構 | 支援的屬性                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>名稱</li><li>ClassName</li><li>優先順序</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>特性</li></ul>                                   |

`<operator>` 描述屬性和值之間的關聯性：

| 運算子 | 函式        |
| :------: | --------------- |
| `=`      | 完全相符     |
| `!=`     | 不完全相符 |
| `~`      | 包含        |
| `!~`     | 不包含    |

`<value>` 為字串。 所有的查閱皆不區分大小寫。

沒有 `<operator>` 的運算式會自動被視為 `contains` 屬性上的 `FullyQualifiedName` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。

運算式可以使用條件運算子聯結：

| 運算子            | 函式 |
| ------------------- | -------- |
| <code>&#124;</code> | OR       |
| `&`                 | AND      |

使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。

如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

## <a name="see-also"></a>另請參閱

- [架構與目標](../../standard/frameworks.md)
- [.NET Core 執行階段識別項 (RID) 目錄](../rid-catalog.md)
