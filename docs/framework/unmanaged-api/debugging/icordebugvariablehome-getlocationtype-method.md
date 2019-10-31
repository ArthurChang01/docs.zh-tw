---
title: ICorDebugVariableHome：： GetLocationType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 1dd4e9510831b4c878e9c1246dabe4add919130c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125104"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="7a370-102">ICorDebugVariableHome：： GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="7a370-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="7a370-103">取得變數原生位置的類型。</span><span class="sxs-lookup"><span data-stu-id="7a370-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a370-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a370-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a370-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a370-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="7a370-106">脫銷變數原生位置之類型的指標。</span><span class="sxs-lookup"><span data-stu-id="7a370-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="7a370-107">如需詳細資訊，請參閱[VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="7a370-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a370-108">需求</span><span class="sxs-lookup"><span data-stu-id="7a370-108">Requirements</span></span>  
 <span data-ttu-id="7a370-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a370-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a370-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a370-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a370-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a370-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a370-112">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a370-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a370-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a370-113">See also</span></span>

- [<span data-ttu-id="7a370-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="7a370-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="7a370-115">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="7a370-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
