---
title: 使用 .NET Core 命令列介面 (CLI) 工具建立 NuGet 套件
description: 了解如何使用 'dotnet pack' 命令建立 NuGet 套件。
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 2d876f921d079972e2a638788195aa69a2423c49
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771935"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>如何使用 .NET Core 命令列介面 (CLI) 工具建立 NuGet 套件

> [!NOTE]
> 下圖顯示使用 Unix 的命令列範例。 此處顯示的 `dotnet pack` 命令，運作運作方式與在 Windows 上如出一轍。

.NET Standard 和 .NET Core 程式庫預期以 NuGet 封裝方式散發。 實際上，所有的 .NET Standard 程式庫都是以這種方式散發及取用。 `dotnet pack` 命令最容易完成此作業。

假設您剛寫完酷炫的新程式庫，希望透過 NuGet 散發。 您可以使用跨平台工具建立 NuGet 封裝，絲毫不差地完成此作業！ 下例假設 **SuperAwesomeLibrary** 程式庫以 `netstandard1.0` 為目標。

如果您有可轉移的相依性，也就是相依於另一個套件的專案，您必須先使用 `dotnet restore` 命令確保還原整個解決方案的套件，再建立 NuGet 套件。 未完成這項操作，會導致 `dotnet pack` 命令無法正常運作。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

在確定封裝還原後，您可以瀏覽至程式庫所在的目錄︰

```console
cd src/SuperAwesomeLibrary
```

然後，只要從命令列發出單一命令︰

```dotnetcli
dotnet pack
```

您的 */bin/Debug*資料夾現在看起來像這樣：

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

請注意，這會產生能夠被偵錯的封裝。 如果想要建置具有版本二進位檔案的 NuGet 套件，您只需要新增 `--configuration` (或 `-c`) 參數，並使用 `release` 作為引數。

```dotnetcli
dotnet pack --configuration release
```

您的 */bin*資料夾現在會有一個*發行*資料夾，其中包含發行二進位檔的 NuGet 套件：

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

現在您有發行 NuGet 封裝所需的檔案！

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>請勿混淆 `dotnet pack` 與 `dotnet publish`

請務必注意，和 `dotnet publish` 命令一點關係都沒有。 `dotnet publish` 命令是要使用相同組合中的所有相依性來部署應用程式，不是用來產生要透過 NuGet 散發及使用的 NuGet 封裝。

## <a name="see-also"></a>請參閱

- [快速入門：建立及發佈套件](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
