---
title: 使用 BindingSource 元件自訂加入專案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738324"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="d89b7-102">如何：使用 Windows Form BindingSource 自訂加入項目</span><span class="sxs-lookup"><span data-stu-id="d89b7-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="d89b7-103">當您使用 <xref:System.Windows.Forms.BindingSource> 元件將 Windows Form 控制項繫結至資料來源時，您可能會發現有必要自訂新項目的建立。</span><span class="sxs-lookup"><span data-stu-id="d89b7-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="d89b7-104"><xref:System.Windows.Forms.BindingSource> 元件提供了通常會在繫結控制項需要建立新項目時引發的 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件，使這項作業毫不費力。</span><span class="sxs-lookup"><span data-stu-id="d89b7-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="d89b7-105">您的事件處理常式能夠提供任何要求的自訂行為，例如在 Web 服務上呼叫方法或者從 Class Factory 取得新物件。</span><span class="sxs-lookup"><span data-stu-id="d89b7-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d89b7-106">當您利用處理 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件來加入項目時，這項加入作業將無法取消。</span><span class="sxs-lookup"><span data-stu-id="d89b7-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d89b7-107">範例</span><span class="sxs-lookup"><span data-stu-id="d89b7-107">Example</span></span>  
 <span data-ttu-id="d89b7-108">下列範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 元件將 <xref:System.Windows.Forms.BindingSource> 控制項繫結至 Class Factory。</span><span class="sxs-lookup"><span data-stu-id="d89b7-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="d89b7-109">當使用者按一下 <xref:System.Windows.Forms.DataGridView> 控制項的新資料列時，就會引發 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件。</span><span class="sxs-lookup"><span data-stu-id="d89b7-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="d89b7-110">事件處理常式將會建立新的 `DemoCustomer` 物件，以指派給 <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d89b7-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d89b7-111">這將使得新的 `DemoCustomer` 物件加入 <xref:System.Windows.Forms.BindingSource> 元件的清單，並於 <xref:System.Windows.Forms.DataGridView> 控制項的新資料列中顯示。</span><span class="sxs-lookup"><span data-stu-id="d89b7-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d89b7-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d89b7-112">Compiling the Code</span></span>  
 <span data-ttu-id="d89b7-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d89b7-113">This example requires:</span></span>  
  
- <span data-ttu-id="d89b7-114">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d89b7-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89b7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d89b7-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="d89b7-116">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="d89b7-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="d89b7-117">如何：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="d89b7-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
