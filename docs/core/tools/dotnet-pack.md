---
title: dotnet pack 命令
description: dotnet pack 命令會建立 .NET Core 專案的 NuGet 套件。
ms.date: 02/14/2020
ms.openlocfilehash: 3b9c46ecd5d67519728896b0018e27fb41ebd861
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463503"
---
# <a name="dotnet-pack"></a>dotnet pack

**本文適用於:✔️** .NET Core 2.x SDK 和更高版本

## <a name="name"></a>名稱

`dotnet pack` - 將程式碼封裝到 NuGet 套件。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a>描述

`dotnet pack` 命令會建置專案，並建立 NuGet 套件。 此命令的結果是 NuGet 包(即 *.nupkg*檔)。

如果要產生包含除錯符號的套件,可以使用兩個選項:

- `--include-symbols`- 它建立符號包。
- `--include-source`- 它建立符號包,其中包含`src`包含來源檔案的資料夾。

封裝專案的 NuGet 相依性會新增至 *.nuspec* 檔案，因此在安裝套件時可以正確地解析它們。 專案對專案參考不會封裝到專案內。 目前，如果您有專案對專案相依性，則必須一個專案各一個套件。

`dotnet pack` 預設會先建置專案。 如果您想要避免這種行為，請傳遞 `--no-build` 選項。 這個選項通常適用於您知道先前剛建立程式碼的持續整合 (CI) 組建案例。

> [!NOTE]
> 在某些情況下,無法執行隱式生成。 設置時`GeneratePackageOnBuild`可能會發生這種情況,以避免生成目標和包目標之間存在循環依賴關係。 如果存在鎖定的檔或其他問題,生成也可能失敗。

您可以提供 MSBuild 屬性給 `dotnet pack` 命令來壓縮程序。 如需詳細資訊，請參閱 [NuGet 中繼資料屬性](csproj.md#nuget-metadata-properties)和 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。 [範例](#examples)一節示範針對數個不同案例使用 MSBuild -p 參數的方法。

Web 專案預設無法封裝。 若要覆寫預設行為，請將下列屬性新增至您的 .csproj** 檔案：

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>引數

`PROJECT | SOLUTION`

  要打包的專案或解決方案。 它要麼是[csproj 檔案](csproj.md)、解決方案檔或目錄的路徑。 如果未指定,該命令將搜索當前目錄以搜索專案或解決方案檔。

## <a name="options"></a>選項。

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 大多數項目的預設值為,`Debug`但您可以覆蓋專案中的生成配置設置。

- **`--force`**

  即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--include-source`**

  除了輸出目錄中的常規 NuGet 包之外,還包括調試符號 NuGet 包。 源檔包含在符號包中的`src`資料夾中。

- **`--include-symbols`**

  除了輸出目錄中的常規 NuGet 包之外,還包括調試符號 NuGet 包。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作 (例如完成驗證)。 自 .NET Core 3.0 SDK 起提供。

- **`--no-build`**

  不會在封裝前建置專案。 選項也會隱含設定 `--no-restore` 旗標。

- **`--no-dependencies`**

  忽略專案對專案參考，並且只還原根專案。

- **`--no-restore`**

  執行命令時，不會執行隱含還原。

- **`--nologo`**

  不要顯示程式啟始橫幅或著作權訊息。 自 .NET Core 3.0 SDK 起提供。

- **`-o|--output <OUTPUT_DIRECTORY>`**

  將已建置的套件放置在指定的目錄中。

- **`--runtime <RUNTIME_IDENTIFIER>`**

  指定要還原套件的目標執行階段。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

- **`-s|--serviceable`**

  在套件中設定可提供服務的旗標。 如需詳細資訊，請參閱 [.NET 部落格︰.NET 4.5.1 支援適用於 .NET NuGet 程式庫的 Microsoft 安全性更新 (英文)](https://aka.ms/nupkgservicing)。

- **`--version-suffix <VERSION_SUFFIX>`**

  在專案中定義 `$(VersionSuffix)` MSBuild 屬性的值。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

## <a name="examples"></a>範例

- 封裝目前目錄中的專案：

  ```dotnetcli
  dotnet pack
  ```

- 封裝 `app1` 專案：

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- 封裝目前目錄中的專案，並將產生的套件放置到 `nupkgs` 資料夾中：

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- 將目前目錄中的專案封裝到 `nupkgs` 資料夾，並略過建置步驟︰

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- 在 *.csproj* 檔案中將專案的版本尾碼設定為 `<VersionSuffix>$(VersionSuffix)</VersionSuffix>`，封裝目前的專案並使用指定尾碼更新產生的套件版本︰

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- 使用 `PackageVersion` MSBuild 屬性將封裝版本設定為 `2.1.0`：

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- 將專案針對特定[目標 Framework](../../standard/frameworks.md) 進行封裝：

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- 包裝專案並使用特定的執行時(Windows 10)進行還原操作:

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- 使用 [.nuspec 檔案](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)來封裝專案：

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
