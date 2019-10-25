---
title: 使用 dotnet vstest 測試已發行的輸出
description: 了解如何使用 dotnet vstest 命令在已發行的程式庫 (而不是原始程式碼) 上執行測試。
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: e4fd25dc9ff30bdfe85cd1167a1dc41ea20a5f80
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771929"
---
# <a name="test-published-output-with-dotnet-vstest"></a>使用 dotnet vstest 測試已發行的輸出

您可以使用 `dotnet vstest` 命令在已經發行的輸出上執行測試。 此作法適用於 xUnit、MSTest 和 NUnit 測試。 只需找到已發行輸出之一部分的 DLL 檔，並執行：

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

其中 `<MyPublishedTests>` 是已發行測試專案的名稱。

## <a name="example"></a>範例

下列命令示範如何在已發行的 DLL 上執行測試。

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> 注意：如果您的應用程式以 `netcoreapp` 以外的架構為目標，您仍然可以藉由使用架構旗標傳入目標架構，來執行 `dotnet vstest` 命令。 例如，`dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`。 在 Visual Studio 2017 Update 5 和更新版本中，會自動偵測所需的架構。

## <a name="see-also"></a>請參閱

- [使用 dotnet test 及 xUnit 執行單元測試](unit-testing-with-dotnet-test.md)
- [使用 dotnet test 和 NUnit 執行單元測試](unit-testing-with-nunit.md)
- [使用 dotnet test 及 MSTest 執行單元測試](unit-testing-with-mstest.md)
