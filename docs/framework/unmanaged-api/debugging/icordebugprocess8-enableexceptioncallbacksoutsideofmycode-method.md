---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: b6bfd258f35f19719be5e5169a1edc22a358371c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123382"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
[在 .NET Framework 4.6 和更新版本中支援]  
  
 啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>參數  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>備註  
 如果 `enableExceptionsOutsideOfJMC` 的值為 `false`：  
  
- DEBUG_EXCEPTION_FIRST_CHANCE 例外狀況不會導致偵錯工具的回呼。  
  
- 如果例外狀況絕對不會在使用者程式碼中進行轉義（也就是從例外狀況來源到例外狀況處理常式的路徑沒有標記為 JustMyCode 或 JMC 的方法），則 DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外狀況不會導致偵錯工具的回呼。  
  
 `enableExceptionsOutsideOfJMC` 的預設值為 `true`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess8 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
