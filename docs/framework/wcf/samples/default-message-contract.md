---
title: 預設訊息合約
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 46b69697616ad7983daed16f8a180a4da7f61a16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183762"
---
# <a name="default-message-contract"></a><span data-ttu-id="7394e-102">預設訊息合約</span><span class="sxs-lookup"><span data-stu-id="7394e-102">Default Message Contract</span></span>
<span data-ttu-id="7394e-103">預設訊息合約範例會示範一個服務，在這個服務中可以對服務作業來回傳遞自訂的使用者定義訊息。</span><span class="sxs-lookup"><span data-stu-id="7394e-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="7394e-104">此示例基於將計算機介面實現為類型化服務的[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7394e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="7394e-105">此示例傳遞一個自訂消息，其中包含運算元和運算子，並返回算術計算的結果，而不是["開始"](../../../../docs/framework/wcf/samples/getting-started-sample.md)中使用的添加、減法、乘法和除法的單個服務操作。</span><span class="sxs-lookup"><span data-stu-id="7394e-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="7394e-106">用戶端是主控台程式 (.exe)，而服務程式庫 (.dll) 是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="7394e-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7394e-107">您可以在主控台視窗中看到用戶端活動。</span><span class="sxs-lookup"><span data-stu-id="7394e-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7394e-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="7394e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7394e-109">在服務中，會定義單一服務作業，而這個作業會接受並傳回型別為 `MyMessage` 的自訂訊息。</span><span class="sxs-lookup"><span data-stu-id="7394e-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="7394e-110">雖然這個範例中的要求和回應訊息型別相同，但在必要時一定是不同的訊息合約。</span><span class="sxs-lookup"><span data-stu-id="7394e-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="7394e-111">自訂訊息 `MyMessage` 是定義在以 <xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性標註的類別中。</span><span class="sxs-lookup"><span data-stu-id="7394e-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="7394e-112">這個範例中只使用了第三個建構函式。</span><span class="sxs-lookup"><span data-stu-id="7394e-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="7394e-113">使用訊息合約可讓您完全控制 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="7394e-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="7394e-114">在這個範例中，會使用 <xref:System.ServiceModel.MessageHeaderAttribute> 屬性，將 `Operation` 放在 SOAP 標頭中。</span><span class="sxs-lookup"><span data-stu-id="7394e-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="7394e-115">因為運算元 `N1`、`N2` 和 `Result` 都套用了 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性，所以會出現在 SOAP 本文中。</span><span class="sxs-lookup"><span data-stu-id="7394e-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="7394e-116">實作類別包含 `Calculate` 服務作業的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7394e-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="7394e-117">`CalculateService` 類別會從要求訊息中取得運算元和運算子，然後建立包含所要求之計算結果的回應訊息，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7394e-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="7394e-118">使用[服務模型中繼資料實用程式工具 （Svcutil.exe） 工具](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)創建了用戶端生成的用戶端代碼。</span><span class="sxs-lookup"><span data-stu-id="7394e-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="7394e-119">必要時，這個工具會自動在產生的用戶端程式碼中建立訊息合約類型。</span><span class="sxs-lookup"><span data-stu-id="7394e-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="7394e-120">您也可以指定 `/messageContract` 命令選項來強制產生訊息合約。</span><span class="sxs-lookup"><span data-stu-id="7394e-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="7394e-121">下列範例程式碼示範使用 `MyMessage` 訊息的用戶端。</span><span class="sxs-lookup"><span data-stu-id="7394e-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage()
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="7394e-122">當您執行範例時，計算過程會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="7394e-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="7394e-123">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="7394e-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7394e-124">此時，自訂的使用者定義訊息已在用戶端和服務作業之間傳遞。</span><span class="sxs-lookup"><span data-stu-id="7394e-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="7394e-125">訊息合約已定義將運算元和結果放在訊息本文中，而將運算子放在訊息標頭中。</span><span class="sxs-lookup"><span data-stu-id="7394e-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="7394e-126">您可以設定訊息記錄來觀察這個訊息結構。</span><span class="sxs-lookup"><span data-stu-id="7394e-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7394e-127">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="7394e-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7394e-128">確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7394e-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7394e-129">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="7394e-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7394e-130">要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。</span><span class="sxs-lookup"><span data-stu-id="7394e-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7394e-131">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7394e-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7394e-132">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7394e-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7394e-133">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="7394e-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7394e-134">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7394e-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
