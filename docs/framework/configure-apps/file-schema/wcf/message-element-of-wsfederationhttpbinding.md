---
title: <message> 的 <wsFederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738990"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="d244b-102">\<wsFederationHttpBinding 的 \<message > 元素 ></span><span class="sxs-lookup"><span data-stu-id="d244b-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="d244b-103">定義[\<wsFederationHttpBinding >](wsfederationhttpbinding.md)的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d244b-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="d244b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d244b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d244b-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d244b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d244b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="d244b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d244b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d244b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d244b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="d244b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d244b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d244b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d244b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**訊息 >**</span><span class="sxs-lookup"><span data-stu-id="d244b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d244b-111">語法</span><span class="sxs-lookup"><span data-stu-id="d244b-111">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d244b-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d244b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d244b-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d244b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d244b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d244b-114">Attributes</span></span>  
  
|<span data-ttu-id="d244b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d244b-115">Attribute</span></span>|<span data-ttu-id="d244b-116">描述</span><span class="sxs-lookup"><span data-stu-id="d244b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d244b-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="d244b-117">algorithmSuite</span></span>|<span data-ttu-id="d244b-118">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="d244b-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="d244b-119">請參閱「algorithmSuite 屬性」表格中此屬性的有效值。</span><span class="sxs-lookup"><span data-stu-id="d244b-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="d244b-120">預設值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="d244b-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="d244b-121">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="d244b-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="d244b-122">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="d244b-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="d244b-123">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="d244b-123">issuedKeyType</span></span>|<span data-ttu-id="d244b-124">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="d244b-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="d244b-125">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="d244b-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d244b-126">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="d244b-126">-   SymmetricKey</span></span><br /><span data-ttu-id="d244b-127">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="d244b-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="d244b-128">預設為 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="d244b-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="d244b-129">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="d244b-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="d244b-130">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="d244b-130">issuedTokenType</span></span>|<span data-ttu-id="d244b-131">字串，其中包含的 URI 指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="d244b-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="d244b-132">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="d244b-132">The default is `null`.</span></span>|  
|<span data-ttu-id="d244b-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="d244b-133">negotiateServiceCredential</span></span>|<span data-ttu-id="d244b-134">布林值，指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="d244b-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="d244b-135">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="d244b-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="d244b-136">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="d244b-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="d244b-137">值</span><span class="sxs-lookup"><span data-stu-id="d244b-137">Value</span></span>|<span data-ttu-id="d244b-138">描述</span><span class="sxs-lookup"><span data-stu-id="d244b-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d244b-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="d244b-139">Basic128</span></span>|<span data-ttu-id="d244b-140">使用 Basic128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d244b-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="d244b-141">Basic192</span></span>|<span data-ttu-id="d244b-142">使用 Basic192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d244b-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="d244b-143">Basic256</span></span>|<span data-ttu-id="d244b-144">使用 Basic256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d244b-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d244b-145">Basic256Rsa15</span></span>|<span data-ttu-id="d244b-146">將 Basic256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d244b-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="d244b-147">Basic192Rsa15</span></span>|<span data-ttu-id="d244b-148">將 Basic192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d244b-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="d244b-149">TripleDes</span></span>|<span data-ttu-id="d244b-150">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d244b-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="d244b-151">Basic128Rsa15</span></span>|<span data-ttu-id="d244b-152">將 Basic128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d244b-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="d244b-153">TripleDesRsa15</span></span>|<span data-ttu-id="d244b-154">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d244b-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="d244b-155">Basic128Sha256</span></span>|<span data-ttu-id="d244b-156">將 Basic128 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d244b-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="d244b-157">Basic192Sha256</span></span>|<span data-ttu-id="d244b-158">將 Basic192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d244b-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="d244b-159">Basic256Sha256</span></span>|<span data-ttu-id="d244b-160">將 Basic256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d244b-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="d244b-161">TripleDesSha256</span></span>|<span data-ttu-id="d244b-162">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d244b-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d244b-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="d244b-164">將 Basic128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d244b-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d244b-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="d244b-166">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d244b-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d244b-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="d244b-168">將 Basic256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d244b-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d244b-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="d244b-170">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d244b-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d244b-171">子項目</span><span class="sxs-lookup"><span data-stu-id="d244b-171">Child Elements</span></span>  
  
|<span data-ttu-id="d244b-172">項目</span><span class="sxs-lookup"><span data-stu-id="d244b-172">Element</span></span>|<span data-ttu-id="d244b-173">描述</span><span class="sxs-lookup"><span data-stu-id="d244b-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d244b-174">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d244b-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="d244b-175">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="d244b-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="d244b-176">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="d244b-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="d244b-177">issuer</span><span class="sxs-lookup"><span data-stu-id="d244b-177">issuer</span></span>|<span data-ttu-id="d244b-178">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="d244b-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="d244b-179">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="d244b-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="d244b-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="d244b-180">issuerMetadata</span></span>|<span data-ttu-id="d244b-181">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="d244b-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="d244b-182">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="d244b-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="d244b-183">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="d244b-183">A collection of token request parameters.</span></span> <span data-ttu-id="d244b-184">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="d244b-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d244b-185">父項目</span><span class="sxs-lookup"><span data-stu-id="d244b-185">Parent Elements</span></span>  
  
|<span data-ttu-id="d244b-186">項目</span><span class="sxs-lookup"><span data-stu-id="d244b-186">Element</span></span>|<span data-ttu-id="d244b-187">描述</span><span class="sxs-lookup"><span data-stu-id="d244b-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d244b-188">\<security ></span><span class="sxs-lookup"><span data-stu-id="d244b-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="d244b-189">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d244b-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d244b-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="d244b-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="d244b-191">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d244b-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d244b-192">繫結</span><span class="sxs-lookup"><span data-stu-id="d244b-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d244b-193">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d244b-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d244b-194">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="d244b-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d244b-195">\<binding ></span><span class="sxs-lookup"><span data-stu-id="d244b-195">\<binding></span></span>](bindings.md)
