---
title: 端點建立概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: bf6bfb10123223bf689945ef93ff09219a68092c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319919"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="8511d-102">端點建立概觀</span><span class="sxs-lookup"><span data-stu-id="8511d-102">Endpoint Creation Overview</span></span>

<span data-ttu-id="8511d-103">所有與 Windows Communication Foundation （WCF）服務的通訊都是透過服務的*端點*進行。</span><span class="sxs-lookup"><span data-stu-id="8511d-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="8511d-104">端點可讓用戶端存取 WCF 服務所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="8511d-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="8511d-105">本章節說明端點的結構，並且摘要說明如何透過組態與程式碼來定義端點。</span><span class="sxs-lookup"><span data-stu-id="8511d-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="8511d-106">端點結構</span><span class="sxs-lookup"><span data-stu-id="8511d-106">The Structure of an Endpoint</span></span>

<span data-ttu-id="8511d-107">每個端點都包含一個位址用以指出該到何處尋找端點、一個指定用戶端與端點如何進行通訊的繫結，以及一個可識別可用方法的合約。</span><span class="sxs-lookup"><span data-stu-id="8511d-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>

- <span data-ttu-id="8511d-108">**位址**。</span><span class="sxs-lookup"><span data-stu-id="8511d-108">**Address**.</span></span> <span data-ttu-id="8511d-109">位址會唯一識別端點並告訴潛在取用者服務的位置。</span><span class="sxs-lookup"><span data-stu-id="8511d-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="8511d-110">它在 WCF 物件模型中是以 <xref:System.ServiceModel.EndpointAddress> 位址表示，其中包含統一資源識別元（URI）和位址屬性，其中包括身分識別、某些 Web 服務描述語言（WSDL）元素，以及選擇性標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="8511d-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="8511d-111">選用標頭會提供額外的詳細位址資訊來識別端點或與端點互動。</span><span class="sxs-lookup"><span data-stu-id="8511d-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="8511d-112">如需詳細資訊，請參閱[指定端點位址](specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="8511d-112">For more information, see [Specifying an Endpoint Address](specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="8511d-113">**Binding**。</span><span class="sxs-lookup"><span data-stu-id="8511d-113">**Binding**.</span></span> <span data-ttu-id="8511d-114">繫結會指定與端點的通訊方式。</span><span class="sxs-lookup"><span data-stu-id="8511d-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="8511d-115">繫結程序會指定端點與世界的通訊方式，包括要使用的傳輸通訊協定 (例如，TCP 或 HTTP)、訊息使用的編碼 (例如，文字或二進位)，以及必要的安全性要求有哪些 (例如，Secure Sockets Layer [SSL] 或 SOAP 訊息安全性)。</span><span class="sxs-lookup"><span data-stu-id="8511d-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="8511d-116">如需詳細資訊，請參閱使用系結[來設定服務和用戶端](using-bindings-to-configure-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="8511d-116">For more information, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

- <span data-ttu-id="8511d-117">**服務合約**。</span><span class="sxs-lookup"><span data-stu-id="8511d-117">**Service contract**.</span></span> <span data-ttu-id="8511d-118">服務合約會概略說明端點公開哪些功能給用戶端。</span><span class="sxs-lookup"><span data-stu-id="8511d-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="8511d-119">合約指定了用戶端可以呼叫的作業、訊息格式與輸入參數型別或是呼叫作業時必要的資料，以及用戶端能夠預期的處理或回應訊息類型。</span><span class="sxs-lookup"><span data-stu-id="8511d-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="8511d-120">三種基本合約型別都對應至基本的訊息交換模式 (MEP)：資料包 (單向)、要求/回覆，與雙工 (雙向)。</span><span class="sxs-lookup"><span data-stu-id="8511d-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="8511d-121">當服務合約遭到存取，也能使用資料與訊息合約來要求特定資料類型與訊息格式。</span><span class="sxs-lookup"><span data-stu-id="8511d-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="8511d-122">如需如何定義服務合約的詳細資訊，請參閱[設計服務](designing-service-contracts.md)合約。</span><span class="sxs-lookup"><span data-stu-id="8511d-122">For more information about how to define a service contract, see [Designing Service Contracts](designing-service-contracts.md).</span></span> <span data-ttu-id="8511d-123">請注意，用戶端可能也會被要求實作服務定義合約 (稱為回呼合約)，以便在雙工 MEP 中從服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="8511d-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="8511d-124">如需詳細資訊，請參閱[雙工服務](./feature-details/duplex-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8511d-124">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>

<span data-ttu-id="8511d-125">您可以透過命令式程式碼或是宣告式組態來指定服務端點。</span><span class="sxs-lookup"><span data-stu-id="8511d-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="8511d-126">如果沒有指定端點，則執行階段會針對服務所實作的每個服務合約，為每個基底位址加入一個預設端點，藉以提供預設端點。</span><span class="sxs-lookup"><span data-stu-id="8511d-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="8511d-127">在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。</span><span class="sxs-lookup"><span data-stu-id="8511d-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="8511d-128">一般來說，透過組態來定義服務端點會比透過程式碼來得實際一些。</span><span class="sxs-lookup"><span data-stu-id="8511d-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="8511d-129">將繫結和位址資訊留在程式碼外面可讓它們直接進行變更，而不需要重新編譯或重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="8511d-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>

> [!NOTE]
> <span data-ttu-id="8511d-130">在新增可執行模擬服務端點時，您必須使用其中一個 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法或是 <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> 方法，將合約適當地載入新的 <xref:System.ServiceModel.Description.ServiceDescription> 物件中。</span><span class="sxs-lookup"><span data-stu-id="8511d-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>

## <a name="defining-endpoints-in-code"></a><span data-ttu-id="8511d-131">在程式碼中定義端點</span><span class="sxs-lookup"><span data-stu-id="8511d-131">Defining Endpoints in Code</span></span>

<span data-ttu-id="8511d-132">下列範例將說明如何使用下列各項在程式碼中指定端點：</span><span class="sxs-lookup"><span data-stu-id="8511d-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>

- <span data-ttu-id="8511d-133">定義 `IEcho` 類型服務的合約，以接受具有回應 "Hello \<name >！" 的某人名稱和 echo。</span><span class="sxs-lookup"><span data-stu-id="8511d-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>

- <span data-ttu-id="8511d-134">實作由 `Echo` 合約定義的 `IEcho` 服務型別。</span><span class="sxs-lookup"><span data-stu-id="8511d-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>

- <span data-ttu-id="8511d-135">指定服務 `http://localhost:8000/Echo` 的端點位址。</span><span class="sxs-lookup"><span data-stu-id="8511d-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>

- <span data-ttu-id="8511d-136">使用 `Echo` 繫結來設定 <xref:System.ServiceModel.WSHttpBinding> 服務。</span><span class="sxs-lookup"><span data-stu-id="8511d-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Use a predefined WSHttpBinding to configure the service.
          WSHttpBinding binding = new WSHttpBinding();

          // Add the endpoint for this service to the service host.
          serviceHost.AddServiceEndpoint(
             typeof(IEcho),
             binding,
             echoUri
           );

          // Open the service host to run it.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Create a ServiceHost for the Echo service.
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)

' Use a predefined WSHttpBinding to configure the service.
Dim binding As New WSHttpBinding()

' Add the endpoint for this service to the service host.
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)

' Open the service host to run it.
serviceHost.Open()
```

> [!NOTE]
> <span data-ttu-id="8511d-137">使用基底位址建立服務主機，然後將相對於基底位址的其餘位址指定為端點的一部分。</span><span class="sxs-lookup"><span data-stu-id="8511d-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="8511d-138">這種位址分割方式可讓您更方便地針對主機上的服務定義多個端點。</span><span class="sxs-lookup"><span data-stu-id="8511d-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>

> [!NOTE]
> <span data-ttu-id="8511d-139">服務應用程式中的 <xref:System.ServiceModel.Description.ServiceDescription> 屬性不得在 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 上的 <xref:System.ServiceModel.ServiceHostBase> 方法之後修改。</span><span class="sxs-lookup"><span data-stu-id="8511d-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="8511d-140">一些成員，像是 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 屬性及 `AddServiceEndpoint` 與 <xref:System.ServiceModel.ServiceHostBase> 上的 <xref:System.ServiceModel.ServiceHost> 方法，如果在通過該點之後修改，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8511d-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="8511d-141">其他成員可讓您加以修改，但結果仍未定義。</span><span class="sxs-lookup"><span data-stu-id="8511d-141">Others permit you to modify them, but the result is undefined.</span></span>
>
> <span data-ttu-id="8511d-142">同樣地，您不可以在呼叫 <xref:System.ServiceModel.Description.ServiceEndpoint> 上的 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 之後修改用戶端上的 <xref:System.ServiceModel.ChannelFactory> 值。</span><span class="sxs-lookup"><span data-stu-id="8511d-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="8511d-143"><xref:System.ServiceModel.ChannelFactory.Credentials%2A> 屬性如果在通過該點之後修改，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8511d-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="8511d-144">其他的用戶端說明值可以修改而不會造成錯誤，但是結果仍為未定義。</span><span class="sxs-lookup"><span data-stu-id="8511d-144">The other client description values can be modified without error, but the result is undefined.</span></span>
>
> <span data-ttu-id="8511d-145">無論是在服務或是用戶端，建議的做法都是在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前修改說明。</span><span class="sxs-lookup"><span data-stu-id="8511d-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>

## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="8511d-146">在組態中定義端點</span><span class="sxs-lookup"><span data-stu-id="8511d-146">Defining Endpoints in Configuration</span></span>

<span data-ttu-id="8511d-147">建立應用程式時，您經常會想要延遲負責部署應用程式之系統管理員的決定。</span><span class="sxs-lookup"><span data-stu-id="8511d-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="8511d-148">例如，經常無法預先得知服務位址 (URI) 會是怎樣。</span><span class="sxs-lookup"><span data-stu-id="8511d-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="8511d-149">這時候，為位址進行硬式編碼並不是理想的作法，較好的作法是讓系統管理員在建立服務後再處理。</span><span class="sxs-lookup"><span data-stu-id="8511d-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="8511d-150">這樣的靈活性是透過組態達成。</span><span class="sxs-lookup"><span data-stu-id="8511d-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="8511d-151">如需詳細資訊，請參閱設定[服務](configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8511d-151">For details, see [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8511d-152">使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](servicemodel-metadata-utility-tool-svcutil-exe.md)搭配 `/config:`*filename* `[,`*filename* `]` 參數，以快速建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="8511d-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>

## <a name="using-default-endpoints"></a><span data-ttu-id="8511d-153">使用預設端點</span><span class="sxs-lookup"><span data-stu-id="8511d-153">Using Default Endpoints</span></span>

<span data-ttu-id="8511d-154">如果在程式碼或組態中沒有指定端點，則執行階段會針對服務所實作的每個服務合約，為每個基底位址加入一個預設端點，藉以提供預設端點。</span><span class="sxs-lookup"><span data-stu-id="8511d-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="8511d-155">基底位址可以在程式碼或組態中指定，而預設端點則會在 <xref:System.ServiceModel.ICommunicationObject.Open> 上呼叫 <xref:System.ServiceModel.ServiceHost> 時加入。</span><span class="sxs-lookup"><span data-stu-id="8511d-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="8511d-156">這個範例和上一節的範例相同，但是因為沒有指定端點，所以會加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="8511d-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Open the service host to run it. Default endpoints
          // are added when the service is opened.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Open the service host to run it. Default endpoints
' are added when the service is opened.
serviceHost.Open()
```

 <span data-ttu-id="8511d-157">如果沒有明確提供端點，在呼叫 <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> 之前，仍可藉由在 <xref:System.ServiceModel.ServiceHost> 上呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 來加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="8511d-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="8511d-158">如需預設端點的詳細資訊，請參閱[簡化](simplified-configuration.md)的設定和[WCF 服務的簡化](./samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="8511d-158">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8511d-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="8511d-159">See also</span></span>

- [<span data-ttu-id="8511d-160">履行服務合約</span><span class="sxs-lookup"><span data-stu-id="8511d-160">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
