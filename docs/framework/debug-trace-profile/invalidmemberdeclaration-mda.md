---
title: invalidMemberDeclaration MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 6033cd4178b2bc493794b5dcc527bc543ba24284
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216303"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
會啟動 `invalidMemberDeclaration` Managed 偵錯助理 (MDA) 來報告錯誤，這些錯誤發生在決定如何封送處理成員參數為由 COM 所呼叫時。  
  
## <a name="symptoms"></a>徵狀  
 失敗的 HRESULT 會傳回給 COM，而不呼叫 Managed 方法。  
  
## <a name="cause"></a>原因  
 最可能的原因是其中一個參數上不相容的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。  
  
## <a name="resolution"></a>解決方案  
 請在此參數上指定有效的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>輸出  
 告知性訊息，包含成員名稱、類型名稱和錯誤訊息。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [使用 Managed 偵錯助理診斷錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
