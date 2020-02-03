---
title: DataGridView 儲存格中的主控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a64521a15a272ca8140302f39d15e7f17e0c423b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736535"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>如何：Windows Forms DataGridView 儲存格中的主控制項
<xref:System.Windows.Forms.DataGridView> 控制項提供許多資料行類型，讓使用者以各種不同的方式輸入和編輯值。 如果這些資料行類型不符合您輸入資料的需求，則您仍可用裝載您所選擇的控制項之儲存格來建立自己的資料行類型。 若要這樣做，您必須定義衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.DataGridViewCell> 的類別。 您也必須定義衍生自 <xref:System.Windows.Forms.Control> 的類別，並實作 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面。  
  
 下列程式碼範例示範如何建立行事曆資料行。 這個資料行的儲存格會在一般文字方塊中的儲存格顯示日期，但是當使用者編輯儲存格時，<xref:System.Windows.Forms.DateTimePicker> 控制項就會出現。 若要避免再次實作文字方塊顯示功能，則 `CalendarCell` 類別要衍生自 <xref:System.Windows.Forms.DataGridViewTextBoxCell> 類別，而不是直接繼承 <xref:System.Windows.Forms.DataGridViewCell> 類別。  
  
> [!NOTE]
> 當您自 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 中衍生時，以及在衍生類別中加入新的屬性時，請務必覆寫 `Clone` 方法，在複製作業期間複製新的屬性。 您也應該呼叫基底類別的 `Clone` 方法，以便將基底類別的屬性複製到新的儲存格或資料行。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 下列範例需要：  
  
- System 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView 控制項架構](datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
