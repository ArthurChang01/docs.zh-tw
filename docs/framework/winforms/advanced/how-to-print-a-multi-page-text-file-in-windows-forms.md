---
title: 如何：列印多頁文字檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740656"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="5527c-102">如何：在 Windows Forms 中列印多頁文字檔</span><span class="sxs-lookup"><span data-stu-id="5527c-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="5527c-103">Windows 應用程式列印文字的情況極為常見。</span><span class="sxs-lookup"><span data-stu-id="5527c-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="5527c-104"><xref:System.Drawing.Graphics> 類別提供將物件 (圖形或文字) 繪製到螢幕或印表機等裝置的方法。</span><span class="sxs-lookup"><span data-stu-id="5527c-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5527c-105"><xref:System.Windows.Forms.TextRenderer> 的 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法不支援列印。</span><span class="sxs-lookup"><span data-stu-id="5527c-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="5527c-106">您應該一律使用 <xref:System.Drawing.Graphics> 的 <xref:System.Drawing.Graphics.DrawString%2A> 方法，來繪製要用於列印的文字，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="5527c-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="5527c-107">列印文字</span><span class="sxs-lookup"><span data-stu-id="5527c-107">To print text</span></span>  
  
1. <span data-ttu-id="5527c-108">將一個 <xref:System.Drawing.Printing.PrintDocument> 元件和一個字串加入您的表單。</span><span class="sxs-lookup"><span data-stu-id="5527c-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="5527c-109">如果是在列印文件，請將 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 屬性設定為您想要列印的文件，並且開啟文件內容，讀取到您在之前所加入的字串。</span><span class="sxs-lookup"><span data-stu-id="5527c-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="5527c-110">在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中，使用 <xref:System.Drawing.Printing.PrintPageEventArgs> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 屬性和文件內容來計算行的長度和每頁的行數。</span><span class="sxs-lookup"><span data-stu-id="5527c-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="5527c-111">在繪製每一頁之後，請檢查該頁面是否為最後一頁，並且據此設定 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 的 <xref:System.Drawing.Printing.PrintPageEventArgs> 屬性。</span><span class="sxs-lookup"><span data-stu-id="5527c-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="5527c-112">在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 成為 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 之前，會持續引發 `false`事件。</span><span class="sxs-lookup"><span data-stu-id="5527c-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="5527c-113">此外，也請確定 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件與其事件處理方法相關聯。</span><span class="sxs-lookup"><span data-stu-id="5527c-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="5527c-114">在下列程式碼範例中，會使用事件處理常式以表單上所使用的相同字型來列印 "testPage.txt" 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="5527c-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="5527c-115">呼叫 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法以引發 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。</span><span class="sxs-lookup"><span data-stu-id="5527c-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="5527c-116">範例</span><span class="sxs-lookup"><span data-stu-id="5527c-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5527c-117">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5527c-117">Compiling the Code</span></span>  
 <span data-ttu-id="5527c-118">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="5527c-118">This example requires:</span></span>  
  
- <span data-ttu-id="5527c-119">位於磁碟機 C:\\ 根目錄之名為 testPage.txt 的文字檔，其中包含要列印的文字。</span><span class="sxs-lookup"><span data-stu-id="5527c-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="5527c-120">編輯這個程式碼可列印不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="5527c-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="5527c-121">System、System.Windows.Forms、System.Drawing 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="5527c-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="5527c-122">如需從 Visual Basic 或視覺效果C#的命令列建立此範例的詳細資訊，請參閱[從命令列建立](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc 建立命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="5527c-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5527c-123">您也可以藉由將程式碼貼入新的專案中，在 Visual Studio 中建立此範例。</span><span class="sxs-lookup"><span data-stu-id="5527c-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5527c-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="5527c-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="5527c-125">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="5527c-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
