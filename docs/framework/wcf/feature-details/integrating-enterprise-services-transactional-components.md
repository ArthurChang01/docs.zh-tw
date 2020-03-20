---
title: 整合 Enterprise Services 異動元件
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 292573f911459d8a8419e09d81fd1e54dbc6c70b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184744"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="a0188-102">整合 Enterprise Services 異動元件</span><span class="sxs-lookup"><span data-stu-id="a0188-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="a0188-103">Windows 通信基礎 （WCF） 提供了與企業服務集成的自動機制（請參閱[與 COM+ 應用程式集成](integrating-with-com-plus-applications.md)）。</span><span class="sxs-lookup"><span data-stu-id="a0188-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="a0188-104">不過，您可能希望能夠彈性地開發出可透過內部方式使用裝載於 Enterprise Services 之異動元件的服務。</span><span class="sxs-lookup"><span data-stu-id="a0188-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="a0188-105">由於 WCF 事務功能構建在<xref:System.Transactions>基礎結構上，因此將企業服務與 WCF 集成的過程與指定與企業服務之間的<xref:System.Transactions>互通性的過程相同，如[與企業服務和 COM+ 事務的互通性](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))中所述。</span><span class="sxs-lookup"><span data-stu-id="a0188-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="a0188-106">為了在傳入的流動異動和 COM+ 內容異動之間提供所需等級的互通性，此服務的實作必須建立 <xref:System.Transactions.TransactionScope> 執行個體並使用適當的 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="a0188-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="a0188-107">整合 Enterprise Services 和服務作業</span><span class="sxs-lookup"><span data-stu-id="a0188-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="a0188-108">下列程式碼範例會示範一項允許異動流程的作業，這項作業會建立具有 <xref:System.Transactions.TransactionScope> 選項的 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>。</span><span class="sxs-lookup"><span data-stu-id="a0188-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="a0188-109">下列狀況適用於本案例：</span><span class="sxs-lookup"><span data-stu-id="a0188-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="a0188-110">如果用戶端流動交易，則作業 (包括 Enterprise Services 元件的呼叫) 會在該交易的範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="a0188-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="a0188-111">使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 會確保交易與 <xref:System.EnterpriseServices> 內容為同步處理，也就是說 <xref:System.Transactions> 的環境交易和 <xref:System.EnterpriseServices> 會是相同的。</span><span class="sxs-lookup"><span data-stu-id="a0188-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="a0188-112">如果用戶端沒有流動異動，此時將 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 設定為 `true` 便會建立供作業使用的新異動範圍。</span><span class="sxs-lookup"><span data-stu-id="a0188-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="a0188-113">同樣地，使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 可確保作業的交易與 <xref:System.EnterpriseServices> 元件內容中所使用的交易是相同的。</span><span class="sxs-lookup"><span data-stu-id="a0188-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="a0188-114">任何其他的方法呼叫也會發生在相同作業的交易範圍內。</span><span class="sxs-lookup"><span data-stu-id="a0188-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services
         // component
  
         // Call UpdateOtherCustomerData method on an Enterprise
         // Services component
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 <span data-ttu-id="a0188-115">如果作業的目前交易和 Enterprise Services 交易元件的呼叫之間不需要同步處理，那麼請在初始化 <xref:System.Transactions.EnterpriseServicesInteropOption.None> 執行個體時使用 <xref:System.Transactions.TransactionScope> 選項。</span><span class="sxs-lookup"><span data-stu-id="a0188-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="a0188-116">整合 Enterprise Services 和用戶端</span><span class="sxs-lookup"><span data-stu-id="a0188-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="a0188-117">下列程式碼會示範以 <xref:System.Transactions.TransactionScope> 設定來使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 執行個體的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0188-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="a0188-118">在此案例中，支援異動流程的服務作業呼叫會發生於呼叫 Enterprise Services 元件的相同異動範圍內，</span><span class="sxs-lookup"><span data-stu-id="a0188-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services
        // component
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0188-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0188-119">See also</span></span>

- [<span data-ttu-id="a0188-120">與 COM+ 應用程式集成</span><span class="sxs-lookup"><span data-stu-id="a0188-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a0188-121">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="a0188-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
