---
title: 使用 NumericUpDown 控制項設定和傳回數值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: a0b264fec9619b467c293bcb96278c4517775ac3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743030"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a><span data-ttu-id="b0b80-102">如何：使用 Windows Form NumericUpDown 控制項設定和傳回數值</span><span class="sxs-lookup"><span data-stu-id="b0b80-102">How to: Set and Return Numeric Values with the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="b0b80-103">Windows Forms <xref:System.Windows.Forms.NumericUpDown> 控制項的數值是由其 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性所決定。</span><span class="sxs-lookup"><span data-stu-id="b0b80-103">The numeric value of the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control is determined by its <xref:System.Windows.Forms.NumericUpDown.Value%2A> property.</span></span> <span data-ttu-id="b0b80-104">您可以撰寫控制項值的條件式測試，就像使用任何其他屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="b0b80-104">You can write conditional tests for the control's value just as with any other property.</span></span> <span data-ttu-id="b0b80-105">設定 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性之後，您可以撰寫程式碼來直接調整它，以在其上執行作業，或者您可以呼叫 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b0b80-105">Once the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property is set, you can adjust it directly by writing code to perform operations on it, or you can call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> methods.</span></span>  
  
### <a name="to-set-the-numeric-value"></a><span data-ttu-id="b0b80-106">若要設定數值</span><span class="sxs-lookup"><span data-stu-id="b0b80-106">To set the numeric value</span></span>  
  
1. <span data-ttu-id="b0b80-107">在程式碼或屬性視窗中，將值指派給 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b0b80-107">Assign a value to the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code or in the Properties window.</span></span>  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     <span data-ttu-id="b0b80-108">-或-</span><span class="sxs-lookup"><span data-stu-id="b0b80-108">-or-</span></span>  
  
2. <span data-ttu-id="b0b80-109">呼叫 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> 或 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> 方法，以 <xref:System.Windows.Forms.NumericUpDown.Increment%2A> 屬性中指定的數量來增加或減少值。</span><span class="sxs-lookup"><span data-stu-id="b0b80-109">Call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> or <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> method to increase or decrease the value by the amount specified in the <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property.</span></span>  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a><span data-ttu-id="b0b80-110">傳回數值</span><span class="sxs-lookup"><span data-stu-id="b0b80-110">To return the numeric value</span></span>  
  
- <span data-ttu-id="b0b80-111">存取程式碼中的 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b0b80-111">Access the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code.</span></span>  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b0b80-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0b80-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b0b80-113">NumericUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="b0b80-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="b0b80-114">NumericUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b0b80-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
