---
title: ICorDebugVariableHome：： GetSlotIndex 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 542bfa05c55ef224d1b9111f9af6c069e9e23542
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790976"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome：： GetSlotIndex 方法
取得本機變數的 managed 位置索引。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>參數  
 `pSlotIndex`  
 脫銷本機變數位置索引的指標。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回下列值。  
  
|{2&gt;值&lt;2}|描述|  
|-----------|-----------------|  
|`S_OK`|方法呼叫會在 `pSlotIndex`中傳回位置索引值。|  
|`E_FAIL`|目前的[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例代表函式引數。|  
  
## <a name="remarks"></a>備註  
 位置索引可以用來抓取此區域變數的中繼資料。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugVariableHome 介面](icordebugvariablehome-interface.md)
