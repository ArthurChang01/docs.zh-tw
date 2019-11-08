---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736503"
---
# <a name="peertransport"></a>\<peerTransport >
定義自訂繫結的對等傳輸。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerTransport >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|listenIpAddress|字串，指定對等節點接聽 TCP 訊息的 IP 位址。 預設為 `null`。|  
|maxBufferPoolSize|正整數，指定緩衝集區的大小上限。 預設值為 524288。<br /><br /> WCF 有許多組件會使用緩衝區。 每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。 有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區， 因此可以避免建立及終結緩衝區的負荷。|  
|maxReceivedMessageSize|正整數，這個正整數會定義包含標頭之訊息的大小上限 (以位元組為單位)。 當對收件者而言訊息太大時，寄件者便會收到 SOAP 錯誤。 收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。 預設值為 65536。|  
|連接埠|整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。 這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。 預設值為 0。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security >](security-of-peertransport.md)|定義此傳輸的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding >](bindings.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 這個傳輸不可與具有要求/回覆作業的合約一起使用。  
  
## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [傳輸](../../../wcf/feature-details/transports.md)
- [選擇傳輸](../../../wcf/feature-details/choosing-a-transport.md)
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
