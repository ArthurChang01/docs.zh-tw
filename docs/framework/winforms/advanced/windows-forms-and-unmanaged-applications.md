---
title: 未受管理的應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 17dc20653d1628dfd460a9891e1b0a21c0ebecbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746363"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="c6464-102">Windows Form 和 Unmanaged 應用程式</span><span class="sxs-lookup"><span data-stu-id="c6464-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="c6464-103">伴隨著某些注意事項，Windows Form 應用程式和控制項能與 Unmanaged 應用程式交互操作。</span><span class="sxs-lookup"><span data-stu-id="c6464-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="c6464-104">下列各節描述 Windows Form 應用程式和控制項支援及不支援的案例和組態。</span><span class="sxs-lookup"><span data-stu-id="c6464-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6464-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="c6464-105">In This Section</span></span>  
 [<span data-ttu-id="c6464-106">Windows Forms 和 Unmanaged 應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="c6464-106">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="c6464-107">針對如何使用及實作 Windows Form 控制項來與 Unmanaged 應用程式搭配運作，提供一般相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c6464-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="c6464-108">操作說明：顯示 Windows Forms 和 ShowDialog 方法以支援 COM Interop</span><span class="sxs-lookup"><span data-stu-id="c6464-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="c6464-109">提供程式碼範例，示範如何使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法，在 Unmanaged 應用程式中執行 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="c6464-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="c6464-110">操作說明：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop</span><span class="sxs-lookup"><span data-stu-id="c6464-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="c6464-111">提供程式碼範例，示範如何讓 Windows Form 在其自己的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="c6464-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="c6464-112">另請參閱 [逐步解說：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="c6464-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c6464-113">參考</span><span class="sxs-lookup"><span data-stu-id="c6464-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="c6464-114">用來為 Windows Form 建立個別的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c6464-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="c6464-115">為執行緒啟動訊息迴圈。</span><span class="sxs-lookup"><span data-stu-id="c6464-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="c6464-116">將呼叫從 Unmanaged 應用程式封送處理至表單。</span><span class="sxs-lookup"><span data-stu-id="c6464-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c6464-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="c6464-117">Related Sections</span></span>  
 [<span data-ttu-id="c6464-118">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="c6464-118">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="c6464-119">針對如何在 Unmanaged 應用程式中使用 .NET Framework 類型，提供一般相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c6464-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
