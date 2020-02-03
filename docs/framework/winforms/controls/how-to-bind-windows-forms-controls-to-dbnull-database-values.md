---
title: 將控制項系結至 DBNull 資料庫值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746659"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="2d1ef-102">如何：將 Windows Forms 控制項繫結至 DBNull 資料庫數值</span><span class="sxs-lookup"><span data-stu-id="2d1ef-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="2d1ef-103">當您將 Windows Form 控制項繫結至資料來源，且資料來源傳回 <xref:System.DBNull> 值時，您可以替代為適當值，而不需處理、格式化或剖析事件。</span><span class="sxs-lookup"><span data-stu-id="2d1ef-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="2d1ef-104">在格式化或剖析資料來源值的時候，<xref:System.Windows.Forms.Binding.NullValue%2A> 屬性會轉換 <xref:System.DBNull> 為指定的物件。</span><span class="sxs-lookup"><span data-stu-id="2d1ef-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d1ef-105">範例</span><span class="sxs-lookup"><span data-stu-id="2d1ef-105">Example</span></span>  
 <span data-ttu-id="2d1ef-106">下列範例示範如何在兩個不同的情況下繫結 <xref:System.DBNull> 的值。</span><span class="sxs-lookup"><span data-stu-id="2d1ef-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="2d1ef-107">第一個範例示範如何為字串屬性設定 <xref:System.Windows.Forms.Binding.NullValue%2A>；第二個示範如何為影像屬性設定 <xref:System.Windows.Forms.Binding.NullValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="2d1ef-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="2d1ef-108">繫結屬性和 <xref:System.Windows.Forms.Binding.NullValue%2A> 屬性的類型都必須相同，否則會產生錯誤，將不會再進一步處理 <xref:System.Windows.Forms.Binding.NullValue%2A> 的值。</span><span class="sxs-lookup"><span data-stu-id="2d1ef-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="2d1ef-109">在此情況下，將不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2d1ef-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d1ef-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2d1ef-110">Compiling the Code</span></span>  
 <span data-ttu-id="2d1ef-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="2d1ef-111">This example requires:</span></span>  
  
- <span data-ttu-id="2d1ef-112">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="2d1ef-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1ef-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d1ef-113">See also</span></span>

- [<span data-ttu-id="2d1ef-114">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="2d1ef-114">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="2d1ef-115">操作說明：處理資料繫結時所發生的錯誤和例外狀況</span><span class="sxs-lookup"><span data-stu-id="2d1ef-115">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="2d1ef-116">如何：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="2d1ef-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
