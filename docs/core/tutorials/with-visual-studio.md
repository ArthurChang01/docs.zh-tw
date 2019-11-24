---
title: 在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式
description: 了解如何使用 Visual Studio 2017 以 C# 建置簡單的 .NET Core 主控台應用程式。
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: cc7d78006998b79fe9d522e71883ce1af817c051
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428556"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 .NET Core SDK 來建置 C# Hello World 應用程式

This article provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using C# in Visual Studio 2017. Visual Studio 2017 提供功能完整的開發環境來建置 .NET Core 應用程式。 只要應用程式沒有平台特定的相依性，應用程式就可以在 .NET Core 的任何目標平台，以及安裝 .NET Core 的任何系統上執行。

## <a name="prerequisites"></a>Prerequisites

[Visual Studio 2017 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed. You can develop your app with .NET Core 2.1 or later versions.

For more information, see the [.NET Core dependencies and requirements](../install/sdk.md?tabs=netcore30&pivots=os-windows#install-with-visual-studio)article.

## <a name="a-simple-hello-world-application"></a>簡單的 Hello World 應用程式

請開始建立簡單的 "Hello World" 主控台應用程式。 請依照下列步驟：

1. 啟動 Visual Studio。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。 然後選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，鍵入 "HelloWorld"。 選取 [確定] 按鈕。

   ![已選取 [主控台應用程式] 的 [新增專案] 對話方塊](./media/with-visual-studio/visual-studio-new-project.png)

1. Visual Studio 使用範本建立專案。 .NET Core 的 C# 主控台應用程式範本會自動定義一個 `Program` 類別，該類別具有採用 <xref:System.String> 陣列為引數的單一 `Main` 方法。 `Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/visual-studio-main-window.png)

   此範本會建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法，以在主控台視窗中顯示常值字串 "Hello World!" 。 透過使用工具列上的綠色箭頭選取 **HelloWorld** 按鈕，您可以 [偵錯] 模式執行程式。 不過，如果您這樣做，主控台視窗將會在簡短顯示之後關閉。 這是因為在 `Main` 方法中的單一陳述式執行完畢之後，`Main` 方法會立即終止，而應用程式會立即結束。

1. 若要使應用程式在關閉主控台視窗之前先暫停，請在 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法呼叫之後立即新增下列程式碼：

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   此程式碼會提示使用者按下任意鍵，並暫停程式直到按下按鍵為止。

1. 在功能表列中，選取 [組建]  >  [組建方案]。 這會將您的程式編譯成中繼語言 (IL)，而該語言是由 Just-In-Time (JIT) 編譯器轉換為二進位程式碼。

1. 透過使用工具列上的綠色箭頭選取 **HelloWorld** 按鈕來執行程式。

   ![主控台視窗顯示 Hello World，請按任意鍵以繼續](./media/with-visual-studio/hello-world-console.png)

1. 按任意鍵以關閉主控台視窗。

## <a name="enhancing-the-hello-world-application"></a>增強 Hello World 應用程式

增強您的應用程式以提示使用者輸入其名稱，並將其與日期和時間一起顯示。 若要修改並測試程式，請執行下列動作︰

1. Enter the following C# code in the code window immediately after the opening bracket that follows the `static void Main(string[] args)` line and before the first closing curly bracket:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   此程式碼會取代 `Main` 方法的內容。

   ![含有已更新之 Main 方法的 Visual Studio 程式 c-sharp 檔案](./media/with-visual-studio/visual-csharp-code-window.png)

   此程式碼會在主控台中顯示「What is your name?」， 然後等待使用者輸入字串並按 Enter 鍵。 它會將此字串儲存至名為 `name` 的變數。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 最後，使用[字串插值](../../csharp/language-reference/tokens/interpolated.md)在主控台視窗中顯示這些值。

1. 選擇 [建置]  >  [建置方案] 來編譯程式。

1. 在 Visual Studio 中以 [偵錯] 模式執行程式，方法為選取工具列上的綠色箭頭，按 F5，或是選擇 [偵錯]  >  [開始偵錯] 功能表項目。 輸入名稱並按 Enter 鍵來回應提示。

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. 按任意鍵以關閉主控台視窗。

您已建立並執行應用程式。 若要開發專業的應用程式，請執行一些其他步驟，來針對發行準備應用程式：

- 如需對應用程式進行偵錯的資訊，請參閱[使用 Visual Studio 2017 針對 .NET Core Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)。

- 如需開發和發行應用程式可散發版本的資訊，請參閱[使用 Visual Studio 2017 發行 .NET Core Hello World 應用程式](publishing-with-visual-studio.md)。

## <a name="related-articles"></a>相關文章

除了主控台應用程式之外，您也可以使用 .NET Core 和 Visual Studio 2017 建置類別庫。 如需逐步介紹，請參閱[在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫](library-with-visual-studio.md)。

您也可以使用 [Visual Studio Code](https://code.visualstudio.com/) (可免費下載的程式碼編輯器)，在 Mac、Linux 和 Windows 上開發 .NET Core 主控台應用程式。 如需逐步教學課程，請參閱[開始使用 Visual Studio Code](with-visual-studio-code.md)。
