---
title: <transport> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 28c8c877a766e0d881dd04f27298fae332bf08f8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736030"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="ce303-102">\<msmqIntegrationBinding 的 \<傳輸 > ></span><span class="sxs-lookup"><span data-stu-id="ce303-102">\<transport> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="ce303-103">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ce303-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
<span data-ttu-id="ce303-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce303-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ce303-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ce303-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ce303-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="ce303-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ce303-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<msmqIntegrationBinding >** ](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ce303-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="ce303-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="ce303-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ce303-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ce303-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="ce303-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="ce303-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce303-111">語法</span><span class="sxs-lookup"><span data-stu-id="ce303-111">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce303-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ce303-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ce303-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="ce303-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce303-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ce303-114">Attributes</span></span>  
  
|<span data-ttu-id="ce303-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ce303-115">Attribute</span></span>|<span data-ttu-id="ce303-116">描述</span><span class="sxs-lookup"><span data-stu-id="ce303-116">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="ce303-117">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="ce303-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="ce303-118">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="ce303-118">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="ce303-119">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ce303-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ce303-120">-None：不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="ce303-120">-   None: No authentication.</span></span><br /><span data-ttu-id="ce303-121">-WindowsDomain：驗證機制會使用 Active Directory 來取得與訊息相關聯之 SID 的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="ce303-121">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="ce303-122">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="ce303-122">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="ce303-123">-Certificate：通道會從憑證存放區取得憑證。</span><span class="sxs-lookup"><span data-stu-id="ce303-123">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="ce303-124">預設值為 WindowsDomain。</span><span class="sxs-lookup"><span data-stu-id="ce303-124">The default value is WindowsDomain.</span></span> <span data-ttu-id="ce303-125">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="ce303-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="ce303-126">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="ce303-126">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="ce303-127">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ce303-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ce303-128">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="ce303-128">-   RC4Stream</span></span><br /><span data-ttu-id="ce303-129">-AES</span><span class="sxs-lookup"><span data-stu-id="ce303-129">-   AES</span></span><br /><br /> <span data-ttu-id="ce303-130">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="ce303-130">The default value is RC4Stream.</span></span> <span data-ttu-id="ce303-131">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="ce303-131">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="ce303-132">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="ce303-132">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="ce303-133">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性，也就是訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="ce303-133">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="ce303-134">-有效的值包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="ce303-134">-   Valid values include the following:</span></span><br /><span data-ttu-id="ce303-135">-None：沒有保護。</span><span class="sxs-lookup"><span data-stu-id="ce303-135">-   None: No protection.</span></span><br /><span data-ttu-id="ce303-136">-Sign：訊息已簽署。</span><span class="sxs-lookup"><span data-stu-id="ce303-136">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="ce303-137">-EncryptAndSign：訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="ce303-137">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="ce303-138">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="ce303-138">The default value is Sign.</span></span> <span data-ttu-id="ce303-139">此屬性的型別為 ProtectionLevel。</span><span class="sxs-lookup"><span data-stu-id="ce303-139">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="ce303-140">-指定要用來將摘要計算為簽章一部分的演算法。</span><span class="sxs-lookup"><span data-stu-id="ce303-140">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="ce303-141">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ce303-141">Valid values include the following:</span></span><br /><span data-ttu-id="ce303-142">-MD5</span><span class="sxs-lookup"><span data-stu-id="ce303-142">-   MD5</span></span><br /><span data-ttu-id="ce303-143">-SHA1</span><span class="sxs-lookup"><span data-stu-id="ce303-143">-   SHA1</span></span><br /><span data-ttu-id="ce303-144">-SHA256</span><span class="sxs-lookup"><span data-stu-id="ce303-144">-   SHA256</span></span><br /><span data-ttu-id="ce303-145">-SHA512</span><span class="sxs-lookup"><span data-stu-id="ce303-145">-   SHA512</span></span><br /><br /> <span data-ttu-id="ce303-146">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="ce303-146">The default value is SHA1.</span></span> <span data-ttu-id="ce303-147">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="ce303-147">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="ce303-148">由於 MD5 和 SHA1 的衝突問題，Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="ce303-148">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce303-149">子項目</span><span class="sxs-lookup"><span data-stu-id="ce303-149">Child Elements</span></span>  
 <span data-ttu-id="ce303-150">None</span><span class="sxs-lookup"><span data-stu-id="ce303-150">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce303-151">父項目</span><span class="sxs-lookup"><span data-stu-id="ce303-151">Parent Elements</span></span>  
  
|<span data-ttu-id="ce303-152">項目</span><span class="sxs-lookup"><span data-stu-id="ce303-152">Element</span></span>|<span data-ttu-id="ce303-153">描述</span><span class="sxs-lookup"><span data-stu-id="ce303-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce303-154">\<security ></span><span class="sxs-lookup"><span data-stu-id="ce303-154">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="ce303-155">定義 MSMQ 繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ce303-155">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce303-156">備註</span><span class="sxs-lookup"><span data-stu-id="ce303-156">Remarks</span></span>  
 <span data-ttu-id="ce303-157">這個項目會封裝訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ce303-157">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="ce303-158">這些設定同時適用於訊息佇列整合和已佇列之傳輸。</span><span class="sxs-lookup"><span data-stu-id="ce303-158">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="ce303-159">它還可讓您設定驗證模式、加密演算法、安全雜湊演算法和保護層級。</span><span class="sxs-lookup"><span data-stu-id="ce303-159">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce303-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce303-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="ce303-161">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ce303-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ce303-162">繫結</span><span class="sxs-lookup"><span data-stu-id="ce303-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ce303-163">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="ce303-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ce303-164">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="ce303-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ce303-165">\<binding ></span><span class="sxs-lookup"><span data-stu-id="ce303-165">\<binding></span></span>](bindings.md)
