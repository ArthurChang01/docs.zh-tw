---
title: <clientCertificate> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: fb95ef3168378227e41e55c6fd5e5b772cb7ad0f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400510"
---
# <a name="clientcertificate-of-clientcredentials-element"></a>\<clientCredentials > 元素\<的 clientCertificate >
定義用於向服務驗證的 X.509 憑證。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientCertificate >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<clientCertificate findValue="String"
                   storeLocation="LocalMachine/CurrentUser"
                   storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                   X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`findValue`|字串，其中包含要在 X.509 憑證存放區內搜尋的值。 這個屬性所包含的型別必須滿足 `X509FindType` 屬性值的需求。 預設值是空字串。|  
|`storeLocation`|指定 X.509 憑證的位置，用戶端會使用該憑證來進行對服務的自我驗證。 有效值包括以下的值：<br /><br /> -LocalMachine：指派給本機電腦的憑證存放區。<br />-CurrentUser：指派給目前使用者的憑證存放區。<br /><br /> 預設為 LocalMachine。 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。|  
|`storeName`|指定要搜尋之 X.509 憑證存放區的名稱。 有效值包括以下的值：<br /><br /> 通訊錄其他使用者的憑證存放區。<br />AuthRoot協力廠商憑證授權單位單位（Ca）的憑證存放區。<br />CertificateAuthority中繼憑證授權單位單位（Ca）的憑證存放區。<br />禁止已撤銷憑證的憑證存放區。<br />'個人憑證的憑證存放區。<br />路徑受信任的根憑證授權單位（Ca）的憑證存放區。<br />TrustedPeople直接信任之人員和資源的憑證存放區。<br />TrustedPublisher直接信任之發行者的憑證存放區。<br /><br /> 預設為 My。 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreName>。|  
|X509FindType|定義要執行之 X.509 搜尋的類型。 `findValue` 屬性中所包含的型別必須滿足此屬性的需求。 有效值包括以下的值：<br /><br /> -FindByThumbPrint<br />-   FindBySubjectName<br />-FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />- FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> 預設值為 FindBySubjectDistinguishedName。 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509FindType>。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## <a name="remarks"></a>備註  
 這個組態項目會指定憑證，此憑證會用來驗證具有這個項目的用戶端。 如需詳細資訊，請參閱[如何：指定用戶端認證](../../../wcf/how-to-specify-client-credential-values.md)值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [如何：指定用戶端認證值](../../../wcf/how-to-specify-client-credential-values.md)
- [保護用戶端安全](../../../wcf/securing-clients.md)
- [使用憑證](../../../wcf/feature-details/working-with-certificates.md)
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
