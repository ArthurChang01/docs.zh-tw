---
title: 如何：重新調整 Windows Form 上控制項的大小
ms.date: 03/30/2017
f1_keywords:
- Size.Height
- Size.Width
helpviewer_keywords:
- controls [Windows Forms], resizing
- size [Windows Forms], controls
- Windows Forms controls, size
ms.assetid: d2dba441-a8c0-4705-b8e8-2e5d86d6e7ec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3aacc9434199eb7881e362a67e1fe0c08784c4a7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459549"
---
# <a name="how-to-resize-controls-on-windows-forms"></a><span data-ttu-id="2a42b-102">如何：在 Windows Forms 上調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="2a42b-102">How to: Resize controls on Windows Forms</span></span>

<span data-ttu-id="2a42b-103">您可以調整個別控制項的大小，也可以調整相同或不同類型的多個控制項大小，例如 <xref:System.Windows.Forms.Button> 和 <xref:System.Windows.Forms.GroupBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="2a42b-103">You can resize individual controls, and you can resize multiple controls of the same or different kind, such as <xref:System.Windows.Forms.Button> and <xref:System.Windows.Forms.GroupBox> controls.</span></span>

## <a name="to-resize-a-control"></a><span data-ttu-id="2a42b-104">調整控制項的大小</span><span class="sxs-lookup"><span data-stu-id="2a42b-104">To resize a control</span></span>

<span data-ttu-id="2a42b-105">在 Visual Studio 中，選取要調整大小的控制項，然後拖曳其中一個八個大小控點。</span><span class="sxs-lookup"><span data-stu-id="2a42b-105">In Visual Studio, select the control to be resized and drag one of the eight sizing handles.</span></span>

> [!NOTE]
> <span data-ttu-id="2a42b-106">選取控制項，然後在按住**Shift**鍵時按**箭頭**鍵，一次調整控制項的一個圖元。</span><span class="sxs-lookup"><span data-stu-id="2a42b-106">Select the control and press the **arrow** keys while holding down the **Shift** key to resize the control one pixel at a time.</span></span> <span data-ttu-id="2a42b-107">按**向下**鍵或**向右鍵**，同時按住**Shift**和**Ctrl**鍵，以大幅增加控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="2a42b-107">Press the **down arrow** or **right arrow** keys while holding down the **Shift** and **Ctrl** keys to resize the control in large increments.</span></span>

## <a name="to-resize-multiple-controls-on-a-form"></a><span data-ttu-id="2a42b-108">調整表單上的多個控制項大小</span><span class="sxs-lookup"><span data-stu-id="2a42b-108">To resize multiple controls on a form</span></span>

1. <span data-ttu-id="2a42b-109">在 Visual Studio 中，按住**Ctrl**或**Shift**鍵，然後選取您想要調整大小的控制項。</span><span class="sxs-lookup"><span data-stu-id="2a42b-109">In Visual Studio, hold down the **Ctrl** or **Shift** key and select the controls you want to resize.</span></span> <span data-ttu-id="2a42b-110">您選取的第一個控制項的大小會用於其他控制項。</span><span class="sxs-lookup"><span data-stu-id="2a42b-110">The size of the first control you select is used for the other controls.</span></span>

2. <span data-ttu-id="2a42b-111">在 [**格式**] 功能表上，選擇 [**設成相同大小**]，然後選取四個選項的其中一個。</span><span class="sxs-lookup"><span data-stu-id="2a42b-111">On the **Format** menu, choose **Make Same Size**, and select one of the four options.</span></span> <span data-ttu-id="2a42b-112">前三個命令會變更控制項的維度，以符合第一個選取的控制項。</span><span class="sxs-lookup"><span data-stu-id="2a42b-112">The first three commands change the dimensions of the controls to match the first-selected control.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a42b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a42b-113">See also</span></span>

- [<span data-ttu-id="2a42b-114">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="2a42b-114">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="2a42b-115">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="2a42b-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="2a42b-116">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="2a42b-116">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="2a42b-117">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="2a42b-117">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="2a42b-118">[如何：使用設計工具調整 Windows Forms 大小](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a42b-118">[How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))</span></span>
