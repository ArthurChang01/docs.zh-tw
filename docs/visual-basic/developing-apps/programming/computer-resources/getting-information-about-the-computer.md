---
title: 取得電腦的相關資訊 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Info object [Visual Basic], tasks
ms.assetid: 13c145bc-5c85-4fea-a5dd-2ca8681a0252
ms.openlocfilehash: c313f96ec17e2cfb1d94fedebbce5b2f5b8dbc95
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581252"
---
# <a name="getting-information-about-the-computer-visual-basic"></a><span data-ttu-id="16df9-102">取得電腦的相關資訊 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16df9-102">Getting Information about the Computer (Visual Basic)</span></span>

<span data-ttu-id="16df9-103">`My.Computer.Info` 物件所提供的屬性可用來取得電腦的記憶體、已載入組件、名稱和作業系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="16df9-103">The `My.Computer.Info` object provides properties for getting information about the computer's memory, loaded assemblies, name, and operating system.</span></span>

## <a name="remarks"></a><span data-ttu-id="16df9-104">備註</span><span class="sxs-lookup"><span data-stu-id="16df9-104">Remarks</span></span>

<span data-ttu-id="16df9-105">此表列出經常透過 `My.Computer.Info` 物件完成的工作，並指向示範各執行方式的主題。</span><span class="sxs-lookup"><span data-stu-id="16df9-105">This table lists tasks commonly accomplished through the `My.Computer.Info` object and points to topics demonstrating how to perform each.</span></span>

|<span data-ttu-id="16df9-106">若要</span><span class="sxs-lookup"><span data-stu-id="16df9-106">To</span></span>|<span data-ttu-id="16df9-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="16df9-107">See</span></span>|
|---|---|
|<span data-ttu-id="16df9-108">判斷已安裝應用程式的電腦有多少虛擬位址空間可用。</span><span class="sxs-lookup"><span data-stu-id="16df9-108">Determine how much virtual address space is available for the computer on which the application is installed</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.TotalVirtualMemory%2A>|
|<span data-ttu-id="16df9-109">判斷應用程式執行所在電腦的平台類型。</span><span class="sxs-lookup"><span data-stu-id="16df9-109">Determine the platform type of the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSPlatform%2A>|
|<span data-ttu-id="16df9-110">判斷應用程式執行所在電腦的作業系統。</span><span class="sxs-lookup"><span data-stu-id="16df9-110">Determine the operating system of the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName%2A>|
|<span data-ttu-id="16df9-111">判斷應用程式執行所在電腦上已安裝的 Service Pack。</span><span class="sxs-lookup"><span data-stu-id="16df9-111">Determine what service packs have been installed on the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSVersion%2A>|
|<span data-ttu-id="16df9-112">判斷應用程式執行所在電腦上已安裝的 `UICulture`。</span><span class="sxs-lookup"><span data-stu-id="16df9-112">Determine the installed `UICulture` on the computer on which the application is running.</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.InstalledUICulture%2A>|

## <a name="see-also"></a><span data-ttu-id="16df9-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="16df9-113">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
