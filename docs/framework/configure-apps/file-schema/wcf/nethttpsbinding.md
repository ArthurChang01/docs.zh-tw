---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 4e15a52603df12ea3e1332efcf707f7d0c389976
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430255"
---
# <a name="nethttpsbinding"></a><span data-ttu-id="762be-101">\<NetHTTPsbinding 設定 ></span><span class="sxs-lookup"><span data-stu-id="762be-101">\<netHttpsBinding></span></span>
<span data-ttu-id="762be-102">表示 Windows Communication Foundation （WCF）服務可用來設定和公開能夠透過 HTTPS 進行通訊之端點的系結。</span><span class="sxs-lookup"><span data-stu-id="762be-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="762be-103">與雙工合約搭配使用時，將會使用 Web 通訊端，否則使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="762be-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
<span data-ttu-id="762be-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="762be-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="762be-105">&nbsp;&nbsp;[ **\<system.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="762be-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="762be-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="762be-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="762be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netHTTPsbinding 設定 >**</span><span class="sxs-lookup"><span data-stu-id="762be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpsBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="762be-108">語法</span><span class="sxs-lookup"><span data-stu-id="762be-108">Syntax</span></span>  
  
```xml  
<netHttpsBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a><span data-ttu-id="762be-109">類型</span><span class="sxs-lookup"><span data-stu-id="762be-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="762be-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="762be-110">Attributes and Elements</span></span>  
 <span data-ttu-id="762be-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="762be-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="762be-112">屬性</span><span class="sxs-lookup"><span data-stu-id="762be-112">Attributes</span></span>  
  
|<span data-ttu-id="762be-113">屬性</span><span class="sxs-lookup"><span data-stu-id="762be-113">Attribute</span></span>|<span data-ttu-id="762be-114">描述</span><span class="sxs-lookup"><span data-stu-id="762be-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="762be-115">布林值，表示用戶端是否接受 Cookie 並在未來要求時傳播 Cookie。</span><span class="sxs-lookup"><span data-stu-id="762be-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="762be-116">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="762be-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="762be-117">當您與使用 Cookie 的 ASMX Web 服務互動時，可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="762be-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="762be-118">如此一來，從伺服器傳回的 Cookie 就一定會自動複製到該服務未來所有的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="762be-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="762be-119">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="762be-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="762be-120">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="762be-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="762be-121">如果網際網路資源有本機位址，則此資源為本機資源。</span><span class="sxs-lookup"><span data-stu-id="762be-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="762be-122">本機位址是指位於相同電腦上的本機 LAN 或內部網路，在語法上，在 Uri "http://webserver/" 和 "http://localhost/" 中缺少句點（.）。</span><span class="sxs-lookup"><span data-stu-id="762be-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="762be-123">設定這個屬性可決定以 BasicHttpBinding 設定的端點在存取本機資源時，是否使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="762be-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="762be-124">如果這個屬性為 `true`，則所有對本機網際網路資源的要求都不會使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="762be-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="762be-125">當這個屬性設定為 `true` 時，如果想要讓用戶端在與相同電腦上的服務進行交談時通過 Proxy，請使用主機名稱 (而非 localhost)。</span><span class="sxs-lookup"><span data-stu-id="762be-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="762be-126">當這個屬性設定為 `false` 時，則所有的網際網路要求都會通過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="762be-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="762be-127"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="762be-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="762be-128">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="762be-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="762be-129">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="762be-129">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="762be-130">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="762be-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="762be-131">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="762be-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="762be-132">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="762be-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="762be-133">整數值，指定配置供從通道接收訊息之訊息緩衝區管理員使用的最大記憶體量。</span><span class="sxs-lookup"><span data-stu-id="762be-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="762be-134">預設值為 524288 (0x80000) 位元組。</span><span class="sxs-lookup"><span data-stu-id="762be-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="762be-135">緩衝區管理員會利用緩衝區集區，將使用緩衝區的成本降至最低。</span><span class="sxs-lookup"><span data-stu-id="762be-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="762be-136">當訊息從通道送出時，服務將需要緩衝區來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="762be-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="762be-137">如果緩衝區集區中沒有足夠的記憶體可以處理訊息負載，緩衝區管理員就必須從 CLR 堆積配置額外的記憶體，進而增加記憶體回收負荷。</span><span class="sxs-lookup"><span data-stu-id="762be-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="762be-138">從 CLR 記憶體回收堆積所產生的大量配置表示緩衝區集區太小，而提高這個屬性指定的限制來提供較大的配置，便可改善效能。</span><span class="sxs-lookup"><span data-stu-id="762be-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="762be-139">整數值，指定儲存訊息之緩衝區的大小上限 (以位元組為單位)。在為此繫結設定的端點處理訊息時，可以將訊息儲存在緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="762be-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="762be-140">預設值為 65,536 位元組。</span><span class="sxs-lookup"><span data-stu-id="762be-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="762be-141">正整數，定義在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="762be-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="762be-142">如果對收件者而言訊息太大，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="762be-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="762be-143">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="762be-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="762be-144">預設為 65,536 個位元組。</span><span class="sxs-lookup"><span data-stu-id="762be-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="762be-145">定義用來對 SOAP 訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="762be-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="762be-146">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="762be-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="762be-147">-Text：使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="762be-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="762be-148">-Mtom：使用訊息傳輸組織機制1.0 （MTOM）編碼器。</span><span class="sxs-lookup"><span data-stu-id="762be-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="762be-149">預設值是 Text。</span><span class="sxs-lookup"><span data-stu-id="762be-149">The default is Text.</span></span> <span data-ttu-id="762be-150">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="762be-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="762be-151">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="762be-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="762be-152">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="762be-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="762be-153">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="762be-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="762be-154">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="762be-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="762be-155"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="762be-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="762be-156">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="762be-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="762be-157">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="762be-157">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="762be-158">包含 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="762be-158">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="762be-159">如果 `useSystemWebProxy` 設定為 `true`，則這個設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="762be-159">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="762be-160">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="762be-160">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="762be-161"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="762be-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="762be-162">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="762be-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="762be-163">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="762be-163">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="762be-164"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="762be-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="762be-165">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="762be-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="762be-166">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="762be-166">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="762be-167">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="762be-167">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="762be-168">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="762be-168">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="762be-169">-BigEndianUnicode： Unicode BigEndian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="762be-169">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="762be-170">-Unicode：16位編碼方式。</span><span class="sxs-lookup"><span data-stu-id="762be-170">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="762be-171">-UTF8：8位編碼</span><span class="sxs-lookup"><span data-stu-id="762be-171">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="762be-172">預設值為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="762be-172">The default is UTF8.</span></span> <span data-ttu-id="762be-173">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="762be-173">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="762be-174">有效的 <xref:System.ServiceModel.TransferMode> 值，指定進行要求或回應時，訊息是經過緩衝處理或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="762be-174">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="762be-175">布林值，指定是否應使用系統自動設定的 HTTP Proxy (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="762be-175">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="762be-176">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="762be-176">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="762be-177">子元素</span><span class="sxs-lookup"><span data-stu-id="762be-177">Child Elements</span></span>  
  
|<span data-ttu-id="762be-178">項目</span><span class="sxs-lookup"><span data-stu-id="762be-178">Element</span></span>|<span data-ttu-id="762be-179">描述</span><span class="sxs-lookup"><span data-stu-id="762be-179">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="762be-180">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="762be-180">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="762be-181">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="762be-181">Defines the security settings for the binding.</span></span> <span data-ttu-id="762be-182">此項目的型別為 <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="762be-182">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|<span data-ttu-id="762be-183">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="762be-183">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="762be-184">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="762be-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="762be-185">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="762be-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="762be-186">父項目</span><span class="sxs-lookup"><span data-stu-id="762be-186">Parent Elements</span></span>  
  
|<span data-ttu-id="762be-187">項目</span><span class="sxs-lookup"><span data-stu-id="762be-187">Element</span></span>|<span data-ttu-id="762be-188">描述</span><span class="sxs-lookup"><span data-stu-id="762be-188">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="762be-189">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="762be-189">\<bindings></span></span>](bindings.md)|<span data-ttu-id="762be-190">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="762be-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="762be-191">備註</span><span class="sxs-lookup"><span data-stu-id="762be-191">Remarks</span></span>  
 <span data-ttu-id="762be-192">NetHttpsBinding 使用 HTTPS 做為傳送訊息的傳輸。</span><span class="sxs-lookup"><span data-stu-id="762be-192">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="762be-193">與雙工合約搭配使用時，將會使用 Web 通訊端。</span><span class="sxs-lookup"><span data-stu-id="762be-193">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="762be-194">與要求-回覆合約搭配使用時，NetHttpsBinding 的行為就像具有二進位編碼器的 BasicHttpsBinding。</span><span class="sxs-lookup"><span data-stu-id="762be-194">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="762be-195">安全性預設是關閉的，但是可以將[\<安全性 >](security-of-basichttpbinding.md)子項目的 mode 屬性，設定為 `None`以外的值。</span><span class="sxs-lookup"><span data-stu-id="762be-195">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="762be-196">根據預設，它使用「文字」訊息編碼和 UTF-8 文字編碼。</span><span class="sxs-lookup"><span data-stu-id="762be-196">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="762be-197">範例</span><span class="sxs-lookup"><span data-stu-id="762be-197">Example</span></span>  
 <span data-ttu-id="762be-198">下列範例示範 <xref:System.ServiceModel.NetHttpBinding> 的使用方式，它利用第一代和第二代 Web 服務來提供 HTTPS 通訊和最大的互通性。</span><span class="sxs-lookup"><span data-stu-id="762be-198">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="762be-199">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="762be-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="762be-200">繫結型別是使用 `binding` 項目的 `<endpoint>` 屬性所指定的。</span><span class="sxs-lookup"><span data-stu-id="762be-200">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="762be-201">如果您要設定基本繫結，並變更其部分設定，則必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="762be-201">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="762be-202">端點必須使用 `bindingConfiguration` 項目的 `<endpoint>` 屬性來按照名稱參考繫結組態，如下列服務的組態程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="762be-202">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="762be-203">範例</span><span class="sxs-lookup"><span data-stu-id="762be-203">Example</span></span>  
 <span data-ttu-id="762be-204">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="762be-204">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="762be-205">從端點位址和系結中的名稱移除 bindingConfiguration，即可完成上一個範例中的功能。</span><span class="sxs-lookup"><span data-stu-id="762be-205">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="762be-206">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="762be-206">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762be-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="762be-207">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="762be-208">繫結</span><span class="sxs-lookup"><span data-stu-id="762be-208">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="762be-209">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="762be-209">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="762be-210">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="762be-210">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="762be-211">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="762be-211">\<binding></span></span>](bindings.md)
