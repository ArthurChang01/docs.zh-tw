---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f1aa68bcdda43fd77bee397c079695f7937faa52
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139477"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="0e6ed-101">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="0e6ed-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="0e6ed-102">為電腦上跨處理序通訊定義安全、可靠且經過最佳化的繫結。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="0e6ed-103">根據預設，這個繫結會產生一個執行階段通訊堆疊，並且具備 WS-ReliableMessaging (提供可靠性)、傳輸安全性、具名管道 (用於訊息傳遞) 和二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
<span data-ttu-id="0e6ed-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0e6ed-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0e6ed-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="0e6ed-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0e6ed-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="0e6ed-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0e6ed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="0e6ed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e6ed-108">語法</span><span class="sxs-lookup"><span data-stu-id="0e6ed-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e6ed-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0e6ed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0e6ed-110">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="0e6ed-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e6ed-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0e6ed-111">Attributes</span></span>  
  
|<span data-ttu-id="0e6ed-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0e6ed-112">Attribute</span></span>|<span data-ttu-id="0e6ed-113">描述</span><span class="sxs-lookup"><span data-stu-id="0e6ed-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e6ed-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="0e6ed-114">closeTimeout</span></span>|<span data-ttu-id="0e6ed-115"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0e6ed-116">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e6ed-117">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0e6ed-118">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="0e6ed-118">hostNameComparisonMode</span></span>|<span data-ttu-id="0e6ed-119">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0e6ed-120">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-120">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0e6ed-121">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-121">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="0e6ed-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0e6ed-122">maxBufferPoolSize</span></span>|<span data-ttu-id="0e6ed-123">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="0e6ed-124">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="0e6ed-125">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="0e6ed-126">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="0e6ed-127">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="0e6ed-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="0e6ed-128">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="0e6ed-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="0e6ed-129">maxBufferSize</span></span>|<span data-ttu-id="0e6ed-130">正整數，指定記憶體中用來儲存訊息的緩衝區大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="0e6ed-131">如果緩衝區已滿，超過的資料會保留在基礎通訊端中，直到緩衝區再度有空間為止。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="0e6ed-132">這個值不能小於 `maxReceivedMessageSize` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="0e6ed-133">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-133">The default is 65536.</span></span> <span data-ttu-id="0e6ed-134">如需詳細資訊，請參閱<xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="0e6ed-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="0e6ed-135">maxConnections</span></span>|<span data-ttu-id="0e6ed-136">整數，指定服務建立/接受的傳出和傳入連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="0e6ed-137">傳入和傳出連線是依據此屬性指定的個別限制來計算的。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="0e6ed-138">超過限制的傳入連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="0e6ed-139">超過限制的傳出連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="0e6ed-140">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-140">The default is 10.</span></span>|  
|<span data-ttu-id="0e6ed-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="0e6ed-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="0e6ed-142">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0e6ed-143">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="0e6ed-144">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0e6ed-145">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-145">The default is 65536.</span></span>|  
|<span data-ttu-id="0e6ed-146">NAME</span><span class="sxs-lookup"><span data-stu-id="0e6ed-146">name</span></span>|<span data-ttu-id="0e6ed-147">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0e6ed-148">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0e6ed-149">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0e6ed-150">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="0e6ed-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="0e6ed-151">openTimeout</span></span>|<span data-ttu-id="0e6ed-152"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0e6ed-153">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e6ed-154">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0e6ed-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="0e6ed-155">receiveTimeout</span></span>|<span data-ttu-id="0e6ed-156"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0e6ed-157">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e6ed-158">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="0e6ed-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="0e6ed-159">sendTimeout</span></span>|<span data-ttu-id="0e6ed-160"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0e6ed-161">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e6ed-162">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0e6ed-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="0e6ed-163">transactionFlow</span></span>|<span data-ttu-id="0e6ed-164">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="0e6ed-165">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-165">The default is `false`.</span></span>|  
|<span data-ttu-id="0e6ed-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="0e6ed-166">transactionProtocol</span></span>|<span data-ttu-id="0e6ed-167">指定要搭配此繫結程序使用的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="0e6ed-168">有效值為</span><span class="sxs-lookup"><span data-stu-id="0e6ed-168">Valid values are</span></span><br /><br /> <span data-ttu-id="0e6ed-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="0e6ed-169">-   OleTransactions</span></span><br /><span data-ttu-id="0e6ed-170">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="0e6ed-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="0e6ed-171">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-171">The default is OleTransactions.</span></span> <span data-ttu-id="0e6ed-172">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="0e6ed-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="0e6ed-173">transferMode</span></span>|<span data-ttu-id="0e6ed-174"><xref:System.ServiceModel.TransferMode> 值，指定訊息要經過緩衝處理或資料流處理，或為要求或回應。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e6ed-175">子項目</span><span class="sxs-lookup"><span data-stu-id="0e6ed-175">Child Elements</span></span>  
  
|<span data-ttu-id="0e6ed-176">項目</span><span class="sxs-lookup"><span data-stu-id="0e6ed-176">Element</span></span>|<span data-ttu-id="0e6ed-177">描述</span><span class="sxs-lookup"><span data-stu-id="0e6ed-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e6ed-178">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="0e6ed-178">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="0e6ed-179">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="0e6ed-180">此項目的型別為 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="0e6ed-181">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0e6ed-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="0e6ed-182">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0e6ed-183">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e6ed-184">父項目</span><span class="sxs-lookup"><span data-stu-id="0e6ed-184">Parent Elements</span></span>  
  
|<span data-ttu-id="0e6ed-185">項目</span><span class="sxs-lookup"><span data-stu-id="0e6ed-185">Element</span></span>|<span data-ttu-id="0e6ed-186">描述</span><span class="sxs-lookup"><span data-stu-id="0e6ed-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e6ed-187">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="0e6ed-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0e6ed-188">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e6ed-189">備註</span><span class="sxs-lookup"><span data-stu-id="0e6ed-189">Remarks</span></span>  
 <span data-ttu-id="0e6ed-190">根據預設，`NetNamedPipeBinding` 會產生執行階段通訊堆疊，此堆疊使用傳輸安全性、具名管道 (用於訊息傳遞) 和二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="0e6ed-191">此繫結為適當的 Windows Communication Foundation (WCF) 系統提供的現成選擇，可用於電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="0e6ed-192">它也支援交易。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="0e6ed-193">`NetNamedPipeBinding` 的預設組態類似於 `NetTcpBinding` 所提供的組態，但較為簡單，因為 WCF 實作只針對電腦應用，所以公開的功能不多。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="0e6ed-194">最顯著的差異在於，`securityMode` 設定只提供 `None` 和 `Transport` 選項。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="0e6ed-195">SOAP 安全性支援並非包含的選項。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="0e6ed-196">安全性行為可以使用選擇性的 `securityMode` 屬性進行設定。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e6ed-197">範例</span><span class="sxs-lookup"><span data-stu-id="0e6ed-197">Example</span></span>  
 <span data-ttu-id="0e6ed-198">下列範例示範 netNamedPipeBinding 繫結，這會在相同電腦上提供跨處理序通訊。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="0e6ed-199">具名通道不會跨電腦作業。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="0e6ed-200">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="0e6ed-201">繫結型別是在 `binding` 項目的 `<endpoint>` 屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="0e6ed-202">如果您要設定 netNamedPipeBinding 繫結，並變更其部分設定，則您必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="0e6ed-203">端點必須使用 `bindingConfiguration` 屬性，按照名稱參考繫結組態。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="0e6ed-204">在這個範例中，繫結組態的名稱為 Binding1。</span><span class="sxs-lookup"><span data-stu-id="0e6ed-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="0e6ed-205">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e6ed-205">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="0e6ed-206">\<binding ></span><span class="sxs-lookup"><span data-stu-id="0e6ed-206">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="0e6ed-207">繫結</span><span class="sxs-lookup"><span data-stu-id="0e6ed-207">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0e6ed-208">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="0e6ed-208">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0e6ed-209">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="0e6ed-209">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
