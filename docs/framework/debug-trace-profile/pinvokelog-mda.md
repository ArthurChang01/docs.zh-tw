---
title: pInvokeLog MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: 12d7f60bcaedc5a97a7718610f40188547f87050
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216121"
---
# <a name="pinvokelog-mda"></a>pInvokeLog MDA
針對執行期間所使用的每個唯一平台叫用簽章，啟用 `pInvokeLog` Managed 偵錯助理 (MDA)。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>輸出  
 指出在執行期間使用平台叫用簽章的訊息。  
  
## <a name="configuration"></a>組態  
 每個 match 項目都會篩選要對其進行平台叫用呼叫的 .dll 檔案。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- [使用 Managed 偵錯助理診斷錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [使用 Unmanaged DLL 函式](../interop/consuming-unmanaged-dll-functions.md)
