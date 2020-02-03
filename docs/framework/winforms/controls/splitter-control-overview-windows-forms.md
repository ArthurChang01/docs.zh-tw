---
title: Splitter 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 3d6da8daf9bb0e8df4f69554a87725a7ddb65acb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742895"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="b4935-102">Splitter 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="b4935-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="b4935-103">雖然 <xref:System.Windows.Forms.SplitContainer> 會取代並且將功能加入至之前版本的 <xref:System.Windows.Forms.Splitter> 控制項；不過，也可以選擇保留 <xref:System.Windows.Forms.Splitter>，以提供回溯相容性 (Backward Compatibility) 以及供未來使用。</span><span class="sxs-lookup"><span data-stu-id="b4935-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="b4935-104">Windows Forms <xref:System.Windows.Forms.Splitter> 控制項用來在執行時間調整停駐的控制項大小。</span><span class="sxs-lookup"><span data-stu-id="b4935-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="b4935-105"><xref:System.Windows.Forms.Splitter> 控制項通常用於具有不同資料長度之控制項的表單，例如 Windows Explorer，其資料窗格包含不同時間的差異寬度資訊。</span><span class="sxs-lookup"><span data-stu-id="b4935-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="b4935-106">使用分隔器控制項</span><span class="sxs-lookup"><span data-stu-id="b4935-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="b4935-107">當使用者將滑鼠指標指向控制項的停駐邊緣，可由分隔器控制項調整大小時，指標會變更其外觀，以指出控制項可以調整大小。</span><span class="sxs-lookup"><span data-stu-id="b4935-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="b4935-108">使用分隔器控制項，使用者可以調整緊接在其前面的停駐控制項大小。</span><span class="sxs-lookup"><span data-stu-id="b4935-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="b4935-109">因此，若要讓使用者在執行時間調整停駐控制項的大小，請將控制項的大小設為容器的邊緣，然後將分隔器控制項停駐在該容器的同一側邊。</span><span class="sxs-lookup"><span data-stu-id="b4935-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4935-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4935-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="b4935-111">操作說明：將控制項停駐在 Windows Forms 上</span><span class="sxs-lookup"><span data-stu-id="b4935-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="b4935-112">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="b4935-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
