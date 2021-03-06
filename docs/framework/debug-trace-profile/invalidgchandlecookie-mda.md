---
title: invalidGCHandleCookie MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: c1d8fab863c34313c0cdb778136c6f69a64defeb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216313"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
當嘗試從無效的 `invalidGCHandleCookie` Cookie 轉換成 <xref:System.IntPtr> 時，就會啟動 <xref:System.Runtime.InteropServices.GCHandle> Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵狀  
 未定義的行為，例如嘗試使用或擷取 <xref:System.Runtime.InteropServices.GCHandle> 的 <xref:System.IntPtr> 時的存取違規與記憶體損毀。  
  
## <a name="cause"></a>原因  
 Cookie 可能無效，因為它原本不是從代表已經釋放之 <xref:System.Runtime.InteropServices.GCHandle> 的 <xref:System.Runtime.InteropServices.GCHandle> 中建立的，它是不同應用程式網域中之 <xref:System.Runtime.InteropServices.GCHandle> 的 Cookie，或曾封送處理到原生程式碼當成 <xref:System.Runtime.InteropServices.GCHandle>，但傳遞回 CLR 當成在其中嘗試轉型的 <xref:System.IntPtr>，。  
  
## <a name="resolution"></a>解決方案  
 為 <xref:System.IntPtr> 指定有效的 <xref:System.Runtime.InteropServices.GCHandle> Cookie。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 啟用此 MDA 時，偵錯工具即不再能夠追蹤回其物件的根，因為傳回的 Cookie 值和未啟用 MDA 時傳回的 Cookie 值不同。  
  
## <a name="output"></a>輸出  
 已報告無效的 <xref:System.IntPtr> Cookie 值。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [使用 Managed 偵錯助理診斷錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
