---
title: 偵錯 Windows 驗證錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: 45e4926905bbf3b5a24af15de153afc7bd2a4823
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964561"
---
# <a name="debugging-windows-authentication-errors"></a><span data-ttu-id="42fd8-102">偵錯 Windows 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="42fd8-102">Debugging Windows Authentication Errors</span></span>
<span data-ttu-id="42fd8-103">當使用 Windows 驗證做為安全性機制時，安全性支援提供者介面 (SSPI) 便會處理安全性程序。</span><span class="sxs-lookup"><span data-stu-id="42fd8-103">When using Windows authentication as a security mechanism, the Security Support Provider Interface (SSPI) handles security processes.</span></span> <span data-ttu-id="42fd8-104">當 SSPI 層發生安全性錯誤時，它們會由 Windows Communication Foundation （WCF）來呈現。</span><span class="sxs-lookup"><span data-stu-id="42fd8-104">When security errors occur at the SSPI layer, they are surfaced by Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="42fd8-105">本主題會提供可協助診斷這些錯誤的架構與問題集。</span><span class="sxs-lookup"><span data-stu-id="42fd8-105">This topic provides a framework and set of questions to help diagnose the errors.</span></span>  
  
 <span data-ttu-id="42fd8-106">如需 Kerberos 通訊協定的總覽，請參閱[Kerberos 說明](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10));如需 SSPI 的總覽，請參閱[sspi](/windows/win32/secauthn/sspi)。</span><span class="sxs-lookup"><span data-stu-id="42fd8-106">For an overview of the Kerberos protocol, see [Kerberos Explained](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10)); for an overview of SSPI, see [SSPI](/windows/win32/secauthn/sspi).</span></span>  
  
 <span data-ttu-id="42fd8-107">對於 Windows 驗證，WCF 通常會使用*Negotiate*安全性支援提供者（SSP），這會在用戶端和服務之間執行 Kerberos 相互驗證。</span><span class="sxs-lookup"><span data-stu-id="42fd8-107">For Windows authentication, WCF typically uses the *Negotiate* Security Support Provider (SSP), which performs Kerberos mutual authentication between the client and service.</span></span> <span data-ttu-id="42fd8-108">如果 Kerberos 通訊協定無法使用，依預設，WCF 會回到 NT LAN Manager （NTLM）。</span><span class="sxs-lookup"><span data-stu-id="42fd8-108">If the Kerberos protocol is not available, by default WCF falls back to NT LAN Manager (NTLM).</span></span> <span data-ttu-id="42fd8-109">不過，您可以將 WCF 設定為僅使用 Kerberos 通訊協定（並在無法使用 Kerberos 的情況下擲回例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="42fd8-109">However, you can configure WCF to use only the Kerberos protocol (and to throw an exception if Kerberos is not available).</span></span> <span data-ttu-id="42fd8-110">您也可以設定 WCF 使用 Kerberos 通訊協定的受限形式。</span><span class="sxs-lookup"><span data-stu-id="42fd8-110">You can also configure WCF to use restricted forms of the Kerberos protocol.</span></span>  
  
## <a name="debugging-methodology"></a><span data-ttu-id="42fd8-111">偵錯方法</span><span class="sxs-lookup"><span data-stu-id="42fd8-111">Debugging Methodology</span></span>  
 <span data-ttu-id="42fd8-112">下面列出基本的方法：</span><span class="sxs-lookup"><span data-stu-id="42fd8-112">The basic method is as follows:</span></span>  
  
1. <span data-ttu-id="42fd8-113">判斷您是否在使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="42fd8-113">Determine whether you are using Windows authentication.</span></span> <span data-ttu-id="42fd8-114">如果您是使用其他任何配置，這個主題就不適用。</span><span class="sxs-lookup"><span data-stu-id="42fd8-114">If you are using any other scheme, this topic does not apply.</span></span>  
  
2. <span data-ttu-id="42fd8-115">如果您確定使用的是 Windows 驗證，請判斷您的 WCF 設定是否使用 Kerberos direct 或 Negotiate。</span><span class="sxs-lookup"><span data-stu-id="42fd8-115">If you are sure you are using Windows authentication, determine whether your WCF configuration uses Kerberos direct or Negotiate.</span></span>  
  
3. <span data-ttu-id="42fd8-116">判斷出您的組態是使用 Kerberos 通訊協定或 NTLM 之後，您就能夠了解在正確環境中的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="42fd8-116">Once you have determined whether your configuration is using the Kerberos protocol or NTLM, you can understand error messages in the correct context.</span></span>  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a><span data-ttu-id="42fd8-117">Kerberos 通訊協定與 NTLM 的可用性</span><span class="sxs-lookup"><span data-stu-id="42fd8-117">Availability of the Kerberos Protocol and NTLM</span></span>  
 <span data-ttu-id="42fd8-118">Kerberos SSP 需要網域控制站擔任 Kerberos 金鑰發佈中心 (KDC)。</span><span class="sxs-lookup"><span data-stu-id="42fd8-118">The Kerberos SSP requires a domain controller to act as the Kerberos Key Distribution Center (KDC).</span></span> <span data-ttu-id="42fd8-119">唯有當用戶端與服務都使用網域識別時，才可以使用 Kerberos 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="42fd8-119">The Kerberos protocol is available only when both the client and service are using domain identities.</span></span> <span data-ttu-id="42fd8-120">在其他帳戶組合中則是使用 NTLM，如下表摘要所示。</span><span class="sxs-lookup"><span data-stu-id="42fd8-120">In other account combinations, NTLM is used, as summarized in the following table.</span></span>  
  
 <span data-ttu-id="42fd8-121">表格標頭會顯示伺服器可能使用的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="42fd8-121">The table headers show possible account types used by the server.</span></span> <span data-ttu-id="42fd8-122">左欄則顯示用戶端可能使用的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="42fd8-122">The left column shows possible account types used by the client.</span></span>  
  
||<span data-ttu-id="42fd8-123">本機使用者</span><span class="sxs-lookup"><span data-stu-id="42fd8-123">Local User</span></span>|<span data-ttu-id="42fd8-124">Local System (本機系統)</span><span class="sxs-lookup"><span data-stu-id="42fd8-124">Local System</span></span>|<span data-ttu-id="42fd8-125">網域使用者</span><span class="sxs-lookup"><span data-stu-id="42fd8-125">Domain User</span></span>|<span data-ttu-id="42fd8-126">網域電腦</span><span class="sxs-lookup"><span data-stu-id="42fd8-126">Domain Machine</span></span>|  
|-|----------------|------------------|-----------------|--------------------|  
|<span data-ttu-id="42fd8-127">本機使用者</span><span class="sxs-lookup"><span data-stu-id="42fd8-127">Local User</span></span>|<span data-ttu-id="42fd8-128">NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-128">NTLM</span></span>|<span data-ttu-id="42fd8-129">NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-129">NTLM</span></span>|<span data-ttu-id="42fd8-130">NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-130">NTLM</span></span>|<span data-ttu-id="42fd8-131">NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-131">NTLM</span></span>|  
|<span data-ttu-id="42fd8-132">Local System (本機系統)</span><span class="sxs-lookup"><span data-stu-id="42fd8-132">Local System</span></span>|<span data-ttu-id="42fd8-133">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-133">Anonymous NTLM</span></span>|<span data-ttu-id="42fd8-134">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-134">Anonymous NTLM</span></span>|<span data-ttu-id="42fd8-135">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-135">Anonymous NTLM</span></span>|<span data-ttu-id="42fd8-136">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-136">Anonymous NTLM</span></span>|  
|<span data-ttu-id="42fd8-137">網域使用者</span><span class="sxs-lookup"><span data-stu-id="42fd8-137">Domain User</span></span>|<span data-ttu-id="42fd8-138">NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-138">NTLM</span></span>|<span data-ttu-id="42fd8-139">NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-139">NTLM</span></span>|<span data-ttu-id="42fd8-140">Kerberos</span><span class="sxs-lookup"><span data-stu-id="42fd8-140">Kerberos</span></span>|<span data-ttu-id="42fd8-141">Kerberos</span><span class="sxs-lookup"><span data-stu-id="42fd8-141">Kerberos</span></span>|  
|<span data-ttu-id="42fd8-142">網域電腦</span><span class="sxs-lookup"><span data-stu-id="42fd8-142">Domain Machine</span></span>|<span data-ttu-id="42fd8-143">NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-143">NTLM</span></span>|<span data-ttu-id="42fd8-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="42fd8-144">NTLM</span></span>|<span data-ttu-id="42fd8-145">Kerberos</span><span class="sxs-lookup"><span data-stu-id="42fd8-145">Kerberos</span></span>|<span data-ttu-id="42fd8-146">Kerberos</span><span class="sxs-lookup"><span data-stu-id="42fd8-146">Kerberos</span></span>|  
  
 <span data-ttu-id="42fd8-147">具體而言，這四種帳戶類型包括：</span><span class="sxs-lookup"><span data-stu-id="42fd8-147">Specifically, the four account types include:</span></span>  
  
- <span data-ttu-id="42fd8-148">本機使用者：僅限電腦的使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="42fd8-148">Local User: Machine-only user profile.</span></span> <span data-ttu-id="42fd8-149">例如：`MachineName\Administrator` 或 `MachineName\ProfileName`。</span><span class="sxs-lookup"><span data-stu-id="42fd8-149">For example: `MachineName\Administrator` or `MachineName\ProfileName`.</span></span>  
  
- <span data-ttu-id="42fd8-150">本機系統：未加入網域之電腦上的內建帳戶 SYSTEM。</span><span class="sxs-lookup"><span data-stu-id="42fd8-150">Local System: The built-in account SYSTEM on a machine that is not joined to a domain.</span></span>  
  
- <span data-ttu-id="42fd8-151">網域使用者：Windows 網域上的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="42fd8-151">Domain User: A user account on a Windows domain.</span></span> <span data-ttu-id="42fd8-152">例如：`DomainName\ProfileName`。</span><span class="sxs-lookup"><span data-stu-id="42fd8-152">For example: `DomainName\ProfileName`.</span></span>  
  
- <span data-ttu-id="42fd8-153">網域電腦：處理序，其具有執行於已加入 Windows 網域之電腦的電腦身分識別。</span><span class="sxs-lookup"><span data-stu-id="42fd8-153">Domain Machine: A process with machine identity running on a machine joined to a Windows domain.</span></span> <span data-ttu-id="42fd8-154">例如：`MachineName\Network Service`。</span><span class="sxs-lookup"><span data-stu-id="42fd8-154">For example: `MachineName\Network Service`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42fd8-155">當呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 類別的 <xref:System.ServiceModel.ServiceHost> 方法時，便會擷取服務認證。</span><span class="sxs-lookup"><span data-stu-id="42fd8-155">The service credential is captured when the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method of the <xref:System.ServiceModel.ServiceHost> class is called.</span></span> <span data-ttu-id="42fd8-156">每當用戶端傳送訊息時就會讀取此用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="42fd8-156">The client credential is read whenever the client sends a message.</span></span>  
  
## <a name="common-windows-authentication-problems"></a><span data-ttu-id="42fd8-157">常見 Windows 驗證問題</span><span class="sxs-lookup"><span data-stu-id="42fd8-157">Common Windows Authentication Problems</span></span>  
 <span data-ttu-id="42fd8-158">本節會討論一些常見的 Windows 驗證問題以及可能的補救方法。</span><span class="sxs-lookup"><span data-stu-id="42fd8-158">This section discusses some common Windows authentication problems and possible remedies.</span></span>  
  
### <a name="kerberos-protocol"></a><span data-ttu-id="42fd8-159">Kerberos 通訊協定</span><span class="sxs-lookup"><span data-stu-id="42fd8-159">Kerberos Protocol</span></span>  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a><span data-ttu-id="42fd8-160">Kerberos 通訊協定的 SPN/UPN 問題</span><span class="sxs-lookup"><span data-stu-id="42fd8-160">SPN/UPN Problems with the Kerberos Protocol</span></span>  
 <span data-ttu-id="42fd8-161">當使用 Windows 驗證，而且 SSPI 有使用或交涉 Kerberos 通訊協定時，用戶端端點所使用的 URL 就必須包含在服務 URL 內之服務主機的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="42fd8-161">When using Windows authentication, and the Kerberos protocol is used or negotiated by SSPI, the URL the client endpoint uses must include the fully qualified domain name of the service's host inside the service URL.</span></span> <span data-ttu-id="42fd8-162">這假設用來執行服務的帳戶具有電腦（預設）服務主體名稱（SPN）金鑰的存取權，這是在電腦新增至 Active Directory 網域時所建立的，最常見的作法是在Network Service 帳戶。</span><span class="sxs-lookup"><span data-stu-id="42fd8-162">This assumes that the account under which the service is running has access to the machine (default) service principal name (SPN) key that is created when the computer is added to the Active Directory domain, which is most commonly done by running the service under the Network Service account.</span></span> <span data-ttu-id="42fd8-163">如果服務無法存取電腦 SPN 金鑰，您就必須在用戶端端點身分識別中，提供用來執行服務之帳戶的正確 SPN 或使用者主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="42fd8-163">If the service does not have access to the machine SPN key, you must supply the correct SPN or user principal name (UPN) of the account under which the service is running in the client's endpoint identity.</span></span> <span data-ttu-id="42fd8-164">如需 WCF 如何與 SPN 和 UPN 搭配運作的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="42fd8-164">For more information about how WCF works with SPN and UPN, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="42fd8-165">在負載平衡的使用案例 (例如 Web 伺服陣列與 Web 處理序區) 中，常見的作法是為每一個應用程式定義一個唯一的帳戶、指派一個 SPN 給該帳戶，並且確保應用程式的所有服務都以該帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="42fd8-165">In load-balancing scenarios, such as Web farms or Web gardens, a common practice is to define a unique account for each application, assign an SPN to that account, and ensure that all of the application's services run in that account.</span></span>  
  
 <span data-ttu-id="42fd8-166">如果您要取得服務帳戶的 SPN，您必須是 Active Directory 網域的管理員。</span><span class="sxs-lookup"><span data-stu-id="42fd8-166">To obtain an SPN for your service's account, you need to be an Active Directory domain administrator.</span></span> <span data-ttu-id="42fd8-167">如需詳細資訊，請參閱[Windows 的 Kerberos 技術補充](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="42fd8-167">For more information, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span>  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a><span data-ttu-id="42fd8-168">Kerberos 通訊協定 Direct 要求使用網域電腦帳戶來執行服務。</span><span class="sxs-lookup"><span data-stu-id="42fd8-168">Kerberos Protocol Direct Requires the Service to Run Under a Domain Machine Account</span></span>  
 <span data-ttu-id="42fd8-169">當 `ClientCredentialType` 屬性設定為 `Windows`，而且 <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> 屬性設定為 `false` 時，便會發生這種情況，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="42fd8-169">This occurs when the `ClientCredentialType` property is set to `Windows` and the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> property is set to `false`, as shown in the following code.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 <span data-ttu-id="42fd8-170">若要修正此問題，請使用網域電腦帳戶來執行服務，例如，在加入網域之電腦上的 Network Service 帳戶。</span><span class="sxs-lookup"><span data-stu-id="42fd8-170">To remedy, run the service using a Domain Machine account, such as Network Service, on a domain joined machine.</span></span>  
  
### <a name="delegation-requires-credential-negotiation"></a><span data-ttu-id="42fd8-171">委派需要認證交涉</span><span class="sxs-lookup"><span data-stu-id="42fd8-171">Delegation Requires Credential Negotiation</span></span>  
 <span data-ttu-id="42fd8-172">若要將 Kerberos 驗證通訊協定與委派搭配使用，您必須實作具有認證交涉的 Kerberos 通訊協定 (有時也稱做「多支線」(Multi-leg) 或「多步驟」(Multi-step) Kerberos)。</span><span class="sxs-lookup"><span data-stu-id="42fd8-172">To use the Kerberos authentication protocol with delegation, you must implement the Kerberos protocol with credential negotiation (sometimes called "multi-leg" or "multi-step" Kerberos).</span></span> <span data-ttu-id="42fd8-173">如果您實作不具有認證交涉的 Kerberos 驗證 (有時也稱做「單次」(One-shot) 或「單支線」(Single-leg) Kerberos)，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42fd8-173">If you implement Kerberos authentication without credential negotiation (sometimes called "one-shot" or "single-leg" Kerberos), an exception will be thrown.</span></span>  
  
 <span data-ttu-id="42fd8-174">若要實作具有認證交涉的 Kerberos，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="42fd8-174">To implement Kerberos with credential negotiation, do the following steps:</span></span>  
  
1. <span data-ttu-id="42fd8-175">將 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> 以實作委派。</span><span class="sxs-lookup"><span data-stu-id="42fd8-175">Implement delegation by setting <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> to <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span>  
  
2. <span data-ttu-id="42fd8-176">要求 SSPI 交涉：</span><span class="sxs-lookup"><span data-stu-id="42fd8-176">Require SSPI negotiation:</span></span>  
  
    1. <span data-ttu-id="42fd8-177">如果您是使用標準繫結，請將 `NegotiateServiceCredential` 屬性 (Property) 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="42fd8-177">If you are using standard bindings, set the `NegotiateServiceCredential` property to `true`.</span></span>  
  
    2. <span data-ttu-id="42fd8-178">如果您是使用自訂繫結，請將 `AuthenticationMode` 項目的 `Security` 屬性 (Attribute) 設定為 `SspiNegotiated`。</span><span class="sxs-lookup"><span data-stu-id="42fd8-178">If you are using custom bindings, set the `AuthenticationMode` attribute of the `Security` element to `SspiNegotiated`.</span></span>  
  
3. <span data-ttu-id="42fd8-179">透過拒絕使用 NTLM 來要求 SSPI 交涉使用 Kerberos：</span><span class="sxs-lookup"><span data-stu-id="42fd8-179">Require the SSPI negotiation to use Kerberos by disallowing the use of NTLM:</span></span>  
  
    1. <span data-ttu-id="42fd8-180">在程式碼中使用下列陳述式來做到這點：`ChannelFactory.Credentials.Windows.AllowNtlm = false`</span><span class="sxs-lookup"><span data-stu-id="42fd8-180">Do this in code, with the following statement: `ChannelFactory.Credentials.Windows.AllowNtlm = false`</span></span>  
  
    2. <span data-ttu-id="42fd8-181">或者，您可以將組態檔中的 `allowNtlm` 屬性設定為 `false` 來做到這點。</span><span class="sxs-lookup"><span data-stu-id="42fd8-181">Or you can do this in the configuration file by setting the `allowNtlm` attribute to `false`.</span></span> <span data-ttu-id="42fd8-182">這個屬性包含在\<的[windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)中。</span><span class="sxs-lookup"><span data-stu-id="42fd8-182">This attribute is contained in the [\<windows>](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).</span></span>  
  
### <a name="ntlm-protocol"></a><span data-ttu-id="42fd8-183">NTLM 通訊協定</span><span class="sxs-lookup"><span data-stu-id="42fd8-183">NTLM Protocol</span></span>  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a><span data-ttu-id="42fd8-184">交涉 SSP 退而使用 NTLM，但是 NTLM 已停用</span><span class="sxs-lookup"><span data-stu-id="42fd8-184">Negotiate SSP Falls Back to NTLM, but NTLM Is Disabled</span></span>  
 <span data-ttu-id="42fd8-185">[<xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>] 屬性會設定為 [`false`]，這會導致 Windows Communication Foundation （WCF）在使用 NTLM 時，盡力擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42fd8-185">The <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> property is set to `false`, which causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="42fd8-186">請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。</span><span class="sxs-lookup"><span data-stu-id="42fd8-186">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>  
  
 <span data-ttu-id="42fd8-187">下列程式碼示範如何停用退回使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="42fd8-187">The following shows how to disable fallback to NTLM.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a><span data-ttu-id="42fd8-188">NTLM 登入失敗</span><span class="sxs-lookup"><span data-stu-id="42fd8-188">NTLM Logon Fails</span></span>  
 <span data-ttu-id="42fd8-189">用戶端認證在服務上屬於無效。</span><span class="sxs-lookup"><span data-stu-id="42fd8-189">The client credentials are not valid on the service.</span></span> <span data-ttu-id="42fd8-190">請檢查使用者名稱與密碼是否有正確設定，以及是否有對應到服務執行所在電腦所認得的帳戶。</span><span class="sxs-lookup"><span data-stu-id="42fd8-190">Check that the user name and password are correctly set and correspond to an account that is known to the computer where the service is running.</span></span> <span data-ttu-id="42fd8-191">NTLM 會使用指定的認證來登入該服務的電腦。</span><span class="sxs-lookup"><span data-stu-id="42fd8-191">NTLM uses the specified credentials to log on to the service's computer.</span></span> <span data-ttu-id="42fd8-192">儘管在用戶端執行所在電腦上的認證可能是有效的，如果該認證在服務的電腦上屬於無效，這項登入仍然會失敗。</span><span class="sxs-lookup"><span data-stu-id="42fd8-192">While the credentials may be valid on the computer where the client is running, this logon will fail if the credentials are not valid on the service's computer.</span></span>  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a><span data-ttu-id="42fd8-193">發生匿名 NTLM 登入，不過匿名登入已依預設地停用。</span><span class="sxs-lookup"><span data-stu-id="42fd8-193">Anonymous NTLM Logon Occurs, but Anonymous Logons Are Disabled by Default</span></span>  
 <span data-ttu-id="42fd8-194">當建立用戶端時，<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 屬性已設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>，但是伺服器卻已依預設地拒絕匿名登入，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="42fd8-194">When creating a client, the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property is set to <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, as shown in the following example, but by default the server disallows anonymous logons.</span></span> <span data-ttu-id="42fd8-195">這種情況的發生原因在於 <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> 類別之 <xref:System.ServiceModel.Security.WindowsServiceCredential> 屬性的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="42fd8-195">This occurs because the default value of the <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> property of the <xref:System.ServiceModel.Security.WindowsServiceCredential> class is `false`.</span></span>  
  
 <span data-ttu-id="42fd8-196">下列用戶端程式碼會嘗試啟用匿名登入 (請注意，預設屬性是 `Identification`)。</span><span class="sxs-lookup"><span data-stu-id="42fd8-196">The following client code attempts to enable anonymous logons (note that the default property is `Identification`).</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 <span data-ttu-id="42fd8-197">下列服務程式碼會變更預設值，讓伺服器允許匿名登入。</span><span class="sxs-lookup"><span data-stu-id="42fd8-197">The following service code changes the default to enable anonymous logons by the server.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 <span data-ttu-id="42fd8-198">如需模擬的詳細資訊，請參閱[委派和](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)模擬。</span><span class="sxs-lookup"><span data-stu-id="42fd8-198">For more information about impersonation, see [Delegation and Impersonation](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="42fd8-199">或者，用戶端會使用內建帳戶 SYSTEM 來執行為 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="42fd8-199">Alternatively, the client is running as a Windows service, using the built-in account SYSTEM.</span></span>  
  
### <a name="other-problems"></a><span data-ttu-id="42fd8-200">其他問題</span><span class="sxs-lookup"><span data-stu-id="42fd8-200">Other Problems</span></span>  
  
#### <a name="client-credentials-are-not-set-correctly"></a><span data-ttu-id="42fd8-201">用戶端認證沒有正確設定</span><span class="sxs-lookup"><span data-stu-id="42fd8-201">Client Credentials Are Not Set Correctly</span></span>  
 <span data-ttu-id="42fd8-202">Windows 驗證使用由 <xref:System.ServiceModel.Security.WindowsClientCredential> 類別之 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性傳回的 <xref:System.ServiceModel.ClientBase%601> 執行個體，而不是使用 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>。</span><span class="sxs-lookup"><span data-stu-id="42fd8-202">Windows authentication uses the <xref:System.ServiceModel.Security.WindowsClientCredential> instance returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class, not the <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>.</span></span> <span data-ttu-id="42fd8-203">下面舉出不正確的範例。</span><span class="sxs-lookup"><span data-stu-id="42fd8-203">The following shows an incorrect example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 <span data-ttu-id="42fd8-204">下面舉出正確的範例。</span><span class="sxs-lookup"><span data-stu-id="42fd8-204">The following shows the correct example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a><span data-ttu-id="42fd8-205">無法使用 SSPI</span><span class="sxs-lookup"><span data-stu-id="42fd8-205">SSPI Is Not Available</span></span>  
 <span data-ttu-id="42fd8-206">下列作業系統不支援做為伺服器使用的 Windows 驗證： [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition 和 Windows Vista Home edition。</span><span class="sxs-lookup"><span data-stu-id="42fd8-206">The following operating systems do not support Windows authentication when used as a server: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition, and Windows Vista Home editions.</span></span>  
  
#### <a name="developing-and-deploying-with-different-identities"></a><span data-ttu-id="42fd8-207">以不同的身分進行開發及部署</span><span class="sxs-lookup"><span data-stu-id="42fd8-207">Developing and Deploying with Different Identities</span></span>  
 <span data-ttu-id="42fd8-208">如果您在某一台電腦上開發應用程式，然後又在另一台電腦上進行部署，而且在每一台電腦上都使用不同的帳戶類型進行驗證，您可能會產生不同的行為。</span><span class="sxs-lookup"><span data-stu-id="42fd8-208">If you develop your application on one machine, and deploy on another, and use different account types to authenticate on each machine, you may experience different behavior.</span></span> <span data-ttu-id="42fd8-209">例如，假設您是使用 `SSPI Negotiated`驗證模式，在 Windows XP Pro 機器上開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="42fd8-209">For example, suppose you develop your application on a Windows XP Pro machine using the `SSPI Negotiated` authentication mode.</span></span> <span data-ttu-id="42fd8-210">您又使用本機使用者帳戶進行身分驗證，然後又使用了 NTLM 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="42fd8-210">If you use a local user account to authenticate with, then NTLM protocol will be used.</span></span> <span data-ttu-id="42fd8-211">應用程式開發完成後，您以網域帳戶先在 Windows Server 2003 機器上部署服務而後執行。</span><span class="sxs-lookup"><span data-stu-id="42fd8-211">Once the application is developed, you deploy the service to a Windows Server 2003 machine where it runs under a domain account.</span></span> <span data-ttu-id="42fd8-212">此時，用戶端將無法驗證該服務，因為用戶端使用的是 Kerberos 及網域控制站。</span><span class="sxs-lookup"><span data-stu-id="42fd8-212">At this point the client will not be able to authenticate the service because it will be using Kerberos and a domain controller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42fd8-213">請參閱</span><span class="sxs-lookup"><span data-stu-id="42fd8-213">See also</span></span>

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="42fd8-214">委派和模擬</span><span class="sxs-lookup"><span data-stu-id="42fd8-214">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [<span data-ttu-id="42fd8-215">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="42fd8-215">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
