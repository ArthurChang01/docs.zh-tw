---
title: 依本文路由
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144184"
---
# <a name="route-by-body"></a><span data-ttu-id="78ab7-102">依本文路由</span><span class="sxs-lookup"><span data-stu-id="78ab7-102">Route by Body</span></span>
<span data-ttu-id="78ab7-103">這個範例會示範如何實作使用任何 SOAP 動作接受訊息物件的服務。</span><span class="sxs-lookup"><span data-stu-id="78ab7-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="78ab7-104">此示例基於實現計算機服務的[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="78ab7-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="78ab7-105">此服務會實作接受 `Calculate` 要求參數並傳回 <xref:System.ServiceModel.Channels.Message> 回應的單一 <xref:System.ServiceModel.Channels.Message> 作業。</span><span class="sxs-lookup"><span data-stu-id="78ab7-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="78ab7-106">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務是裝載在 IIS 中。</span><span class="sxs-lookup"><span data-stu-id="78ab7-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78ab7-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="78ab7-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="78ab7-108">下列範例會示範根據本文內容的訊息分派。</span><span class="sxs-lookup"><span data-stu-id="78ab7-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="78ab7-109">內置的 Windows 通信基礎 （WCF） 服務模型消息調度機制基於消息操作。</span><span class="sxs-lookup"><span data-stu-id="78ab7-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="78ab7-110">然而，有很多現有的 Web 服務以 Action="" 定義其所有作業。</span><span class="sxs-lookup"><span data-stu-id="78ab7-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="78ab7-111">根據以 Action 資訊為基礎保留分派要求訊息的 WSDL 來建置服務，是不可能的。</span><span class="sxs-lookup"><span data-stu-id="78ab7-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="78ab7-112">這個範例會示範根據 WSDL 的服務合約 (WSDL 包含在範例隨附的 Service.wsdl 中)。</span><span class="sxs-lookup"><span data-stu-id="78ab7-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="78ab7-113">服務協定是計算機，類似于[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)中使用的協定。</span><span class="sxs-lookup"><span data-stu-id="78ab7-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="78ab7-114">不過，`[OperationContract]` 會指定所有作業的 `Action=""`。</span><span class="sxs-lookup"><span data-stu-id="78ab7-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="78ab7-115">如果是合約，服務需要自訂分派行為 `DispatchByBodyBehavior`，以允許在作業之間分派訊息。</span><span class="sxs-lookup"><span data-stu-id="78ab7-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="78ab7-116">此調度行為用由相應包裝`DispatchByBodyElementOperationSelector`元素的 QName 鍵控的操作名稱表初始化自訂操作選擇器。</span><span class="sxs-lookup"><span data-stu-id="78ab7-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="78ab7-117">`DispatchByBodyElementOperationSelector` 會查看本文之第一個子系的開始標記，並使用先前提到的資料表來選取作業。</span><span class="sxs-lookup"><span data-stu-id="78ab7-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="78ab7-118">用戶端使用服務[模型中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務匯出的 WSDL 自動生成的代理。</span><span class="sxs-lookup"><span data-stu-id="78ab7-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="78ab7-119">除了自動產生之 Proxy 中的 Action 參數以外，所有作業的動作都是空的，這事實對用戶端程式碼沒有影響。</span><span class="sxs-lookup"><span data-stu-id="78ab7-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="78ab7-120">用戶端程式碼會執行數次計算。</span><span class="sxs-lookup"><span data-stu-id="78ab7-120">The client code performs several calculations.</span></span> <span data-ttu-id="78ab7-121">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="78ab7-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="78ab7-122">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="78ab7-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="78ab7-123">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="78ab7-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="78ab7-124">確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="78ab7-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="78ab7-125">要生成解決方案，請按照生成 Windows[通信基礎示例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的說明進行操作。</span><span class="sxs-lookup"><span data-stu-id="78ab7-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="78ab7-126">要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。</span><span class="sxs-lookup"><span data-stu-id="78ab7-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="78ab7-127">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="78ab7-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="78ab7-128">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="78ab7-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="78ab7-129">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="78ab7-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="78ab7-130">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="78ab7-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
