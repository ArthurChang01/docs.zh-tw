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
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>如何：將 Windows Form 控制項繫結至 DBNull 資料庫值
當您將 Windows Form 控制項繫結至資料來源，且資料來源傳回 <xref:System.DBNull> 值時，您可以替代為適當值，而不需處理、格式化或剖析事件。 在格式化或剖析資料來源值的時候，<xref:System.Windows.Forms.Binding.NullValue%2A> 屬性會轉換 <xref:System.DBNull> 為指定的物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何在兩個不同的情況下繫結 <xref:System.DBNull> 的值。 第一個範例示範如何為字串屬性設定 <xref:System.Windows.Forms.Binding.NullValue%2A>；第二個示範如何為影像屬性設定 <xref:System.Windows.Forms.Binding.NullValue%2A>。  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 繫結屬性和 <xref:System.Windows.Forms.Binding.NullValue%2A> 屬性的類型都必須相同，否則會產生錯誤，將不會再進一步處理 <xref:System.Windows.Forms.Binding.NullValue%2A> 的值。 在此情況下，將不會擲回例外狀況。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>請參閱

- [BindingSource 元件](bindingsource-component.md)
- [操作說明：處理資料繫結時所發生的錯誤和例外狀況](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [如何：將 Windows Forms 控制項繫結至型別](how-to-bind-a-windows-forms-control-to-a-type.md)
