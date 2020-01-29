---
title: 事件的順序
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 618ac5a6a6a32ae1a53fc60ac80700d7648c81a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734855"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="6a62a-102">Windows Form 中的事件順序</span><span class="sxs-lookup"><span data-stu-id="6a62a-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="6a62a-103">關於 Windows Form 應用程式中被引發的事件，程式開發人員會特別關注他們的順序，並且盡力依次處理每個事件。</span><span class="sxs-lookup"><span data-stu-id="6a62a-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="6a62a-104">當遇到需要謹慎處理事件的狀況，例如當您重新繪製部分表單時，對於在執行階段時被引發的事件，感知其精確的順序是必需的。</span><span class="sxs-lookup"><span data-stu-id="6a62a-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="6a62a-105">本主題提供一些有關在應用程式以及控制項存留期中，幾個重要階段裡事件順序的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6a62a-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="6a62a-106">如需滑鼠輸入事件順序的特定詳細資料，請參閱[Windows Forms 中的滑鼠事件](mouse-events-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="6a62a-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="6a62a-107">如需 Windows Forms 中事件的總覽，請參閱[事件總覽](events-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="6a62a-107">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="6a62a-108">如需事件處理常式的相關詳細資訊，請參閱[事件處理常式總覽](event-handlers-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="6a62a-108">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="6a62a-109">應用程式啟動和關閉事件</span><span class="sxs-lookup"><span data-stu-id="6a62a-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="6a62a-110"><xref:System.Windows.Forms.Form> 和 <xref:System.Windows.Forms.Control> 類別會公開一組關於應用程式啟動和關閉的事件。</span><span class="sxs-lookup"><span data-stu-id="6a62a-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="6a62a-111">當 Windows Form 應用程式啟動時，主要表單的啟動事件會依照下列順序引發：</span><span class="sxs-lookup"><span data-stu-id="6a62a-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="6a62a-112">當 Windows Form 應用程式關閉時，主要表單的關閉事件會依照下列順序引發：</span><span class="sxs-lookup"><span data-stu-id="6a62a-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="6a62a-113"><xref:System.Windows.Forms.Application> 類別的 <xref:System.Windows.Forms.Application.ApplicationExit> 事件會在主要表單的關閉事件之後引發。</span><span class="sxs-lookup"><span data-stu-id="6a62a-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a62a-114">Visual Basic 2005 包含其他應用程式事件，例如 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> 和 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6a62a-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="6a62a-115">焦點和驗證事件。</span><span class="sxs-lookup"><span data-stu-id="6a62a-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="6a62a-116">當您使用鍵盤 (TAB、SHIFT + TAB 等等) 變更焦點時，藉由呼叫 <xref:System.Windows.Forms.Control.Select%2A> 或 <xref:System.Windows.Forms.Control.SelectNextControl%2A> 方法，或藉由設定 <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> 屬性到目前表單， <xref:System.Windows.Forms.Control> 類別的焦點事件會以下列順序發生：</span><span class="sxs-lookup"><span data-stu-id="6a62a-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="6a62a-117">當您使用滑鼠或藉由呼叫 <xref:System.Windows.Forms.Control.Focus%2A> 方法來變更焦點， <xref:System.Windows.Forms.Control> 類別的焦點事件會以下列順序發生：</span><span class="sxs-lookup"><span data-stu-id="6a62a-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="6a62a-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="6a62a-118">See also</span></span>

- [<span data-ttu-id="6a62a-119">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="6a62a-119">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
