---
title: 將按鈕指定為 [取消] 按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743255"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="5602d-102">如何：將 Windows Form 中的 Button 指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="5602d-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="5602d-103">在任何 Windows Form 上，您都可以將 <xref:System.Windows.Forms.Button> 控制項指定為 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5602d-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="5602d-104">每當使用者按下 ESC 鍵時，就會按一下 [取消] 按鈕，而不論表單上的其他控制項有哪些焦點。</span><span class="sxs-lookup"><span data-stu-id="5602d-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="5602d-105">這類按鈕通常是程式設計的，可讓使用者快速結束作業，而不需要認可任何動作。</span><span class="sxs-lookup"><span data-stu-id="5602d-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="5602d-106">若要指定取消按鈕</span><span class="sxs-lookup"><span data-stu-id="5602d-106">To designate the cancel button</span></span>  
  
1. <span data-ttu-id="5602d-107">將表單的 <xref:System.Windows.Forms.Form.CancelButton%2A> 屬性設定為適當的 <xref:System.Windows.Forms.Button> 控制項。</span><span class="sxs-lookup"><span data-stu-id="5602d-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5602d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5602d-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="5602d-109">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="5602d-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="5602d-110">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="5602d-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="5602d-111">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="5602d-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="5602d-112">操作說明：將 Windows Forms 中的 Button 指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="5602d-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="5602d-113">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="5602d-113">Button Control</span></span>](button-control-windows-forms.md)
