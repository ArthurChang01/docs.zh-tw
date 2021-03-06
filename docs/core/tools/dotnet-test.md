---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624887"
---
# <a name="dotnet-test"></a>dotnet test

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>描述

`dotnet test` 命令是用來在指定的專案中執行單元測試。 `dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。 測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。 如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。 針對多目標專案，會針對每個目標架構執行測試。 測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。

測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a>隱含還原

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>引數

- **`PROJECT | SOLUTION`**

  測試專案或方案的路徑。 如果未指定，則會預設為目前目錄。

## <a name="options"></a>選項。

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  在測試執行中，從指定的路徑使用自訂測試配接器。

- **`--blame`**

  在歸責模式下執行測試。 此選項有助於隔離導致測試主控制項損毀的問題測試。 它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  測試回合啟用資料收集器。 如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  啟用測試平臺的診斷模式，並將診斷訊息寫入至指定的檔案。

- **`-f|--framework <FRAMEWORK>`**

  尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。

- **`--filter <EXPRESSION>`**

  使用指定的運算式篩選出目前專案中的測試。 如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。 如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--interactive`**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 自 .NET Core 3.0 SDK 起提供。

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  指定測試結果的記錄器。 不同于`-l "console;v=d"` MSBuild，dotnet 測試不接受縮寫：而不`-l "console;verbosity=detailed"`是使用。

- **`--no-build`**

  不會在執行前建置測試專案。 它也會隱含地設定`--no-restore` -旗標。

- **`--nologo`**

  執行測試而不顯示 Microsoft TestPlatform 橫幅。 自 .NET Core 3.0 SDK 起提供。

- **`--no-restore`**

  執行命令時，不會執行隱含還原。

- **`-o|--output <OUTPUT_DIRECTORY>`**

  在其中尋找要執行的二進位檔的目錄。 如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。  針對具有多個目標 framework 的專案（ `TargetFrameworks`透過屬性），您也需要在`--framework`指定此選項時定義。 `dotnet test`一律從輸出目錄執行測試。 您可以使用<xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType>來取用輸出目錄中的測試資產。

- **`-r|--results-directory <PATH>`**

  要放置測試結果的目錄。 如果指定的目錄不存在，則會建立該目錄。 預設值是`TestResults`在包含專案檔的目錄中。

- **`--runtime <RUNTIME_IDENTIFIER>`**

  要測試的目標執行時間。

- **`-s|--settings <SETTINGS_FILE>`**

  用來執行測試的 `.runsettings` 檔案。 請注意， `TargetPlatform`元素（x86 | x64）對沒有任何作用`dotnet test`。 若要執行以 x86 為目標的測試，請安裝 x86 版本的 .NET Core。 路徑上*dotnet*的位就是用來執行測試的。 如需詳細資訊，請參閱下列資源：

  - [使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。
  - [設定測試回合](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md) \(英文\)

- **`-t|--list-tests`**

  列出在目前專案中探索到的所有測試。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值為 `minimal`。 如需詳細資訊，請參閱 <xref:Microsoft.Build.Framework.LoggerVerbosity>。

- **`RunSettings`** 參量

  引數會當做`RunSettings`測試的設定來傳遞。 指定為 "-- " 後 (注意 -- 後方的空格) 之 `[name]=[value]` 組的引數。 空格適用來分隔多個 `[name]=[value]` 組。

  範例： `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  如需詳細資訊，請參閱[透過命令列傳遞 .runsettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。

## <a name="examples"></a>範例

- 執行目前目錄之專案中的測試：

  ```dotnetcli
  dotnet test
  ```

- 執行 `test1` 專案中的測試︰

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- 在目前目錄的專案中執行測試，並產生 .trx 格式的測試結果檔案：

  ```dotnetcli
  dotnet test --logger trx
  ```

- 在目前目錄中執行專案中的測試，並使用主控台的詳細詳細資訊記錄：

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

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

沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。

運算式可以使用條件運算子聯結：

| 運算子            | 函式 |
| ------------------- | -------- |
| <code>&#124;</code> | 或者       |
| `&`                 | AND      |

使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。

如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

## <a name="see-also"></a>另請參閱

- [架構和目標](../../standard/frameworks.md)
- [.NET Core 執行階段識別項 (RID) 目錄](../rid-catalog.md)
- [透過命令列傳遞 .runsettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
