---
title: dotnet 新增參考命令
description: dotnet add reference 命令提供方便的選項，以新增專案對專案參考。
ms.date: 06/26/2019
ms.openlocfilehash: dc8bc01a2bff4f2cf3a8af9efb233448d7de337f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733279"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**本文適用于：** ✔️ .net CORE 1.x SDK 和更新版本

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>名稱

`dotnet add reference` - 新增專案對專案 (P2P) 參考。

## <a name="synopsis"></a>概要

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>描述

`dotnet add reference` 命令提供方便的選項，將專案參考新增至專案。 執行命令之後，`<ProjectReference>` 元素會加入至專案檔。

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>引數

- **`PROJECT`**

  指定專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

- **`PROJECT_REFERENCES`**

  要新增的專案對專案 (P2P) 參考。 指定一個或多個專案。 Unix/Linux 系統支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。

## <a name="options"></a>選項

- **`-h|--help`**

  印出命令的簡短說明。

- **`-f|--framework <FRAMEWORK>`**

  只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增專案參考。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作 (例如完成驗證)。 自 .NET Core 3.0 SDK 起提供使用。

## <a name="examples"></a>範例

- 新增專案參考：

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- 新增目前目錄中專案的多個專案參考：

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- 在 Linux/Unix 上使用 Glob 模式新增多個專案參考：

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
