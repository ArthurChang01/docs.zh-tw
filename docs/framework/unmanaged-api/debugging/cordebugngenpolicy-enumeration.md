---
title: CorDebugNGenPolicy 列舉
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 826dfceb28512e4fd3157c432b7a4d94fba704fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097865"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy 列舉
提供用來判定偵錯工具是否從原生影像快取載入原生 (NGen) 影像的值。  
  
## <a name="syntax"></a>語法  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Members  
  
|成員名稱|描述|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|在 [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] 應用程式中，會停用本機原生映射快取中的影像。 在桌面應用程式中，這項設定沒有作用。|  
  
## <a name="remarks"></a>備註  
 [ICorDebugProcess5：： EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)方法會使用 `CorDebugNGENPolicy` 列舉。 停用本機原生映射快取中的影像，可以藉由確保偵錯工具載入可調試的 JIT 編譯影像，而不是優化的原生映射，來提供一致的偵測體驗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
