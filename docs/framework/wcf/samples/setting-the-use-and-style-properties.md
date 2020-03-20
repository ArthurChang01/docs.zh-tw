---
title: 設置"使用"和"樣式"屬性示例
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f400c0bc08588afa951ae33f221663b47b37602c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144028"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="6678b-102">設定 Use 與 Style 屬性</span><span class="sxs-lookup"><span data-stu-id="6678b-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="6678b-103">這個範例會示範如何在 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 和 <xref:System.ServiceModel.DataContractFormatAttribute> 上使用 Use 和 Style 屬性。</span><span class="sxs-lookup"><span data-stu-id="6678b-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="6678b-104">這些屬性會影響訊息的格式化方式。</span><span class="sxs-lookup"><span data-stu-id="6678b-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="6678b-105">根據預設，會以設為 <xref:System.ServiceModel.OperationFormatStyle.Document> 的樣式來格式化訊息本文。</span><span class="sxs-lookup"><span data-stu-id="6678b-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="6678b-106">這些設定可以指定於服務合約層級或作業合約層級。</span><span class="sxs-lookup"><span data-stu-id="6678b-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="6678b-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="6678b-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="6678b-108"><xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> 樣式屬性會判斷該服務之 WSDL 中繼資料格式化的方式。</span><span class="sxs-lookup"><span data-stu-id="6678b-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="6678b-109">可能的值為 <xref:System.ServiceModel.OperationFormatStyle.Document> 和 <xref:System.ServiceModel.OperationFormatStyle.Rpc>。</span><span class="sxs-lookup"><span data-stu-id="6678b-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="6678b-110">RPC 表示為某個作業交換之訊息的 WSDL 表示法，如同遠端程序呼叫一般含有參數。</span><span class="sxs-lookup"><span data-stu-id="6678b-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="6678b-111">以下是一個範例。</span><span class="sxs-lookup"><span data-stu-id="6678b-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="6678b-112">將樣式設為 <xref:System.ServiceModel.OperationFormatStyle.Document> 代表 WSDL 表示法含有一個代表文件的項目，此文件會為某作業進行交換，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="6678b-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="6678b-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 屬性會決定訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="6678b-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="6678b-114">可能的值為 <xref:System.ServiceModel.OperationFormatUse.Literal> 和 <xref:System.ServiceModel.OperationFormatUse.Encoded>；預設值為 <xref:System.ServiceModel.OperationFormatUse.Literal>。</span><span class="sxs-lookup"><span data-stu-id="6678b-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="6678b-115">Literal 表示訊息是 WSDL 中結構描述的常值 (Literal) 執行個體，如下列 Document/Literal 範例所示。</span><span class="sxs-lookup"><span data-stu-id="6678b-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="6678b-116">Encoded 表示 WSDL 中的結構描述是根據 SOAP 1.1 第 5 節的規則編碼的抽象規格。</span><span class="sxs-lookup"><span data-stu-id="6678b-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="6678b-117">下列式 RPC/Encoded 的範例。</span><span class="sxs-lookup"><span data-stu-id="6678b-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="6678b-118">WS-I Basic Profile 1.0 禁止使用 <xref:System.ServiceModel.OperationFormatUse.Encoded>，只有在舊版服務需要時才使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="6678b-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="6678b-119">此 `Encoded` 訊息格式只會在使用 XmlSerializer 時才會提供。</span><span class="sxs-lookup"><span data-stu-id="6678b-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="6678b-120">為了允許您查看正在發送和接收的消息，此示例基於[跟蹤和消息日誌記錄](tracing-and-message-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="6678b-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="6678b-121">服務組態與原始程式碼已修改成啟用並利用追蹤以及訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="6678b-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="6678b-122">此外，<xref:System.ServiceModel.WSHttpBinding> 已經設定成不使用安全性，因此已記錄的訊息可以用未加密的格式檢視。</span><span class="sxs-lookup"><span data-stu-id="6678b-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="6678b-123">生成的跟蹤日誌（系統.ServiceModel.e2e 和 Message.log）應使用[服務跟蹤檢視器工具 （SvcTraceViewer.exe）](../service-trace-viewer-tool-svctraceviewer-exe.md)進行查看。</span><span class="sxs-lookup"><span data-stu-id="6678b-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="6678b-124">這些追蹤已設定為建立在 C:\LOGS 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6678b-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="6678b-125">先建立資料夾，再執行此範例。</span><span class="sxs-lookup"><span data-stu-id="6678b-125">Create the folder before running the sample.</span></span> <span data-ttu-id="6678b-126">要查看"跟蹤檢視器"工具中的消息內容，請選擇工具的左側和右側窗格中**的消息**。</span><span class="sxs-lookup"><span data-stu-id="6678b-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="6678b-127">下列程式碼會示範 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 屬性已設為 <xref:System.ServiceModel.OperationFormatUse>，而訊息本文格式已從預設的 <xref:System.ServiceModel.OperationFormatStyle> 變更為 <xref:System.ServiceModel.OperationFormatStyle.Document> 的服務合約。</span><span class="sxs-lookup"><span data-stu-id="6678b-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="6678b-128">若要檢視不同 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 和 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> 設定之間的差異，請修改服務中的這些設定，接著重新產生用戶端、執行範例，然後使用服務追蹤檢視器工具檢查 c:\logs\message.logs 檔。</span><span class="sxs-lookup"><span data-stu-id="6678b-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="6678b-129">還要通過查看`http://localhost/ServiceModelSamples/service.svc?wsdl`來觀察對中繼資料的影響。</span><span class="sxs-lookup"><span data-stu-id="6678b-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="6678b-130">服務的中繼資料通常會分成好幾頁。</span><span class="sxs-lookup"><span data-stu-id="6678b-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="6678b-131">主 wsdl 頁包含 WSDL 綁定，但視圖`http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0`以觀察消息定義。</span><span class="sxs-lookup"><span data-stu-id="6678b-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6678b-132">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="6678b-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6678b-133">確保已為 Windows[通信基礎示例執行一次性設置過程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6678b-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6678b-134">建立用於記錄訊息的 C:\LOGS 目錄。</span><span class="sxs-lookup"><span data-stu-id="6678b-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="6678b-135">給予使用者這個目錄的網路服務寫入權限。</span><span class="sxs-lookup"><span data-stu-id="6678b-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="6678b-136">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="6678b-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="6678b-137">要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](running-the-samples.md)說明操作。</span><span class="sxs-lookup"><span data-stu-id="6678b-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6678b-138">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6678b-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6678b-139">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6678b-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6678b-140">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="6678b-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6678b-141">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6678b-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
