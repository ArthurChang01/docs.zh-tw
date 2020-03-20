---
title: 暫停的執行個體管理
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 784ec3cdda8eedb188c3c776ed412ea40baf37ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182795"
---
# <a name="suspended-instance-management"></a>暫停的執行個體管理
這個範例會示範如何管理已暫止的工作流程執行個體。  <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 的預設動作為 `AbandonAndSuspend`。 這表示根據預設，從裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中之工作流程執行個體所擲回的未處理例外狀況將會造成此執行個體從記憶體中處置 (放棄)，而且此執行個體的永久性/持續版本將會標示為已暫停。 暫停的工作流程執行個體要等到取消暫停之後才能夠執行。

 此範例會示範如何實作命令列公用程式來查詢暫停的執行個體，以及如何提供使用者繼續或終止執行個體的選擇。 在這個範例中，工作流程服務會故意擲回例外狀況，使得它遭到暫停。 然後可以使用此命令列公用程式來查詢執行個體，之後再繼續或終止執行個體。

## <a name="demonstrates"></a>示範
 <xref:System.ServiceModel.WorkflowServiceHost>和<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior><xref:System.ServiceModel.Activities.WorkflowControlEndpoint>在 Windows 工作流基礎 （WF）。

## <a name="discussion"></a>討論區
 這個範例中所實作的命令列公用程式是 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 隨附之 SQL 執行個體存放區實作所特有。 如果您擁有執行個體存放區的自訂實作，您可以改寫此公用程式，其方式是使用您的執行個體存放區所特有的實作來取代範例中的 `WorkflowInstanceCommand` 實作。

 提供的實作會直接針對 SQL 執行個體存放區來執行 SQL 命令，以列出暫停的執行個體，而且此實作會依賴加入至 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 的 <xref:System.ServiceModel.WorkflowServiceHost> 來結束或終止執行個體。

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 本範例需要啟用下列 Windows 元件：

    1. Microsoft Message Queues (MSMQ) 伺服器

    2. SQL Server Express

2. 設定 SQL Server 資料庫。

    1. 從 Visual Studio 2010 命令提示符中，從掛起實例管理示例目錄中運行"setup.cmd"，該目錄執行以下操作：

        1. 使用 SQL Server Express 建立持續性資料庫。 如果持續性資料庫已經存在，請將它卸除然後重新建立。

        2. 設定資料庫擁有持續性。

        3. 將 IIS APPPOOL\DefaultAppPool 和 NT AUTHORITY\Network Service 加入至 InstanceStoreUsers 角色，這是設定資料庫擁有持續性時所定義的角色。

3. 設定服務佇列。

    1. 在 Visual Studio 2010 中，按右鍵**示例工作流應用**專案，然後按一下"**設置為啟動專案**"。

    2. 通過按**F5**編譯並運行示例工作流應用程式。 這樣會建立所需的佇列。

    3. 按**Enter**以停止示例工作流應用。

    4. 從命令提示字元執行 Compmgmt.msc，開啟 [電腦管理] 主控台。

    5. 擴展**服務和應用程式**，**訊息佇列**，**私用佇列**.

    6. 按右鍵**ReceiveTx**佇列並選擇**屬性**。

    7. 選擇"**安全**"選項卡，並允許**每個人都**具有**接收消息**、**查看消息**和**發送消息的許可權**。

4. 現在，請執行範例。

    1. 在 Visual Studio 2010 中，通過按**Ctrl_F5**再次運行示例工作流App 專案，而無需調試。 兩個端點位址將會列印到主控台視窗：一個適用於應用程式端點，另一個來自 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>。 然後會建立工作流程執行個體，該執行個體的追蹤記錄將會出現在主控台視窗。 工作流程執行個體將會擲回例外狀況，造成執行個體被暫停及中止。

    2. 然後可以使用此命令列公用程式來針對任何執行個體採取進一步的動作。 命令列引數的語法如下：

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         支援的命令為：`Query`、`Resume` 和 `Terminate`。  只有 `Resume` 和 `Terminate` 作業需要 InstanceId 參數。

#### <a name="to-cleanup-optional"></a>若要清除 (選擇性)

1. 從 `vs2010` 命令提示字元執行 Compmgmt.msc，開啟 [電腦管理] 主控台。

2. 擴展**服務和應用程式**，**訊息佇列**，**私用佇列**.

3. 刪除**接收Tx**佇列。

4. 若要移除持續性資料庫，請執行 cleanup.cmd。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
