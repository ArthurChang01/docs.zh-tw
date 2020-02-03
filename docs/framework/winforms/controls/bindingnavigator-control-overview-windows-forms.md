---
title: BindingNavigator 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: c2747a6801d4aa9cfde4227ffd5c29ca1de78d48
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744109"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator 控制項概觀 (Windows Form)
您可以使用 <xref:System.Windows.Forms.BindingNavigator> 控制項來建立標準化的方法，讓使用者用來搜尋和變更 Windows Form 上的資料。 您經常使用 <xref:System.Windows.Forms.BindingNavigator> 搭配 <xref:System.Windows.Forms.BindingSource> 元件，讓使用者能夠瀏覽表單上的資料記錄，以及與記錄互動。  
  
## <a name="how-the-bindingnavigator-works"></a>BindingNavigator 的運作方式  

 <xref:System.Windows.Forms.BindingNavigator> 控制項是由 <xref:System.Windows.Forms.ToolStrip> 與一系列 <xref:System.Windows.Forms.ToolStripItem> 物件所組成，可用來進行大多數常見的資料相關動作：加入資料、刪除資料，以及巡覽資料。 根據預設，<xref:System.Windows.Forms.BindingNavigator> 控制項會包含這些標準按鈕。 下列螢幕擷取畫面顯示表單上的 <xref:System.Windows.Forms.BindingNavigator> 控制項：
  
 ![顯示 BindingNavigator 控制項的螢幕擷取畫面。](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 下表列出控制項，並描述其功能。  
  
|控制項|函數|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> 按鈕|將新資料列插入基礎資料來源中。|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕|從基礎資料來源中刪除目前的資料列。|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕|移至基礎資料來源中的第一個項目。|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> 按鈕|移至基礎資料來源中的最後一個項目。|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> 按鈕|移至基礎資料來源中的下一個項目。|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> 按鈕|移至基礎資料來源中的上一個項目。|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> 文字方塊|傳回在基礎資料來源內的目前位置。|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> 文字方塊|傳回基礎資料來源中的項目總數。|  
  
 針對此集合中的每個控制項，各有一個 <xref:System.Windows.Forms.BindingSource> 元件的對應成員，它會以程式設計的方式提供相同的功能。 例如，<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> 元件的 <xref:System.Windows.Forms.BindingSource> 方法，<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> 方法等。  
  
 如果預設按鈕不適合您的應用程式，或者如果您需要其他按鈕來支援其他類型的功能，您可以提供自己的 <xref:System.Windows.Forms.ToolStrip> 按鈕。 另請參閱[如何：將載入、儲存和取消按鈕新增至 Windows Forms BindingNavigator 控制項](load-save-and-cancel-bindingnavigator.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator 控制項](bindingnavigator-control-windows-forms.md)
