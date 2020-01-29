---
title: 如何：建立唯讀文字方塊
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 17ae9524009c687cd62fb315f842e188e120ac68
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731266"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="55f6c-102">如何：建立唯讀文字方塊 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="55f6c-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="55f6c-103">您可以將可編輯的 Windows Forms 文字方塊轉換成隻讀控制項。</span><span class="sxs-lookup"><span data-stu-id="55f6c-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="55f6c-104">例如，因為應用程式的狀態，文字方塊可能會顯示通常已編輯但目前可能不是的值。</span><span class="sxs-lookup"><span data-stu-id="55f6c-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="55f6c-105">若要建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="55f6c-105">To create a read-only text box</span></span>

1. <span data-ttu-id="55f6c-106">將 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> 屬性設定為 [`true`]。</span><span class="sxs-lookup"><span data-stu-id="55f6c-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="55f6c-107">當屬性設定為 [`true`] 時，使用者仍然可以在文字方塊中滾動並反白顯示文字，而不允許變更。</span><span class="sxs-lookup"><span data-stu-id="55f6c-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="55f6c-108">**複製**命令在文字方塊中可正常運作，但**剪**下和**貼**上命令則不會。</span><span class="sxs-lookup"><span data-stu-id="55f6c-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="55f6c-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> 屬性只會影響執行時間的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="55f6c-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="55f6c-110">您仍然可以藉由變更文字方塊的 [<xref:System.Windows.Forms.TextBox.Text%2A>] 屬性，在執行時間以程式設計方式變更文字方塊內容。</span><span class="sxs-lookup"><span data-stu-id="55f6c-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="55f6c-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="55f6c-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="55f6c-112">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="55f6c-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="55f6c-113">操作說明：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="55f6c-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="55f6c-114">操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="55f6c-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="55f6c-115">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="55f6c-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="55f6c-116">操作說明：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="55f6c-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="55f6c-117">操作說明：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="55f6c-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="55f6c-118">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="55f6c-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
