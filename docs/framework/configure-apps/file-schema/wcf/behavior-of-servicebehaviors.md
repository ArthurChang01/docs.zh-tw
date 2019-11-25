---
title: <behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139728"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="87fbe-102">\<serviceBehaviors 的 \<行為 > ></span><span class="sxs-lookup"><span data-stu-id="87fbe-102">\<behavior> of \<serviceBehaviors></span></span>
<span data-ttu-id="87fbe-103">`behavior` 項目包含服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="87fbe-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="87fbe-104">各個行為是依其 `name` 進行索引。</span><span class="sxs-lookup"><span data-stu-id="87fbe-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="87fbe-105">服務可以透過這個名稱連結至每個行為，其方式是使用[\<端點 >](endpoint-element.md)元素的 `behaviorConfiguration` 屬性。</span><span class="sxs-lookup"><span data-stu-id="87fbe-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="87fbe-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="87fbe-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="87fbe-107">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="87fbe-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="87fbe-108">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="87fbe-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87fbe-109">Windows 工作流程活動特定的行為專案（例如[\<sendMessageChannelCache >](../windows-workflow-foundation/sendmessagechannelcache.md)元素）記載于[\<serviceBehaviors > 頁面的\<行為 >](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)中。</span><span class="sxs-lookup"><span data-stu-id="87fbe-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
<span data-ttu-id="87fbe-110">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87fbe-110">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="87fbe-111">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="87fbe-111">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="87fbe-112">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="87fbe-112">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="87fbe-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="87fbe-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="87fbe-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<行為 >**</span><span class="sxs-lookup"><span data-stu-id="87fbe-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87fbe-115">語法</span><span class="sxs-lookup"><span data-stu-id="87fbe-115">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87fbe-116">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87fbe-116">Attributes and Elements</span></span>  
 <span data-ttu-id="87fbe-117">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="87fbe-117">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87fbe-118">屬性</span><span class="sxs-lookup"><span data-stu-id="87fbe-118">Attributes</span></span>  
  
|<span data-ttu-id="87fbe-119">屬性</span><span class="sxs-lookup"><span data-stu-id="87fbe-119">Attribute</span></span>|<span data-ttu-id="87fbe-120">描述</span><span class="sxs-lookup"><span data-stu-id="87fbe-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87fbe-121">NAME</span><span class="sxs-lookup"><span data-stu-id="87fbe-121">name</span></span>|<span data-ttu-id="87fbe-122">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="87fbe-122">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="87fbe-123">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="87fbe-123">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="87fbe-124">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="87fbe-124">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="87fbe-125">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="87fbe-125">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87fbe-126">子項目</span><span class="sxs-lookup"><span data-stu-id="87fbe-126">Child Elements</span></span>  
  
|<span data-ttu-id="87fbe-127">項目</span><span class="sxs-lookup"><span data-stu-id="87fbe-127">Element</span></span>|<span data-ttu-id="87fbe-128">描述</span><span class="sxs-lookup"><span data-stu-id="87fbe-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87fbe-129">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="87fbe-129">\<dataContractSerializer></span></span>](datacontractserializer-element.md)|<span data-ttu-id="87fbe-130">包含 DataContractSerializer 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="87fbe-130">Contains configuration data for the DataContractSerializer.</span></span>|  
|[<span data-ttu-id="87fbe-131">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="87fbe-131">\<persistenceProvider></span></span>](persistenceprovider.md)|<span data-ttu-id="87fbe-132">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="87fbe-132">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[<span data-ttu-id="87fbe-133">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="87fbe-133">\<routing></span></span>](routing-of-servicebehavior.md)|<span data-ttu-id="87fbe-134">提供於執行階段存取路由服務的功能，可用來動態修改路由組態。</span><span class="sxs-lookup"><span data-stu-id="87fbe-134">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[<span data-ttu-id="87fbe-135">\<r ></span><span class="sxs-lookup"><span data-stu-id="87fbe-135">\<serviceAuthenticationManager></span></span>](serviceauthenticationmanager.md)|<span data-ttu-id="87fbe-136">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="87fbe-136">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[<span data-ttu-id="87fbe-137">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="87fbe-137">\<serviceAuthorization></span></span>](serviceauthorization-element.md)|<span data-ttu-id="87fbe-138">指定將存取權授權給服務作業的設定。</span><span class="sxs-lookup"><span data-stu-id="87fbe-138">Specifies settings that authorize access to service operations.</span></span>|  
|[<span data-ttu-id="87fbe-139">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="87fbe-139">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="87fbe-140">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="87fbe-140">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[<span data-ttu-id="87fbe-141">\<serviceDebug ></span><span class="sxs-lookup"><span data-stu-id="87fbe-141">\<serviceDebug></span></span>](servicedebug.md)|<span data-ttu-id="87fbe-142">指定 Windows Communication Foundation （WCF）服務的偵錯工具和說明資訊功能。</span><span class="sxs-lookup"><span data-stu-id="87fbe-142">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[<span data-ttu-id="87fbe-143">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="87fbe-143">\<serviceDiscovery></span></span>](servicediscovery.md)|<span data-ttu-id="87fbe-144">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="87fbe-144">Specifies the discoverability of service endpoints.</span></span>|  
|[<span data-ttu-id="87fbe-145">\<serviceMetadata ></span><span class="sxs-lookup"><span data-stu-id="87fbe-145">\<serviceMetadata></span></span>](servicemetadata.md)|<span data-ttu-id="87fbe-146">指定服務中繼資料和相關資訊的發行。</span><span class="sxs-lookup"><span data-stu-id="87fbe-146">Specifies the publication of service metadata and associated information.</span></span>|  
|[<span data-ttu-id="87fbe-147">\<serviceSecurityAudit ></span><span class="sxs-lookup"><span data-stu-id="87fbe-147">\<serviceSecurityAudit></span></span>](servicesecurityaudit.md)|<span data-ttu-id="87fbe-148">指定在服務作業期間啟用安全性事件稽核的設定。</span><span class="sxs-lookup"><span data-stu-id="87fbe-148">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[<span data-ttu-id="87fbe-149">\<serviceThrottling ></span><span class="sxs-lookup"><span data-stu-id="87fbe-149">\<serviceThrottling></span></span>](servicethrottling.md)|<span data-ttu-id="87fbe-150">指定 WCF 服務的節流機制。</span><span class="sxs-lookup"><span data-stu-id="87fbe-150">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[<span data-ttu-id="87fbe-151">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="87fbe-151">\<serviceTimeouts></span></span>](servicetimeouts.md)|<span data-ttu-id="87fbe-152">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="87fbe-152">Specifies the timeout for a service.</span></span>|  
|[<span data-ttu-id="87fbe-153">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="87fbe-153">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="87fbe-154">指定用來裝載以工作流程為基礎之 WCF 服務的 WorkflowRuntime 實例設定。</span><span class="sxs-lookup"><span data-stu-id="87fbe-154">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[<span data-ttu-id="87fbe-155">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="87fbe-155">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="87fbe-156">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="87fbe-156">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87fbe-157">父項目</span><span class="sxs-lookup"><span data-stu-id="87fbe-157">Parent Elements</span></span>  
  
|<span data-ttu-id="87fbe-158">項目</span><span class="sxs-lookup"><span data-stu-id="87fbe-158">Element</span></span>|<span data-ttu-id="87fbe-159">描述</span><span class="sxs-lookup"><span data-stu-id="87fbe-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87fbe-160">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="87fbe-160">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="87fbe-161">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="87fbe-161">A collection of service behavior elements.</span></span>|
