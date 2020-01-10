---
title: 非同步檔案 I/O
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
ms.openlocfilehash: 66e7d01f37a1119b9d2076a9131aa40f26d15625
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708187"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="04570-102">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="04570-102">Asynchronous File I/O</span></span>

<span data-ttu-id="04570-103">非同步作業可讓您執行耗用大量資源的 I/O 作業，而不需要封鎖主執行緒。</span><span class="sxs-lookup"><span data-stu-id="04570-103">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="04570-104">這項效能考慮在 Windows 8.x 儲存應用程式或傳統型應用程式中特別重要，因為在此情況下，耗時的資料流程作業可以封鎖 UI 執行緒，讓您的應用程式看起來像是無法運作。</span><span class="sxs-lookup"><span data-stu-id="04570-104">This performance consideration is particularly important in a Windows 8.x Store app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="04570-105">從 .NET Framework 4.5 開始，I/O 類型包含非同步方法，可簡化非同步作業。</span><span class="sxs-lookup"><span data-stu-id="04570-105">Starting with the .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="04570-106">非同步方法在其名稱中包含 `Async` ，例如 <xref:System.IO.Stream.ReadAsync%2A>、 <xref:System.IO.Stream.WriteAsync%2A>、 <xref:System.IO.Stream.CopyToAsync%2A>、 <xref:System.IO.Stream.FlushAsync%2A>、 <xref:System.IO.TextReader.ReadLineAsync%2A>和 <xref:System.IO.TextReader.ReadToEndAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="04570-106">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="04570-107">這些非同步方法會在 Stream 類別上實作 (例如 <xref:System.IO.Stream>、 <xref:System.IO.FileStream>和 <xref:System.IO.MemoryStream>)，以及在用於從資料流讀取或寫入資料流的類別上實作 (例如 <xref:System.IO.TextReader> 和 <xref:System.IO.TextWriter>)。</span><span class="sxs-lookup"><span data-stu-id="04570-107">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="04570-108">在 .NET Framework 4 (含) 以前版本中，您必須使用方法 (例如 <xref:System.IO.Stream.BeginRead%2A> 和 <xref:System.IO.Stream.EndRead%2A> ) 實作非同步 I/O 作業。</span><span class="sxs-lookup"><span data-stu-id="04570-108">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="04570-109">.NET Framework 4.5 仍會提供這些方法以支援舊版程式碼；不過，非同步方法可協助您更輕鬆地實作非同步 I/O 作業。</span><span class="sxs-lookup"><span data-stu-id="04570-109">These methods are still available in the .NET Framework 4.5 to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="04570-110">C# 和 Visual Basic 各有兩個進行非同步程式設計的關鍵字：</span><span class="sxs-lookup"><span data-stu-id="04570-110">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="04570-111">`Async` (Visual Basic) 或 `async` (C#) 修飾詞，用來標記包含非同步作業的方法。</span><span class="sxs-lookup"><span data-stu-id="04570-111">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="04570-112">`Await` (Visual Basic) 或 `await` (C#) 運算子，會套用至非同步方法的結果。</span><span class="sxs-lookup"><span data-stu-id="04570-112">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="04570-113">若要實作非同步 I/O 作業，請搭配非同步方法使用這些關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="04570-113">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="04570-114">如需詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](../../csharp/programming-guide/concepts/async/index.md) 或[使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="04570-114">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="04570-115">下列範例示範如何使用兩個 <xref:System.IO.FileStream> 物件，以非同步方式將檔案從一個目錄複製到另一個目錄。</span><span class="sxs-lookup"><span data-stu-id="04570-115">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="04570-116">請注意， <xref:System.Web.UI.WebControls.Button.Click> 控制項的 <xref:System.Windows.Controls.Button> 事件處理常式由於會呼叫非同步方法，因此會以 `async` 修飾詞標記。</span><span class="sxs-lookup"><span data-stu-id="04570-116">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="04570-117">下一個範例與前一個範例類似，但使用 <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter> 物件以非同步方式讀取及寫入文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="04570-117">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="04570-118">下一個範例顯示程式碼後置檔案和 XAML 檔案，這些檔案是用來開啟檔案做為 Windows 8.x 存放區應用程式中的 <xref:System.IO.Stream>，並使用 <xref:System.IO.StreamReader> 類別的實例來讀取其內容。</span><span class="sxs-lookup"><span data-stu-id="04570-118">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a Windows 8.x Store app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="04570-119">它會使用非同步方法開啟檔案作為資料流並讀取其內容。</span><span class="sxs-lookup"><span data-stu-id="04570-119">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="04570-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="04570-120">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="04570-121">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="04570-121">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="04570-122">使用 async 和 await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="04570-122">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="04570-123">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04570-123">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
