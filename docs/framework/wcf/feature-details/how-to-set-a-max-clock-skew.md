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
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="3a4de-102">HOW TO：設定最大時鐘誤差</span><span class="sxs-lookup"><span data-stu-id="3a4de-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="3a4de-103">如果兩台電腦上的時鐘設定不相同，時間關鍵功能將脫離常軌。</span><span class="sxs-lookup"><span data-stu-id="3a4de-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="3a4de-104">若要降低這種可能性，您可以將 `MaxClockSkew` 屬性設定為 <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="3a4de-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="3a4de-105">此屬性可在兩種類別上使用：</span><span class="sxs-lookup"><span data-stu-id="3a4de-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a4de-106">針對安全對話，當啟動服務或用戶端時，必須對 `MaxClockSkew` 屬性進行變更。</span><span class="sxs-lookup"><span data-stu-id="3a4de-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="3a4de-107">若要這樣做，您必須在 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> 屬性所傳回的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 上設定屬性。</span><span class="sxs-lookup"><span data-stu-id="3a4de-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="3a4de-108">若要變更其中一個系統提供繫結上的屬性，您必須在繫結集合中尋找安全性繫結項目，然後將 `MaxClockSkew` 屬性設定為新值。</span><span class="sxs-lookup"><span data-stu-id="3a4de-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="3a4de-109">衍生自 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的兩個類別：<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 和 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="3a4de-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="3a4de-110">從集合上擷取安全性繫結時，您必須轉換至這些型別的其中一個型別以正確設定 `MaxClockSkew` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3a4de-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="3a4de-111">下列範例使用運用 <xref:System.ServiceModel.WSHttpBinding> 的 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="3a4de-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="3a4de-112">如需指定要在每個系統提供的系結中使用哪一種安全性系結類型的清單，請參閱[系統提供](../../../../docs/framework/wcf/system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="3a4de-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="3a4de-113">若要使用程式碼中的新時鐘扭曲值立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3a4de-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="3a4de-114">在您的程式碼中加入下列命名空間的參考： <xref:System.ServiceModel.Channels>、<xref:System.ServiceModel.Description>、<xref:System.Security.Permissions>和 <xref:System.ServiceModel.Security.Tokens>。</span><span class="sxs-lookup"><span data-stu-id="3a4de-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="3a4de-115">建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將其安全性模式設定為 <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3a4de-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="3a4de-116">呼叫 <xref:System.ServiceModel.Channels.BindingElementCollection> 方法建立 <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a4de-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="3a4de-117">使用 <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> 類別的 <xref:System.ServiceModel.Channels.BindingElementCollection> 方法尋找安全性繫結項目。</span><span class="sxs-lookup"><span data-stu-id="3a4de-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="3a4de-118">使用 <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> 方法時，轉換為實際型別。</span><span class="sxs-lookup"><span data-stu-id="3a4de-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="3a4de-119">下列範例轉換為 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="3a4de-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="3a4de-120">設定安全性繫結項目上的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="3a4de-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="3a4de-121">使用適當的服務型別和基底位址建立 <xref:System.ServiceModel.ServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="3a4de-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="3a4de-122">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增端點並加入 <xref:System.ServiceModel.Channels.CustomBinding>。</span><span class="sxs-lookup"><span data-stu-id="3a4de-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="3a4de-123">若要設定組態中的 MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="3a4de-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="3a4de-124">在\<系結[>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)元素一節中建立[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3a4de-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="3a4de-125">建立\<系結[>](../../configure-apps/file-schema/wcf/bindings.md)元素，並將 `name` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="3a4de-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="3a4de-126">下列範例將它設定為 `MaxClockSkewBinding`。</span><span class="sxs-lookup"><span data-stu-id="3a4de-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="3a4de-127">新增編碼項目。</span><span class="sxs-lookup"><span data-stu-id="3a4de-127">Add an encoding element.</span></span> <span data-ttu-id="3a4de-128">下列範例會新增[\<的 textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)。</span><span class="sxs-lookup"><span data-stu-id="3a4de-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="3a4de-129">新增[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)元素，並將 `authenticationMode` 屬性設定為適當的設定。</span><span class="sxs-lookup"><span data-stu-id="3a4de-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="3a4de-130">下列範例將屬性設定為 `Kerberos` 以說明該服務使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="3a4de-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="3a4de-131">新增[\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ，並將 `maxClockSkew` 屬性設定為 `"##:##:##"`格式的值。</span><span class="sxs-lookup"><span data-stu-id="3a4de-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="3a4de-132">下列範例將它設定為 7 分鐘。</span><span class="sxs-lookup"><span data-stu-id="3a4de-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="3a4de-133">（選擇性）新增[\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ，並將 `maxClockSkew` 屬性設定為適當的設定。</span><span class="sxs-lookup"><span data-stu-id="3a4de-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="3a4de-134">新增傳輸項目。</span><span class="sxs-lookup"><span data-stu-id="3a4de-134">Add a transport element.</span></span> <span data-ttu-id="3a4de-135">下列範例會使用[\<的 HTTPTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)。</span><span class="sxs-lookup"><span data-stu-id="3a4de-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="3a4de-136">針對安全對話，安全性設定必須發生在啟動程式的[\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)元素中。</span><span class="sxs-lookup"><span data-stu-id="3a4de-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a4de-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a4de-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3a4de-138">如何：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3a4de-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
