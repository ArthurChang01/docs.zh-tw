---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320632"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="6149e-102">控制 WCF 服務主機的自動啟動功能</span><span class="sxs-lookup"><span data-stu-id="6149e-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="6149e-103">您可以控制 WCF 服務程式庫專案的 Windows Communication Foundation （WCF）服務主機（WcfSvcHost）的自動啟動功能，當您在同一個包含多個專案的 Visual Studio 方案中，對另一個專案進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="6149e-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="6149e-104">若要這樣做，請在**方案總管**的 WCF 服務專案上按一下滑鼠右鍵，選擇 [**屬性**]，然後按一下 [ **WCF 選項**] 索引標籤。預設會啟用 [在**同一個方案中偵測到另一個專案時啟動 WCF 服務主機**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6149e-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="6149e-105">您可以清除此方塊，如此一來，在相同的方案中調試另一個專案時，就不會啟動此特定專案的 WCF 服務主機。</span><span class="sxs-lookup"><span data-stu-id="6149e-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="6149e-106">這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。</span><span class="sxs-lookup"><span data-stu-id="6149e-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="6149e-107">這個選項可供下列專案使用：</span><span class="sxs-lookup"><span data-stu-id="6149e-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="6149e-108">WCF 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="6149e-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="6149e-109">循序工作流程服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="6149e-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="6149e-110">狀態機器工作流程服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="6149e-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="6149e-111">新聞訂閱服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="6149e-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6149e-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="6149e-112">See also</span></span>

- [<span data-ttu-id="6149e-113">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="6149e-113">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
