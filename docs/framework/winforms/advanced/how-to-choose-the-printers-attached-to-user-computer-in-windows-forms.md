---
title: 如何：選擇附加至使用者電腦的印表機
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 7fc2427468540ac0a1480f6140cbb34c3a0f1ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746505"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="6d03b-102">如何：在 Windows Form 中選擇附加至使用者電腦的印表機</span><span class="sxs-lookup"><span data-stu-id="6d03b-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="6d03b-103">通常，使用者會想要選擇列印到非預設的印表機。</span><span class="sxs-lookup"><span data-stu-id="6d03b-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="6d03b-104">使用 <xref:System.Windows.Forms.PrintDialog> 元件，即可讓使用者從目前安裝的印表機中選擇印表機。</span><span class="sxs-lookup"><span data-stu-id="6d03b-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="6d03b-105">透過 <xref:System.Windows.Forms.PrintDialog> 元件，擷取 <xref:System.Windows.Forms.DialogResult> 元件的 <xref:System.Windows.Forms.PrintDialog> 並將其用來選取印表機。</span><span class="sxs-lookup"><span data-stu-id="6d03b-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="6d03b-106">在下列程序中，選取要列印至預設印表機的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="6d03b-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="6d03b-107">然後具現化 <xref:System.Windows.Forms.PrintDialog> 類別。</span><span class="sxs-lookup"><span data-stu-id="6d03b-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="6d03b-108">選擇印表機，然後列印檔案</span><span class="sxs-lookup"><span data-stu-id="6d03b-108">To choose a printer and then print a file</span></span>  
  
1. <span data-ttu-id="6d03b-109">選取要使用 <xref:System.Windows.Forms.PrintDialog> 元件的印表機。</span><span class="sxs-lookup"><span data-stu-id="6d03b-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="6d03b-110">在下列程式碼範例中，有兩個要處理的事件。</span><span class="sxs-lookup"><span data-stu-id="6d03b-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="6d03b-111">在第一個 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件中，會具現化 <xref:System.Windows.Forms.PrintDialog> 類別，並在 <xref:System.Windows.Forms.DialogResult> 屬性中捕捉使用者所選取的印表機。</span><span class="sxs-lookup"><span data-stu-id="6d03b-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="6d03b-112">在第二個事件中，<xref:System.Drawing.Printing.PrintDocument> 元件的 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，會將範例檔列印到指定的印表機。</span><span class="sxs-lookup"><span data-stu-id="6d03b-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="6d03b-113">（視覺C#效果和C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6d03b-113">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6d03b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d03b-114">See also</span></span>

- [<span data-ttu-id="6d03b-115">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="6d03b-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
