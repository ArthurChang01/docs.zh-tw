---
title: ICorDebugExceptionDebugEvent：： GetStackPointer 方法
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 688f5aec457298a43d95a35fdbc6e04e29a306a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084680"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>ICorDebugExceptionDebugEvent：： GetStackPointer 方法
取得這個例外狀況偵錯事件的堆疊指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a>參數  
 `pStackPointer`  
 [out] 這個例外狀況偵錯事件之堆疊指標的位址指標。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
 這個堆疊指標的意義取決於事件類型，如下表所示。  
  
|事件類型|`pStackPointer` 值的意義|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|擲回例外狀況之框架的堆疊指標。|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|最接近擲回例外狀況位置之使用者程式碼框架的堆疊指標。|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|包含 catch 處理常式之框架的堆疊指標。|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pStackPointer` 為 **null**。|  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
 事件種類可從[ICorDebugDebugEvent：： GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法取得。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugExceptionDebugEvent 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
