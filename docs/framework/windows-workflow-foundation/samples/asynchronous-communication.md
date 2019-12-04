---
title: 非同步通訊
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 28b325a6bd870282577a2989b616628d52262deb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711854"
---
# <a name="asynchronous-communication"></a>非同步通訊
這個範例會示範兩個不同 Windows Workflow Foundation （WF）服務之間的通訊預設如何以非同步方式執行。  
  
## <a name="demonstrates"></a>示範  
 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 服務之間的非同步通訊。  
  
## <a name="discussion"></a>討論  
 這個範例示範如何在 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 應用程式之間使用 .NET Framework 提供的訊息處理活動，以非同步方式進行通訊。  
  
 這個範例包含下列三個專案。  
  
 CreditCheckService  
 這項服務會接受特定人員的信用得分，或是要擷取的項目值，然後決定是否給予該人員信用額度。  
  
 RentalApprovalService  
 這項服務會接收需要一些信用額度的人提出的申請。 這項服務會以非同步方式與 `CreditCheckService` 進行通訊，決定信用額度申請是否有效。  
  
 Client  
 Client 會以同步方式與 `RentalApprovalService` 進行通訊，了解信用額度是否核准。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 以滑鼠右鍵按一下 [ **AsynchronousCommunication** ] 方案，然後選取 [**屬性**]。  
  
2. 在 [**通用屬性**] 中，選取 [**啟始專案**]，然後選取 [**多個啟始專案**]。  
  
3. 將**RentalApprovalService**移至清單中的第一個位置，後面接著**CreditCheckService**，接著**用戶端**。 在所有三個專案上設定 [**啟動**] 動作。  
  
4. 按一下 **[確定]** ，然後按 F5 執行範例。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
