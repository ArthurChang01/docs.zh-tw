---
title: ToolBar 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 027c96bb49e9446244e4b08ba93c551ef043b3c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735462"
---
# <a name="toolbar-control-windows-forms"></a>ToolBar 控制項 (Windows Form)
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> 控制項會取代 `ToolBar` 控制項並加入其他功能，不過您也可以選擇保留 `ToolBar` 控制項，以提供回溯相容性及未來使用。  
  
 Windows Form `ToolBar` 控制項在表單中，是當做顯示下拉式功能表其中一列的控制列和啟動命令的點陣圖按鈕使用。 因此，按一下工具列按鈕相當於選擇功能表命令。 您可將這些按鈕設定成和按鈕、下拉式功能表或分隔符號一樣顯示和運作。 一般而言，工具列包含對應至應用程式功能表結構中項目的按鈕和功能表，可以快速存取應用程式中最常使用的功能和命令。  
  
> [!NOTE]
> `ToolBar` 控制項的 <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> 屬性會將 <xref:System.Windows.Forms.ContextMenu> 類別的執行個體當做參考。 請仔細考慮在應用程式中實作工具列上這類按鈕時所傳遞的參考，因為這個屬性會接受任何繼承自 <xref:System.Windows.Forms.Menu> 類別的物件。  
  
## <a name="in-this-section"></a>本節內容  
 [工具列控制項概觀](toolbar-control-overview-windows-forms.md)  
 介紹 `ToolBar` 控制項的一般概念，讓您能夠設計自訂工具列以供使用者利用。  
  
 [操作說明：將按鈕新增至工具列控制項](how-to-add-buttons-to-a-toolbar-control.md)  
 描述如何將按鈕加入 `ToolBar` 控制項。  
  
 [操作說明：定義工具列按鈕的圖示](how-to-define-an-icon-for-a-toolbar-button.md)  
 描述如何在 `ToolBar` 控制項的按鈕內顯示圖示。  
  
 [如何：觸發工具列按鈕的功能表事件](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 指示如何撰寫程式碼，來解譯使用者在 `ToolBar` 控制項中按的是哪一個按鈕。  
  
 另請參閱[如何：使用設計工具定義工具列按鈕的圖示](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md)，[如何：使用設計工具將按鈕加入工具列控制項](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md)。  
  
## <a name="reference"></a>參考  
 <xref:System.Windows.Forms.ToolBar> 類別  
 提供這個類別及其成員的相關參考資訊。  
  
## <a name="related-sections"></a>相關章節  
 [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)  
 提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。  
  
 [ToolStrip 控制項](toolstrip-control-windows-forms.md)  
 描述可以在 Windows Forms 應用程式中裝載功能表、控制項和使用者控制項的工具列。
