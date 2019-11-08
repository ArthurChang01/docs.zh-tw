---
title: <transport> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: c563339e4f854cc4e60f92dd5b8c0b39112dc000
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736115"
---
# <a name="transport-of-basichttpbinding"></a>\<basicHttpBinding 的 \<傳輸 > >
定義可控制 HTTP 傳輸之驗證參數的屬性。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**傳輸 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|clientCredentialType|-指定使用 HTTP 驗證執行用戶端驗證時，所要使用的認證類型。  預設為 `None`。 此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。|  
|proxyCredentialType|-指定在透過 HTTP 使用 proxy 從網域內執行用戶端驗證時，所要使用的認證類型。 這個屬性僅適用於父 `mode` 項目的 `security` 屬性是 `Transport` 或 `TransportCredentialsOnly` 時。 此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。|  
|realm|字串，指定摘要式驗證或基本驗證的 HTTP 驗證配置所使用的領域。 預設為空字串。|  
|policyEnforcement|此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。<br /><br /> 1. 永不–永遠不會強制執行原則（已停用 [擴充保護]）。<br />2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行原則。<br />3. always –一律強制執行原則。 不支援延伸保護的用戶端將無法驗證。|  
|protectionScenario|此列舉會指定原則強制執行的保護案例。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|None|傳輸期間不會保護訊息的安全。|  
|基本|指定基本驗證。|  
|摘要|指定摘要式驗證。|  
|Ntlm|指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。|  
|Windows|指定 Windows 整合式驗證。|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|None|-傳輸期間不會保護訊息的安全。|  
|基本|指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的基本驗證。|  
|摘要|指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的摘要式驗證。|  
|Ntlm|指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。|  
|Windows|指定 Windows 整合式驗證。|  
|憑證|使用憑證執行用戶端驗證。 這個選項只有在父 `Mode` 項目的 `security` 屬性設為 Transport 時才能使用，如果該屬性設為 TransportCredentialOnly，則無法使用。|  
  
### <a name="child-elements"></a>子項目  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security >](security-of-basichttpbinding.md)|定義[\<basicHttpBinding >](basichttpbinding.md)的安全性功能。|  
  
## <a name="example"></a>範例  
 下列範例示範透過基本繫結來使用 SSL 傳輸安全性。 根據預設，基本繫結支援 HTTP 通訊。  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
