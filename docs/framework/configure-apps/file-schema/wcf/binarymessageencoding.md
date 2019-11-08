---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: afe0479d9cbf6d754b309c18e23d3a479870177c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739079"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="17c0b-101">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="17c0b-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="17c0b-102">定義二進位訊息編碼器，以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="17c0b-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
<span data-ttu-id="17c0b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="17c0b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="17c0b-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="17c0b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="17c0b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="17c0b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="17c0b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="17c0b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="17c0b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="17c0b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="17c0b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<binaryMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="17c0b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17c0b-109">語法</span><span class="sxs-lookup"><span data-stu-id="17c0b-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17c0b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="17c0b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="17c0b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="17c0b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17c0b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="17c0b-112">Attributes</span></span>  
  
|<span data-ttu-id="17c0b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="17c0b-113">Attribute</span></span>|<span data-ttu-id="17c0b-114">描述</span><span class="sxs-lookup"><span data-stu-id="17c0b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17c0b-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="17c0b-115">maxReadPoolSize</span></span>|<span data-ttu-id="17c0b-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="17c0b-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="17c0b-117">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="17c0b-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="17c0b-118">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="17c0b-118">The default is 64.</span></span>|  
|<span data-ttu-id="17c0b-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="17c0b-119">maxSessionSize</span></span>|<span data-ttu-id="17c0b-120">正整數，設定用於編碼的緩衝區大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="17c0b-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="17c0b-121">較大的緩衝區會增加編碼速度，但是會犧牲工作集的大小。</span><span class="sxs-lookup"><span data-stu-id="17c0b-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="17c0b-122">預設值為 2048。</span><span class="sxs-lookup"><span data-stu-id="17c0b-122">The default is 2048.</span></span>|  
|<span data-ttu-id="17c0b-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="17c0b-123">maxWritePoolSize</span></span>|<span data-ttu-id="17c0b-124">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="17c0b-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="17c0b-125">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="17c0b-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="17c0b-126">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="17c0b-126">The default is 16.</span></span>|  
|<span data-ttu-id="17c0b-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="17c0b-127">messageVersion</span></span>|<span data-ttu-id="17c0b-128">指定已使用或必須使用的 SOAP 訊息和 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="17c0b-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17c0b-129">子項目</span><span class="sxs-lookup"><span data-stu-id="17c0b-129">Child Elements</span></span>  
  
|<span data-ttu-id="17c0b-130">項目</span><span class="sxs-lookup"><span data-stu-id="17c0b-130">Element</span></span>|<span data-ttu-id="17c0b-131">描述</span><span class="sxs-lookup"><span data-stu-id="17c0b-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17c0b-132">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17c0b-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="17c0b-133">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="17c0b-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="17c0b-134">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="17c0b-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17c0b-135">父項目</span><span class="sxs-lookup"><span data-stu-id="17c0b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="17c0b-136">項目</span><span class="sxs-lookup"><span data-stu-id="17c0b-136">Element</span></span>|<span data-ttu-id="17c0b-137">描述</span><span class="sxs-lookup"><span data-stu-id="17c0b-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17c0b-138">\<binding ></span><span class="sxs-lookup"><span data-stu-id="17c0b-138">\<binding></span></span>](bindings.md)|<span data-ttu-id="17c0b-139">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="17c0b-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17c0b-140">備註</span><span class="sxs-lookup"><span data-stu-id="17c0b-140">Remarks</span></span>  
 <span data-ttu-id="17c0b-141">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="17c0b-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="17c0b-142">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="17c0b-142">Decoding is the reverse process.</span></span> <span data-ttu-id="17c0b-143">Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="17c0b-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="17c0b-144">`binaryMessageEncoding` 項目會指定 XML 的 .NET 二進位格式，並且提供指定字元編碼以及要使用之 SOAP 和 WS-Addressing 版本的選項。</span><span class="sxs-lookup"><span data-stu-id="17c0b-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="17c0b-145">二進位訊息編碼器會以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="17c0b-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="17c0b-146">雖然這個編碼會讓訊息傳輸速度非常快，但是會失去以 WS-\* 標準為基礎的互通性 (Interoperability)。</span><span class="sxs-lookup"><span data-stu-id="17c0b-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17c0b-147">範例</span><span class="sxs-lookup"><span data-stu-id="17c0b-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="17c0b-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="17c0b-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="17c0b-149">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="17c0b-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="17c0b-150">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="17c0b-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="17c0b-151">繫結</span><span class="sxs-lookup"><span data-stu-id="17c0b-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="17c0b-152">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="17c0b-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="17c0b-153">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="17c0b-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="17c0b-154">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="17c0b-154">\<customBinding></span></span>](custombinding.md)
