---
title: dotnet nuget push 命令
description: dotnet nuget push 命令會將套件推送至伺服器並發行。
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: d4ef8e58908fe488c712debff3b313ac0908b43e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503667"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**本文適用于：✔️** .NET Core 2.x SDK 和更高版本

## <a name="name"></a>名稱

`dotnet nuget push` - 將套件推送至伺服器並發行。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>描述

`dotnet nuget push` 命令會將套件推送至伺服器並發行。 推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。 如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。 NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。

## <a name="arguments"></a>引數

- **`ROOT`**

  指定套件推送目標的檔案路徑。

## <a name="options"></a>選項。

- **`-d|--disable-buffering`**

  推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。

- **`--force-english-output`**

  強制使用非變異英文文化特性來執行應用程式。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--interactive`**

  允許命令進行封鎖及要求對驗證之類的作業採取手動動作。 自 .NET Core 2.2 SDK 起可用的選項。

- **`-k|--api-key <API_KEY>`**

  伺服器的 API 金鑰。

- **`-n|--no-symbols`**

  不推送符號 (即使存在)。

- **`--no-service-endpoint`**

  不會將 "api/v2/package" 附加至來源 URL。 自 .NET Core 2.1 SDK 起可用的選項。

- **`-s|--source <SOURCE>`**

  指定伺服器 URL。 除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。

- **`--skip-duplicate`**

  將多個包推送到 HTTP（S） 伺服器時，將任何 409 衝突回應視為警告，以便推送可以繼續。 自 .NET 核心 3.1 SDK 以來可用。

- **`-sk|--symbol-api-key <API_KEY>`**

  符號伺服器的 API 金鑰。

- **`-ss|--symbol-source <SOURCE>`**

  指定符號伺服器 URL。

- **`-t|--timeout <TIMEOUT>`**

  指定推送至伺服器的逾時 (以秒為單位)。 預設為 300 秒 (5 分鐘)。 指定 0 (零秒) 會套用預設值。

## <a name="examples"></a>範例

- 將 *foo.nupkg* 推送至預設推送來源，指定 API 金鑰：

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- 將*foo.nupkg*推送到正式的 NuGet 伺服器，指定 API 金鑰：

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * 將 *foo.nupkg* 推送至自訂推送來源 `https://customsource`，指定 API 金鑰：

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- 將 *foo.nupkg* 推送至預設推送來源：

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- 將 *foo.symbols.nupkg* 推送至預設符號來源：

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- 將 *foo.nupkg* 推送至預設推送來源，指定 360 秒逾時：

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- 將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源：

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > 如果此命令無法運作，可能是舊版 SDK (.NET Core 2.1 SDK 及更舊版本) 中有 Bug 所致。
  > 若要修正此問題，請升級您的 SDK 版本，或改為執行下列命令：`dotnet nuget push **/*.nupkg`

- 即使 HTTP（S） 伺服器返回 409 衝突回應，也會推送所有 *.nupkg*檔：

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
