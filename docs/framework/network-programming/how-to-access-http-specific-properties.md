---
title: 如何：存取 HTTP 特定屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 68ad6b2c55cd5cc467e53441caa778ea10b994fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180857"
---
# <a name="how-to-access-http-specific-properties"></a>如何：存取 HTTP 特定屬性
這個範例示範如何關閉 HTTP **保持運作**行為，以及如何從 Web 伺服器取得通訊協定版本號碼。  
  
## <a name="example"></a>範例  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 對 **System.Net** 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- [通過代理訪問互聯網](accessing-the-internet-through-a-proxy.md)
- [使用應用程式通訊協定](using-application-protocols.md)
- [HTTP](http.md)
