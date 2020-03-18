---
title: 輪詢非同步作業的狀態
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: ff9cefc73adfe1ece1bf7545c75ccb6cc618e89f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123967"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>輪詢非同步作業的狀態
可等待非同步作業的結果而執行其他工作的應用程式不應封鎖等待，直到作業完成為止。 使用下列其中一個選項，在等候非同步作業完成時繼續執行指示：  
  
- <xref:System.IAsyncResult.IsCompleted%2A>使用非同步作業的<xref:System.IAsyncResult>**"開始**_操作名稱_"方法返回的屬性來確定操作是否已完成。 此方法稱為輪詢且會在本主題中示範。  
  
- 使用 <xref:System.AsyncCallback> 委派以處理不同執行緒中非同步作業的結果。 如需示範此方法的範例，請參閱[使用 AsyncCallback 委派結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## <a name="example"></a>範例  
 下列範例示範在 <xref:System.Net.Dns> 類別中使用非同步方法，以擷取使用者指定電腦的網域名稱系統資訊。 此範例會啟動非同步作業，然後在主控台中列印句點 (".")，直到作業完成為止。 請注意，因為使用此方式時並不需要 <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> 與 <xref:System.Object> 參數，所以已為這些引數傳遞 **null** (在 Visual Basic 中為 **Nothing**)。  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
