---
title: 進出工作流程服務的異動流動
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185271"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="d83d6-102">進出工作流程服務的異動流動</span><span class="sxs-lookup"><span data-stu-id="d83d6-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="d83d6-103">工作流程服務與用戶端都可以參與交易。</span><span class="sxs-lookup"><span data-stu-id="d83d6-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="d83d6-104">若要讓服務作業變成環境交易的一部分，請將 <xref:System.ServiceModel.Activities.Receive> 活動放在 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動內。</span><span class="sxs-lookup"><span data-stu-id="d83d6-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="d83d6-105"><xref:System.ServiceModel.Activities.Send> 或 <xref:System.ServiceModel.Activities.SendReply> 活動在 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 內所進行的任何呼叫也會在環境交易中進行。</span><span class="sxs-lookup"><span data-stu-id="d83d6-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="d83d6-106">工作流程用戶端應用程式可以使用 <xref:System.Activities.Statements.TransactionScope> 活動建立環境異動，然後使用環境異動呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="d83d6-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="d83d6-107">本主題逐步帶領您建立參與交易的工作流程服務和工作流程用戶端。</span><span class="sxs-lookup"><span data-stu-id="d83d6-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d83d6-108">如果在事務中載入工作流服務實例，並且工作流包含<xref:System.Activities.Statements.Persist>活動，工作流實例將阻止，直到事務超時。</span><span class="sxs-lookup"><span data-stu-id="d83d6-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d83d6-109">每當您使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 時，建議您將工作流程中的所有 Receive 放在 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動內。</span><span class="sxs-lookup"><span data-stu-id="d83d6-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d83d6-110">如果使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 而且訊息按照錯誤的順序送達，工作流程就會在嘗試傳送第一則順序錯誤的訊息時中止。</span><span class="sxs-lookup"><span data-stu-id="d83d6-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="d83d6-111">當工作流程閒置時，您必須確定工作流程永遠位於一致的停止點。</span><span class="sxs-lookup"><span data-stu-id="d83d6-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="d83d6-112">萬一工作流程已中止，這樣做可讓您從上一個保存點重新啟動工作流程。</span><span class="sxs-lookup"><span data-stu-id="d83d6-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="d83d6-113">建立共用程式庫</span><span class="sxs-lookup"><span data-stu-id="d83d6-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="d83d6-114">建立一個新的空白 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="d83d6-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="d83d6-115">加入稱為 `Common` 的新類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="d83d6-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="d83d6-116">加入下列組件的參考：</span><span class="sxs-lookup"><span data-stu-id="d83d6-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="d83d6-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="d83d6-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="d83d6-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="d83d6-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="d83d6-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="d83d6-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="d83d6-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="d83d6-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="d83d6-121">將稱為 `PrintTransactionInfo` 的新類別加入至 `Common` 專案。</span><span class="sxs-lookup"><span data-stu-id="d83d6-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="d83d6-122">此類別衍生自 <xref:System.Activities.NativeActivity>，而且會多載 <xref:System.Activities.NativeActivity.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d83d6-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     <span data-ttu-id="d83d6-123">這是一種原生活動，該活動可顯示環境異動的相關資訊，而且可同時用於本主題中所使用的服務和用戶端工作流程。</span><span class="sxs-lookup"><span data-stu-id="d83d6-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="d83d6-124">生成解決方案以使此活動在**工具箱**的 **"通用**"部分可用。</span><span class="sxs-lookup"><span data-stu-id="d83d6-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="d83d6-125">實作工作流程服務</span><span class="sxs-lookup"><span data-stu-id="d83d6-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="d83d6-126">添加新的 WCF 工作流服務，`WorkflowService`該服務調用`Common`到專案中。</span><span class="sxs-lookup"><span data-stu-id="d83d6-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="d83d6-127">要執行此操作，`Common`請按一下專案，選擇 **"添加**"**新專案..."，"** 在**已安裝範本**下選擇**工作流**"並選擇**WCF 工作流服務**。</span><span class="sxs-lookup"><span data-stu-id="d83d6-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![加入工作流程服務](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="d83d6-129">刪除預設的 `ReceiveRequest` 和 `SendResponse` 活動。</span><span class="sxs-lookup"><span data-stu-id="d83d6-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="d83d6-130">將 <xref:System.Activities.Statements.WriteLine> 活動拖放到 `Sequential Service` 活動中。</span><span class="sxs-lookup"><span data-stu-id="d83d6-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="d83d6-131">將文字屬性設定為 `"Workflow Service starting ..."`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d83d6-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="d83d6-132">!•將 WriteLine 活動添加到順序服務活動（./媒體/流式事務-進入和退出工作流服務/添加-寫入行-順序服務.jpg）</span><span class="sxs-lookup"><span data-stu-id="d83d6-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="d83d6-133">將 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 拖放到 <xref:System.Activities.Statements.WriteLine> 活動後面。</span><span class="sxs-lookup"><span data-stu-id="d83d6-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="d83d6-134">活動<xref:System.ServiceModel.Activities.TransactedReceiveScope>可以在**工具箱**的 **"消息"** 部分中找到。</span><span class="sxs-lookup"><span data-stu-id="d83d6-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="d83d6-135">活動<xref:System.ServiceModel.Activities.TransactedReceiveScope>由**請求**和**正文**兩個部分組成。</span><span class="sxs-lookup"><span data-stu-id="d83d6-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="d83d6-136">"**請求**"部分包含活動<xref:System.ServiceModel.Activities.Receive>。</span><span class="sxs-lookup"><span data-stu-id="d83d6-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="d83d6-137">**"正文"** 部分包含在收到消息後要在事務內執行的活動。</span><span class="sxs-lookup"><span data-stu-id="d83d6-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![加入 TransactedReceiveScope 活動](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="d83d6-139">選擇活動<xref:System.ServiceModel.Activities.TransactedReceiveScope>並按一下 **"變數"** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d83d6-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="d83d6-140">加入下列變數。</span><span class="sxs-lookup"><span data-stu-id="d83d6-140">Add the following variables.</span></span>  
  
     ![向交易接收範圍添加變數](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="d83d6-142">根據預設，您可以刪除現有的資料變數。</span><span class="sxs-lookup"><span data-stu-id="d83d6-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="d83d6-143">您也可以使用現有的控制碼變數。</span><span class="sxs-lookup"><span data-stu-id="d83d6-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="d83d6-144">在<xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.TransactedReceiveScope>活動的 **"請求"** 部分中拖放活動。</span><span class="sxs-lookup"><span data-stu-id="d83d6-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="d83d6-145">設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d83d6-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="d83d6-146">屬性</span><span class="sxs-lookup"><span data-stu-id="d83d6-146">Property</span></span>|<span data-ttu-id="d83d6-147">值</span><span class="sxs-lookup"><span data-stu-id="d83d6-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d83d6-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="d83d6-148">CanCreateInstance</span></span>|<span data-ttu-id="d83d6-149">True (核取此核取方塊)</span><span class="sxs-lookup"><span data-stu-id="d83d6-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="d83d6-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="d83d6-150">OperationName</span></span>|<span data-ttu-id="d83d6-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="d83d6-151">StartSample</span></span>|  
    |<span data-ttu-id="d83d6-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="d83d6-152">ServiceContractName</span></span>|<span data-ttu-id="d83d6-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="d83d6-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="d83d6-154">工作流程的外觀應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d83d6-154">The workflow should look like this:</span></span>  
  
     ![加入 Receive 活動](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="d83d6-156">按一下<xref:System.ServiceModel.Activities.Receive>活動中的 **"定義..."** 連結並設置以下設置：</span><span class="sxs-lookup"><span data-stu-id="d83d6-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![為"接收"活動設置消息設置](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="d83d6-158">將 <xref:System.Activities.Statements.Sequence> 活動拖放到 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 的 [主體] 區段內。</span><span class="sxs-lookup"><span data-stu-id="d83d6-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="d83d6-159">拖放 <xref:System.Activities.Statements.Sequence> 活動內的兩個 <xref:System.Activities.Statements.WriteLine> 活動，並設定 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d83d6-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="d83d6-160">活動</span><span class="sxs-lookup"><span data-stu-id="d83d6-160">Activity</span></span>|<span data-ttu-id="d83d6-161">值</span><span class="sxs-lookup"><span data-stu-id="d83d6-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d83d6-162">第一個 WriteLine</span><span class="sxs-lookup"><span data-stu-id="d83d6-162">1st WriteLine</span></span>|<span data-ttu-id="d83d6-163">"服務：接收已完成"</span><span class="sxs-lookup"><span data-stu-id="d83d6-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="d83d6-164">第二個 WriteLine</span><span class="sxs-lookup"><span data-stu-id="d83d6-164">2nd WriteLine</span></span>|<span data-ttu-id="d83d6-165">"Service: Received = " + requestMessage</span><span class="sxs-lookup"><span data-stu-id="d83d6-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="d83d6-166">工作流程的外觀現在應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d83d6-166">The workflow should now look like this:</span></span>  
  
     ![添加寫入行活動後的序列](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="d83d6-168">`PrintTransactionInfo` <xref:System.Activities.Statements.WriteLine>在<xref:System.ServiceModel.Activities.TransactedReceiveScope>**活動中的"正文"** 中的第二個活動之後，拖放活動。</span><span class="sxs-lookup"><span data-stu-id="d83d6-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![添加列印交易資訊後的順序](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="d83d6-170">將 <xref:System.Activities.Statements.Assign> 活動拖放到 `PrintTransactionInfo` 活動後面，然後根據下表設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="d83d6-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="d83d6-171">屬性</span><span class="sxs-lookup"><span data-stu-id="d83d6-171">Property</span></span>|<span data-ttu-id="d83d6-172">值</span><span class="sxs-lookup"><span data-stu-id="d83d6-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d83d6-173">至</span><span class="sxs-lookup"><span data-stu-id="d83d6-173">To</span></span>|<span data-ttu-id="d83d6-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="d83d6-174">replyMessage</span></span>|  
    |<span data-ttu-id="d83d6-175">值</span><span class="sxs-lookup"><span data-stu-id="d83d6-175">Value</span></span>|<span data-ttu-id="d83d6-176">"Service: Sending reply."</span><span class="sxs-lookup"><span data-stu-id="d83d6-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="d83d6-177">將 <xref:System.Activities.Statements.WriteLine> 活動拖放到 <xref:System.Activities.Statements.Assign> 活動後面，並將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Service: Begin reply"。</span><span class="sxs-lookup"><span data-stu-id="d83d6-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="d83d6-178">工作流程的外觀現在應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d83d6-178">The workflow should now look like this:</span></span>  
  
     ![加入 Assign 和 WriteLine 之後](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="d83d6-180">按右鍵<xref:System.ServiceModel.Activities.Receive>活動並選擇 **"創建發送回復"，** 並在上次<xref:System.Activities.Statements.WriteLine>活動後粘貼。</span><span class="sxs-lookup"><span data-stu-id="d83d6-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="d83d6-181">按一下`SendReplyToReceive`活動中的 **"定義..."** 連結，然後進行以下設置。</span><span class="sxs-lookup"><span data-stu-id="d83d6-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![回覆訊息設定](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="d83d6-183">在<xref:System.Activities.Statements.WriteLine>`SendReplyToReceive`活動後拖放活動並將其<xref:System.Activities.Statements.WriteLine.Text%2A>屬性設置為"服務：已發送回復"。</span><span class="sxs-lookup"><span data-stu-id="d83d6-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="d83d6-184">將 <xref:System.Activities.Statements.WriteLine> 活動拖放到工作流程的底部，然後將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Service: Workflow ends, press ENTER to exit"。</span><span class="sxs-lookup"><span data-stu-id="d83d6-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="d83d6-185">完成的服務工作流程外觀應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d83d6-185">The completed service workflow should look like this:</span></span>  
  
     ![完成服務工作流程](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="d83d6-187">實作工作流程用戶端</span><span class="sxs-lookup"><span data-stu-id="d83d6-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="d83d6-188">將稱為 `WorkflowClient` 的新 WCF 工作流程應用程式加入至 `Common` 專案。</span><span class="sxs-lookup"><span data-stu-id="d83d6-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="d83d6-189">要執行此操作，`Common`請按一下專案，選擇 **"添加\*\*\*\*"新專案..."，"** 在**已安裝範本**下選擇**工作流**並選擇**活動**"。</span><span class="sxs-lookup"><span data-stu-id="d83d6-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![加入 [活動] 專案](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="d83d6-191">將 <xref:System.Activities.Statements.Sequence> 活動拖放至設計介面上。</span><span class="sxs-lookup"><span data-stu-id="d83d6-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="d83d6-192">拖放 <xref:System.Activities.Statements.Sequence> 活動內的 <xref:System.Activities.Statements.WriteLine> 活動，並將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 `"Client: Workflow starting"`。</span><span class="sxs-lookup"><span data-stu-id="d83d6-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="d83d6-193">工作流程的外觀現在應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d83d6-193">The workflow should now look like this:</span></span>  
  
     ![加入 WriteLine 活動](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="d83d6-195">將 <xref:System.Activities.Statements.TransactionScope> 活動拖放到 <xref:System.Activities.Statements.WriteLine> 活動後面。</span><span class="sxs-lookup"><span data-stu-id="d83d6-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="d83d6-196">選取 <xref:System.Activities.Statements.TransactionScope> 活動，按一下 [變數] 按鈕，然後加入下列變數。</span><span class="sxs-lookup"><span data-stu-id="d83d6-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![將變數加入至 TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="d83d6-198">將 <xref:System.Activities.Statements.Sequence> 活動拖放到 <xref:System.Activities.Statements.TransactionScope> 活動的主體內。</span><span class="sxs-lookup"><span data-stu-id="d83d6-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="d83d6-199">將 `PrintTransactionInfo` 活動拖放到 <xref:System.Activities.Statements.Sequence> 內</span><span class="sxs-lookup"><span data-stu-id="d83d6-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="d83d6-200">在<xref:System.Activities.Statements.WriteLine>`PrintTransactionInfo`活動後拖放活動並將其<xref:System.Activities.Statements.WriteLine.Text%2A>屬性設置為"用戶端：開始發送"。</span><span class="sxs-lookup"><span data-stu-id="d83d6-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="d83d6-201">工作流程的外觀現在應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d83d6-201">The workflow should now look like this:</span></span>  
  
     ![添加用戶端：開始發送活動](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="d83d6-203">將 <xref:System.ServiceModel.Activities.Send> 活動拖放到 <xref:System.Activities.Statements.Assign> 活動後面，然後設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d83d6-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="d83d6-204">屬性</span><span class="sxs-lookup"><span data-stu-id="d83d6-204">Property</span></span>|<span data-ttu-id="d83d6-205">值</span><span class="sxs-lookup"><span data-stu-id="d83d6-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d83d6-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="d83d6-206">EndpointConfigurationName</span></span>|<span data-ttu-id="d83d6-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="d83d6-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="d83d6-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="d83d6-208">OperationName</span></span>|<span data-ttu-id="d83d6-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="d83d6-209">StartSample</span></span>|  
    |<span data-ttu-id="d83d6-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="d83d6-210">ServiceContractName</span></span>|<span data-ttu-id="d83d6-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="d83d6-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="d83d6-212">工作流程的外觀現在應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d83d6-212">The workflow should now look like this:</span></span>  
  
     ![設定 Send 活動屬性](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="d83d6-214">按一下 **"定義..."** 連結並設置以下設置：</span><span class="sxs-lookup"><span data-stu-id="d83d6-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![傳送活動訊息設定](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="d83d6-216">按右鍵<xref:System.ServiceModel.Activities.Send>活動並選擇 **"創建接收回複**"。</span><span class="sxs-lookup"><span data-stu-id="d83d6-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="d83d6-217"><xref:System.ServiceModel.Activities.ReceiveReply> 活動將會自動放在 <xref:System.ServiceModel.Activities.Send> 活動後面。</span><span class="sxs-lookup"><span data-stu-id="d83d6-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="d83d6-218">按一下 ReceiveReplyForSend 活動中的 [定義] 連結，然後進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="d83d6-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![設定 ReceiveForSend 訊息設定](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="d83d6-220">將 <xref:System.Activities.Statements.WriteLine> 活動拖放到 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動之間，然後將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Client: Send complete"。</span><span class="sxs-lookup"><span data-stu-id="d83d6-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="d83d6-221">將 <xref:System.Activities.Statements.WriteLine> 活動拖放到 <xref:System.ServiceModel.Activities.ReceiveReply> 活動後面，並將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Client side: Reply received = " + replyMessage</span><span class="sxs-lookup"><span data-stu-id="d83d6-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="d83d6-222">將 `PrintTransactionInfo` 活動拖放到 <xref:System.Activities.Statements.WriteLine> 活動後面。</span><span class="sxs-lookup"><span data-stu-id="d83d6-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="d83d6-223">將 <xref:System.Activities.Statements.WriteLine> 活動拖放到工作流程的結尾，然後將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Client workflow ends"。</span><span class="sxs-lookup"><span data-stu-id="d83d6-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="d83d6-224">完成的工作流程外觀應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d83d6-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![已完成的用戶端工作流](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="d83d6-226">建置方案。</span><span class="sxs-lookup"><span data-stu-id="d83d6-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="d83d6-227">建立服務應用程式</span><span class="sxs-lookup"><span data-stu-id="d83d6-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="d83d6-228">將稱為 `Service` 的新主控台應用程式專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="d83d6-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="d83d6-229">加入下列組件的參考：</span><span class="sxs-lookup"><span data-stu-id="d83d6-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="d83d6-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="d83d6-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="d83d6-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="d83d6-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="d83d6-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="d83d6-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="d83d6-233">開啟產生的 Program.cs 檔案以及下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d83d6-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };
          }  
    ```  
  
3. <span data-ttu-id="d83d6-234">將下列 app.config 檔案加入至專案。</span><span class="sxs-lookup"><span data-stu-id="d83d6-234">Add the following app.config file to the project.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a><span data-ttu-id="d83d6-235">建立用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="d83d6-235">Create the client application</span></span>  
  
1. <span data-ttu-id="d83d6-236">將稱為 `Client` 的新主控台應用程式專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="d83d6-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="d83d6-237">將參考加入到 System.Activities.dll。</span><span class="sxs-lookup"><span data-stu-id="d83d6-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="d83d6-238">開啟 program.cs 檔案並加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d83d6-238">Open the program.cs file and add the following code.</span></span>  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d83d6-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d83d6-239">See also</span></span>

- [<span data-ttu-id="d83d6-240">工作流服務</span><span class="sxs-lookup"><span data-stu-id="d83d6-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="d83d6-241">Windows Communication Foundation 異動概觀</span><span class="sxs-lookup"><span data-stu-id="d83d6-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
