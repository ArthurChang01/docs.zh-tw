---
title: 在剪貼簿儲存和讀取資料
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 243fb237f3f9ba53f8b29079df08531c102c78dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349738"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="dc761-102">在剪貼簿儲存和讀取資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc761-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>

<span data-ttu-id="dc761-103">剪貼簿可以用來儲存資料，例如文字和影像。</span><span class="sxs-lookup"><span data-stu-id="dc761-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="dc761-104">因為所有使用中處理序都共用剪貼簿，所以可以使用它在這兩者之間傳輸資料。</span><span class="sxs-lookup"><span data-stu-id="dc761-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="dc761-105">`My.Computer.Clipboard` 物件可讓您輕鬆地存取剪貼簿，以及讀取和寫入它。</span><span class="sxs-lookup"><span data-stu-id="dc761-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="dc761-106">從剪貼簿讀取</span><span class="sxs-lookup"><span data-stu-id="dc761-106">Reading from the Clipboard</span></span>  

 <span data-ttu-id="dc761-107">使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> 方法來讀取剪貼簿中的文字。</span><span class="sxs-lookup"><span data-stu-id="dc761-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="dc761-108">下列程式碼會讀取文字，並將它顯示在訊息方塊中。</span><span class="sxs-lookup"><span data-stu-id="dc761-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="dc761-109">必須要有文字儲存在剪貼簿上，範例才能正確執行。</span><span class="sxs-lookup"><span data-stu-id="dc761-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="dc761-110">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="dc761-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="dc761-111">在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [剪貼簿] 中。</span><span class="sxs-lookup"><span data-stu-id="dc761-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="dc761-112">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="dc761-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="dc761-113">使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> 方法來擷取剪貼簿中的影像。</span><span class="sxs-lookup"><span data-stu-id="dc761-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="dc761-114">這個範例會先確認剪貼簿上是否有影像，再擷取它，並將它指派給 `PictureBox1`。</span><span class="sxs-lookup"><span data-stu-id="dc761-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="dc761-115">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="dc761-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="dc761-116">在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [剪貼簿] 中。如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="dc761-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="dc761-117">即使在關閉應用程式之後，還是會保留放在剪貼簿上的項目。</span><span class="sxs-lookup"><span data-stu-id="dc761-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="dc761-118">判斷儲存在剪貼簿中的檔案類型</span><span class="sxs-lookup"><span data-stu-id="dc761-118">Determining the type of file stored in the Clipboard</span></span>  

 <span data-ttu-id="dc761-119">剪貼簿上的資料可能會有數種不同的格式，例如文字、音訊檔或影像。</span><span class="sxs-lookup"><span data-stu-id="dc761-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="dc761-120">若要判斷哪一種檔案是在剪貼簿上，您可以使用例如 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> 以及 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A> 的方法。</span><span class="sxs-lookup"><span data-stu-id="dc761-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="dc761-121">如果您有想要檢查的自訂格式，可以使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="dc761-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="dc761-122">使用 `ContainsImage` 函式來判斷剪貼簿上所包含的資料是否為影像。</span><span class="sxs-lookup"><span data-stu-id="dc761-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="dc761-123">下列程式碼會確認資料是否為影像，並據此進行報告。</span><span class="sxs-lookup"><span data-stu-id="dc761-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="dc761-124">清除剪貼簿</span><span class="sxs-lookup"><span data-stu-id="dc761-124">Clearing the Clipboard</span></span>  

 <span data-ttu-id="dc761-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> 方法會清除剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc761-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="dc761-126">因為其他處理序會共用剪貼簿，所以清除它可能會影響這些處理序。</span><span class="sxs-lookup"><span data-stu-id="dc761-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="dc761-127">下列程式碼將示範如何使用 `Clear` 方法。</span><span class="sxs-lookup"><span data-stu-id="dc761-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="dc761-128">寫入至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="dc761-128">Writing to the Clipboard</span></span>  

 <span data-ttu-id="dc761-129">使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> 方法，將文字寫入剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc761-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="dc761-130">下列程式碼會將 "This is a test string" 字串寫入至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc761-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="dc761-131">`SetText` 方法可以接受包含 <xref:System.Windows.Forms.TextDataFormat> 類型的格式參數。</span><span class="sxs-lookup"><span data-stu-id="dc761-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="dc761-132">下列程式碼會以 RTF 文字將 "This is a test string" 字串寫入至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc761-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="dc761-133">使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> 方法，將資料寫入剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc761-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="dc761-134">這個範例會以自訂格式 `specialFormat`，將 `DataObject` `dataChunk` 寫入至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc761-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="dc761-135">使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> 方法，將音訊資料寫入剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc761-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="dc761-136">這個範例會建立位元組陣列 `musicReader`，並在其中讀入檔案 `cool.wav`，然後將其寫入至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dc761-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> <span data-ttu-id="dc761-137">因為其他使用者可以存取剪貼簿，所以請不要使用它來儲存機密資訊，例如密碼或機密資料。</span><span class="sxs-lookup"><span data-stu-id="dc761-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc761-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc761-138">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="dc761-139">如何：從 XML 檔案讀取物件資料</span><span class="sxs-lookup"><span data-stu-id="dc761-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="dc761-140">如何：將物件資料寫入 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="dc761-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
