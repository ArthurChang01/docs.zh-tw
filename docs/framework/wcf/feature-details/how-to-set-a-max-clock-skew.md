---
title: HOW TO：設定最大時鐘誤差
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 96afa61d32e1ba744c9f3dbbeeb7fb2e55157f4c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141652"
---
# <a name="how-to-set-a-max-clock-skew"></a>HOW TO：設定最大時鐘誤差
如果兩台電腦上的時鐘設定不相同，時間關鍵功能將脫離常軌。 若要降低這種可能性，您可以將 `MaxClockSkew` 屬性設定為 <xref:System.TimeSpan>。 此屬性可在兩種類別上使用：  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> 針對安全對話，當啟動服務或用戶端時，必須對 `MaxClockSkew` 屬性進行變更。 若要這樣做，您必須在 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> 屬性所傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 上設定屬性。  
  
 若要變更其中一個系統提供繫結上的屬性，您必須在繫結集合中尋找安全性繫結項目，然後將 `MaxClockSkew` 屬性設定為新值。 衍生自 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的兩個類別：<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 和 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>。 從集合上擷取安全性繫結時，您必須轉換至這些型別的其中一個型別以正確設定 `MaxClockSkew` 屬性。 下列範例使用運用 <xref:System.ServiceModel.WSHttpBinding> 的 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>。 如需指定要在每個系統提供的系結中使用哪一種安全性系結類型的清單，請參閱[系統提供](../../../../docs/framework/wcf/system-provided-bindings.md)的系結。  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>若要使用程式碼中的新時鐘扭曲值立自訂繫結  
  
> [!WARNING]
> 在您的程式碼中加入下列命名空間的參考： <xref:System.ServiceModel.Channels>、<xref:System.ServiceModel.Description>、<xref:System.Security.Permissions>和 <xref:System.ServiceModel.Security.Tokens>。  
  
1. 建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將其安全性模式設定為 <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>。  
  
2. 呼叫 <xref:System.ServiceModel.Channels.BindingElementCollection> 方法建立 <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> 類別的新執行個體。  
  
3. 使用 <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> 類別的 <xref:System.ServiceModel.Channels.BindingElementCollection> 方法尋找安全性繫結項目。  
  
4. 使用 <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> 方法時，轉換為實際型別。 下列範例轉換為 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 型別。  
  
5. 設定安全性繫結項目上的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> 屬性。  
  
6. 使用適當的服務型別和基底位址建立 <xref:System.ServiceModel.ServiceHost>。  
  
7. 使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增端點並加入 <xref:System.ServiceModel.Channels.CustomBinding>。  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>若要設定組態中的 MaxClockSkew  
  
1. 在\<系結[>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)元素一節中建立[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) 。  
  
2. 建立\<系結[>](../../configure-apps/file-schema/wcf/bindings.md)元素，並將 `name` 屬性設定為適當的值。 下列範例將它設定為 `MaxClockSkewBinding`。  
  
3. 新增編碼項目。 下列範例會新增[\<的 textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)。  
  
4. 新增[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素，並將 `authenticationMode` 屬性設定為適當的設定。 下列範例將屬性設定為 `Kerberos` 以說明該服務使用 Windows 驗證。  
  
5. 新增[\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ，並將 `maxClockSkew` 屬性設定為 `"##:##:##"`格式的值。 下列範例將它設定為 7 分鐘。 （選擇性）新增[\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ，並將 `maxClockSkew` 屬性設定為適當的設定。  
  
6. 新增傳輸項目。 下列範例會使用[\<的 HTTPTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)。  
  
7. 針對安全對話，安全性設定必須發生在啟動程式的[\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)元素中。  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [如何：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
